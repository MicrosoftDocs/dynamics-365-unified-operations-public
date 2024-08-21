---
title: Monitor the upgrade
description: This article describes how to monitor the upgrade from Microsoft Dynamics 2012 to Dynamics 365 Finance.
author: ttreen
ms.author: ttreen
ms.topic: article
ms.date: 08/20/2024
ms.reviewer: twheeloc
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 
ms.search.form: 2022-04-08
ms.service: dynamics-365-op
---

# Monitor the upgrade

[!include[banner](../includes/banner.md)]

This article provides scripts that can be run to monitor the upgrade process.

## Data upgrade step status
For cloud hosted environments or virtual hard drive (VHD) base upgrades, run the following SQL script to view the steps and status of the upgrade.

For self-service upgrade, the script is the equivalent of running the **DS** command from the Data migration toolkit. 
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

## Database Activity  
It can appear that the upgrade process isn't running as a step is taking some time to complete, and you want to validate that it's running.

Use the following SQL script to check for database activity. This is useful for checking on the database synchronize steps: 
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

## Pre-sync and post-sync scripts
Following queries are used to check the pre-sync and post-sync job statuses.

### Scheduled upgrade jobs
The following script returns the pre-sync or post-sync jobs scheduled to run. This table is populated a few mins after the pre-sync or post-sync step is started.
```SQL
--Scheduled upgrade jobs that will get run
select * from RELEASEUPDATESCRIPTS
 ```
### Upgrade batch job and tasks
The following script is used to see the batch job running the upgrade jobs, and the tasks scheduled in that job.
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
The following script summarizes the status of the tasks. You can see how many tasks have been run, are pending, executing, or failed. 
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
The following script returns the current running upgrade batch tasks and their associated upgrade job class and method. If you don’t see any results, run it again. This is most used for monitoring a longer running upgrade job. 
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

### Upgrade job active summary
During the upgrade the following script can be executed to see the number of pending, completed, executing and failed jobs. It’s similar to the ** Upgrade batch task summary** script above, but data for this is coming from the upgrade framework. 
 ```SQL
--Shows current state and historical summary of jobs waiting or ran
select * from RELEASEUPDATELOG
order by LOGTIME desc
```
### Upgrade job history
After the presync or post-sync jobs are completed, you can check the timing for each of them. This can be useful when you are trying to tune the upgrade and determines what the longer running jobs are. 
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
If the presync or post-sync step fails, run this script for details on the errors. 
```SQL
--Shows upgrade jobs that were in error, including error messages
select * from RELEASEUPDATESCRIPTSERRORLOG
```

