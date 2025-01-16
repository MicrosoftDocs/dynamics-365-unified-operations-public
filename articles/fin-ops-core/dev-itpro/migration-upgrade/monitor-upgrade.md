---
title: Monitor the upgrade
description: This article explains how to monitor the upgrade from Microsoft Dynamics AX 2012 to Dynamics 365 Finance.
author: ttreen
ms.author: ttreen
ms.topic: article
ms.date: 11/14/2024
ms.reviewer: twheeloc
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 
ms.search.form: 2022-04-08
ms.service: dynamics-365-op
---

# Monitor the upgrade

[!include[banner](../includes/banner.md)]

This article provides scripts that you can run to monitor the upgrade process.

## Data upgrade step status

For cloud-hosted environments or virtual hard drive (VHD) base upgrades, run the following SQL script to view the steps and status of the upgrade.

For self-service upgrades, this script is equivalent to running the **DS** command from the Data migration toolkit.

```SQL
--Following query shows the status of the data upgrade servicing 
SELECT StartTime
    ,EndTime
    ,Steps
    ,SubSteps
    ,STATUS
FROM [DBUPGRADE].[DATAUPGRADESTATUS]
ORDER BY EndTime DESC
```

## Database activity

If a step takes a long time to be completed, it can appear that the upgrade process isn't running. In this case, you might want to validate that the process is running.

Run the following SQL script to check for database activity and the database synchronization steps:

- PreReqs-AdditiveDbSync
- PreReqs-PartialDbSync
- DbSync-SyncSchema
- FinalDbSync-SyncSchema

```SQL
SELECT SPID       = er.session_id
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
FROM sys.dm_exec_requests er
    OUTER APPLY sys.dm_exec_sql_text(er.sql_handle) st
    LEFT JOIN sys.dm_exec_sessions ses
    ON ses.session_id = er.session_id
WHERE st.text IS NOT NULL
```

## Synchronize Steps

Use the following script to check the status of the AdditiveSync, PartialSync, DBSync and FinalDBSync steps.

```SQL
IF EXISTS (SELECT * FROM INFORMATION_SCHEMA.TABLES WHERE TABLE_SCHEMA = 'DBUPGRADE' AND TABLE_NAME = 'SERVICINGSTEP')
BEGIN
    WITH DBSyncExecStatsRecords AS (
		SELECT * FROM DBSyncExecStats
		WHERE SyncStep <> 'PartialList, PostTableViewSyncActions'
	),
	ServicingStepsTimestamps AS (
		SELECT 
			MAX(CASE WHEN Path = '/DataUpgrade/PreSync' AND Status = 2 THEN DATEADD(SECOND, -2, ModifiedDateTime) END) AS PreSyncCompletedTime,
			MAX(CASE WHEN Path = '/DataUpgrade/PostSync' AND Status = 2 THEN DATEADD(SECOND, -2, ModifiedDateTime) END) AS PostSyncCompletedTime,
			MAX(CASE WHEN Path = '/DataUpgrade/FinalDbSync/DisableDataUpgradeFlag' AND Status = 2 THEN DATEADD(SECOND, -2, ModifiedDateTime) END) AS FinalDbSyncFlagTime
		FROM DBUPGRADE.SERVICINGSTEP
	),
	SyncRecords AS (
		SELECT 
			T1.RecID,
			CASE
				WHEN T1.SyncStep = 'LegacyIds, AdditiveTableSync' THEN 'PreReqs-AdditiveSync'
				WHEN T1.SyncStep = 'PartialList, LegacyIds' THEN 'PreReqs-PartialSync'
				WHEN T1.SyncStep = 'FullAll' THEN 
					CASE 
						WHEN T2.PostSyncCompletedTime IS NULL AND T1.StartDateTime >= T2.PreSyncCompletedTime THEN 'DbSync-SyncSchema'
						WHEN T2.PostSyncCompletedTime IS NOT NULL AND T1.StartDateTime >= T2.PreSyncCompletedTime AND T1.StartDateTime < T2.PostSyncCompletedTime THEN 'DBSync-SyncSchema'
						WHEN T2.PostSyncCompletedTime IS NOT NULL AND T1.StartDateTime >= T2.PostSyncCompletedTime 
							  AND (T2.FinalDbSyncFlagTime IS NULL OR T1.StartDateTime < T2.FinalDbSyncFlagTime) THEN 'FinalDBSync-SyncSchema'
						ELSE T1.SyncStep + ' - Non Upgrade Sync'
					END
				ELSE T1.SyncStep + ' - Non Upgrade Sync'
			END AS FormattedSyncStep,
			T1.DBSyncActivityId, T1.StartDateTime, T1.FinishTime, T1.Success,
			CASE 
				WHEN T1.FinishTime = '1900-01-01 00:00:00.000' THEN 'Running' -- If FinishTime is '1900-01-01 00:00:00.000', mark as Running
				ELSE CAST(CEILING(DATEDIFF(SECOND, T1.StartDateTime, T1.FinishTime) / 60.0) AS VARCHAR(50)) + ' minutes'
			END AS Duration
		FROM DBSyncExecStatsRecords T1
		CROSS JOIN ServicingStepsTimestamps T2
	)
	SELECT FormattedSyncStep AS SyncStep, DBSyncActivityId, StartDateTime, FinishTime, Success, Duration
	FROM SyncRecords
	ORDER BY RecID DESC
END
ELSE
BEGIN
    PRINT 'Upgrade Not In Progress'
END
```

> [!NOTE]
> The query above shows the status **Running** if there's no end date on the synchronize step. This doesn't always indicate that it's running, you can validate this by running the query in the **Database activity** section above. Run the query multiple times to confirm no database activity. Typically, the database synchronize activity for the upgrade comes from host name SERVICING1. If you haven't seen activity on that server for up to 30 minutes, then it's possible the sync has stalled. In that case, contact Microsoft support for assistance with the DBSyncActivityId value from the query above. 

## Presynchronization and post-synchronization scripts

Use the following queries to check the status of the presynchronization and post-synchronization jobs.

### Scheduled upgrade jobs

The following SQL script returns the presynchronization or post-synchronization jobs that are scheduled to run. The table is populated after the presynchronization or post-synchronization step begins.

```SQL
--Scheduled upgrade jobs that will get run
select * from RELEASEUPDATESCRIPTS
```

### Upgrade batch job and tasks

Run the following SQL script to view the batch job that is running the upgrade jobs, and the tasks that are scheduled in that job.

```SQL
--Find main batch job running the upgrade tasks
select * from batchjob
where caption = 'Data upgrade'
and status = 2

--Check batch tasks for data upgrade job
select caption, classnumber, status, company from batch
where batchjobid in (select recid from batchjob where caption = 'Data upgrade' and status = 2)
```

### Upgrade batch task summary

The following SQL script summarizes the status of the tasks. You can view how many tasks have been run, are pending, are running, or failed.

```SQL
--Check status of batch tasks for data upgrade job
select t1.status, case 
when t1.status = 0 then 'Hold'
when t1.status = 1 then 'Waiting'
when t1.status = 2 then 'Executing'
when t1.status = 3 then 'Error'
when t1.status = 4 then 'Finished'
when t1.status = 5 then 'Ready'
when t1.status = 6 then 'NotRun'
when t1.status = 7 then 'Cancelling'
when t1.status = 8 then 'Cancelled'
when t1.status = 9 then 'Scheduled'
end as ScriptStatus,
count(*) as Total from batch t1
where t1.batchjobid in (select t2.recid from batchjob t2 where t2.caption = 'Data upgrade' and t2.status = 2)
group by t1.status
```

### Upgrade batch task running

The following SQL script returns the upgrade batch tasks that are currently running and their associated upgrade job class and method. If no results are shown, run the script again. This script is mostly used to monitor longer-running upgrade jobs.

```SQL
--Get details upgrade scripts executing
select 
case 
when t1.status = 0 then 'Hold'
when t1.status = 1 then 'Waiting'
when t1.status = 2 then 'Executing'
when t1.status = 3 then 'Error'
when t1.status = 4 then 'Finished'
when t1.status = 5 then 'Ready'
when t1.status = 6 then 'NotRun'
when t1.status = 7 then 'Cancelling'
when t1.status = 8 then 'Cancelled'
when t1.status = 9 then 'Scheduled'
end as ScriptStatus,
t1.caption as BatchTaskCpation, t3.description as ScriptDescription, t3.method as ScriptMethod, t3.classid as ClassId, 
(select name from classidtable where id = t3.classid) as ClassName,
T3.scriptid as ScriptId, t2.company as Company, t1.serverid as ServerId, t1.startdatetime as ScriptStartTime, t1.enddatetime as ScriptEndTime 
from batch t1
join releaseupdatejobstatus T2 on t1.recid = t2.batchid
join releaseupdatescripts T3 on t2.scriptid = t3.scriptid
where t1.status = 2
```

### Upgrade job active summary

During the upgrade, you can run the following SQL script to view the number of pending, completed, running, and failed jobs. This script resembles the **Upgrade batch task summary** script that is described earlier in this article, but the data for it comes from the upgrade framework.

```SQL
--Shows current state and historical summary of jobs waiting or ran
select * from RELEASEUPDATELOG
order by LOGTIME desc
```

### Upgrade job history

After the presynchronization or post-synchronization jobs are completed, you can run the following SQL script to check the timing for each job. This script is useful when you're trying to tune the upgrade and determine what the longer-running jobs are.

```SQL
--Shows the details of each upgrade job method
select * from RELEASEUPDATESCRIPTSLOG

--Shows details for a specific method
select * from RELEASEUPDATESCRIPTSLOG
where METHODNAME = 'allowDupAssociationCreationSequenceNumberIndexMajor'

--Shows a total in mins by company. Note: Due to some global upgrade jobs, you will see timings for company DAT
select company, sum(durationmins) as total_duration_mins
from RELEASEUPDATESCRIPTSLOG
group by company 
order by sum(durationmins) desc
```

### Upgrade job errors

If the presynchronization or post-synchronization step fails, run the following SQL script to get details of the errors.

```SQL
--Shows upgrade jobs that were in error, including error messages
select * from RELEASEUPDATESCRIPTSERRORLOG
```
