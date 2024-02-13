---
title: Archive inventory transaction data in Dynamics 365 Supply Chain Management (preview)
description: This article explains how to archive inventory transaction data in Microsoft Dynamics 365 Supply Chain Management.
author: pnghub
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 2/06/2024
ms.custom:

---
# Archive inventory transaction data in Dynamics 365 Supply Chain Management (preview)

[!INCLUDE [preview-banner](../../../supply-chain/includes/preview-banner.md)]

This article explains how to archive data for inventory transactions with Dataverse long-term retention.

Currently, users can consolidate and compress the inventory transactions table (InventTrans) and archive the original records in the InventTransArchive table. For more information, see [Archive inventory transactions](../../supply-chain/inventory/archive-inventory-transactions.md).

The new **Archive with Dataverse long term retention** feature addresses the data volume issue of the InventTrans table and helps improves system performance. It moves InventTransArchive records to a Microsoft Azure data lake and replicates corresponding records to InventTransArchiveHistory in Dynamics 365 Supply Chain Management for performance optimization.

## Prerequisites

- The **Inventory transactions archive** feature is enabled.
- Inventory transactions are archived from the InventTrans table to the InventTransArchive table.

### Turn on the features in Supply Chain Management

If your system doesn't already include the features, follow these steps.

1. Go to **Feature management**.
2. Enable both the following features:

    - **Inventory transactions archive** – This feature archives inventory transactions from the InventTrans table to the InventTransArchive table.
    - **Archive with Dataverse long term retention** – This feature moves archived inventory transactions from the InventTransArchive table to the Dataverse-managed data lake and replicates the data to the InventTransArchiveHistory table.

### Considerations before you purge inventory transactions

- The **Reverse** function of the **Inventory transactions archive** feature isn't available for purged inventory transaction records.
- The unpurge activity isn't available from the Dataverse-managed data lake to Supply Chain Management.

### Archive inventory transactions before you purge

For more information about how to archive inventory transactions, see [Archive inventory transactions](../../supply-chain/inventory/archive-inventory-transactions.md).

## Schedule the long-term retention job

To move InventTransArchive records to the Dataverse-managed data lake, follow these steps.

1. Go to **Workspaces** \> **Archive with Dataverse long term retention** \> **Inventory transactions**.
1. Select **New long term retention job** to open the **Long term retention job creation** wizard.
1. Enter a name for the job, and then select **Next**.
1. Select the period that has been processed by the **Inventory transactions archive** feature, and then select **Next**.
1. Enter the start date and time of the long-term retention job, and then select **Next**.
1. Review the job details, and create the long-term retention job.

You receive a message that the long-term retention job has been created. The archived records are purged on the scheduled date.

## View the status of the long-term retention job

To view the results of the long-term retention job, follow these steps.

1. Go to **Workspaces** \> **Archive** \> **Inventory transactions**.
1. A list of long-term retention jobs is shown. Select the job where the **Job status** field is set to **Completed**.
1. Under **Results**, select the link.
1. View the **Inventory transactions archive progress** information.
1. Select **View detailed logs** to view the Archive job message log. This log describes the steps of the long-term retention job in detail.

## View historical data

When the long-term retention job moves archived inventory transactions from the InventTransArchive table to the Dataverse-managed data lake, the same data is replicated to the InventTransArchiveHistory table. To view the historical data in the InventTransArchiveHistory table, follow these steps.

1. Go to **Workspaces** \> **Archive** \> **Inventory transactions**.
1. A list of long-term retention jobs is shown. Select the job where the **Job status** field is set to **Completed**.
1. Select **View historical data** to view the data in the InventTransArchiveHistory table.
