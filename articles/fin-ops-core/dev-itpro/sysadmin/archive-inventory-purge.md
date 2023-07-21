---
title: Move inventory transactions history to long term data retention
description: This article describes how to move old inventory transactions from the inventory transaction history table to a Dataverse managed Data Lake for long term data retention. This helps lower storage costs and improve database performance while keeping the records available for historical reporting, auditing, machine learning, legal claims, and other purposes.
author: Banluo
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: ArchiveWorkspace, ProcessScheduleSeriesWizard, InventTransArchiveForm
ms.topic: how-to
ms.date: 06/28/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Move inventory transactions history to long term data retention

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!--KFM: Preview until further notice -->

The [Archive inventory transactions](../../../supply-chain/inventory/archive-inventory-transactions.md) feature consolidates and compresses the inventory transactions table (`InventTrans`) and archives the original records into a related history table (`InventTransArchive`). Moving old data that you probably don't need to access frequently to the history table (`InventTransArchive`), helps improve the performance of the main table (`InventTrans`).

After moving your old inventory transactions to the history table, you can lower your data storage costs and further improve system performance by moving the data to a Dataverse managed Data Lake for long term data retention. The action of moving data from a history table to long term data retention is also called *purging* (because the data is purged from Supply Chain Management). Purging is a permanent action that can't be reversed.

This article describes how to move old inventory transactions from the inventory transaction history table to a Dataverse managed Data Lake for long term data retention.

## Prerequisites

Before you can use this feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.34 or later.
- The data archive micro-service must be installed on your system from Microsoft Dynamics Lifecycle Services. For more information, see [Install the Archive add-in from Lifecycle Services](archive-setup.md#install-addin).
- You must have already [moved the relevant inventory transactions](archive-inventory-transactions) to the history table.
- The following features must be turned on in [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md). For more information, see [Enable the features that you need](archive-setup.md#enable-features).

    - *(Preview) Archive*
    - *(Preview) Archive data to Dataverse managed data lake and purge*
    - *(Preview) Purge archived inventory transactions*

## <a name="archival-requirements"></a>Which inventory transactions can be moved and when

Inventory transactions can be moved from history to long term data retention if all the following conditions are met:

- The relevant inventory transactions have been archived by Inventory transaction archive feature.
- The ledger period that includes a related inventory transactions is either *closed* or *on hold*.
- Inventory has been closed for the period that includes the relevant inventory transactions.

## <a name="archival-requirements"></a>Things to consider before you move inventory transactions

Consider the following issues before you move inventory transactions to long term data retention:

- The **Reverse** function, which lets you move inventory transactions from the history table back to the live table, isn't available after you've moved the records to long term data retention.
- It isn't possible to move records from long term data retention back to the history tables in Supply Chain Management.

## Move inventory transactions to the history table before moving them to long term data retention

You must move your inventory transactions to the history table before you can move them to long term data retention. See [Archive inventory transactions](articles/supply-chain/inventory/archive-inventory-transactions.md) for details.

## Schedule the move of inventory transactions to long term data retention

To schedule the move of inventory transactions to long term data retention, follow these steps.

1. Go to **System administration \> Workspaces \> Archive**.
1. In the **Archive** workspace, open the **Inventory transactions archive** tab.
1. The **Inventory transactions archive** tab shows a list of archive jobs that were used to copy collections of old inventory transaction records to the history table.
1. Select an archive job with a status of *Finish*.
1. Select **Schedule purge** to schedule the selected collection of records to be moved to long term data retention and purged from Supply Chain Management.
1. In the dialog box, verify the **From date** and **To date** of archived period to be purged. Select a date to schedule the move and purge job.
1. Select **OK**.
1. You receive a message that states that your inventory transactions purge job has been created. The archived records will be purged on the scheduled date.

## Review the purge history

To review your purge history, follow these steps.

1. Go to **System administration \> Workspaces \> Archive**.
1. In the **Archive** workspace, open the **Inventory transactions archive** tab.
1. The **Inventory transactions archive** tab shows a list of archive jobs that were used to copy collections of old inventory transaction records to the history table.
1. Select **View purge history**.
1. Your purge history is now shown.
