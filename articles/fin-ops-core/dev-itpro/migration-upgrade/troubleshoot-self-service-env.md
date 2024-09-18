---
title: Troubleshoot upgrades to Dynamics 365 Finance + Operations self-service environments
description: Access troubleshooting guidance for upgrades of Microsoft Dynamics AX 2012 to Dynamics 365 Finance + Operations (on-premises) self-service environments.
author: ttreen
ms.author: ttreen
ms.topic: article
ms.date: 04/26/2022
ms.reviewer: johnmichalakffin
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 
ms.search.form: 2022-04-08
ms.service: dynamics-365-op
---
# Troubleshoot upgrades to Dynamics 365 Finance + Operations self-service environments

[!include[banner](../includes/banner.md)]

This article provides troubleshooting guidance for upgrades of Microsoft Dynamics AX 2012 to Dynamics 365 Finance + Operations (on-premises) self-service environments.

## Scenario 1: The migration app prompts you to enter Project-Id and Environment-Id values.

**Solution**

Make sure that the user who is doing the upgrade is part of the project and assigned to one of the following roles: **ProjectOwner**, **EnvironmentAdmin**, or **OperationsAdmin**.

## Scenario 2: Migration app database connectivity failed for the source database server or the target database server.

**Solution**

In the migration app, complete step 1 in the [Data upgrade preparation: Environment setup activity](data-upgrade-self-service.md#complete-the-data-replication-and-upgrade) procedure.

## Scenario 3: The snapshot for any of the publications failed, and the failure can be tracked in Replication Monitor.

**Solution**

In the SQL Server Replication Monitor, on the **Agents** tab, select the failed publication. Select and hold (or right-click) the snapshot agent, and then select **Start agent** to generate a snapshot.

## Scenario 4: One of the steps fails in the migration app, and you must rerun that step.

If one of the steps fails in the migration app, and you must rerun that step, follow these steps.

1. Close the migration app.
1. In the migration app folder, find the **Data** folder.
1. In the **Data** folder, open the **ReplicationMenu.json** file.
1. In the **ReplicationMenu.json** file, you can view all the menu options that have the same ID sequence. Find the step that you want to rerun, and then update the **Status** value to **0**.

    > [!IMPORTANT]
    > Don't change anything else in the **ReplicationMenu.json** file. Additionally, make sure that the migration app isn't in a running state when you update the file.

1. Open the migration app, and rerun the step.

## Scenario 5: After the publication is created, the replication job fails, and exceptions occur.

After the publication is created, the replication job fails, and the following exceptions occur.

**Exception 1**

> Cannot execute as the database principal because the principal "dbo" does not exist, this type of principal cannot be impersonated, or you do not have permission. (Source: MSSQLServer, Error number: 15517)  
Get help: `http://help/15517`

**Exception 2**

> The process could not execute 'sp\_replcmds' on 'replicationsrv\\MSSQLSERVER2016'. (Source: MSSQL\_REPL, Error number: MSSQL\_REPL20011)  
Get help: `http://help/MSSQL_REPL20011`
>
> Cannot execute as the database principal because the principal "dbo" does not exist, this type of principal cannot be impersonated, or you do not have permission. (Source: MSSQLServer, Error number: 15517)  
Get help: `http://help/15517`

**Solution**

In SQL Server Management Studio (SSMS), open a query window, connect to the source database, and run the following SQL command.

```sql
EXEC sp_changedbowner 'sa'
```

## Scenario 6: The Microsoft Dynamics Lifecycle Service status is "Failed," but the data upgrade trigger is successful in the migration app.

**Solution**

In the migration app, run the **'ds'** option. This option reads the status of the Microsoft Dynamics Lifecycle Services environment and the data upgrade status for every step and substep.

> [!NOTE]
> If the data upgrade status and the Lifecycle Services environment status are both **Failed**, the status of step 10 in the [Complete the data replication and upgrade](data-upgrade-self-service.md#complete-the-data-replication-and-upgrade) procedure is updated to **Resume**. You can then resume the operation from the point where the upgrade process failed.

## Scenario 7: You want to skip a manually run step that failed and move on to other steps.

To skip a manually run step that failed and move on to other steps, follow these steps.

1. Close the migration app.
1. In the migration app folder, find the **Data** folder.
1. In the **Data** folder, open the **ReplicationMenu.json** file.
1. In the **ReplicationMenu.json** file, you can view all the menu options that have the same ID sequence. Find the step that you want to rerun, and update the **Status** value to **1**. In this way, you mark the step as completed.

    > [!IMPORTANT]
    > Don't change anything else in the **ReplicationMenu.json** file. Additionally, make sure that the migration app isn't in a running state when you update the file.

## Scenario 8: You want to migrate from an old version of the console app to the new version.

To migrate from an old version of the console app to the new version, follow these steps.

1. Download the latest version of the console app from Lifecycle Services.
1. Copy the **/paramsdata.txt** and **/Data/ReplicationMenu.json** files from the old version of the console app, and put them under the same paths in the new version of the console app.
1. Rerun the app.

## Scenario 9: The replication status for any of the publications is shown as "Waiting for snapshot to complete" for more than two hours.

**Solution**

In the Replication Monitor, select and hold (or right-click) the publication, and then select **Reinitialize Subscription**.

## Scenario 10: You want to resume the data upgrade.

**Solution**

The data upgrade status might not have been updated in the console app.

To resume the data upgrade, follow these steps.

1. To learn the status of the console app, use the **Help** option. This option lists all the menu options and shows the current state.
1. If the status of step 10 in the [Complete the data replication and upgrade](data-upgrade-self-service.md#complete-the-data-replication-and-upgrade) procedure is **Successful**, run the **'ds'** option in the migration app. This option updates the data upgrade status.

After the **'ds'** option is run, two types of status will be listed: the Lifecycle Services environment status and the data upgrade status.

- **Case 1:** If the Lifecycle Services environment status is **Failed**, and the last step of the data upgrade is **Failed**, step 10 shows the **Resume** option.
- **Case 2:** If the Lifecycle Services environment status is **Failed**, and the last step of the data upgrade is **Completed**, step 10 shows the **Resume** option.
- **Case 3:** If the Lifecycle Services environment status is **Deployed**, and the last step of the data upgrade is **Completed**, step 10 shows **Successful**.
- **Case 4:** If the Lifecycle Services environment status is **Deployed**, and the last step of the data upgrade is **In Progress**, step 10 shows **Successful**, because the data upgrade job is running in the background.

## Scenario 11: After the publication is created, snapshot creation fails with errors.

After the publication is created, snapshot creation fails, and the following errors are thrown:

> Error messages:  
Source: Microsoft.SqlServer.Smo  
Target Site: Void PrefetchObjectsImpl(System.Type, Microsoft.SqlServer.Management.Smo.ScriptingPreferences)  
Message: Prefetch objects failed for Database 'AxDB\_ASIA'.  
Stack:    at Microsoft.SqlServer.Management.Smo.Database.PrefetchObjectsImpl(Type objectType, ScriptingPreferences scriptingPreferences)  
          at Microsoft.SqlServer.Replication.Snapshot.SmoScriptingManager.ObjectPrefetchControl.DoPrefetch(Database database)  
          at Microsoft.SqlServer.Replication.Snapshot.SmoScriptingManager.PrefetchObjects(ObjectPrefetchControl\[\] objectPrefetchControls)  
          at Microsoft.SqlServer.Replication.Snapshot.SmoScriptingManager.DoPrefetchWithRetry()  
          at Microsoft.SqlServer.Replication.Snapshot.SmoScriptingManager.DoScripting()  
          at Microsoft.SqlServer.Replication.Snapshot.SqlServerSnapshotProvider.DoScripting()  
          at Microsoft.SqlServer.Replication.Snapshot.SqlServerSnapshotProvider.GenerateSnapshot()  
          at Microsoft.SqlServer.Replication.SnapshotGenerationAgent.InternalRun()  
          at Microsoft.SqlServer.Replication.AgentCore.Run() (Source: Microsoft.SqlServer.Smo, Error number: 0)

**Solution**

In the Replication Monitor, select and hold (or right-click) the failed publication, and then select **Generate Snapshot**.

## Scenario 12: Data upgrade PreSync and PostSync processes are taking a long time, and you want to determine which process or job is taking more time.

**Solution**

The ReleaseUpgradeDB framework logs the execution of each script in the **ReleaseUpdateScriptsLog** table. When you tune the performance of the data upgrade process, you can monitor the duration of scripts that are run. In the table, you can easily identify the longest-running process or job. You can use some of the following queries on the target AxDB to check progress and more.

**Check running processes**

To check running processes in AxDB, use the following query.

```sql
SELECT   SPID       = er.session_id
 ,STATUS         = ses.STATUS
 ,[Login]        = ses.login_name
 ,Host           = ses.host_name
 ,BlkBy          = er.blocking_session_id
 ,DBName         = DB_Name(er.database_id)
 ,CommandType    = er.command
 ,ObjectName     = OBJECT_NAME(st.objectid)
 ,CPUTime        = er.cpu_time
 ,StartTime      = er.start_time
 ,TimeElapsed    = CAST(GETDATE() - er.start_time AS TIME)
 ,SQLStatement   = st.text
FROM    sys.dm_exec_requests er
    OUTER APPLY sys.dm_exec_sql_text(er.sql_handle) st
    LEFT JOIN sys.dm_exec_sessions ses
    ON ses.session_id = er.session_id
WHERE   st.text IS NOT NULL
```

**Check dbupgrade status**

To check the status of the data upgrade servicing, use the following query.

```sql
SELECT StartTime,EndTime,Steps,SubSteps,STATUS FROM [DBUPGRADE].[DATAUPGRADESTATUS]
ORDER BY EndTime DESC
```

**Check batch job–related details**

To check batch job–related details, use the following queries.

```sql
select RECID, CAPTION, * from batchjob where STATUS=2
```

```sql
select * from batch where BATCHJOBID = _jobid_ and status=2
```

```sql
select serverid, status, caption, datediff(mi, startdatetime, ENDDATETIME), startdatetime, ENDDATETIME ,* from batchhistory where Batchjobid = _jobid_
```

```sql
select serverid, status, caption, Classnumber, datediff(mi, startdatetime, ENDDATETIME), _timetakeninmin, startdatetime, ENDDATETIME ,* from batch where batchjobid = _jobid_
```

```sql
select * from CLASSIDTABLE where ID in (select distinct classnumber from batch where batchjobid= _jobid_ )
```
