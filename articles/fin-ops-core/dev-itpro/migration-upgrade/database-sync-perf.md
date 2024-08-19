---
title: Database synchronization performance
description: This article describes the Shadow copy sync process that improves the performance of database synchronization during an upgrade.
author: ttreen
ms.author: ttreen
ms.topic: article
ms.date: 08/15/2024
ms.reviewer: twheeloc
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 
ms.search.form: 2022-04-08
ms.service: dynamics-365-op
---

# Database synchronization performance

[!include[banner](../includes/banner.md)]

This article describes the **Shadow copy sync** process that improves the performance of database synchronization during a Microsoft Dynamics AX 2012 upgrade in self-service environments.

## Background

During the upgrade, three synchronization processes are run:

- **AdditiveSync** – This process is run as part of the Prereq steps. It adds new tables and fields. It also adds most new indexes (except unique indexes) to existing tables.
- **DBSync** – This process is the first full synchronization, where new fields are added to existing tables, and changes are made to existing fields. Unique indexes that were disabled during the Pre-Sync step aren't created during this step.
- **FinalDBSync** – This process is the final database synchronization that syncs all remaining objects in the database and runs the final synchronization data preparation steps.

It isn't unusual for the synchronization processes to take several hours or longer. The time that is required depends on the size of the database. More specifically, it's related to large tables that have changes to the design.

During the DBSync process, one of the slowest changes is a change in the precision of a numeric field type. If a table contains multiple numeric fields that have changes, each **Alter column** statement can take minutes or hours to be completed. If each table has many of these column types, the running time of the synchronization increases. In AX 2012, the precision for most numeric field types is set to **32,16**. In Dynamics 365 Finance, the precision for most numeric field types is set to **32,6**.

## Solution

As a solution, the synchronization engine has a **Shadow copy sync** process. A new version of the table is created in the upgraded Dynamics 365 Finance format. This table has an owner schema that is named **Shadow**. Data from the old table is inserted into the new one. The following actions then occur:

1. Indexes are applied to the shadow table.
2. The old table in the **dbo** schema is dropped.
3. The shadow table is reassigned to the **dbo** schema.

The **Shadow copy sync** process is enabled for all upgrades that meet the following conditions:

- The table size is more than 20,480 megabytes (MB) (20 gigabytes \[GB\]).
- The table has one or more numeric fields where the precision is changed.

Any table that doesn't meet these conditions is synced in the standard way.

## Check table sizes

Run the following SQL script to find tables that are larger than 500 MB in the target Dynamics 365 Finance Azure SQL database for the environment. To connect to the database, you must enable a just-in-time (JIT) session from Microsoft Dynamics Lifecycle Services.

```SQL
SELECT t.NAME AS TableName, (sum(a.used_pages) * 8) / 1024 as UsedSpaceMB
FROM sys.tables t WITH(NOLOCK)
INNER JOIN sys.schemas s WITH(NOLOCK) ON t.schema_id = s.schema_id and s.name = 'dbo'
INNER JOIN sys.indexes i WITH(NOLOCK) ON t.OBJECT_ID = i.object_id
INNER JOIN sys.partitions p WITH(NOLOCK) ON i.object_id = p.OBJECT_ID AND i.index_id = p.index_id
INNER JOIN sys.allocation_units a WITH(NOLOCK) ON p.partition_id = a.container_id
WHERE t.NAME NOT LIKE 'dt%' AND i.OBJECT_ID > 255 AND i.index_id <= 1
GROUP BY t.NAME, i.object_id, i.index_id, i.name
HAVING ((sum(a.used_pages) * 8) / 1024) > 500 --Edit this to a lower number if needed
ORDER BY sum(a.used_pages) desc
```

## Tune the shadow copy sync thresholds

Depending on your dataset, you can increase or decrease the tables that are included in the **Shadow copy sync** process.

Typically, threshold values are decreased to include more tables in the shadow synchronization. However, if you enable too many tables to be synced with the **Shadow** schema, a point is reached where the performance becomes slower than it would be for fewer tables. You must experiment to find the ideal values for your specific database.

> [!NOTE]
> Run the following SQL script before you trigger the database upgrade for self-service from step 10 of the data migration toolkit.

To tune the synchronization threshold, edit and run the following SQL script.

```SQL
--
-- Edit the following two threshold values as needed:
--
DECLARE @tableSizeThreshold int = 20000 --Currently 20GB (default) for min table size
DECLARE @minNumericFieldsThreshold int = 0 --Currently 0 (default) numeric column change

-- Main Script Start
IF NOT EXISTS ( SELECT 1 FROM [dbo].[SQLSYSTEMVARIABLES] WHERE PARM='SHADOWCOPYSIZE' )
BEGIN
    INSERT INTO [dbo].[SQLSYSTEMVARIABLES] 
    ([PARM], [VALUE], [IPARM], [IVALUE])
    VALUES('SHADOWCOPYSIZE', @tableSizeThreshold, 20, NULL);
END
ELSE
BEGIN
    UPDATE [dbo].[SQLSYSTEMVARIABLES] 
    SET VALUE = @tableSizeThreshold
    WHERE PARM='SHADOWCOPYSIZE'
END
IF NOT EXISTS ( SELECT 1 FROM [dbo].[SQLSYSTEMVARIABLES] WHERE PARM='SHADOWCOPYREALSCALECHANGELIMIT' )
BEGIN
    INSERT INTO [dbo].[SQLSYSTEMVARIABLES]
    ([PARM], [VALUE], [IPARM], [IVALUE])
    VALUES ('SHADOWCOPYREALSCALECHANGELIMIT', @minNumericFieldsThreshold, 20, NULL);
END
ELSE
BEGIN
    UPDATE [dbo].[SQLSYSTEMVARIABLES]
    SET VALUE = @minNumericFieldsThreshold
    WHERE PARM='SHADOWCOPYREALSCALECHANGELIMIT'
END
-- Main Script End
```
