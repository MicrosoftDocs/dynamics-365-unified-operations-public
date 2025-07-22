---
title: Purge from history archive (preview)
description: Learn about how to purge data from the history table in Microsoft Dynamics 365.
author: weijiesa
ms.author: weijiesa
ms.topic: how-to
ms.date: 06/11/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
---

# Purge from history archive (preview)

[!INCLUDE[banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article explains how to purge data from the history table in Microsoft Dynamics 365.

The **Archive with Dataverse long term retention** feature decreases the amount of space that customers use in their finance and operations database. To achieve this decrease, it reduces the indexing on the relevant data as it's moved to history tables for archiving. However, as time passes, data that is stored in history tables might no longer be needed. The **Purge from history archive** feature helps minimize storage space for data that is stored in Dynamics 365 by letting customers purge that data from history tables. In this way, customers can benefit fully from the **Archive with Dataverse long term retention** feature.

## Prerequisites

Before you can enable the **Purge from history archive** feature, your system must be running version 10.0.45 or later.

## Enable the Purge from history archive feature

Open the [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) workspace, and turn on the **Purge from history archive** feature.

## Purge data from the history table

Before you can purge data from the history table, the following conditions must be met:

- The archival job for which you want to purge associated data from the history table must be successfully completed. Otherwise, you can't select the archival job.
- You must select at least one archival job. Otherwise, you can't select the **Delete history** button.

> [!NOTE]
> If an archival job is being restored or is scheduled for restoration, you can't purge the data that is associated with it.
To create a purge job to delete data from the history table, follow these steps.

1. Go to **System administration** \> **Workspaces** \> **Archive with Dataverse long term retention**.
1. In the **Archive with Dataverse long term retention** workspace, select a completed archival job. You can also select multiple completed archival jobs for the same functional scenario.
1. Select **Delete history**.
1. A confirmation message prompts you to acknowledge that the purge process can't be reversed. Acknowledge the message, and submit the purge job.

## Purge job status

The following table explains the different statuses that a purge job can have.

| Job status | Description |
|---|---|
| Deletion queued | The purge job can't run immediately. |
| Deletion in progress | The purge job is running. |
| Deleted | The purge job finished running, and the data was successfully purged. In this case, the **Exists in history data** field is set to **No**, and the **Results** field shows the number of records that were deleted. |

## Frequent asked questions

### What is the Purge from history archive feature?

The **Purge from history archive** feature lets users permanently delete historical data from operational history tables after it's successfully archived. This feature ensures that the operational database remains streamlined and performs efficiently while the archived data is securely retained in Dataverse long-term retention storage for regulatory and compliance purposes.

### Why was the feature introduced?

The **Purge from history archive** feature addresses the need to fully optimize storage and database performance by removing redundant records from history tables. Although the existing **Archive with Dataverse long term retention** feature moves inactive data to history tables and Dataverse, it lacks a mechanism for deleting data from history tables. Therefore, organizations can't achieve maximum storage savings. The **Purge from history archive** feature fills the gap to complete the data lifecycle.

### What happens to the archived data in Dataverse during a purge?

The purge process removes data only from the operational history tables in Dynamics 365. The archived data in Dataverse long-term retention remains unaffected and securely accessible. Users can still retrieve archived records that are stored in Dataverse for compliance and reporting purposes.

### Who can use the feature?

The  **Purge from history archive** feature is available to administrators who have access to the **Archive with Dataverse long term retention** workspace in Dynamics 365.

### What are the eligibility criteria for purging data?

The **Purge from history archive** feature is designed to work only with data from completed archive jobs. If an archival job is still in progress or wasn't successfully completed, the **Delete history** button remains unavailable to help prevent accidental data deletion.

### Can multiple purge jobs be scheduled at the same time?

Yes, multiple purge jobs can be scheduled to run simultaneously on different archival scenarios (for example, general ledger and sales orders). In this way, users can clean up history tables for several completed archive jobs in a single operation. This capability helps improve efficiency.

### How can I track the progress of a purge job?

The purge process is fully transparent. Detailed logs are available in the **Archive with Dataverse long term retention** workspace. These logs include the following information:

- The number of records that were deleted
- The tables that were affected
- A timeline of actions that were taken during the purge

Users can monitor the status of purge jobs in real time through the **Results** column.

### What safeguards are in place to help prevent accidental data loss?

The **Purge from history archive** feature includes multiple safeguards.

- The **Delete history** button is available only for completed archive jobs. This limitation helps ensure that no critical data is removed prematurely.
- A confirmation message requires that users acknowledge the irreversible nature of the purge process.
- Archived data in Dataverse long-term retention is unaffected by the **Purge from history archive** feature.

### How does the feature help optimize storage and performance?

By permanently removing data from history tables, the **Purge from history archive** feature provides the following benefits:

- The size of the operational database is reduced. Therefore, system performance is improved.
- Storage costs are minimized, because history tables no longer consume space unnecessarily.
- By combining purging with Dataverse's compression of archived data, users can achieve full capacity savings.

### Does the feature affect compliance or audit requirements?

No, the **Purge from history archive** feature doesn't compromise compliance or audit readiness. All archived data is securely retained in Dataverse long-term retention storage. It remains accessible for reporting, auditing, or regulatory purposes, even after it's purged from history tables.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
