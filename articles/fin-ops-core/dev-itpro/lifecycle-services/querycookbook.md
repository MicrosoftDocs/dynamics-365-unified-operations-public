---
# required metadata

title: Query cookbook 
description: This topic describes queries in the SQL Insights tab and how they should be used when troubleshooting performance issues. 
author: meeramahabala
ms.date: 11/09/2021
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

## End SQL process

### Background
If a SPID is consuming too many resources and degrading the operation of other processes, it might be beneficial to end the SPID process. This will cause the open transaction to roll back, meaning that data should not be lost, but the process might need to be manually restarted. Note that rollback can also take a long time and consume a lot of resources if the transaction has already performed a lot of work. Therefore, this action should be used with caution.

### Next steps
- From the blocking tree and other queries, determine which SPID should end.
- Verify that the processing that is being performed by the SPID can end without causing harm to ongoing business operations.
- Provide the SPID number to end, and roll back that operation.

## Removed features
As stated in [Removed or deprecated platform features](../get-started/removed-deprecated-features-platform-updates.md), some Azure SQL reports and Azure SQL actions have been removed from Lifecycle Services (LCS).

### Removed queries
The following items have been removed from the **Queries** tab of **SQL Insights** in LCS.

| **Name** | **Removed** | **Notes** |
|-------------------------|-------------------------|-------------------------|
| Current blocking tree | No | Currently available. |
| Current running queries | No | Currently available. |
| Current blocking statements | No | Currently available. |
| Get indexes | Yes | No longer applicable.</br><br>**Reason**</br><ul></br><li>Manual index management is no longer needed as this is handled by background platform processes.</li></br></ul></br>**Details**</br><ul></br><li>The system automatically tunes and manages indexes.</li></br></ul> |
| Get lock details | Yes | No longer applicable.</br><br>**Reason**</br>The platform is responsible for:</br><ul></br><li>Optimizing the database's workload and handling any blocking that may occur.</li></br><li>Managing intermittent connectivity issues and provides retries to avoid any concerns with such actions.</li></br></ul></br>**Details**</br><ul></br><li>The platform optimizes workloads and environment to reduce the number of scenarios leading to unresolved process blocking.</li></br><li>Internal monitoring and detection will drive deeper root cause analysis into possible additional scenarios.</li></br></ul> |
| Get list of query ID's | Yes | No longer applicable.</br><br>**Reason**</br><ul></br><li>With the platform being responsible for query tuning and optimization, insights into individual queries, their plans, and their execution statistics are no longer needed.</li></br><li>Query store information is immensely complex and false interpretations can lead to delays in mitigations and root cause identification.</li></br></ul></br>**Details**</br><ul></br><li>The platform will automatically tune and optimize individual queries, removing the need for manual intervention.</li></br><li>Notify Support about performance issues and include high-level details about the areas and timeframes in which slow performance was observed.</li></br></ul> |
| Get the SQL query plan for a given Plan ID | Yes | Same as above. |
| Get query plans and execution status | Yes | Same as above. |
| Get throttle config | Yes | No longer applicable.</br><br>**Reason**</br><ul></br><li>Throttling at resource governor-level is no longer applicable for elastic pool.</li></br></ul></br>**Details**</br><ul></br><li>This report is no longer applicable.</li></br></ul> |
| Get wait stats | Yes | No longer applicable. </br><br>**Reason**</br><ul></br><li>Database performance is automatically managed by the platform and monitoring of the wait statistics is no longer necessary.</li></br><li>While invaluable, wait statistics do not provide all information required for root cause analysis and the added complexity can lead to incorrect interpretations and delays in performance mitigations.</li></br></ul></br>**Details**</br><ul></br><li>The platform will monitor and automatically employ self-healing mechanisms to reduce session wait times.</li></br><li>Notify Support about performance issues and include high-level details about the areas and timeframes in which slow performance was observed.</li></br></ul> |
| List most expensive queries | Yes | No longer applicable. </br><br>**Reason**</br><ul></br><li>The platform targets the top resources consuming queries in several of its automatic tuning operations, meaning the retrieval of these queries are no longer necessary for maintaining system health.</li></br><li>This query may not show the most concerning queries, just the most expensive query at the period of time. Having this list will not point to concerns in the environment. This is a very expensive query, not targeted for troubleshooting custom queries. It provides more of a general check. It currently fails 10 to 30% of the time. </li></br></ul></br>**Details**</br><ul></br><li>The platform will monitor and automatically employ self-healing mechanisms to reduce the resource consumption of the most expensive queries.</li></br><li>Notify Support about performance issues and include high-level details about the areas and timeframes in which slow performance was observed.</li></br></ul> |
| Current DTU (Database Transaction Unit) | Yes | No longer applicable.</br><br>**Reason**</br><ul></br><li>DTU reports are no longer necessary as the platform monitors all databases and provides adequate resources for all workloads.</li></br><li>Current DTU reports no longer provide an accurate picture of database health.</li></br></ul></br>**Details**</br><ul></br><li>The platform will monitor databases and automatically optimize the available resources for each workload.</li></br></ul> |
| Current DTU details | Yes | No longer applicable.</br><br>**Reason**</br><ul></br><li>DTU reports are no longer necessary as the platform monitors all databases and provides adequate resources for all customers' workloads.</li></br><li>Current DTU reports no longer provide an accurate picture of database health.</li></br></ul></br>**Details**</br><ul></br><li>The platform will monitor databases and automatically optimize the available resources for customers' workloads.</li></br></ul> |

### Removed actions

The following action have been removed from the **Actions** tab of **SQL Insights** in LCS.

| Name | Removed | Notes |
|-------------------------|-------------------------|-------------------------|
| Create index | Yes | No longer applicable.</br><br>**Reason**</br><ul></br><li>Manual index creation is no longer needed as this is handled by a background platform processes.</li></br></ul></br>**Details**</br><ul></br><li>A system background process will handle this as required.</li></br></ul> |
| Drop index | Yes | No longer applicable. </br><br>**Reason**</br><ul></br><li>Not included in Data Administration and Management Service (DAMS) because of the periodic nature of Finance and Operations workloads.</li></br></ul></br>**Details**</br><ul></br><li>The system will automatically tune as required.</li></br></ul> |
| Rebuilt index | Yes | No longer applicable.</br><br>**Reason**</br><ul></br><li>Manual index creation is no longer needed as this is handled by background platform processes.</li></br></ul></br>**Details**</br><ul></br><li>A system background process will handle this as required.</li></br></ul> |
| Update statistics | Yes | No longer applicable.</br><br>**Reason**</br><ul></br><li>A platform background process handles index and statistics maintenance.</li></br></ul></br>**Details**</br><ul></br><li>The platform is responsible for index and statistics maintenance.</li></br></ul> |
| Query hint optimization | Yes | No longer applicable.</br><br>**Reason**</br><ul></br><li>The platform handles query hint optimization so customers don't have to do manual tuning.</li></br></ul></br>**Details**</br><ul></br><li>The platform automatically detects the correct hint and applies it to the queries that need optimization.</li></br></ul> |
| Create a plan guide to add table hints | Yes | No longer applicable.</br><br>Query hint optimization is combined with "Create a plan guide to add table hints".</br><br>**Reason**</br><ul></br><li>The platform handles query optimization instead of manual, time-consuming tuning by customers.</li></br><li>DAMS reduces manual efforts in favor of platform automation.</li></br><li>The platform removes usage of plan guides as they are inefficient and difficult to manage.</li></br></ul></br>**Details**</br><ul></br><li>Plan guides are being deprecated in favor of forcing hints through query store.</li></br><li>The platform automatically detects the correct hint and applies it to the queries that need optimization.</li></br></ul> |
| Create a plan guide to force plan | Yes | Same as above. |
| Remove plan guide | Yes | Same as above. |
| List of current plan guide | Yes | No longer applicable.</br><br>**Reason**</br><ul></br><li>The platform handles optimization instead of manual, time-consuming tuning by customers.</li></br><li>DAMS reduces manual efforts in favor of platform automation.</li></br><li>The platform removes usage of plan guides as they are inefficient and difficult to manage.</li></br></ul></br>**Details**</br><ul></br><li>Plan guides are being deprecated in favor of forcing hints through query store.</li></br><li>The platform automatically detects the correct hint and applies it to the queries that need optimization.</li></br></ul> |
| End SQL process | No | Continues to be available.

<!--### Removed live views

The following live views have been removed from the **Live views** tab of **SQL Insights** in LCS.

| Name | Removed | Notes |
|-------------------------|-------------------------|-------------------------|
| Common metrics (DTU) | Yes | No longer applicable.</br><br>**Reason**</br><ul></br><li>Current DTU has been removed from queries.</li></br></ul></br>**Details**</br><ul></br><li>See **Current DTU** under **Queries** above.</li></br></ul> |
| Currently executing statements | No | Remains available in LCS. |
| Blocking statements | No | Remains available in LCS. | -->
