---
title: Devirtualize Company Data
description: Learn about
author: ttreen
ms.author: ttreen
ms.date: 05/23/2022
ms.topic: how-to
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.form: 2022-04-08
---

# Devirtualize Company Data

[!INCLUDE[banner](../includes/banner.md)]

This document outlines the process for devirtualizing company data in Microsoft Dynamics AX 2012 in preparation for upgrading to Microsoft Dynamics 365 Finance and Operations.

## Background

Virtual company accounts have been deprecated in Microsoft Dynamics 365 Finance and Operations. See the following for more information:

- [Deprecated features - Virtual company accounts](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/migration-upgrade/deprecated-features#virtual-company-accounts)
- [Cross-company data sharing (replacement for virtual companies)](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/sysadmin/cross-company-data-sharing)
- [Virtual company setup in AX 2012](https://learn.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/virtual-company-accounts-in-microsoft-dynamics-ax)

## How Virtual Companies Worked in AX 2012

To understand how virtual company accounts impact the upgrade, it’s important to first understand their behavior in AX 2012.

Company data is organized using the `DataAreaId` field for tables with the property **Save Data Per Company** enabled. Consider the following scenario:

- Three companies exist: CMP1, CMP2, and CMP3.
- A virtual company account named `VIR` is created.
- Companies CMP2 and CMP3 are assigned to `VIR`, along with a table collection containing `CustGroup` and `VendGroup`.

In this configuration:

| Company | DataAreaId |
|---------|------------|
| CMP1    | CMP1       |
| CMP2    | VIR        |
| CMP3    | VIR        |

For CMP2 and CMP3, the data is stored under the `VIR` `DataAreaId`, meaning their records are shared.

### SQL Behavior in AX 2012 vs. D365

When a SQL query is generated, the AX 2012 kernel would exchange, in the WHERE clause, the actual company ID to the virtual ID, so the data could be returned from the tables, see the following SQL SELECT examples:

Company: CMP1
```SQL
SELECT   T1.CUSTGROUP, T1.NAME, T1.CREDITMAX, T1.BLOCKED, T1.DATAAREAID, T1.PARTITION
FROM CUSTGROUP T1
WHERE T1.DATAAREAID = 'CMP1'
AND T1.PARTITION = 5637144576
```
Companies: CMP2, CMP3
```SQL
SELECT   T1.CUSTGROUP, T1.NAME, T1. TAXGROUPID, T1.DATAAREAID, T1.PARTITION
FROM CUSTGROUP T1
WHERE T1.DATAAREAID = 'VIR'
AND T1.PARTITION = 5637144576
```
In D365, this translation does not occur. The query for CMP2 would be:
D365 Query: CMP2
```SQL
SELECT   T1.CUSTGROUP, T1.NAME, T1. TAXGROUPID, T1.DATAAREAID, T1.PARTITION
FROM CUSTGROUP T1
WHERE T1.DATAAREAID = 'CMP2'
AND T1.PARTITION = 5637144576
```
Since there are no records with DataAreaId = 'CMP2', the query returns nothing. This results in missing data post-upgrade unless the data is devirtualized beforehand.

## Devirtualizing Data
Devirtualizing data is complex and depends heavily on the original virtual company setup. If you are unfamiliar with the concepts or tooling involved, we strongly recommend involving a qualified professional.
The steps below are intended as general guidance—not a complete, end-to-end solution. The exact process may differ based on your specific table-collection setup, including the structure, relationships, and volume of your data, which can vary significantly between implementations.
> [!IMPORTANT]
> Always back up your data before starting. Perform thorough testing after devirtualization to confirm data integrity.

### Step 1: Determine the virtual company setup
Review the virtual company configuration:
- Use the AOT to identify tables in table collections.
- Use the Virtual Company form to determine which companies are linked to which collections.

### Step 2: Relationships to RecId
For each identified table, check if it has a foreign key referencing the **RecId** of the virtualized table.  
For example, if `CustomsTariffCodeTable_IN` was virtualized, use the [AX 2012 Cross-reference Tool](https://learn.microsoft.com/en-us/previous-versions/dynamicsax-2012/developer/cross-reference-tool?redirectedfrom=MSDN) to find related tables.  

You'll see that `TaxData` has the following relation:  
**TaxData.CustomsTariffCodeTable_IN = CustomsTariffCodeTable_IN.RecId**

This indicates that `TaxData` references the `RecId` of the virtualized table.

### Step 3: Hidden Relationships
In addition to direct table relations defined in the AOT, there may also be references based on **table IDs**. These typically use a pair of fields like `RefTableId` and `RefRecId`, though the exact field names can vary. The combination of a table ID and a RecId establishes the relationship.

The following SQL query helps identify such tables, returning only those that contain records:

```sql
SELECT T1.TABLE_NAME, T1.COLUMN_NAME, T2.COLUMN_NAME
FROM INFORMATION_SCHEMA.COLUMNS T1
JOIN INFORMATION_SCHEMA.COLUMNS T2
    ON T1.TABLE_NAME = T2.TABLE_NAME
JOIN sys.tables st
    ON st.name = T1.TABLE_NAME
JOIN sys.partitions sp
    ON st.object_id = sp.object_id
WHERE T1.COLUMN_NAME LIKE '%RefTableId%'
  AND T2.COLUMN_NAME LIKE '%RefRecId%'
  AND sp.index_id IN (0, 1)  -- 0 = heap, 1 = clustered index
  AND sp.rows > 0            -- Only return tables with data
GROUP BY T1.TABLE_NAME, T1.COLUMN_NAME, T2.COLUMN_NAME
ORDER BY T1.TABLE_NAME;
```
> [!NOTE]
>
> This script should identify most references, but be sure to validate results against any system customizations or changes.
>
> After running the query, check whether any of the returned tables reference those involved in the virtual company setup. You can retrieve the necessary table IDs from the AOT. Be sure to track any tables that contain references to virtualized tables.

### Step 4: Other Fields
You’ll also need to examine the data within the virtualized tables for any additional fields that may reference the **virtual company ID**.  

For example, in the `CUSTQUOTATIONTRANS` table, there is a field named `COMPANY`. If the values in this field correspond to the virtual company ID, you’ll need to document this and account for it during the devirtualization process.  

These references may not be part of formal table relationships but can still affect how data is interpreted, so they must be handled carefully.

### Step 5: Copying and creating records
Use the script below to duplicate data from the virtual company to individual legal entities:

Make sure to change:
- @TableName
- @VirtualCompany
- @CompanyList

```
-- Edit following three values as needed
DECLARE @TableName NVARCHAR(128) = 'CUSTGROUP'; -- Your table name
DECLARE @VirtualCompany NVARCHAR(10) = 'vir'; -- Virtual company (e.g., 'vir')
DECLARE @CompanyList NVARCHAR(MAX) = ' cmp2, cmp3'; -- List of companies to insert records for

-- Script Start
DECLARE @ColumnList NVARCHAR(MAX);
DECLARE @MaxRecId BIGINT;
DECLARE @SQL NVARCHAR(MAX);
DECLARE @Company NVARCHAR(50);
DECLARE @CurrentMaxRecId BIGINT;
DECLARE @xml XML;
DECLARE @IndexName NVARCHAR(128);
DECLARE @TabId INT;
DECLARE @NextVal BIGINT;
DECLARE @NewMaxRecId BIGINT;

SET @IndexName = 'DEVIRTUALIZEIDX_' + @TableName;

IF NOT EXISTS (SELECT 1 FROM INFORMATION_SCHEMA.COLUMNS 
               WHERE TABLE_NAME = @TableName AND COLUMN_NAME = 'OLDRECID')
BEGIN
    SET @SQL = 'ALTER TABLE ' + QUOTENAME(@TableName) + ' ADD OLDRECID BIGINT;';
    EXEC sp_executesql @SQL;
END

SELECT @ColumnList = STUFF((SELECT ', ' + COLUMN_NAME
                            FROM INFORMATION_SCHEMA.COLUMNS
                            WHERE TABLE_NAME = @TableName
                            AND COLUMN_NAME NOT IN ('DATAAREAID', 'RECID', 'OLDRECID')
                            FOR XML PATH('')), 1, 2, '');

SET @CompanyList = REPLACE(@CompanyList, ' ', '');
SET @xml = (SELECT CAST('<cr>' + REPLACE(@CompanyList, ',', '</cr><cr>') + '</cr>' AS XML) AS STRING);

DECLARE CompanyCursor CURSOR FOR 
    SELECT t.value('.', 'varchar(max)') AS COMPANYLIST FROM @xml.nodes('//cr') AS a(t);

OPEN CompanyCursor;
FETCH NEXT FROM CompanyCursor INTO @Company;

WHILE @@FETCH_STATUS = 0
BEGIN
    SET @SQL = 'SELECT @MaxRecId = MAX(RECID) FROM ' + QUOTENAME(@TableName) + ';';
    EXEC sp_executesql @SQL, N'@MaxRecId BIGINT OUTPUT', @MaxRecId OUTPUT;

    SET @SQL = 'INSERT INTO ' + QUOTENAME(@TableName) + ' (' + @ColumnList + ', DATAAREAID, RECID, OLDRECID) ' + 
               'SELECT ' +  @ColumnList + ', ''' + @Company + ''', ' +
               'ROW_NUMBER() OVER (ORDER BY RECID) + ' + CAST(@MaxRecId AS NVARCHAR) + ', ' +
               'RECID ' + -- Populate OldRecId with the existing RecId
               'FROM ' + QUOTENAME(@TableName) + ' ' +
               'WHERE DATAAREAID = ''' +  @VirtualCompany + ''';';
    EXEC sp_executesql @SQL, N'@VirtualCompany NVARCHAR(10)', @VirtualCompany;

    FETCH NEXT FROM CompanyCursor INTO @Company;
END;

CLOSE CompanyCursor;
DEALLOCATE CompanyCursor;

-- Optional - add in an index for field OLDRECID, used when updating foreign relations. 
-- Comment out if not required
IF NOT EXISTS (SELECT 1 FROM sys.indexes WHERE name = @IndexName AND object_id = OBJECT_ID(@TableName))
BEGIN
    SET @SQL = 'CREATE INDEX ' + QUOTENAME(@IndexName) + ' ON ' + QUOTENAME(@TableName) + ' (OLDRECID, RECID, DATAAREAID);';
    EXEC sp_executesql @SQL;
END
-- End of OLDRECID index section

-- Update SYSTEMSEQUENCES
SELECT @TabId = TABLEID FROM SQLDICTIONARY 
WHERE SQLNAME = @TableName AND FIELDID = 0 AND ARRAY = 0;

SET @SQL = 'SELECT @NewMaxRecId = ISNULL(MAX(RECID), 0) FROM ' + QUOTENAME(@TableName) + ';';
EXEC sp_executesql @SQL, N'@NewMaxRecId BIGINT OUTPUT', @NewMaxRecId OUTPUT;

SELECT @NextVal = NEXTVAL FROM SYSTEMSEQUENCES 
WHERE TABID = @TabId;

IF @NextVal IS NOT NULL AND @NextVal < @NewMaxRecId + 1
BEGIN
    UPDATE SYSTEMSEQUENCES 
    SET NEXTVAL = @NewMaxRecId + 1 
    WHERE TABID = @TabId;
END
-- End Of Script
```

### Step 6: Update relationships
Once you’ve devirtualized the data in a table, you’ll need to update any related table references that point to it. As noted earlier, these are often fields like `RefRecId`, but the exact field names may vary.

To maintain referential integrity, you must update these related fields with the **new RecId** values—using the corresponding `OLDRECID` from the devirtualized table as a reference.

See the example script below for how this can be done:
```SQL
UPDATE T2
SET T2.REFRECID = T1.RECID
FROM TABLE2 AS T2
JOIN TABLE1 AS T1
    ON T1.OLDRECID = T2.REFRECID
    AND T1.DATAAREAID = T2.DATAAREAID
    AND T1.PARTITION = T2.PARTITION
WHERE T2.DATAAREAID IN ('cmp1', 'cmp2')
```


### Step 7: Remove virtualized records
After the data has been successfully devirtualized, you can remove the original records associated with the virtual company. This cleanup must be performed using SQL.

The example below shows how to delete these records:
```SQL
--Edit TABLE and PARTITIONKEY as needed. 
DELETE FROM TABLE
WHERE DATAAREAID = 'vir'
AND PARTITION = (SELECT RECID FROM PARTITIONS WHERE PARTITIONKEY = 'initial')
```

Additionally, if you didn’t comment out the part of the devirtualization script that creates an index on OLDRECID, you’ll need to drop that index after cleanup to avoid leaving unnecessary objects in the database.

> [!IMPORTANT]
>
> Always validate the records before deletion to prevent unintended data loss.

### Step 8: Clean up virtualized companies
inally, delete virtual company definitions via the AX 2012 Virtual Company setup form.
See: https://learn.microsoft.com/en-us/previous-versions/dynamicsax-2012/appuser-itpro/virtual-company-accounts-in-microsoft-dynamics-ax#delete-a-virtual-company-account

> [!NOTE]
> While this guide assumes devirtualization in AX 2012, you could choose to devirtualize after restoring the AX database as AXDB in a Cloud Hosted Environment (CHE), or in the Sandbox just before triggering the upgrade (Step 10 of the Data Migration Toolkit).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
