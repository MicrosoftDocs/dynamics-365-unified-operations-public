---
# required metadata

title: Reset the financial reporting data mart 
description: This topic describes how to reset the financial reporting data mart. 
author: aolson
manager: AnnBe
ms.date: 12/01/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 261824
ms.search.region: Global
# ms.search.industry: 
ms.author: aloson
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Reset the financial reporting data mart 

[!include[banner](../includes/banner.md)]


This topic explains how to reset the Financial reporting data mart for the following versions:

- Microsoft Dynamics 365 for Finance and Operations Financial reporting release 7.2.6.0 and later

- Microsoft Dynamics 365 for Finance and Operations Financial reporting release 7.0.10000.4 and later

- Microsoft Dynamics 365 for Finance and Operations, Enterprise edition (on-premises)

To get Financial reporting, version 7.2.6.0, you can download KB 4052514 from https://support.microsoft.com/en-us/help/4052514.

## Reset the Financial reporting data mart for Finance and Operations Financial reporting release 7.2.6.0 and later

###Resetting the Financial reporting data mart from Report designer

>[!NOTE] 
> The steps in this process are supported for Finance and Operations Financial reporting release 7.2.6.0 and later. If you have an earlier release, contact the Support team for assistance.

In specific scenarios, you might have to reset the data mart for Financial reporting. You can complete this task in the Report designer client. Here are some scenarios where you might have to reset the data mart:

•	The Finance and Operations database was restored, but the data mart database wasn't restored.

•	You see incorrect data for a period.

•	Support instructs you to reset the data mart as part of a troubleshooting step.

The data mart reset should be done only during times when the amount of processing on the database is small. Financial reporting will be unavailable during the reset process.

####Reset the data mart
To reset the data mart, in Report designer, on the Tools menu, select Reset Data Mart. The dialog box that appears has two sections: Statistics and Reset.

[![Statistics](./media/Statistics.png)](./media/Statistics.png)

#####Integration attempts

The **Integration attempts** grid shows how many times the system has tried to integrate transactions. The system continues to try to integrate data over a period of days if the first few attempts aren't successful. You will know that the data mart must be reset is if the number of attempts is 8 or more, and if there are many Dimension combination or Transaction records. In this situation, the data won't be reported on.

#### Data status

The Data status grid provides a snapshot of the transactions, exchange rates, and dimension values in the data mart. A large number of stale records indicates that numerous updates to the records have occurred. This situation might cause slower report generation times.


#### Misaligned main account categories
If the Financial reporting version is earlier than 7.2.1, you might have to reset the data mart if you rename accounts and move accounts between account categories. These actions can cause main account categories to become misaligned. The Misaligned main account categories field shows whether you're experiencing that issue.



###**Reset in Financial reporting version 7.2.6.0**

[![Reset Data Mart](./media/Reset-7.2.JPG)](./media/Reset-7.2.JPG)

To reset the data mart in version 7.2.6.0 and earlier, select the Reset data mart checkbox and click OK. This should only be selected during scheduled downtime. 

###**Reset data mart and Reason in 7.3.0**

If you determine that a data mart reset is required, you can select the Reset data mart check box. Then select a reason in the Reason field. The following options are available:

•	Missing or incorrect data – Based on the statistics, you've determined that data might be missing. Before you continue, we recommend that you work with Support to determine the root cause.

•	Restore database – The Finance and Operations database was restored, but the database for the Financial reporting data mart wasn't restored.

•	Other – You're resetting the data mart for another reason. If you're concerned that there is an issue, contact Support to identify it.

> [!NOTE]
> Verify that all existing tasks have finished integrating before completing the steps. You can view the status by clicking Tools > Integration status.

**Clear users and companies**

Select the **Clear users and companies** check box if you restored your database and have made changes to users or companies. You should rarely have to select this check box.

When you're ready to start the reset process, select OK. You're prompted to confirm that you're ready to begin the process. Note that Financial reporting won't be available during the reset and the initial data integration that occurs afterward.

If you want to review the status of the integration, select Tools > Integration status to see the last time that the integration was run and the status.

[![View the status of the integration](./media/integration.png)](./media/integration.png)


## Reset the Financial reporting data mart for Finance and Operations Financial reporting release 7.0.10000.4 and later

If you ever restore your Finance and Operations database from a backup or copy the database from another environment, you must follow the steps in this topic to ensure that the financial reporting data mart is correctly using the restored Finance and Operations database. 
> [!Note] 
> The steps in this process are supported for Dynamics 365 for Operation May 2016 release (App build 7.0.1265.23014 and financial reporting build 7.0.10000.4) and newer releases. If you have an earlier release of Finance and Operations, contact our Support team for assistance.

## Export report definitions
First, export the report designs located in the Report Designer, using the following steps:

1.  In the Report Designer, go to **Company** &gt; **Building Block Groups**.
2.  Select the building block group to export, and click **Export**. 

    > [!Note] 
    > For Finance and Operations, only one building block group is supported, **Default**.
    
3.  Select the report definitions to export:
    -   To export all your report definitions and the associated building blocks, click **Select All**.
    -   To export specific reports, rows, columns, trees, or dimension sets, click the appropriate tab, and then select the items to export. Press and hold the Ctrl key to select multiple items in a tab. When you select reports to export, the associated rows, columns, trees, and dimension sets are selected.

4.  Click **Export**.
5.  Enter a file name and select a secure location where you want to save the exported report definitions.
6.  Click **Save**.

You can copy or uploade the file to a secure location. In this way, the file can be imported into a different environment later. Information about how to use a Microsoft Azure storage account, see [Transfer data with the AzCopy Command-Line Utility](/azure/storage/storage-use-azcopy). 

> [!NOTE]
> Microsoft doesn’t provide a storage account as part of your Finance and Operations agreement. You must either purchase a storage account or use a storage account from a separate Azure subscription. 

> [!WARNING]
> Be aware of the behavior of the D drive on Azure Virtual Machines(VM's). Don't permanently store your exported building block groups on drive D. For more information about temporary drives, see [Understanding the temporary drive on Windows Azure Virtual Machines](https://blogs.msdn.microsoft.com/mast/2013/12/06/understanding-the-temporary-drive-on-windows-azure-virtual-machines/).

## Stop services
The following Microsoft Windows services will have open connections to the Finance and Operations database. Therefore, you must use Microsoft Remote Desktop to connect to all the computers in the environment and then stop these services by using **services.msc**:

-   World wide web publishing service (on all Application Object Servers [AOS] computers)
-   Microsoft Dynamics 365 for Finance and Operations Batch Management Service (on non-private AOS computers only)
-   Management Reporter 2012 Process Service (on Business intelligence [BI] computers only)

These services will have open connections to the Finance and Operations database.

## Reset
### Download the latest MinorVersionDataUpgrade.zip package

Download the latest MinorVersionDataUpgrade.zip package. For instructions about how to find and download the correct version of the data upgrade package, see [Download the latest data upgrade deployable package](..\migration-upgrade\upgrade-data-to-latest-update.md#download-the-latest-data-upgrade-deployable-packages). An upgrade is not required in order to download the MinorVersionDataUpgrade.zip package. Therefor, you just have follow the steps in the “Download the latest data upgrade deployable package” section of this topice. You can skip all the other steps in the topic. 

### Run scripts against Finance and Operations database

Run the following scripts against the Finance and Operations database (not against the financial reporting database).

-   DataUpgrade.zip\\AosService\\Scripts\\ConfigureAxReportingIntegration.sql
-   DataUpgrade.zip\\AosService\\Scripts\\GrantAzViewChangeTracking.sql

These scripts help guarantee that the users, roles, and change tracking settings are correct.

### Run a Windows PowerShell command to reset database

On the AOS computer, start Microsoft Windows PowerShell as an administrator, and run the following commands to reset the integration between Finance and Operations and Financial reporting.

```
F:
cd F:\MRApplicationService\MRInstallDirectory
Import-Module .\Server\MRDeploy\MRDeploy.psd1
Reset-DatamartIntegration -Reason OTHER -ReasonDetail “<my reason for resetting>”
```
Here is an explanation of the parameters in the **Reset-DatamartIntegration** command:

-   The valid values for **-Reason** are: **SERVICING, BADDATA, OTHER**.
-   The **-ReasonDetail** parameter is free text.
-   The reason and reasonDetail will be recorded in telemetry/environment monitoring.

> [!NOTE]
> After executing the commands, you will be asked to enter “Y” to confirm.

### Start services
Use services.msc to restart the services that you stopped earlier:

-   World wide web publishing service (on all AOS computers)
-   Microsoft Dynamics 365 for Finance and Operations Batch Management Service (on non-private AOS computers only)
-   Management Reporter 2012 Process Service (on BI computers only)

### Import report definitions
Import your report designs from the Report Designer, using the file created during the export:

1.  In the Report Designer, go to **Company** &gt; **Building Block Groups**.
2.  Select the building block group to export, and click **Export**. 

    > [!NOTE]
    > For Finance and Operations, only one building block group is supported, **Default**.
    
3.  Select the **Default** building block and click **Import**.
4.  Select the file containing the exported report definitions and click **Open**.
5.  In the Import dialog box, select the report definitions to import:
    -   To import all the report definitions and the supporting building blocks, click **Select All**.
    -   To import specific reports, rows, columns, trees, or dimension sets, select the reports, rows, columns, trees, or dimension sets to import.

6.  Select **Import**.

## Reset the Financial reporting data mart for Finance and Operations (on-premises)

1. Instruct all users to exit Report designer and the Financial reporting area of Finance and Operations.

2. Run the following script against the Financial reporting database (MRDB).

```
DECLARE @triggerIds table(id uniqueidentifier, taskTypeId uniqueidentifier)
INSERT INTO @triggerIds SELECT tr.[Id], tt.[Id]
FROM [Scheduling].[Task] t with(nolock)
JOIN [Scheduling].[Trigger] tr ON t.[TriggerId] = tr.[Id]
JOIN [Scheduling].[TaskState] ts ON ts.[TaskId] = t.[Id]
LEFT JOIN [Scheduling].[TaskCategory] tc ON tc.[Id] = t.[CategoryId]
JOIN [Scheduling].[TaskType] tt ON t.[TypeId] = tt.[Id]
WHERE tt.[Id] IN ('D81C1197-D486-4FB7-AF8C-078C110893A0', '55D3F71A-2618-4EAE-9AA6-D48767B974D8') -- 'Maintenance Task', 'Map Task'
PRINT 'Disable integration tasks'
UPDATE [Scheduling].[Trigger] SET IsEnabled = 0 WHERE [Id] in (SELECT id FROM @triggerIds)
```

3. Truncate or delete all records from the FINANCIALREPORTS table in the Finance and Operations database (AXDB).

4. Truncate or delete all records from the FINANCIALREPORTVERSION table, if this table exists in the Finance and Operations database. If the table doesn't exist, skip this step.

5. Run the ResetDatamart.sql script against the Financial reporting database. This script disables the data mart integration, deletes all the data mart data, and then enables the data integration again.

```
  DECLARE @triggerIds table(id uniqueidentifier, taskTypeId uniqueidentifier)
INSERT INTO @triggerIds SELECT tr.[Id], tt.[Id]
FROM [Scheduling].[Task] t with(nolock)
JOIN [Scheduling].[Trigger] tr ON t.[TriggerId] = tr.[Id]
JOIN [Scheduling].[TaskState] ts ON ts.[TaskId] = t.[Id]
LEFT JOIN [Scheduling].[TaskCategory] tc ON tc.[Id] = t.[CategoryId]
JOIN [Scheduling].[TaskType] tt ON t.[TypeId] = tt.[Id]
WHERE tt.[Id] IN ('D81C1197-D486-4FB7-AF8C-078C110893A0', '55D3F71A-2618-4EAE-9AA6-D48767B974D8') -- 'Maintenance Task', 'Map Task'
PRINT 'Disable integration tasks'
UPDATE [Scheduling].[Trigger] SET IsEnabled = 0 WHERE [Id] in (SELECT id FROM @triggerIds)
------------------------------
PRINT 'Drop archive tables'
------------------------------
DECLARE @tableId nvarchar(max)
DECLARE dropCursor CURSOR LOCAL FAST_FORWARD FOR
SELECT Id FROM [Datamart].Archive
OPEN dropCursor
FETCH NEXT FROM dropCursor INTO @tableId
WHILE @@FETCH_STATUS = 0
BEGIN
	   IF EXISTS (SELECT 1 FROM INFORMATION_SCHEMA.TABLES t WHERE t.TABLE_NAME = 'FactStaging' + @tableId and t.TABLE_SCHEMA = 'Datamart')
		  EXEC('DROP TABLE [Datamart].FactStaging' + @tableId)
	   IF EXISTS (SELECT 1 FROM INFORMATION_SCHEMA.TABLES t WHERE t.TABLE_NAME = 'DimensionCombinationStaging' + @tableId and t.TABLE_SCHEMA = 'Datamart')
		  EXEC('DROP TABLE [Datamart].DimensionCombinationStaging' + @tableId)       
	   FETCH NEXT FROM dropCursor INTO @tableId
END
CLOSE dropCursor
DEALLOCATE dropCursor
IF EXISTS (SELECT 1 FROM INFORMATION_SCHEMA.TABLES t WHERE t.TABLE_NAME = 'DimensionCombinationProcessing' and t.TABLE_SCHEMA = 'Datamart')
		  EXEC('DROP TABLE [Datamart].DimensionCombinationProcessing')
------------------------------
PRINT 'Begin Truncating tables'
------------------------------
DECLARE @tablename nvarchar(200)
DECLARE @schemaname nvarchar(200)
DECLARE clear_tables CURSOR
  FOR SELECT TABLE_NAME, TABLE_SCHEMA FROM INFORMATION_SCHEMA.TABLES WHERE TABLE_SCHEMA = 'Datamart' AND TABLE_TYPE='BASE TABLE'
PRINT 'remove check constraints'
OPEN clear_tables
FETCH NEXT FROM clear_tables INTO @tablename, @schemaname
WHILE @@FETCH_STATUS = 0
BEGIN
  IF @tablename <> 'VersionHistory'
  BEGIN
	EXEC('ALTER TABLE [' + @schemaname + '].[' + @tablename + '] NOCHECK CONSTRAINT ALL')
  END
  FETCH NEXT FROM clear_tables INTO @tablename, @schemaname
END
CLOSE clear_tables
------------------------------
PRINT 'delete data from tables and rebuild indexes'
------------------------------
OPEN clear_tables
FETCH NEXT FROM clear_tables INTO @tablename, @schemaname
WHILE @@FETCH_STATUS = 0
BEGIN
  IF @tablename <> 'VersionHistory'
  BEGIN
	  IF(EXISTS (select TOP 1 1 from sys.foreign_keys where referenced_object_id = OBJECT_ID(@schemaname + '.' + @tablename)) OR
		EXISTS(SELECT TOP 1 1 FROM sys.sql_expression_dependencies sed
		INNER JOIN sys.objects o ON sed.referencing_id = o.[object_id]
		WHERE o.[type] = 'V' 
		AND referenced_schema_name = @schemaname 
		AND referenced_entity_name = @tablename))
	  BEGIN
		PRINT 'deleting from ' + @tablename
		EXEC('DELETE FROM [' + @schemaname + '].[' + @tablename + ']')
	  END
	  ELSE
	  BEGIN
		PRINT 'truncating from ' + @tablename
		EXEC('TRUNCATE TABLE [' + @schemaname + '].[' + @tablename + ']') 
	  END
  END
  EXEC('ALTER INDEX ALL ON [' + @schemaname + '].[' + @tablename + '] REBUILD')  
  FETCH NEXT FROM clear_tables INTO @tablename, @schemaname
END
CLOSE clear_tables
------------------------------
PRINT 'reenable check constraints'
------------------------------
OPEN clear_tables
FETCH NEXT FROM clear_tables INTO @tablename, @schemaname
WHILE @@FETCH_STATUS = 0
BEGIN
  IF @tablename <> 'VersionHistory'
  BEGIN
	EXEC('ALTER TABLE [' + @schemaname + '].[' + @tablename +'] WITH CHECK CHECK CONSTRAINT ALL')
  END
  FETCH NEXT FROM clear_tables INTO @tablename, @schemaname
END
CLOSE clear_tables
DEALLOCATE clear_tables
------------------------------
PRINT 'Complete Truncating tables'
------------------------------
------------------------------
PRINT 'Remove indexes from DimensionCombination'
------------------------------
DECLARE @indexname nvarchar(200)
DECLARE drop_indexes CURSOR
FOR SELECT Name FROM sys.indexes WHERE object_id = OBJECT_ID('[Datamart].[DimensionCombination]') AND is_primary_key = 0
OPEN drop_indexes
FETCH NEXT FROM drop_indexes INTO @indexname
WHILE @@FETCH_STATUS = 0
BEGIN
  EXEC('DROP INDEX [' + @indexname + '] on [Datamart].[DimensionCombination]')
  FETCH NEXT FROM drop_indexes INTO @indexname
END
CLOSE drop_indexes
DEALLOCATE drop_indexes
------------------------------
PRINT 'Drop Columns on DimensionCombination'
------------------------------
DECLARE @objectname nvarchar(200)
DECLARE drop_objects CURSOR
FOR SELECT Name FROM sys.columns WHERE object_id = OBJECT_ID('[Datamart].[DimensionCombination]')
OPEN drop_objects
FETCH NEXT FROM drop_objects INTO @objectname
WHILE @@FETCH_STATUS = 0
BEGIN
  IF @objectname NOT IN ('Id', 'Description', 'SourceKey', 'OrganizationId', 'InactiveDimensions')
  BEGIN
	EXEC('ALTER TABLE [Datamart].[DimensionCombination] DROP COLUMN ' + @objectname)
  END
  FETCH NEXT FROM drop_objects INTO @objectname
END
CLOSE drop_objects
DEALLOCATE drop_objects
------------------------------
PRINT 'Drop Columns on DimensionCombinationResolving'
------------------------------
DECLARE drop_objects CURSOR
FOR SELECT Name FROM sys.columns WHERE object_id = OBJECT_ID('[Datamart].[DimensionCombinationResolving]')
OPEN drop_objects
FETCH NEXT FROM drop_objects INTO @objectname
WHILE @@FETCH_STATUS = 0
BEGIN
  IF @objectname NOT IN ('Id', 'Description', 'SourceKey', 'OrganizationId')
  BEGIN
	EXEC('ALTER TABLE [Datamart].[DimensionCombinationResolving] DROP COLUMN ' + @objectname)
  END
  FETCH NEXT FROM drop_objects INTO @objectname
END
CLOSE drop_objects
DEALLOCATE drop_objects
------------------------------
PRINT 'Drop Columns on DimensionCombinationStaging'
------------------------------
DECLARE drop_objects CURSOR
FOR SELECT Name FROM sys.columns WHERE object_id = OBJECT_ID('[Datamart].[DimensionCombinationStaging]')
OPEN drop_objects
FETCH NEXT FROM drop_objects INTO @objectname
WHILE @@FETCH_STATUS = 0
BEGIN
  IF @objectname NOT IN ('Id', 'OrganizationId', 'Description', 'SourceKey', 'OrganizationKey', 'FreshnessDate')
  BEGIN
	EXEC('ALTER TABLE [Datamart].[DimensionCombinationStaging] DROP COLUMN ' + @objectname)
  END
  FETCH NEXT FROM drop_objects INTO @objectname
END
CLOSE drop_objects
DEALLOCATE drop_objects
------------------------------
PRINT 'Drop Columns on DimensionCombinationUnreferenced'
------------------------------
DECLARE drop_objects CURSOR
FOR SELECT Name FROM sys.columns WHERE object_id = OBJECT_ID('[Datamart].[DimensionCombinationUnreferenced]')
OPEN drop_objects
FETCH NEXT FROM drop_objects INTO @objectname
WHILE @@FETCH_STATUS = 0
BEGIN
  IF @objectname NOT IN ('Id', 'Description', 'SourceKey', 'OrganizationId')
  BEGIN
	EXEC('ALTER TABLE [Datamart].[DimensionCombinationUnreferenced] DROP COLUMN ' + @objectname)
  END
  FETCH NEXT FROM drop_objects INTO @objectname
END
CLOSE drop_objects
DEALLOCATE drop_objects
------------------------------
PRINT 'Drop Columns on DimensionValueAttributeValue'
------------------------------
DECLARE drop_objects CURSOR
FOR SELECT Name FROM sys.columns WHERE object_id = OBJECT_ID('[Datamart].[DimensionValueAttributeValue]')
OPEN drop_objects
FETCH NEXT FROM drop_objects INTO @objectname
WHILE @@FETCH_STATUS = 0
BEGIN
  IF @objectname NOT IN ('DimensionValueId')
  BEGIN
	EXEC('ALTER TABLE [Datamart].[DimensionValueAttributeValue] DROP COLUMN ' + @objectname)
  END
  FETCH NEXT FROM drop_objects INTO @objectname
END
CLOSE drop_objects
DEALLOCATE drop_objects
------------------------------
PRINT 'Drop Columns on FactAttributeValue'
------------------------------
DECLARE drop_objects CURSOR
FOR SELECT Name FROM sys.columns WHERE object_id = OBJECT_ID('[Datamart].[FactAttributeValue]')
OPEN drop_objects
FETCH NEXT FROM drop_objects INTO @objectname
WHILE @@FETCH_STATUS = 0
BEGIN
  IF @objectname NOT IN ('FactId')
  BEGIN
	EXEC('ALTER TABLE [Datamart].[FactAttributeValue] DROP COLUMN ' + @objectname)
  END
  FETCH NEXT FROM drop_objects INTO @objectname
END
CLOSE drop_objects
DEALLOCATE drop_objects
------------------------------
PRINT 'Remove constraints from TranslatedPeriodBalance'
------------------------------
DECLARE @name nvarchar(200)
DECLARE drop_constraints CURSOR
FOR SELECT Name FROM sys.default_constraints WHERE parent_object_id = OBJECT_ID('[Datamart].[TranslatedPeriodBalance]')
OPEN drop_constraints
FETCH NEXT FROM drop_constraints INTO @name
WHILE @@FETCH_STATUS = 0
BEGIN  
  EXEC('ALTER TABLE [Datamart].[TranslatedPeriodBalance] DROP CONSTRAINT [' + @name + ']')  
  FETCH NEXT FROM drop_constraints INTO @name
END
CLOSE drop_constraints
DEALLOCATE drop_constraints
------------------------------
PRINT 'Drop Columns on TranslatedPeriodBalance'
------------------------------
DECLARE drop_objects CURSOR
FOR SELECT Name FROM sys.columns WHERE object_id = OBJECT_ID('[Datamart].[TranslatedPeriodBalance]')
OPEN drop_objects
FETCH NEXT FROM drop_objects INTO @objectname
WHILE @@FETCH_STATUS = 0
BEGIN
  IF @objectname NOT IN ('PeriodId', 'DimensionsId', 'ScenarioId', 'FactType', 'PostingLayerId')
  BEGIN
	EXEC('ALTER TABLE [Datamart].[TranslatedPeriodBalance] DROP COLUMN ' + @objectname)
  END
  FETCH NEXT FROM drop_objects INTO @objectname
END
CLOSE drop_objects
DEALLOCATE drop_objects
------------------------------
PRINT 'Remove constraints from TranslatedPeriodBalanceChanges'
------------------------------
DECLARE drop_constraints CURSOR
FOR SELECT Name FROM sys.default_constraints WHERE parent_object_id = OBJECT_ID('[Datamart].[TranslatedPeriodBalanceChanges]')
OPEN drop_constraints
FETCH NEXT FROM drop_constraints INTO @name
WHILE @@FETCH_STATUS = 0
BEGIN  
  EXEC('ALTER TABLE [Datamart].[TranslatedPeriodBalanceChanges] DROP CONSTRAINT [' + @name + ']')  
  FETCH NEXT FROM drop_constraints INTO @name
END
CLOSE drop_constraints
DEALLOCATE drop_constraints
------------------------------
PRINT 'Drop Columns on TranslatedPeriodBalanceChanges'
------------------------------
DECLARE drop_objects CURSOR
FOR SELECT Name FROM sys.columns WHERE object_id = OBJECT_ID('[Datamart].[TranslatedPeriodBalanceChanges]')
OPEN drop_objects
FETCH NEXT FROM drop_objects INTO @objectname
WHILE @@FETCH_STATUS = 0
BEGIN
  IF @objectname NOT IN ('PeriodId', 'DimensionsId', 'ScenarioId', 'FactType', 'PostingLayerId')
  BEGIN
	EXEC('ALTER TABLE [Datamart].[TranslatedPeriodBalanceChanges] DROP COLUMN ' + @objectname)
  END
  FETCH NEXT FROM drop_objects INTO @objectname
END
CLOSE drop_objects
DEALLOCATE drop_objects
-- Rebuild dropped indexes that are dynamic
EXEC [Datamart].ConfigureIndexesAndConstraints
------------------------------------------
------------------------------------------
PRINT 'Reset the map tokens'
UPDATE [Connector].[Map] SET InitalLoad = 0, ReaderToken=NULL, LastQuerySuccess='1900-01-01' WHERE MapId IN (SELECT t.[Id]
FROM [Scheduling].[Task] t with(nolock)
JOIN [Scheduling].[Trigger] tr ON t.[TriggerId] = tr.[Id]
JOIN [Scheduling].[TaskState] ts ON ts.[TaskId] = t.[Id]
LEFT JOIN [Scheduling].[TaskCategory] tc ON tc.[Id] = t.[CategoryId]
JOIN [Scheduling].[TaskType] tt ON t.[TypeId] = tt.[Id]
WHERE tt.[Id] = '55D3F71A-2618-4EAE-9AA6-D48767B974D8')
PRINT 'Reset the tasks'
UPDATE [Scheduling].[TaskState] SET StateType = 0, Progress = 0.0, LastRunTime = NULL, NextRunTime = NULL WHERE TaskId IN (SELECT ts.[TaskId]
FROM [Scheduling].[Task] t with(nolock)
JOIN [Scheduling].[Trigger] tr ON t.[TriggerId] = tr.[Id]
JOIN [Scheduling].[TaskState] ts ON ts.[TaskId] = t.[Id]
LEFT JOIN [Scheduling].[TaskCategory] tc ON tc.[Id] = t.[CategoryId]
JOIN [Scheduling].[TaskType] tt ON t.[TypeId] = tt.[Id]
WHERE tt.[Id] IN ('D81C1197-D486-4FB7-AF8C-078C110893A0', '55D3F71A-2618-4EAE-9AA6-D48767B974D8'))
PRINT 'Enable integration tasks, RunImmediately'
UPDATE [Scheduling].[Trigger] SET IsEnabled = 1, RunImmediately = 1, StartBoundary = '1900-01-01' 
WHERE Id in (SELECT [id] from @triggerIds WHERE taskTypeId = '55D3F71A-2618-4EAE-9AA6-D48767B974D8')
PRINT 'Enable the Maintenance Task'
UPDATE [Scheduling].[Trigger] SET IsEnabled = 1, RunImmediately = 0, StartBoundary = GETDATE() WHERE Id in
(SELECT [id] from @triggerIds WHERE taskTypeId = 'D81C1197-D486-4FB7-AF8C-078C110893A0')
------------------------------------------
------------------------------------------
```

6. After the reset, you can manually verify the data reload by running the following query against the Financial reporting database.

select ReaderObjectName, WriterObjectName, LastRunTime, StateType from Connector.MapsWithDetail with (nolock)

Confirm that all rows have a **LastRunTime** value, and that **StateType** is set to **5**. A **StateType** value of **5** indicates that the data was successfully reloaded.

A value of **7** indicates a faulted state. Sometimes, the Organization Hierarchy map has this state the first time that it runs. However, the faulted state but should be automatically resolved.
