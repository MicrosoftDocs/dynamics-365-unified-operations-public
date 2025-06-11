---
title: Purge data from history (preview)
description: Learn about how to purge data from the history table in Microsoft Dynamics 365.
author:  weijiesa
ms.author: weijiesa
ms.topic: how-to
ms.date: 06/11/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
---

# Purge data from history (preview)

[!INCLUDE[banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article describes how to purge data from the history table in Microsoft Dynamics 365.

The **Archive with Dataverse long term retention** feature decreases the space used by customers in their finance and operations database. This decrease is accomplished by reducing the indexing on the relevant data as it gets moved to the history tables for archiving. This minimizes the storage space for cold-to-lukewarm data, but, eventually, this archived data grows so cold that it's no longer needed. Customers can purge their archived data from the history tables to get the full benefit of the **Archive with Dataverse long term retention** feature. 

## Prerequisites

Before you can enable the **Purge from history** feature, your system be running version 10.0.45 or later.
  
## Enable the Purge from history feature

Go to [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) workspace and turn on the following feature:

- Purge From History Archive Feature

## Purge data from the history table

The following criteria must be met before you purge data history table:

-  An archive job must be completed successfully, then you can select that archival job to have the data associated with it purged from the history table.
-  You must select at least one archival job before you can select **Delete history**.

 > [!NOTE]
 > If an archival job is being restored or is scheduled to be restored, you can’t purge the data associated with that archival job.

To create a purge job to delete data from history table, follow these steps.

1. To open the **Archive with Dataverse long term retention** workspace, go to **System administration** \> **Archive with Dataverse long term retention**.
1. Select a completed archive job or multiple completed archive jobs of the same functional scenario.
1. Select **Delete history** to open a warning popup with explicit confirmation message, confirm, and submit the purge job.

## Purge job status

1. When a purge job can’t be executed instantly, its job status is **Deletion queued**.
1. When a purge job is being executed, its job status is **Deletion in progress**.
1. When a purge job has been completed, its job status is **Deleted** value of field 'Exists in history data' equal to 'No' and value of field 'Results' shows the number of records deleted.

## Frequent Asked Questions

### What is the **Purge from history** feature? 
The **Purge from history** feature enables users to permanently delete historical data from operational history tables after it has been successfully archived. This ensures the operational database remains streamlined and performs efficiently while retaining the archived data securely in Dataverse long-term retention storage for regulatory and compliance purposes. 

### Why was this feature introduced? 
This feature addresses the need to fully optimize storage and database performance by removing redundant records from history tables. While the existing **Archive with Long-Term Retention** feature moved inactive data to history tables and Dataverse, the lack of a mechanism to delete data from history tables meant organizations couldn't achieve maximum storage savings. The Purge from History feature resolves this by completing the data lifecycle. 
 
### What happens to the archived data in Dataverse during the purge? 
The purge process only removes data from the operational history tables in Dynamics 365 Finance. The archived data in Dataverse long-term retention remains unaffected and securely accessible. Users can still retrieve archived records stored in Dataverse for compliance and reporting purposes. 

### Who can use the "Purge from History" feature? 
The feature is available to administrators who have access to the Archiving workspace in Dynamics 365.  

### What are the eligibility criteria for purging data? 
The **Purge from history** feature is designed to work only with data from completed archive jobs. If an archival job is still in progress or hasn't completed successfully, the **Delete History Data** button remains disabled to prevent accidental data deletion. 

### Can multiple purge jobs be scheduled at the same time? 
Yes, the feature supports scheduling multiple purge jobs to run simultaneously on different archival scenarios (for example, general ledger and sales orders). This allows users to clean up history tables for several completed archive jobs in a single operation, improving efficiency. 

### How can I track the progress of a purge job? 
The purge process is fully transparent, with detailed logs available in the Archiving workspace. These logs include: 
- The number of records deleted. 
- The tables affected. 
- A timeline of actions taken during the purge. 
Users can monitor the status of purge jobs in real time through the results column. 
 
### What safeguards are in place to prevent accidental data loss? 
The Purge from History feature includes multiple safeguards: 
1. The **Delete history** button is only enabled for completed archive jobs, ensuring no critical data is removed prematurely. 
1. A confirmation pop-up requires users to acknowledge the irreversible nature of the purge process. 
1. Archived data in Dataverse long-term retention remains unaffected by the purge from history feature. 

### How does this feature help optimize storage and performance? 
By permanently removing data from history tables: 
- The operational database size is reduced, leading to improved system performance. 
- Storage costs are minimized, as history tables are no longer consuming space unnecessarily. 
- Users can achieve full capacity savings when combining purging with Dataverse's compression of archived data. 

### Will this feature impact compliance or audit requirements? 
No, the feature doesn't compromise compliance or audit readiness. All archived data is securely retained in Dataverse long-term retention storage and remains accessible for reporting, auditing, or regulatory purposes, even after being purged from history tables. 

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
