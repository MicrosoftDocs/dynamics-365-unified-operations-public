---
title: Purge from history (Preview)
description: Learn about how to purge data from history table in Microsoft Dynamics 365.
author:  weijiesa
ms.author: 
ms.topic: how-to
ms.date: 
ms.custom:
ms.reviewer: 
---

# Purge From History (Preview)

This article describes how to purge data from history table in Microsoft Dynamics 365.

The ‘Archive with Dataverse long term retention’ feature decreases the space used by customers in their FnO database. This reduction is accomplished by reducing the indexing on the relevant data as it gets moved to the history tables for archiving. This minimizes the storage space for cold-to-likewarm data, but, eventually, this archived data grows so cold that it is no longer needed. At this point, customers can purge their archived data from the history tables to get the full benefit of the ‘Archive with Dataverse long term retention’ feature. 

## Prerequisites

If your system doesn't already include the features described in this article, go to the [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) workspace and turn on the following feature:

- (Preview) Purge From History Archive Feature

The following prerequisites must be met before you execute purge data from history table:
-  Only an archive job must been completed successfully, then user can select that archival job to have the data associated with it be purged from history table.
-  Users must select at least one archival job before they can click “Delete history (Preview)”.

 > [!NOTE]
 > If an archival job is being restored or is scheduled to be restored, then a user can’t purge the data associated with that archival job.

## Purge data from history table

To create a purge job to deleta data from history table,follow these steps.

1. Go to **System administration** \> **Archive with Dataverse long term retention** to open the **Archive with Dataverse long term retention** workspace.
2. Select an completed Archive Job or multiple completed Archive Jobs of the same functional secnarios.
3. Select **Delete history（Preview）** to open a warning popup with explicit confirmation message, confirm and submit the purge job.

## Purge job status
1. When a purge job can’t be executed instantly, its Job status shows 'Deletion queued'.
1. When a purge job is being executed, its Job Status shows to 'Deletion in progress'.
1. When a purge job has been completed, its Job Status shows to 'Deleted',value of field 'Exists in history data' equal to 'No' and value of field 'Results' shows the number of records deleted.

## Frequent Asked Questions

### What is the "Purge from History" feature? 
The Purge from History feature enables users to permanently delete historical data from operational history tables after it has been successfully archived. This ensures the operational database remains streamlined and performs efficiently while retaining the archived data securely in Dataverse long-term retention storage for regulatory and compliance purposes. 

### Why was this feature introduced? 
This feature addresses the need to fully optimize storage and database performance by removing redundant records from history tables. While the existing Archive with Long-Term Retention feature moved inactive data to history tables and Dataverse, the lack of a mechanism to delete data from history tables meant organizations could not achieve maximum storage savings. The Purge from History feature resolves this by completing the data lifecycle. 
 
### What happens to the archived data in Dataverse during the purge? 
The purge process only removes data from the operational history tables in Dynamics 365 Finance. The archived data in Dataverse long-term retention remains unaffected and securely accessible. Users can still retrieve archived records stored in Dataverse for compliance and reporting purposes. 

### Who can use the "Purge from History" feature? 
The feature is available to administrators who have access to the Archiving workspace in Dynamics 365.  

### What is the eligibility criteria for purging data? 
The Purge from History feature is designed to work only with data from completed archive jobs. If an archival job is still in progress or has not been completed successfully, the "Delete History Data" button will remain disabled to prevent accidental data deletion. 

### Can multiple purge jobs be scheduled at the same time? 
Yes, the feature supports scheduling multiple purge jobs to run simultaneously on different archival scenarios (e.g. general ledger and sales orders). This allows users to clean up history tables for several completed archive jobs in a single operation, improving efficiency. 

### How can I track the progress of a purge job? 
The purge process is fully transparent, with detailed logs available in the Archiving workspace. These logs include: 
- The number of records deleted. 
- The tables affected. 
- A timeline of actions taken during the purge. 
Users can monitor the status of purge jobs in real time through the results column. 
 
### What safeguards are in place to prevent accidental data loss? 
The Purge from History feature includes multiple safeguards: 
1. The "Delete history (Preview)" button is only enabled for completed archive jobs, ensuring no critical data is removed prematurely. 
1. A confirmation pop-up requires users to acknowledge the irreversible nature of the purge process. 
1. Archived data in Dataverse long-term retention remains unaffected by the purge from history feature. 

### How does this feature help optimize storage and performance? 
By permanently removing data from history tables: 
- The operational database size is significantly reduced, leading to improved system performance. 
- Storage costs are minimized, as history tables are no longer consuming space unnecessarily. 
- Users can achieve full capacity savings when combining purging with Dataverse's compression of archived data. 

### Will this feature impact compliance or audit requirements? 
No, the feature does not compromise compliance or audit readiness. All archived data is securely retained in Dataverse long-term retention storage and remains accessible for reporting, auditing, or regulatory purposes, even after being purged from history tables. 
