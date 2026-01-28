---
title: Query cookbook
description: Learn about queries in the SQL Insights tab and how they should be used when troubleshooting performance issues.
author: sericks007
ms.author: johnmichalak
ms.topic: article
ms.date: 01/20/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
ms.assetid: eb056816-ccf4-43a5-aed3-cf72543353de
---

# Query cookbook

[!include [banner](../includes/banner.md)]

This article provides details on each query under the **SQL Insights** tab on the **Environment Monitoring** page in Lifecycle Services. It explains how to use these queries when troubleshooting performance problems. For more information about this feature, see [Performance troubleshooting using tools in Lifecycle Services](performancetroubleshooting.md).

## Current blocking

### Description

Lists any currently blocked queries. It also shows the SPID that blocks each query, how long each query has been blocked, and what resource each query is waiting on. Use this query with the query to see the blocking tree, which provides a graphical overview of some of the same information. Blocking by itself is normal in a healthy system. It's only a problem when it becomes excessive or starts degrading business activities.

### Next steps

- Determine which process is blocked, and which process is blocking it and why.
- To resolve blocking, you have two options: let it run and clear naturally, or end the lead blocker process, which rolls back work. Generally, end the lead blocker only in situations where you don't believe it clears naturally (such as a bad query plan), or in situations where a critical process can't run and needs to be completed immediately.
- To avoid the same blocking in the future, use indexes or plan guides, or disable lock escalation and page locks if processes block each other while operating on different records. If processes operate on the same records, the only way to avoid blocking is by refactoring or rescheduling the processes so that they don't operate on the same records at the same time.

## Current blocking tree

### Description

Provides a graphical view of the SPIDs and statements that currently cause blocking or are blocked. Use this query with the current blocking query to see more detailed information. Blocking by itself is normal in a healthy system. It's only a problem when it becomes excessive or starts degrading business activities.

### Next steps

- Determine which process is blocked, and which process is blocking it and why.
- To resolve blocking, you have two options: let it run and clear naturally, or end the lead blocker process, which rolls back work. Generally, end the lead blocker only in situations where you don't believe it clears naturally (such as a bad query plan), or in situations where a critical process can't run and needs to be completed immediately.
- To avoid the same blocking in the future, use indexes or plan guides, or disable lock escalation and page locks if processes block each other while operating on different records. If processes operate on the same records, the only way to avoid blocking is by refactoring or rescheduling the processes so that they don't operate on the same records at the same time.

## Currently running queries

### Description

This report provides a list of all queries that are currently running or blocked on this database. It also shows the total execution and wait times for each query. Queries that have high execution time and low wait time often have bad query plans. Queries with high wait time and low execution time indicate blocking. If relatively fast operations run many times, you can sometimes find them by running this query multiple times in a row and looking for commonly occurring queries with fast execution time.

### Next steps

- If you see high CPU time, get the query plan for the query. Check whether other query plans for this query are more efficient. Consider addressing the problems by creating a new index, changing the query, or, as a last resort, adding a plan guide.
- If you see high wait time, view the current blocking and current blocking tree to determine why the query is blocked. You can occasionally fix this problem by disabling lock escalation or page locks if those settings cause the blocking. More often, you fix the problem by segmenting the work that the query performs to ensure that the same record isn't processed by two queries at the same time.

## End SQL process

### Background

If a SPID consumes too many resources and degrades the operation of other processes, you might want to end the SPID process. Ending the process rolls back the open transaction. Data isn't lost, but you might need to manually restart the process. Rollback can also take a long time and consume numerous resources if the transaction already performed numerous work. Therefore, use this action with caution.

### Next steps

- From the blocking tree and other queries, determine which SPID to end.
- Verify that the processing that the SPID performs can end without causing harm to ongoing business operations.
- Provide the SPID number to end and roll back that operation.

## Removed features

As stated in [Removed or deprecated platform features](../get-started/removed-deprecated-features-platform-updates.md), some Azure SQL reports and Azure SQL actions are removed from Lifecycle Services.

### Removed queries

The following items are removed from the **Queries** tab of **SQL Insights** in Lifecycle Services.

| **Name** | **Removed** | **Notes** |
|-------------------------|-------------------------|-------------------------|
| Current blocking tree | No | Currently available. |
| Current running queries | No | Currently available. |
| Current blocking statements | No | Currently available. |
| Get indexes | Yes | No longer applicable.</br><br>**Reason**</br><ul></br><li>Manual index management is no longer needed as background platform processes handle this task.</li></br></ul></br>**Details**</br><ul></br><li>The system automatically tunes and manages indexes.</li></br></ul> |
| Get lock details | Yes | No longer applicable.</br><br>**Reason**</br>The platform is responsible for:</br><ul></br><li>Optimizing the database's workload and handling any blocking that occurs.</li></br><li>Managing intermittent connectivity problems and providing retries to avoid any concerns with such actions.</li></br></ul></br>**Details**</br><ul></br><li>The platform optimizes workloads and environment to reduce the number of scenarios leading to unresolved process blocking.</li></br><li>Internal monitoring and detection drive deeper root cause analysis into possible other scenarios.</li></br></ul> |
| Get list of query IDs | Yes | No longer applicable.</br><br>**Reason**</br><ul></br><li>With the platform responsible for query tuning and optimization, insights into individual queries, their plans, and their execution statistics are no longer needed.</li></br><li>Query store information is immensely complex and false interpretations can lead to delays in mitigations and root cause identification.</li></br></ul></br>**Details**</br><ul></br><li>The platform automatically tunes and optimizes individual queries, removing the need for manual intervention.</li></br><li>Notify Support about performance problems and include high-level details about the areas and timeframes in which slow performance was observed.</li></br></ul> |
| Get the SQL query plan for a given Plan ID | Yes | Same as above. |
| Get query plans and execution status | Yes | Same as above. |
| Get throttle config | Yes | No longer applicable.</br><br>**Reason**</br><ul></br><li>Throttling at resource governor level is no longer applicable for elastic pool.</li></br></ul></br>**Details**</br><ul></br><li>This report is no longer applicable.</li></br></ul> |
| Get wait stats | Yes | No longer applicable. </br><br>**Reason**</br><ul></br><li>The platform automatically manages database performance and monitoring of the wait statistics is no longer necessary.</li></br><li>While invaluable, wait statistics don't provide all information required for root cause analysis, and the added complexity can lead to incorrect interpretations and delays in performance mitigations.</li></br></ul></br>**Details**</br><ul></br><li>The platform monitors and automatically employs self-healing mechanisms to reduce session wait times.</li></br><li>Notify Support about performance problems and include high-level details about the areas and timeframes in which slow performance was observed.</li></br></ul> |
| List most expensive queries | Yes | No longer applicable. </br><br>**Reason**</br><ul></br><li>The platform targets the top resource-consuming queries in several of its automatic tuning operations, so retrieving these queries is no longer necessary for maintaining system health.</li></br><li>This query might not show the most concerning queries, just the most expensive query at the period of time. Having this list doesn't point to concerns in the environment. This query is expensive, and it's not targeted for troubleshooting custom queries. It provides more of a general check. It currently fails 10% to 30% of the time. </li></br></ul></br>**Details**</br><ul></br><li>The platform monitors and automatically employs self-healing mechanisms to reduce the resource consumption of the most expensive queries.</li></br><li>Notify Support about performance problems and include high-level details about the areas and timeframes in which slow performance was observed.</li></br></ul> |
| Current DTU (Database Transaction Unit) | Yes | No longer applicable.</br><br>**Reason**</br><ul></br><li>DTU reports are no longer necessary as the platform monitors all databases and provides adequate resources for all workloads.</li></br><li>Current DTU reports no longer provide an accurate picture of database health.</li></br></ul></br>**Details**</br><ul></br><li>The platform monitors databases and automatically optimizes the available resources for each workload.</li></br></ul> |
| Current DTU details | Yes | No longer applicable.</br><br>**Reason**</br><ul></br><li>DTU reports are no longer necessary as the platform monitors all databases and provides adequate resources for all customers' workloads.</li></br><li>Current DTU reports no longer provide an accurate picture of database health.</li></br></ul></br>**Details**</br><ul></br><li>The platform monitors databases and automatically optimizes the available resources for customers' workloads.</li></br></ul> |

### Removed actions

The following actions have been removed from the **Actions** tab of **SQL Insights** in Lifecycle Services.

| Name | Removed | Notes |
|-------------------------|-------------------------|-------------------------|
| Create index | Yes | No longer applicable.</br><br>**Reason**</br><ul></br><li>Manual index creation is no longer needed as this is handled by a background platform process.</li></br></ul></br>**Details**</br><ul></br><li>A system background process handles this as required.</li></br></ul> |
| Drop index | Yes | No longer applicable. </br><br>**Reason**</br><ul></br><li>Not included in Data Administration and Management Service (DAMS) because of the periodic nature of finance and operations workloads.</li></br></ul></br>**Details**</br><ul></br><li>The system will automatically tune as required.</li></br></ul> |
| Rebuilt index | Yes | No longer applicable.</br><br>**Reason**</br><ul></br><li>Manual index creation is no longer needed as this is handled by background platform processes.</li></br></ul></br>**Details**</br><ul></br><li>A system background process handles this as required.</li></br></ul> |
| Update statistics | Yes | No longer applicable.</br><br>**Reason**</br><ul></br><li>A platform background process handles index and statistics maintenance.</li></br></ul></br>**Details**</br><ul></br><li>The platform is responsible for index and statistics maintenance.</li></br></ul> |
| Query hint optimization | Yes | No longer applicable.</br><br>**Reason**</br><ul></br><li>The platform handles query hint optimization so customers don't have to do manual tuning.</li></br></ul></br>**Details**</br><ul></br><li>The platform automatically detects the correct hint and applies it to the queries that need optimization.</li></br></ul> |
| Create a plan guide to add table hints | Yes | No longer applicable.</br><br>Query hint optimization is combined with "Create a plan guide to add table hints."</br><br>**Reason**</br><ul></br><li>The platform handles query optimization instead of manual, time-consuming tuning by customers.</li></br><li>DAMS reduces manual efforts in favor of platform automation.</li></br><li>The platform removes usage of plan guides as they're inefficient and difficult to manage.</li></br></ul></br>**Details**</br><ul></br><li>Plan guides are being deprecated in favor of forcing hints through query store.</li></br><li>The platform automatically detects the correct hint and applies it to the queries that need optimization.</li></br></ul> |
| Create a plan guide to force plan | Yes | Same as above. |
| Remove plan guide | Yes | Same as above. |
| List of current plan guide | Yes | No longer applicable.</br><br>**Reason**</br><ul></br><li>The platform handles optimization instead of manual, time-consuming tuning by customers.</li></br><li>DAMS reduces manual efforts in favor of platform automation.</li></br><li>The platform removes usage of plan guides as they're inefficient and difficult to manage.</li></br></ul></br>**Details**</br><ul></br><li>Plan guides are being deprecated in favor of forcing hints through query store.</li></br><li>The platform automatically detects the correct hint and applies it to the queries that need optimization.</li></br></ul> |
| End SQL process | No | Continues to be available.

<!--### Removed live views

The following live views have been removed from the **Live views** tab of **SQL Insights** in Lifecycle Services.

| Name | Removed | Notes |
|-------------------------|-------------------------|-------------------------|
| Common metrics (DTU) | Yes | No longer applicable.</br><br>**Reason**</br><ul></br><li>Current DTU has been removed from queries.</li></br></ul></br>**Details**</br><ul></br><li>See **Current DTU** under **Queries** above.</li></br></ul> |
| Currently executing statements | No | Remains available in Lifecycle Services. |
| Blocking statements | No | Remains available in Lifecycle Services. | -->
