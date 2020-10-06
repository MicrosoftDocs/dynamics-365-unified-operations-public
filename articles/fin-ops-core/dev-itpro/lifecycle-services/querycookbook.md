---
# required metadata

title: Query cookbook 
description: This topic provides details on each query under the SQL Insights tab on the Environment Monitoring page in LCS and how they should be used when troubleshooting performance issues. 
author: meeramahabala
manager: AnnBe
ms.date: 10/02/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 267184
ms.assetid: eb056816-ccf4-43a5-aed3-cf72543353de
ms.search.region: Global
# ms.search.industry: 
ms.author: meeram
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Query cookbook 

[!include [banner](../includes/banner.md)]

This topic provides details on each query under the **SQL Insights** tab on the **Environment Monitoring** page in Lifecycle Services (LCS) and how they should be used when troubleshooting performance issues. For details about this feature, see [Performance troubleshooting using tools in Lifecycle Services (LCS)](performancetroubleshooting.md).

## Current blocking

### Description
Lists any currently blocked queries, and also the SPID that is blocking them, how long they have been blocked, and what resource they are waiting on. This can be used in conjunction with the query to see the blocking tree, which provides a graphical overview of some of the same information. Blocking by itself is normal in a healthy system and is only a problem when it becomes excessive or starts degrading business activities.

### Next steps
- Determine which process is blocked, and which process is blocking it and why.
- To resolve blocking, the only two options are to let it run and clear naturally, or to end the lead blocker process, which will roll back work. Generally, the lead blocker should only end in situations where it is not believed that it will clear naturally (such as a bad query plan), or in situations where a critical process is unable to run and needs to be completed immediately.
- To avoid the same blocking in the future, you can use indexes or plan guides, or disable lock escalation and page locks if processes are blocking each other while operating on different records. If processes are operating on the same records, the only way to avoid blocking is by refactoring or rescheduling the processes so that they do not operate on the same records at the same time.

## Current blocking tree

### Description
Provides a graphical view of the SPIDs and statements that are currently causing blocking or being blocked. This can be used in conjunction with the current blocking query to see more detailed information. Blocking by itself is normal in a healthy system and is only a problem when it becomes excessive or starts degrading business activities.

### Next steps
- Determine which process is blocked, and which process is blocking it and why.
- To resolve blocking, the only two options are to let it run and clear naturally, or to end the lead blocker process, which will roll back work. Generally, the lead blocker should only end in situations where it is believed that it will not clear naturally (such as a bad query plan), or in situations where a critical process is unable to run and needs to be completed immediately.
- To avoid the same blocking in the future, you can use indexes or plan guides, or disable lock escalation and page locks, if processes processes are blocking each other while operating on different records. If processes are operating on the same records, the only way to avoid blocking is by refactoring or rescheduling the processes so that they do not operate on the same records at the same time.

## Current DTU

### Description
Provides a detailed breakdown of the current DTU by component. DTU is a percentage measure of total SQL load and is reported as the maximum value of any of the subcomponents. Use this query to determine which subcomponent is causing high DTU. High CPU is often related to bad query plans. High Data I/O is often related to large imports or exports. A high Log Write percentage is often related to bulk processes, such as reporting, which make changes to large numbers of intermediate records.

### Next steps
- If high CPU is the cause of high DTU, view the currently running queries or most expensive queries for the last hour. To address the issue, get better query plans by adding indexes, changing the query, or, as a last resort, adding plan guides.
- If high Data I/O is the cause of high DTU, look at currently running queries and also current batch jobs, and try to determine what might be writing large volumes of data. Consider scheduling those processes to run outside of business hours.
- If high Log I/O is the cause of high DTU, look at currently running queries and also current batch jobs to determine what might be doing large amounts of intermediate processing. Often, high Log I/O is caused by the use of real fully logged tables as pseudo-temp tables during processing, such as in reporting. Address this by running those processes outside of business hours or by changing the processes.

## Currently running queries

### Description
Provides a list of all queries that are currently in a state of being executed or blocked on this database, and also the total execution and wait times of each query. Queries that have high execution time and low wait time are often indicative of bad query plans. Queries with high wait time and low execution time are indicative of blocking. If relatively fast operations are being run many times, sometimes they can be found by running this query multiple times in a row and looking for commonly occurring queries with fast execution time.

### Next steps
- If high CPU time is seen, get the query plan for the query, and also see whether other query plans that have been used for this query are more efficient. Consider addressing the issues with a new index, with a change to the query, or, as a last resort, by adding a plan guide.
- If high wait time is seen, view the current blocking and current blocking tree to determine why the query is blocked. This is occasionally addressed by disabling lock escalation or page locks if that is the cause of the blocking. More often, it is addressed by segmenting the work that is being performed to ensure that the same record is not processed by two queries at the same time.

## Get fragmentation details

### Description
Fragmentation is when the records are not stored contiguously inside of the page. When there is unused space between records on a page, which occurs through data modification that is made against the table and to the indexes defined on the table, this is SQL index fragmentation. Dynamics 365 Finance and Operations apps use SQL Azure DB premium SKUs which are backed by SSDs. This means that the fragmentation does not cause the same level of issues as on a database that is backed by a SCSI drive, but it still it could cause slower performance. With higher fragmentation, there is a higher chance that it could affect the performance of queries that use this fragmented table/index.

### Next steps
- This query shows the list of tables, indexes with their fragmentation percentage, and a recommendation to either REBUILD the index or REORG the index. When you rebuild or reorg an index it will pack the records next to each other and avoid gaps in between, thus reducing the fragmentation.

## Get index details

### Description
Provides details about all indexes on a given table. This query is usually used before adding new indexes, to ensure there are no existing indexes that should be altered instead.

### Next steps
- If you are adding a new index, verify that there is not an existing index that should just be adjusted instead. Each new index adds overhead on all write operations. Therefore, new indexes should be added sparingly.
- Existing indexes can occasionally cause blocking if they support page locks, and large processes running at the same time are locking pages that contain records for each process. Disabling page locks should also be done sparingly, because it will degrade write operations that would have benefitted from page locks.

## Get lock details

### Description
Provides a list of all locks held by a given SPID. This is useful when a blocking tree shows that a SPID is part of a blocking chain. Sometimes, this query will reveal that page locks or lock escalation are the cause of the blocking. Other times this query is useful for seeing how many keylocks in given tables are being held.

### Next steps
- If page locks or lock escalation are causing issues, they can be disabled. However, this should be done cautiously, because there are valid cases where lock escalation and page locks are needed for good performance.
- If a SPID is just holding large numbers of locks, reducing the amount of data processed within one transactional scope can reduce the number of locks and therefore the chances of experiencing blocking and deadlocks.

### Parameters
The SPID can be obtained either from the list of currently running queries or through the list of current blocking queries. No historical information about SPIDs is available because the SPID ID is only valid while the SPID is currently being executed.

## List of current plan guides

### Description
Provides a list of all plan guides currently installed in the database.

### Next steps
- You can determine whether a query plan was created based on a plan guide by looking in the query plan XML. If the plan was generated based on a plan guide, the plan guide name will be specified in the XML.
- If a plan guide is installed but is not being used, verify that the SQL statement text and parameter list for the plan guide are identical to the actual query. Any differences, even in whitespace, will stop a plan guide from being used.

## Get list of query ID&#39;s

### Description
If query text is known to be causing a problem, this query can be used to find the query ID for that query. This can occur if the SQL statement is showing up in an error message, in tracing, or in telemetry. After the query ID for the statement is found, it can be used for other operations, such as finding query plans or applying plan guides.

### Next steps
- After the query ID for a given statement is found, it can be used to find previous plans for that query so that it can be optimized.

### Parameters
- Provide a substring of the query statement, such as &quot;%FROM GENERALJOURNALENTRY T1%&quot;.

## Get XML for a given plan ID

### Description
This provides the SQL plan in XML format for a given plan ID.

### Next steps
- Save the XML as a .sqlplan file, and open it in SQL Server Management Studio or other plan reading tools. From the query plan, you can often find optimizations, such as index additions, that will be beneficial.
- The plan might have an index recommendation listed, but be cautious when applying those indexes. SQL will often recommend creating indexes with excessive numbers of columns to optimize a single query, which can have a negative impact on other queries or the system as a whole. View these recommended indexes as hints to begin analysis, not as something to be directly applied.

### Parameters
- The plan ID can be obtained from a variety of sources, such as currently running queries. If you only have a query ID, you can use &quot;get a list of query plans for a query&quot; to figure out which plan IDs have been used for a query.

## Get query plan and execution stats

### Description
Provides a list of plans and execution statistics for a given query. This is useful for determining whether a query is obtaining multiple query plans with different performance characteristics over time.

### Next steps
- If a query is getting multiple query plans with vastly different performance characteristics, start by retrieving and analyzing the plans to determine what is different and why one is far better than others.
- In order for SQL to use a better query plan, the best solution is to make index changes or add query hints directly in code.
- If indexes and query hints are not enough, as a last resort, a plan guide can be added to force the better plans always to be used. Be careful when using a plan guide, because sometimes a query plan is fast for some parameter values but overly slow for other parameter values.

### Parameters
- The **query ID** can be obtained from multiple other operations, such as currently running queries, current blocking queries, most expensive queries, and query by statement text.
- The **time interval** in terms of hours will often be specified as &quot;168&quot; to show all plans for the last week or &quot;24&quot; to show all plans for the last day. Often, plans will change multiple times per week but might be stable for a few days. Therefore, selecting larger intervals here is often advantageous.

## Get wait stats

### Description
Provides information about what a given query plan has waited on in a given time range. This is useful when a query regularly takes longer than it should, and you have been unable to determine whether it is CPU time or blocking. Similarly, if you see blocking but need to know what kind it is, this will provide that information.

### Next steps
- If a plan is primarily waiting on CPU, the plan is just inefficient and needs to be fixed through the addition of indexes or hints, or by restructuring the query.
- If it is waiting on lock, the query is experiencing blocking. This is more difficult to determine unless you can see the blocking happening actively through the blocking tree query. In this case, the next step is to evaluate the records that are being edited and try to determine what other processes could be editing the same records at the same time. Often, the same query running in multiple threads at the same time will block itself.
- If it is waiting on I/O or latch, there are likely either large volumes of data being transferred or large numbers of small transactions. If possible, perform writes in small batches instead of just one record per transaction.

### Parameters
- The plan ID can be obtained from a variety of sources, including currently running queries and the most expensive queries. If you have a query ID, you can get plan IDs by using the query to get a list of plans for that query.
- Ideally, the time range should target a specific time when an issue was occurring. For instance, if DTU was high for an hour, you should target just that hour of execution.

## List most expensive queries

### Description
Provides a list of the most expensive queries during the specified period. The decision about which attribute should be considered when computing most expensive queries can also be provided. This is often used when high DTU is seen for a period, to determine which query is causing the high DTU. In order to use this query effectively, it is important to determine which DTU component is being addressed.

### Next steps
- View the most expensive queries by total CPU to find queries that are causing high DTU utilization. These queries are usually fixed through indexes, query changes, or, as a last resort, plan guides.
- View the most expensive queries by total duration to find queries that might be slowing down the user experience. If these queries also have high total CPU, fix the query plans. If they have low CPU, it is likely the result of blocking.

### Parameters
- For the number of hours, specify &quot;0&quot; if you are looking at currently occurring issues, such as currently high DTU. This will provide results for the current hour. If you are looking for generally high DTU over time, specify either &quot;24&quot; for the last day or &quot;168&quot; for the last week.
- For the ordering, select &quot;total cpu&quot; to find high DTU impact for recurring queries. Select &quot;average duration&quot; to find queries that are not run often but that might be slow. Select &quot;total duration&quot; to find recurring queries that might be slowing down users.

## Create non-unique index on table

### Background
Indexes should generally be created through the standard metadata package and database synchronization. This ensures that Sandbox and PROD, and any other environments, always share a common definition. Occasionally, it is necessary to install a new non-unique index at runtime to mitigate an ongoing outage or issue where a regular deployment would take too long. This action can be used to install that non-unique index.

### Next steps
- After specifying the index to create, the next step should be to migrate that same index definition to the next available official metadata release.
- Duplicate indexes generally do not cause any noticeable issues. Therefore, leave the manually created index in the system until after the official index has been completely rolled out.

### Parameters
- The index name is any unique string not currently in use by an existing index on this table. For easy identification, it is recommended but not required that the index name follow the format PERF\_IDX\_\&lt;tablename\&gt;\_\&lt;number\&gt;. For instance, an index might be named PERF\_IDX\_LEDGERJOURNALTRANS\_1.
- The columns parameter is a comma-separated list of physical column names in the order that they should appear in.
- The included columns parameter is a comma-separated list of physical column names in the order that they should appear in. If no included columns must be specified, leave this parameter blank.

## Create a plan guide to force Plan ID

### Description
SQL will recompute a new plan each time the plan cache is flushed, such as when an update of statistics runs. The plan that is chosen is based on &quot;sniffing&quot; the parameters of the first execution of that query. After that, the same plan will be used, regardless of parameters. For this reason, the same query might sometimes get multiple plans, some of which are far worse than others for given data distributions. This action can be used to force SQL to use a specific plan, regardless of which parameters are sniffed. Note that this action applies only to the database that it is executed on. Therefore, it should be used as a last resort, after the addition of indexes, hints, or code changes that will flow between development and production environments.

### Next steps
- After the list of plan IDs and execution statistics for a specific query ID are found, the SQL plan for each ID should be downloaded and analyzed. After the best plan is determined, this script can be used to force that plan to be used, regardless of parameters.

### Parameters
- The force\_plan\_id parameter is the ID of the plan that should be used going forward. This can be found from the query to get all plan IDs for a given query. Be sure to validate that the XML of the plan is a good plan before forcing, because forcing a bad plan can have negative effects.
- The name parameter is any unique string not currently used by an existing plan guide.
- The statement parameter is the SQL statement that should be forced. This can be obtained from many other queries, including currently running queries and most expensive queries. Ensure that this is copied precisely, including whitespace, because differences in whitespace will cause the plan guide not to work. Also, do not include the parameters for the query in this text, because they are specified separately. For instance, on a select query, the first characters of the statement should always be &quot;SELECT&quot;.
- The params parameter is the set of @P1, @P2, and so on, parameters for the query. These can be obtained from other queries, including currently running queries and most expensive queries. When pasting in the parameters, remove the outer parenthesis. For instance, paste in &quot;@P1 int,@P2 nvarchar(21)&quot;. If there are no parameters for the query, leave this value blank.

## Create a plan guide to add table hints

### Description
SQL will recompute a new plan each time the plan cache is flushed, such as when an update of statistics runs. The plan that is chosen is based on &quot;sniffing&quot; the parameters of the first execution of that query. After that, the same plan will be used, regardless of parameters. For this reason, the same query might sometimes get multiple plans, some of which are far worse than others for given data distributions. This action can be used to add specific hints to the query. This is different than forcing a plan guide, because SQL will still perform parameter sniffing and occasionally select different plans. However, the query hints will be applied in those plan computations. Note that this action applies only to the database that it is executed on. Therefore, it should be used as a last resort, after the addition of indexes, hints, or code changes that will flow between development and production environments.

### Next steps
- Usually, query hints are determined after looking through multiple different query plans for a given query. For example, if an index seek on a table always outperforms a scan, it might be beneficial to add a FORCESEEK hint.
- After hints have been determined and tested locally, use this action to install a plan guide that will add those query hints to future executions of the query.

### Parameters
- The name parameter is any unique string not currently used by an existing plan guide.
- The statement parameter is the SQL statement that should be forced. This can be obtained from many other queries, including currently running queries and most expensive queries. Ensure that this is copied precisely, including whitespace, because differences in whitespace will cause the plan guide not to work. Also, do not include the parameters for the query in this text, because they are specified separately. For instance, on a select query the first characters of the statement should always be &quot;SELECT&quot;.
- The params parameter is the set of @P1, @P2, and so on, parameters for the query. These can be obtained from other queries, including currently running queries and most expensive queries. When pasting in the parameters, remove the outer parenthesis. For instance, paste in &quot;@P1 int,@P2 nvarchar(21)&quot;. If there are no parameters for the query, leave this value blank.
- The hints to apply can be tested locally by just manually adding them to the end of a query. If table aliases are used, they should match the table aliases in the statement text.

## Drop index

### Background
Usually, extra indexes on a table only add minor incremental costs. But in some situations, such as high-throughput tables, the existence of an extra index can cause large performance degradation. The correct way to remove indexes is to remove them from metadata. But if they need to be removed more aggressively to mitigate an ongoing issue, this action can be used.

### Next steps
- From the query to list all indexes for a table, determine the index name to drop.
- Verify that no other workloads will be negatively affected by removing this index. This is a dangerous operation to perform and might cause other workloads to regress.
- Provide the table and the index name to drop.
- Apply the same change in other environments, such as DEV and Sandbox, ideally by removing the index in metadata to keep all environments in sync.

## End SQL process

### Background
If a SPID is consuming too many resources and degrading the operation of other processes, it might be beneficial to end the SPID process. This will cause the open transaction to roll back, meaning that data should not be lost, but the process might need to be manually restarted. Note that rollback can also take a long time and consume a lot of resources if the transaction has already performed a lot of work. Therefore, this action should be used with caution.

### Next steps
- From the blocking tree and other queries, determine which SPID should end.
- Verify that the processing that is being performed by the SPID can end without causing harm to ongoing business operations.
- Provide the SPID number to end, and roll back that operation.

## Disable/enable page locks and lock escalation

### Background
In many situations, SQL will either take page locks (locking a full page at a time) or escalate to entire table locks (locking the whole table). This enables SQL to perform actions that edit a high volume of rows more efficiently. However, this can cause problems and unnecessary contention in certain workloads. Consider two large posting jobs, each running for 10 minutes and editing different rows of data that happen to reside on the same physical data page. This might cause the two postings to serialize and to take 20 minutes because of the contention. This query can be used to disable lock escalation and page locks for a given table. It should be used cautiously, however, because there are valid reasons for SQL to use page locks and lock escalation.

### Next steps
- After determining that unnecessary contention is being experienced on a given table because of lock escalation or page locks, use this query to disable those options.

### Parameters
- The table name is the physical name of the table.
- The value of the lock escalation and page locks is either &quot;ON&quot; or &quot;OFF&quot;.

## Rebuild index

### Background
Over time, as processes edit existing records and write new records into tables, indexes might become fragmented. This increases the amount of I/O necessary to process the same number of records, and might cause performance degradation. This operation will rebuild indexes to reduce page fragmentation. This is an expensive operation and has been known to cause contention while running. Therefore, the environment should be monitored while this operation is running.

### Next steps
- Monitor blocking and DTU in the system while this operation is running. If the system degrades unacceptably, consider ending this operation.

## Remove plan guide

### Background
If plan guides have been installed and are having a negative impact, or if they just are not working, it might be necessary to remove a plan guide. This query enables removal of an existing plan guide. Note that removing a plan guide will not affect any currently running queries until the next time they are executed.

### Next steps
- After determining which plan guide should be removed, specify the name of the plan.

### Parameters
- The list of existing plan guides and associated names can be found from the list of current plan guides query.

## Update statistics on table

### Background
Updates statistics on the specified table. Occasionally, statistics can be found to be out of date and to be causing query plan issues, such as after an import process that has skewed the statistics of the table. Note that this action will have a significant performance overhead while running and has also been known to cause blocking on queries that use the same table. Therefore, it should be used sparingly and monitored while running to ensure that the system does not degrade.

### Next steps
- While running this query, monitor both current blocking and current DTU to ensure that system performance does not degrade unacceptably. If it does, consider ending the update statistics command.

### Parameters
- The table name parameter is the physical name of the table to update statistics for.
