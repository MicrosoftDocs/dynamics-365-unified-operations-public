---
title: Inventory Visibility diagnostic tool
description: This article describes how to set up and use the Inventory Visibility diagnostic tool, which helps you identify and fix discrepancies between Dynamics 365 Supply Chain Management on-hand inventory records and the Inventory Visibility service's on-hand inventory records.
author: yufeihuang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 01/11/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Inventory Visibility diagnostic tool

This article describes how to set up and use the Inventory Visibility diagnostic tool, which helps identify and fix discrepancies between Dynamics 365 Supply Chain Management on-hand inventory records and Inventory Visibility on-hand inventory records in the `fno` data source.

## Set up Inventory Visibility diagnostic tool

The Inventory Visibility diagnostic tool requires that Inventory Visibility is set up for your system and the data sync batch job is running, as described in [Set up Inventory Visibility in Supply Chain Management](inventory-visibility-setup.md#setup-dynamics-scm). The tool is otherwise turned on by default, so no extra steps are needed to make it available.

## Use Inventory Visibility diagnostic tool

1. Sign in to your Supply Chain Management environment.
1. Go to **Inventory Management \> Set up \> Inventory Visibility diagnostic tool**.
1. On the **Inventory Visibility diagnostic tool** page, select **Run diagnostic**.
1. The **Inventory Visibility on-hand diagnostic process** dialog opens. Make the following settings:
    - **Fix inventory discrepancy** – Set to *Yes* to immediately force synchronization and address mismatches. Set to *No* to just check for and view discrepancies without fixing or synchronizing them right away (to fix previously found discrepancies, run the tool again later with this option enabled). Allow around a minute for the synchronization process to complete.
    - **Only check warehouse items** – Set to *Yes* if you only want to review items that are enabled for warehouse management processes (WMS). Set to *No* to review all items.
    - **Only check previous mismatched data** – Set to *Yes* to verify the effectiveness of the forced synchronization and confirm the resolution of prior discrepancies. Set to *Yes* to also find any new discrepancies. If **Fix inventory discrepancy** is also set to *Yes*, the system synchronizes any remaining mismatches.
    - **Filter** – Select this link to open a dialog where you can set up filters to limit the set of items to be checked. By default, the filter is set with **No open quantities** set to *No*, which means the tool will only check for items with open quantities, but you can change this option if needed.
    - **Batch Processing** – You must leave this option set to *Yes* because the tool can only run in batch mode.

1. Select **OK** to apply your settings and return to the **Inventory Visibility diagnostic tool** page.
1. The system shows the message, "The Inventory Visibility on-hand diagnostic process job is added to the batch queue." You can monitor the batch job progress by going to **System Administrator \> Inquiries \> Batch Jobs**.
1. When the job is finished, the **Inventory Visibility diagnostic tool** shows the results from the test. If you chose not to fix the discrepancies, you can fix them now by rerunning the diagnostic with **Fix inventory discrepancy** and/or **Only check previous mismatched data** set to *Yes*.
