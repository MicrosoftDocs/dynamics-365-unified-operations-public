---
title: Inventory Visibility diagnostic tool
description: Learn how to set up the Inventory Visibility diagnostic tool, which helps you identify discrepancies between inventory records and the inventory visibility service.
author: yufei-huang
ms.author: yufeihuang
ms.topic: how-to
ms.date: 01/11/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Inventory Visibility diagnostic tool

[!include [banner](../includes/banner.md)]

This article describes how to set up and use the Inventory Visibility diagnostic tool. This tool helps identify and fix discrepancies between on-hand inventory records in Microsoft Dynamics 365 Supply Chain Management and on-hand inventory records in the `fno` data source in Inventory Visibility.

## Set up the Inventory Visibility diagnostic tool

The Inventory Visibility diagnostic tool is turned on by default, and no extra steps are required to make it available. However, the tool requires that Inventory Visibility is set up for your system and the data synchronization batch job is running. Learn more in [Set up Inventory Visibility in Supply Chain Management](inventory-visibility-setup.md#setup-dynamics-scm).

## Use the Inventory Visibility diagnostic tool

1. Sign in to your Supply Chain Management environment.
1. Go to **Inventory Management** \> **Set up** \> **Inventory Visibility diagnostic tool**.
1. On the **Inventory Visibility diagnostic tool** page, select **Run diagnostic**.
1. In the **Inventory Visibility on-hand diagnostic process** dialog box, set the following options:

    - **Fix inventory discrepancy** – Set this option to *Yes* to immediately force synchronization and address mismatches. Set it to *No* to check for and view discrepancies, but without immediately fixing or syncing them. (In this case, you can fix previously found discrepancies later by rerunning the tool and setting this option to *Yes*.) The synchronization process takes about a minute.
    - **Only check warehouse items** – Set this option to *Yes* if you want to review only items that are enabled for warehouse management processes (WMS). Set it to *No* to review all items.
    - **Only check previous mismatched data** – Set this option to *Yes* to verify the effectiveness of the forced synchronization, confirm the resolution of previous discrepancies, and also find any new discrepancies. If the **Fix inventory discrepancy** option is also set to *Yes*, the system syncs any remaining mismatches.
    - **Batch Processing** – You must leave this option set to *Yes*, because the tool can run only in batch mode.

1. Select the **Filter** link to open a dialog box where you can set up a filter to limit the set of items that's checked. By default, the **No open quantities** option for the filter is set to *No*. Therefore, the tool checks only for items that have open quantities. You can change the setting of this option as you require.
1. Select **OK** to apply your settings and return to the **Inventory Visibility diagnostic tool** page.
1. You receive the following message: "The Inventory Visibility on-hand diagnostic process job is added to the batch queue." To monitor the progress of the batch job, go to **System Administrator** \> **Inquiries** \> **Batch Jobs**.
1. When the job has finished running, the Inventory Visibility diagnostic tool shows the results of the test. If you chose not to fix discrepancies, you can fix them now. Rerun the diagnostic, and set the **Fix inventory discrepancy** option and/or the **Only check previous mismatched data** option to *Yes*.
