---
# required metadata

title: Self-service environment
description: An overview sentence that describes what this article is all about.
author: ttreen 
ms.date: 04/08/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: ttreen
ms.search.validFrom: 
ms.search.form: 2022-04-08

---

# Self-Service Environments - Upgrade Troubleshooting

[!include[banner](../includes/banner.md)]

This topic provides troubleshooting information for upgrades of Microsoft Dynamics AX 2012 to Microsoft Dynamics 365 Finance + Operations Self-Service Environments


## Scenario 1: The migration app is prompting you to enter **Project-Id** and **Environment-Id** values.

**Solution:** The user should be part of the project and should be assigned to one of the following roles: **ProjectOwner**, **EnvironmentAdmin**, or **OperationsAdmin**.

## Scenario 2: Migration app database connectivity failed for the source database server or the target database server.

**Solution:** In the migration app, complete step 1, [Data upgrade preparation: Environment setup activity](data-upgrade-self-service.md#complete-the-data-replication-and-upgrade).

## Scenario 3: The snapshot for any of the publications failed. This failure can be tracked in the Replication Monitor.

**Solution:** In the Replication Monitor, on the **Agents** tab, select the failed publication, select and hold (or right-click) the snapshot agent, and then select **Start agent** to generate a snapshot.

## Scenario 4: If one of the steps fails in the migration app, and you must rerun that step, follow these steps:

1. Close the migration app.
2. In the migration app folder, find the **Data** folder.
3. In the **Data** folder, open the **ReplicationMenu.Json** file.
4. In the file, you can see all the menu options that have the same ID sequence. Find the step that you want to rerun, and update the **Status** value to **0**.

> [!IMPORTANT] 
> Don't change anything else in this file. When you update the file, make sure that the migration app isn't in a running state.

5. Open the migration app, and run the step.

## Scenario 5: After the publication is created, the replication job fails, and the following exceptions occur:

**Exception 1:**

> Cannot execute as the database principal because the principal "dbo" does not exist, this type of principal cannot be impersonated, or you do not have permission. (Source: MSSQLServer, Error number: 15517)  
Get help: `http://help/15517`

**Exception 2:**

> The process could not execute 'sp_replcmds' on 'replicationsrv\\MSSQLSERVER2016'. (Source: MSSQL_REPL, Error number: MSSQL_REPL20011)  
Get help: `http://help/MSSQL_REPL20011`
>
> Cannot execute as the database principal because the principal "dbo" does not exist, this type of principal cannot be impersonated, or you do not have permission. (Source: MSSQLServer, Error number: 15517)  
Get help: `http://help/15517`

**Solution:** In SQL Server Management Studio (SSMS), open a query window, connect to the source database, and run the following command:

```sql
EXEC sp_changedbowner 'sa'
```

## Scenario 6: The LCS status is **Failed**. However, in the migration app, the data upgrade trigger is successful.

**Solution:** In the migration app, run the **'ds'** option. This option reads the LCS environment state and the data upgrade status for every step and substep.

> [!NOTE] 
> If the data upgrade status and the LCS environment status are **Failed**, the status of step 10 in the [Complete the data replication and upgrade](data-upgrade-self-service.md#complete-the-data-replication-and-upgrade) procedure will be updated to **Resume**. The user can then resume the operation from the point where the upgrade process failed.

## Scenario 7: If you want to skip the failed step (if that step was manually run) and proceed with further steps, follow these steps:

1. Close the migration app. 
2. In the migration app folder, find the **Data** folder.
3. In the **Data** folder, open the **ReplicationMenu.Json** file.
4. In the file, you can see all the menu options that have the same ID sequence. Find the step that you want to rerun, and update the **Status** value to **1**. By changing the status to **1**, you mark the step as completed.

> [!IMPORTANT] 
> Don't change anything else in this file. When you update the file, make sure that the migration app isn't in a running state.

## Scenario 8: To migrate from an old version to the new version of the console app, follow these steps:

1. Download the latest version of the console app from LCS.
2. Take the **paramsdata.txt** (**/paramsdata.txt**) and **ReplicationMenu.json** (**/Data/ReplicationMenu.json**) files from the old version of the console app, and put them under the same paths in the new version of the console app.
3. Rerun the app.

## Scenario 9: The replication status for any of the publications is shown as **Waiting for snapshot to complete** for more than two hours.

**Solution:** In the Replication Monitor, select and hold (or right-click) the publication, and then select **Reinitialize Subscription**.

## Scenario 10: You want to resume the data upgrade.

**Solution:** The data upgrade status might not have been updated in the console app. Follow these steps to resume the data upgrade:

1. To learn the status of the console app, perform the **Help** option. This option lists all the menu options and shows the current state.
2. In the [Complete the data replication and upgrade](data-upgrade-self-service.md#complete-the-data-replication-and-upgrade) procedure, if the status of step 10 is **Successful**, run the **'ds'** option in the migration app. This option updates the data upgrade status.

After the **'ds'** option is run, two types of status will be listed: the LCS environment status and the data upgrade status.

 - **Case 1:** If the LCS environment status is **Failed**, and the last step of the data upgrade is **Failed**, step 10 will show the **Resume** option.
 - **Case 2:** If the LCS environment status is **Failed**, and the last step of the data upgrade is **Completed**, step 10 will show the **Resume** option.
 - **Case 3:** If the LCS environment status is **Deployed**, and the last step of the data upgrade is **Completed**, step 10 will show **Successful**.
 - **Case 4:** If the LCS environment status is **Deployed**, and the last step of the data upgrade is **In Progress**, step 10 will show **Successful**, because the data upgrade job is running in the background.

## Scenario 11: After creating the publication, if the snapshot creation fails with the following error.

```
Error messages:
Source: Microsoft.SqlServer.Smo
Target Site: Void PrefetchObjectsImpl(System.Type, Microsoft.SqlServer.Management.Smo.ScriptingPreferences)
Message: Prefetch objects failed for Database 'AxDB_ASIA'.
Stack:    at Microsoft.SqlServer.Management.Smo.Database.PrefetchObjectsImpl(Type objectType, ScriptingPreferences scriptingPreferences)
          at Microsoft.SqlServer.Replication.Snapshot.SmoScriptingManager.ObjectPrefetchControl.DoPrefetch(Database database)
          at Microsoft.SqlServer.Replication.Snapshot.SmoScriptingManager.PrefetchObjects(ObjectPrefetchControl[] objectPrefetchControls)
          at Microsoft.SqlServer.Replication.Snapshot.SmoScriptingManager.DoPrefetchWithRetry()
          at Microsoft.SqlServer.Replication.Snapshot.SmoScriptingManager.DoScripting()
          at Microsoft.SqlServer.Replication.Snapshot.SqlServerSnapshotProvider.DoScripting()
          at Microsoft.SqlServer.Replication.Snapshot.SqlServerSnapshotProvider.GenerateSnapshot()
          at Microsoft.SqlServer.Replication.SnapshotGenerationAgent.InternalRun()
          at Microsoft.SqlServer.Replication.AgentCore.Run() (Source: Microsoft.SqlServer.Smo, Error number: 0)
 ```
 **Solution:** In the Replication Monitor, select and right-click the failed publication, and then select **Generate Snapshot**.

## Scenario 12: Data upgrade **pre-sync and post-synch processes are taking time.** How can I troubleshoot which specific process or job is taking more time?.
**Solution:** **ReleaseUpgradeDB*** framework logs the execution of each script into ReleaseUpdateScriptsLog table. You can monitor the duration of scripts that are run in this table. You can easily identify the longest-running process or job when you're trying to tune the performance of the data upgrade process.
