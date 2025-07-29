---
title: Devirtualize company data
description: Learn how to devirtualize company data in Microsoft Dynamics AX 2012 in preparation for an upgrade to Dynamics 365 finance and operations apps.
author: ttreen
ms.author: ttreen
ms.date: 05/30/2025
ms.topic: how-to
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.form: 2022-04-08
---

# Devirtualize company data

[!INCLUDE[banner](../includes/banner.md)]

This article outlines the process for devirtualizing company data in Microsoft Dynamics AX 2012 in preparation for an upgrade to Dynamics 365 finance and operations apps.

> [!IMPORTANT]
> Devirtualizing data isn't a process that's supported by Microsoft Support. The information provided in this document is intended solely for informational and guidance purposes.


## Background

Virtual company accounts were deprecated in finance and operations apps. The virtual companies feature was replaced by cross-company data sharing. Learn more:

- [Virtual company accounts](/dynamics365/fin-ops-core/dev-itpro/migration-upgrade/deprecated-features#virtual-company-accounts)
- [Cross-company data sharing](/dynamics365/fin-ops-core/dev-itpro/sysadmin/cross-company-data-sharing)
- [Virtual company setup in AX 2012](/dynamicsax-2012/appuser-itpro/virtual-company-accounts-in-microsoft-dynamics-ax)

## How virtual companies work in AX 2012

To understand how virtual company accounts affect an upgrade, you must first learn how they work in AX 2012.

Company data uses the `DataAreaId` field for tables where the **Save Data Per Company** property is enabled. Here is an example:

- There are three companies: CMP1, CMP2, and CMP3.
- A virtual company account that is named **VIR** is created.
- Companies CMP2 and CMP3 are assigned to virtual company account **VIR**, together with a table collection that contains the `CustGroup` and `VendGroup` tables.

The following table shows the `DataAreaId` value that data for each company is stored under.

| Company | DataAreaId |
|---------|------------|
| CMP1    | CMP1       |
| CMP2    | VIR        |
| CMP3    | VIR        |

Because the data for companies CMP2 and CMP3 is stored under the `DataAreaId` value of virtual company account **VIR**, their records are shared.

### SQL behavior in AX 2012 vs. Dynamics 365

When a SQL query runs, the AX 2012 kernel swaps the actual company ID for the virtual ID in the `WHERE` clause. This translation enables the data to be returned from the tables. The following examples show SQL `SELECT` statements for companies CMP1, CMP2, and CMP3 in AX 2012.

**Company CMP1**

```SQL
SELECT   T1.CUSTGROUP, T1.NAME, T1.CREDITMAX, T1.BLOCKED, T1.DATAAREAID, T1.PARTITION
FROM CUSTGROUP T1
WHERE T1.DATAAREAID = 'CMP1'
AND T1.PARTITION = 5637144576
```

**Companies CMP2 and CMP3**

```SQL
SELECT   T1.CUSTGROUP, T1.NAME, T1. TAXGROUPID, T1.DATAAREAID, T1.PARTITION
FROM CUSTGROUP T1
WHERE T1.DATAAREAID = 'VIR'
AND T1.PARTITION = 5637144576
```

In Dynamics 365, this translation doesn't occur. The following example shows the query for company CMP2 in Dynamics 365.

```SQL
SELECT   T1.CUSTGROUP, T1.NAME, T1. TAXGROUPID, T1.DATAAREAID, T1.PARTITION
FROM CUSTGROUP T1
WHERE T1.DATAAREAID = 'CMP2'
AND T1.PARTITION = 5637144576
```

Because no records have a `DataAreaId` value of `CMP2`, this query returns nothing. Therefore, data is missing after the upgrade unless you first devirtualize the data.

## Devirtualize data

Data devirtualization is a complex process and depends on the original virtual company setup. If you're unfamiliar with the concepts or tools that are involved, consider working with a qualified professional.

The following steps are general guidance, not a complete, end-to-end solution. The exact process can vary, depending on your table collection setup. This setup includes the structure, relationships, and data volume. All these aspects can vary between implementations.

> [!IMPORTANT]
> Always back up your data before you start. After devirtualization is completed, test thoroughly to confirm data integrity.

### Step 1: Determine the virtual company setup

Review the virtual company configuration:

- Use the Application Object Tree (AOT) to identify tables in table collections.
- Use the **Virtual Company** form to determine which companies are linked to which collections.

### Step 2: Look for relationships to the RecId value

Determine whether each table that you identified in step 1 has a foreign key that references the `RecId` value of the virtualized table.

For example, if the `CustomsTariffCodeTable_IN` table was virtualized, use the [AX 2012 Cross-reference Tool](/previous-versions/dynamicsax-2012/developer/cross-reference-tool?redirectedfrom=MSDN) to find related tables.

In this case, you find that the `TaxData` table has the following relation:

`TaxData.CustomsTariffCodeTable_IN = CustomsTariffCodeTable_IN.RecId`

This relation indicates that the `TaxData` table references the `RecId` value of the virtualized table.

### Step 3: Look for hidden relationships

In addition to direct table relations that are defined in the AOT, there might be references that are based on table IDs. These references typically use a pair of fields such as `RefTableId` and `RefRecId`. (The exact field names can vary.) The combination of a table ID and a `RecId` value establishes the relationship.

The following SQL query helps you find tables of this type and returns only tables that have records.

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
> This script finds most references. However, be sure to review the results against any system customizations or changes.
>
> After you run the query, check whether any of the tables that are returned reference tables in the virtual company setup. Get the table IDs from the AOT. Track any tables that reference virtualized tables.

### Step 4: Look for other fields

Check the data in the virtualized tables for any extra fields that can reference the virtual company ID.

For example, the `CUSTQUOTATIONTRANS` table includes a field that is named `COMPANY`. If the values in this field match the virtual company ID, document this match, and include it in the devirtualization process.

Although these references aren't always part of formal table relationships, they can affect how you interpret data. Therefore, handle them carefully.

### Step 5: Copy and create records

Use the following script to copy data from the virtual company to individual legal entities.

Before you run the script, change the following values as required:

- `@TableName`
- `@VirtualCompany`
- `@CompanyList`

```sql
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

After you devirtualize the data in a table, update any related table references that point to it. As was noted earlier, these references are often fields such as `RefRecId`. However, the field names can vary.

To maintain referential integrity, update these related fields with the new `RecId` values. Use the corresponding `OLDRECID` value from the devirtualized table as a reference.

The following example shows how to update table references.

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

After the data is successfully devirtualized, you can remove the original records that are associated with the virtual company. You must use SQL to do this cleanup.

The following example shows how to delete the records.

```SQL
--Edit TABLE and PARTITIONKEY as needed. 
DELETE FROM TABLE
WHERE DATAAREAID = 'vir'
AND PARTITION = (SELECT RECID FROM PARTITIONS WHERE PARTITIONKEY = 'initial')
```

If you didn't comment out the part of the devirtualization script that creates an index on the `OLDRECID` field, drop that index after cleanup to avoid leaving unnecessary objects in the database.

> [!IMPORTANT]
> To prevent unintended data loss, always review the records before you delete them.

### Step 8: Clean up virtualized companies

Finally, use the **Virtual Company** setup form in AX 2012 to delete virtual company definitions.

Learn more in [Delete a virtual company account](/previous-versions/dynamicsax-2012/appuser-itpro/virtual-company-accounts-in-microsoft-dynamics-ax#delete-a-virtual-company-account).

> [!NOTE]
> Although this article assumes devirtualization in AX 2012, you can devirtualize data after you restore the AX database as AXDB in a cloud-hosted environment (CHE), or in the sandbox just before you start the upgrade (step 10 of the Data migration toolkit).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
