---
# required metadata

title: Troubleshoot upgrades to Dynamics 365 Finance + Operations self-service environments
description: This topic provides troubleshooting guidance for upgrades of Microsoft Dynamics AX 2012 to Microsoft Dynamics 365 Finance + Operations self-service environments.
author: ttreen 
ms.date: 04/22/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: ttreen
ms.search.validFrom: 
ms.search.form: 2022-04-08

---

# Troubleshoot self-service environments

[!include[banner](../includes/banner.md)]

This topic provides troubleshooting guidance for upgrades of Microsoft Dynamics AX 2012 to Microsoft Dynamics 365 Finance + Operations self-service environments.

## Scenario 1: The migration app is prompting you to enter Project-Id and Environment-Id values.

**Solution:** 

Ensure that the user doing the upgrade is part of the project and is assigned to one of the following roles: **ProjectOwner**, **EnvironmentAdmin**, or **OperationsAdmin**.

## Scenario 2: Migration app database connectivity failed for the source database server or the target database server.

**Solution:** 

In the migration app, complete step 1 in [Data upgrade preparation: Environment setup activity](data-upgrade-self-service.md#complete-the-data-replication-and-upgrade).

## Scenario 3: The snapshot for any of the publications failed, and the failure can be tracked in Replication Monitor.

**Solution:** 

In the Microsoft SQL Server Replication Monitor, select the failed publication on the **Agents** tab, select and hold (or right-click) the snapshot agent, and then select **Start agent** to generate a snapshot.

## Scenario 4: One of the steps fails in the migration app and you must rerun that step.

If one of the steps fails in the migration app and you must rerun that step, follow these steps.

1. Close the migration app.
1. In the migration app folder, find the **Data** folder.
1. In the **Data** folder, open the **ReplicationMenu.json** file.
1. In the **ReplicationMenu.json** file you can see all the menu options that have the same ID sequence. Find the step that you want to rerun, and then update the **Status** value to **0**.
    > [!IMPORTANT] 
    > Don't change anything else in the **ReplicationMenu.json** file. Also, when you update the file ensure that the migration app isn't in a running state.
1. Open the migration app, and rerun the step.

## Scenario 5: After the publication is created, the replication job fails and exceptions occur.

After the publication is created, the replication job fails and the following exceptions occur.

**Exception 1:**

`> Cannot execute as the database principal because the principal "dbo" does not exist, this type of principal cannot be impersonated, or you do not have permission. (Source: MSSQLServer, Error number: 15517)  
Get help: http://help/15517`

**Exception 2:**

`> The process could not execute 'sp_replcmds' on 'replicationsrv\\MSSQLSERVER2016'. (Source: MSSQL_REPL, Error number: MSSQL_REPL20011)  
Get help: `http://help/MSSQL_REPL20011`
>
> Cannot execute as the database principal because the principal "dbo" does not exist, this type of principal cannot be impersonated, or you do not have permission. (Source: MSSQLServer, Error number: 15517)  
Get help: http://help/15517`

**Solution:** In SQL Server Management Studio (SSMS), open a query window, connect to the source database, and run the following SQL command:

```sql
EXEC sp_changedbowner 'sa'
```

## Scenario 6: The Microsoft Dynamics Lifecycle Services (LCS) status is "Failed", but in the migration app the data upgrade trigger is successful.

**Solution:** In the migration app, run the **'ds'** option. This option reads the LCS environment state and the data upgrade status for every step and substep.

> [!NOTE] 
> If the data upgrade status and the LCS environment status are both **Failed**, the status of step 10 in the [Complete the data replication and upgrade](data-upgrade-self-service.md#complete-the-data-replication-and-upgrade) procedure will be updated to **Resume**. The user can then resume the operation from the point where the upgrade process failed.

## Scenario 7: You want to skip a manually-run step that failed and proceed with further steps.

To skip a manually-run step that failed and proceed with further steps, follow these steps.

1. Close the migration app. 
1. In the migration app folder, find the **Data** folder.
1. In the **Data** folder, open the **ReplicationMenu.json** file.
4. In the **ReplicationMenu.json** file, you can see all the menu options that have the same ID sequence. Find the step that you want to rerun, and update the **Status** value to **1**. By changing the status to **1**, you mark the step as completed.

> [!IMPORTANT] 
> Don't change anything else in the **ReplicationMenu.json** file. Also, when you update the file ensure that the migration app isn't in a running state.

## Scenario 8: You want to migrate from an old version of the console app to the new version.

To migrate from an old version of the console app to the new version, follow these steps.

1. Download the latest version of the console app from LCS.
1. Copy the **/paramsdata.txt** and **/Data/ReplicationMenu.json** files from the old version of the console app, and place them under the same paths in the new version of the console app.
1. Rerun the app.

## Scenario 9: The replication status for any of the publications is shown as "Waiting for snapshot to complete" for more than two hours.

**Solution:** 

In the Replication Monitor, select and hold (or right-click) the publication, and then select **Reinitialize Subscription**.

## Scenario 10: You want to resume the data upgrade.

**Solution:** 

The data upgrade status may not have been updated in the console app. 

To resume the data upgrade, follow these steps. 

1. To learn the status of the console app, employ the **Help** option. This option lists all the menu options and shows the current state.
1. In the [Complete the data replication and upgrade](data-upgrade-self-service.md#complete-the-data-replication-and-upgrade) procedure, if the status of step 10 is **Successful**, run the **'ds'** option in the migration app. This option updates the data upgrade status.

After the **'ds'** option is run, two types of status will be listed: the LCS environment status and the data upgrade status.

 - **Case 1:** If the LCS environment status is **Failed** and the last step of the data upgrade is **Failed**, step 10 will show the **Resume** option.
 - **Case 2:** If the LCS environment status is **Failed** and the last step of the data upgrade is **Completed**, step 10 will show the **Resume** option.
 - **Case 3:** If the LCS environment status is **Deployed** and the last step of the data upgrade is **Completed**, step 10 will show **Successful**.
 - **Case 4:** If the LCS environment status is **Deployed** and the last step of the data upgrade is **In Progress**, step 10 will show **Successful** because the data upgrade job is running in the background.

## Scenario 11: After creating the publication, the snapshot creation fails with errors.

After creating the publication, the snapshot creation fails with the following errors:

`
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
 `
 **Solution:** 
 
 In the Replication Monitor, select and right-click the failed publication, and then select **Generate Snapshot**.

## Scenario 12: Data upgrade PreSync and PostSynch processes are taking a long time. How can I troubleshoot which specific process or job is taking more time?.

**Solution:** 

The **ReleaseUpgradeDB*** framework logs the execution of each script into the **ReleaseUpdateScriptsLog** table. When tuning the performance of the data upgrade process, you can monitor the duration of scripts that are run and easily identify the longest-running process or job in this table.


