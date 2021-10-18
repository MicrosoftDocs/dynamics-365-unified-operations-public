---
# required metadata

title: Query cookbook 
description: This topic describes queries in the SQL Insights tab and how they should be used when troubleshooting performance issues. 
author: meeramahabala
ms.date: 10/06/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
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

## Currently running queries

### Description
Provides a list of all queries that are currently in a state of being executed or blocked on this database, and also the total execution and wait times of each query. Queries that have high execution time and low wait time are often indicative of bad query plans. Queries with high wait time and low execution time are indicative of blocking. If relatively fast operations are being run many times, sometimes they can be found by running this query multiple times in a row and looking for commonly occurring queries with fast execution time.

### Next steps
- If high CPU time is seen, get the query plan for the query, and also see whether other query plans that have been used for this query are more efficient. Consider addressing the issues with a new index, with a change to the query, or, as a last resort, by adding a plan guide.
- If high wait time is seen, view the current blocking and current blocking tree to determine why the query is blocked. This is occasionally addressed by disabling lock escalation or page locks if that is the cause of the blocking. More often, it is addressed by segmenting the work that is being performed to ensure that the same record is not processed by two queries at the same time.

## Get index details

### Description
Provides details about all indexes on a given table. This query is usually used before adding new indexes, to ensure there are no existing indexes that should be altered instead.

### Next steps
- If you are adding a new index, verify that there is not an existing index that should just be adjusted instead. Each new index adds overhead on all write operations. Therefore, new indexes should be added sparingly.
- Existing indexes can occasionally cause blocking if they support page locks, and large processes running at the same time are locking pages that contain records for each process. Disabling page locks should also be done sparingly, because it will degrade write operations that would have benefitted from page locks.

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

## Removed features

| Feature  |  Removed?  |  Note |
|----------|-------------|-------|
|  Current Blocking Tree        |    No        |  Feature continues to be available.     |
| Current Runing Queries         |    No        |    Feature continues to be available.   |
| Current Blocking Statements         |    No        |    Feature continues to be available.   |
|          |            |       |
|          |            |       |
|          |            |       |
|          |            |       |
|          |            |       |
|          |            |       |
|          |            |       |
|          |            |       |
|          |            |       |
|          |            |       |
|          |            |       |
|          |            |       |
|          |            |       |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
