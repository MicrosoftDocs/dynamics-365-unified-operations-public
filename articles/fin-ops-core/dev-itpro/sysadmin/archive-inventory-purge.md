---
title: Move inventory transactions history to long-term data retention
description: This article describes how to move old inventory transactions from the inventory transaction history table to a Microsoft Dataverse-managed data lake for long-term data retention.
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

# Move inventory transactions history to long-term data retention

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!--KFM: Preview until further notice -->

The *[Inventory transaction archive](../../../supply-chain/inventory/archive-inventory-transactions.md)* feature consolidates and compresses the inventory transactions table (`InventTrans`) and archives the original records into a related history table (`InventTransArchive`). By moving old data that you probably don't have to access very often to the history table (`InventTransArchive`), this feature helps improve the performance of the main table (`InventTrans`).

After your old inventory transactions are moved to the history table, you can help lower your data storage costs and further improve system performance by moving the data to a Microsoft Dataverse–managed data lake for long-term data retention. After the move, the records remain available for historical reporting, auditing, machine learning, legal claims, and other purposes.

The action of moving data from a history table to long-term data retention is also known as *purging*, because the data is purged from Dynamics 365 Supply Chain Management. Purging is a permanent action that can't be reversed.

This article describes how to move old inventory transactions from the inventory transaction history table to a Dataverse-managed data lake for long-term data retention.

## Prerequisites

Before you can use this feature, your system must meet the following requirements:

- You must be running Supply Chain Management 10.0.34 or later.
- The data archive microservice must be installed on your system from Microsoft Dynamics Lifecycle Services. For more information, see [Install the Archive add-in from Lifecycle Services](archive-setup.md#install-addin).
- You must have already [moved the relevant inventory transactions](archive-inventory-transactions) to the history table.
- The following features must be turned on in [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md). For more information, see [Enable the features that you need](archive-setup.md#enable-features).

    - *(Preview) Archive*
    - *(Preview) Archive data to Dataverse managed data lake and purge*
    - *(Preview) Purge archived inventory transactions*

## <a name="archival-requirements"></a>Which inventory transactions can be moved and when

Inventory transactions can be moved from history to long-term data retention if all the following conditions are met:

- The relevant inventory transactions have been archived by the *Inventory transaction archive* feature.
- The ledger period that includes related inventory transactions is either *closed* or *on hold*.
- Inventory has been closed for the period that includes the relevant inventory transactions.

## <a name="archival-requirements"></a>Issues to consider before you move inventory transactions

Consider the following issues before you move inventory transactions to long-term data retention:

- The **Reverse** function, which lets you move inventory transactions from the history table back to the live table, isn't available after you move records to long-term data retention.
- You can't move records from long-term data retention back to the history tables in Supply Chain Management.

## Move inventory transactions to the history table before you move them to long-term data retention

You must move your inventory transactions to the history table before you can move them to long-term data retention. For more information, see [Archive inventory transactions](articles/supply-chain/inventory/archive-inventory-transactions.md).

## Schedule the move of inventory transactions to long-term data retention

To schedule the move of inventory transactions to long-term data retention, follow these steps.

1. Go to **System administration \> Workspaces \> Archive**.
1. In the **Archive** workspace, select the **Inventory transactions archive** tab. This tab shows a list of archive jobs that were used to copy collections of old inventory transaction records to the history table.
1. Select an archive job that has a status of *Finish*.
1. Select **Schedule purge** to schedule the selected collection of records to be moved to long-term data retention and purged from Supply Chain Management.
1. In the dialog box, verify the **From date** and **To date** values of the archived period that you want to purge. Select a date to schedule the move and purge job.
1. Select **OK**. A message informs you that your inventory transactions purge job has been created. The archived records will be purged on the scheduled date.

## Review the purge history

To review your purge history, follow these steps.

1. Go to **System administration \> Workspaces \> Archive**.
1. In the **Archive** workspace, select the **Inventory transactions archive** tab. This tab shows a list of archive jobs that were used to copy collections of old inventory transaction records to the history table.
1. Select **View purge history**. Your purge history is shown.
