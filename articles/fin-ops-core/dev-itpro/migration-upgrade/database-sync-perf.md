---
title: Database synchronize performance 
description: This article describes the **Shadow Copy Sync** process that can be used to improve the database synchronize performance in upgrade from AX 2012 within self-service environments.
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

# Database synchronize performance 

[!include[banner](../includes/banner.md)]

This article describes the **Shadow copy sync** process to improve the database synchronize performance in upgrade from AX 2012 within self-service environments.

## Background

During the upgrade three different database synchronize processes are run:

- AdditiveSync - Run as part of the PreReq steps. This adds new tables and new fields and most new indexes to existing tables (excludes unique indexes). 
- DBSync – This step does the first full synchronization. New fields are added to existing tables, and changes to existing fields are made. Unique indexes that were disabled during the PreSync step aren't created during this step.
- FinalDBSync – This step does the final database synchronization that synchronizes all remaining objects in the database and runs final sync data preparation steps.

It's not unusual for the synchronization processes to take several hours or longer. The length of time generally depends on the size of the database, but more specifically is related to large tables where there are changes to the design. 

One of the slowest changes in the sync process is when a numeric field type has its precision changed, this occurs during the DBSync step. If a table has multiple **Numeric** field types with changes, then each **Alter Column** statement can take many minutes or hours to complete, and if there a high number of these column types in each table, this adds to the sync running time. In Microsoft Dynamics AX 2012, most numeric field types had the precision set to 32,16, in Dynamics 365 Finance this is now 32,6 for most.

## Solution

As a solution, the sync engine has a **Shadow copy sync** process. This creates a new version of the table in the upgraded Dynamics 365 Finance format, with an owner schema named **Shadow**, and then inserts the data from the old table into this new one. After the records are inserted, indexes are applied to the shadow table, and the old table in the dbo schema is dropped, and the shadow schema table reassigned back to the dbo schema. 

This **Shadow copy sync** is enabled for all upgrades, with the following thresholds:
 - Table must be greater that 20480MB (20GB)
 - If the size threshold is met, the table must have 1 or more numeric fields where the precision has changed.

If a table doesn't meet the threshold, then it will be synchronized the standard way.

## Checking table sizes

You can run the following SQL script to show all tables over 500MB. This needs to be run on the target Dynamics 365 Finance Azure SQL database for the environment. You need to enable a JIT session from LCS to connect to the database.

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

## Tuning the shadow copy sync thresholds

Depending on your dataset, you might want to tune the **Shadow copy sync** thresholds, to increase or decrease the tables that are included in this process. 

Typically, you will decrease the threshold values, to include more tables in the shadow sync. There will be a tipping point where enabling too many tables to be synchronized with the shadow schema will be slower than if you do less. You'll need to experiment to find the ideal values for your specific database. 

> [!NOTE]
> The following SQL script needs to be run prior to triggering the database upgrade for self-service from the data migration toolkit Step 10.

If you wish to tune the sync threshold, then edit and run the following SQL Script:

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
