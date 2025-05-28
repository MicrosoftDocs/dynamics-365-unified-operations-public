---
title: Devirtualize Company Data
description: Learn about
author: ttreen
ms.author: ttreen
ms.date: 05/30/2025
ms.topic: how-to
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.form: 2022-04-08
---

# Devirtualize Company Data

[!INCLUDE[banner](../includes/banner.md)]

This document outlines the process for devirtualizing company data in Microsoft Dynamics AX 2012 in preparation for upgrading to Microsoft Dynamics 365 Finance and Operations.

## Background

Virtual company accounts have been deprecated in Microsoft Dynamics 365 Finance and Operations. Learn more in:

- [Deprecated features - Virtual company accounts](/dynamics365/fin-ops-core/dev-itpro/migration-upgrade/deprecated-features#virtual-company-accounts)
- [Cross-company data sharing (replacement for virtual companies)](/dynamics365/fin-ops-core/dev-itpro/sysadmin/cross-company-data-sharing)
- [Virtual company setup in AX 2012](/dynamicsax-2012/appuser-itpro/virtual-company-accounts-in-microsoft-dynamics-ax)

## How Virtual Companies Worked in AX 2012

To see how virtual company accounts affect the upgrade, first learn how they work in AX 2012.

Company data uses the `DataAreaId` field for tables with the **Save Data Per Company** property enabled. Here’s an example:

- There are three companies: CMP1, CMP2, and CMP3.

- A virtual company account named `VIR` is created.

- Companies CMP2 and CMP3 are assigned to `VIR`, along with a table collection containing `CustGroup` and `VendGroup`.

In this configuration:

| Company   | DataAreaId |
|-----------|------------|
| CMP1      | CMP1       |
| CMP2      | VIR        |
| CMP3      | VIR        |

For CMP2 and CMP3, data is stored under the `VIR` `DataAreaId`, so their records are shared.

### SQL Behavior in AX 2012 vs. Dynamics 365

When a SQL query runs, the AX 2012 kernel swaps the actual company ID for the virtual ID in the WHERE clause. This lets the data return from the tables. See the following SQL SELECT examples:

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

In Dynamics 365, this translation doesn’t happen. The query for CMP2 is:

Dynamics 365 Query: CMP2

```SQL
SELECT   T1.CUSTGROUP, T1.NAME, T1. TAXGROUPID, T1.DATAAREAID, T1.PARTITION
FROM CUSTGROUP T1
WHERE T1.DATAAREAID = 'CMP2'
AND T1.PARTITION = 5637144576
```

Because there aren’t any records with DataAreaId = 'CMP2', the query returns nothing. This means data is missing after the upgrade unless you devirtualize the data first.

## Devirtualizing Data

Devirtualizing data is complex and depends on the original virtual company setup. If you're unfamiliar with the concepts or tools involved, consider working with a qualified professional.

The following steps are general guidance—not a complete, end-to-end solution. The exact process can differ based on your table collection setup, including the structure, relationships, and data volume, which can vary between implementations.

> [!IMPORTANT]
> Always back up your data before you start. Test thoroughly after devirtualization to confirm data integrity.

### Step 1: Determine the virtual company setup

Review the virtual company configuration:

- Use the AOT to identify tables in table collections.

- Use the Virtual Company form to determine which companies are linked to which collections.

### Step 2: Relationships to RecId

For each identified table, check if it has a foreign key referencing the **RecId** of the virtualized table.  

For example, if `CustomsTariffCodeTable_IN` was virtualized, use the [AX 2012 Cross-reference Tool](/previous-versions/dynamicsax-2012/developer/cross-reference-tool?redirectedfrom=MSDN) to find related tables.  

You notice that `TaxData` has the following relation:  
**TaxData.CustomsTariffCodeTable_IN = CustomsTariffCodeTable_IN.RecId**

This relationship indicates that `TaxData` references the `RecId` of the virtualized table.

### Step 3: Hidden Relationships

In addition to direct table relations defined in the AOT, there may also be references based on **table IDs**. These references typically use a pair of fields like `RefTableId` and `RefRecId`, though the exact field names can vary. The combination of a table ID and a RecId establishes the relationship.

The following SQL query helps you find such tables and returns only tables that have records:

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
> This script finds most references, but check the results against any system customizations or changes.
>
> After you run the query, check if any of the returned tables reference tables in the virtual company setup. Get the table IDs from the AOT. Track any tables that reference virtualized tables.

### Step 4: Other Fields

Check the data in the virtualized tables for any extra fields that can reference the **virtual company ID**.

For example, in the `CUSTQUOTATIONTRANS` table, there's a field named `COMPANY`. If the values in this field match the virtual company ID, document this match and include it in the devirtualization process.

These references aren't always part of formal table relationships but can affect how you interpret data, so handle them carefully.

### Step 5: Copy and create records

Use the following script to copy data from the virtual company to individual legal entities.

Change the following values:

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

After you devirtualize the data in a table, update any related table references that point to it. As noted earlier, these are often fields like `RefRecId`, but the field names can vary.

To keep referential integrity, update these related fields with the **new RecId** values, using the corresponding `OLDRECID` from the devirtualized table as a reference.

See the example in the following script.

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

After the data was successfully devirtualized, you can remove the original records associated with the virtual company. This cleanup must be performed using SQL.

The following example shows how to delete these records.

```SQL
--Edit TABLE and PARTITIONKEY as needed. 
DELETE FROM TABLE
WHERE DATAAREAID = 'vir'
AND PARTITION = (SELECT RECID FROM PARTITIONS WHERE PARTITIONKEY = 'initial')
```

If you didn't comment out the part of the devirtualization script that creates an index on OLDRECID, drop that index after cleanup to avoid leaving unnecessary objects in the database.

> [!IMPORTANT]
>
> Always check the records before you delete them to prevent unintended data loss.

### Step 8: Clean up virtualized companies

Finally, delete virtual company definitions using the AX 2012 Virtual Company setup form.

See: /previous-versions/dynamicsax-2012/appuser-itpro/virtual-company-accounts-in-microsoft-dynamics-ax#delete-a-virtual-company-account

> [!NOTE]
> While this guide assumes devirtualization in AX 2012, you can devirtualize after restoring the AX database as AXDB in a Cloud Hosted Environment (CHE), or in the Sandbox just before you start the upgrade (Step 10 of the Data Migration Toolkit).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
