---
# required metadata

title: Archive inventory transactions
description: This topic describes how archive inventory transaction data to help improve the system performance.
author: sherry-zheng
manager: tfehr
ms.date: 03/01/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: InventTransArchiveProcessForm
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: chuzheng
ms.search.validFrom: 2021-03-01
ms.dyn365.ops.version: Release 10.0.18
---
# Archive inventory transactions

[!include [banner](../includes/banner.md)]

Over time, the inventory transactions table (`InventTrans`) will grow to consume more and more database space, which will gradually slow down queries made against the table. This topic describes how to use the *inventory transactions archive* feature to archive inventory transaction data to help improve system performance.

> [!NOTE]
> Only financial updated inventory transactions can be archived in a selected closed ledger period. To be archived, financial updated outbound inventory transactions must have an **Issue** status of *Sold* and inbound inventory transactions must have a **Receipt** status of *Purchased*.

When you archive inventory transactions, all related transactions will be moved to the `InventTransArchive` table. Inventory issue transactions and inventory receipt transactions will be archived separately based on the combination of the item ID (`itemId`) and inventory dimension ID (`inventDimId`) and will be put into the summarized issue and summarized receipt transactions.

If an `itemId` and `inventDimId` combination only contains one receipt or issue transaction, the transactions will not be archived.

## Turn on the feature in your system

If your system doesn't already include the features described in this topic, go to [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) and turn on the *Inventory transactions archive* feature.

## Things to consider before archiving inventory transactions

Before archiving your inventory transactions, consider the following business scenarios, which will be impacted by the operation:

- When auditing inventory transactions from related documents (such as purchase order lines) the inventory transactions will now be shown as archived. This means that you must go to **Inventory management \> Periodic tasks \> Clean up \> Inventory transactions archive** to review the archived transactions.
- Inventory closing cancellation is not allowed for archived periods. You must reverse the inventory transaction archive for the relevant period before cancelling the inventory closing.
- Standard cost conversion is not allowed for archived periods. You must reverse the inventory transaction archive for the relevant period before doing the standard cost conversion.
- Inventory reports that source from inventory transactions (such as the inventory aging report and inventory value reports) will be impacted when you archive inventory transactions.
- Inventory forecasts might be affected if run within the time horizon of archived periods.

## Prerequisites

Inventory transactions can only be archived during periods where the following conditions are met:

- The ledger period must be closed.
- Inventory closing must be run on or after the end-period date of the archive.
- The period must be at least one year before the from-period date of the archive.
- There must not be any existing inventory recalculations.

## Archive inventory transactions

To archive your inventory transactions:

1. Go to **Inventory management** \> **Periodic tasks** \> **Clean up** \> **Inventory transaction archive**.
1. The **Inventory transactions archive** page opens showing a list of archived process records.

    ![The Inventory transactions archive page](media/archive-inventory-empty.png "The Inventory transactions archive page")

1. Select **Inventory transactions archive** on the Action Pane to create a new inventory transaction archive.
1. The **Inventory transactions archive** dialog box opens. Make the following settings here:

    - **From date in closed ledger period** - Select the oldest transaction date to include in the archive.
    - **To date in closed ledger period** - Select the newest transaction date to include in the archive.

    ![The Inventory transactions archive dialog box](media/archive-inventory-dates.png "The Inventory transactions archive dialog box")

    > [!NOTE]
    > Only periods that meet the [prerequisite criteria](#prerequisites) will be available for selection.

1. If necessary, expand the **Run in the background** FastTab and set up batch processing details as usual for Supply Chain Management batch jobs.
1. Select **OK**. A message is shown to help you decide whether to proceed. Read the message carefully and select **Yes** if you wish to continue.
1. Another message appears, telling you that your inventory transactions archive job has been added to the batch queue. It will now start archiving inventory transactions from the selected period.

## View archived inventory transactions

The **Inventory transactions archive** page shows your full archiving history. Each row shows information about when the archive was created, who created it, and what its status is.

![Archive list](media/archive-inventory-full.png "Archive list")

Select one of the following values from the drop-down list at the top of the page to filter the archives shown in the grid:

- *Active* - Only shows active (not reversed) archives.
- *All* - Lists all archives, including both active and reversed.

Each transaction shown in the grid provides the following information:

- **Active** - Shows a check mark for archives that are active.
- **From date** - Shows the date of the oldest transaction that may be included in the archive.
- **To date** - Shows the date of the newest transaction that may be included in the archive.
- **Scheduled by** - Shows the user account that created the archive.
- **Executed** - Shows the date on which the archive was created.
- **Reverse** - Shows a check mark for rows that have been reversed.
- **Stop current update** - Shows a check mark for archives that are *In progress* but have been paused.
- **State** - Shows the processing status of the archive (*Waiting*, *In progress*, or *Finished*).

The toolbar at the top of the grid provides the following buttons for operating on a selected archive:

- **Archived transactions** - To view the full details of an archive, select the archive in the grid and then select **Archived transactions** from the grid toolbar. This opens the **Archived transactions** page, which shows a list of all the transactions in the selected archive.
- **Pause archiving** - Pauses an archive that is currently being processed. The pause will take effect only when the archiving task has finished being generated, so it may take a short time for the pause to take effect. Paused archives show a check in their **Stop current update** column.
- **Resume archiving** - Resumes processing for an archive that is currently paused.
- **Reverse** - Reverse the selected archive. You can only reverse archives that show a **State** of *Finished*. Reversed archives show a check mark in their **Reverse** column.

The following screenshot shows an example of the **Archived transactions** page. To get more information about a transaction listed here, select it in the grid and then select **Archived transaction details** on the Action Pane. This opens the **Archived transaction details** page, which shows information such as ledger posting, related sub-ledger references, financial dimensions, and more.

![The Archived transactions page](media/archive-inventory-transactions.png "The Archived transactions page")
