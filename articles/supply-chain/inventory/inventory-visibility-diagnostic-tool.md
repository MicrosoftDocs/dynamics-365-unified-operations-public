---
title: Inventory Visibility diagnostic tool
description: This article describes how to set up and use the Inventory Visibility diagnostic tool, which helps you identify and fix discrepancies between Dynamics 365 Supply Chain Management on-hand inventory records and the Inventory Visibility service's on-hand inventory records.
author: yufeihuang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 11/16/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Inventory Visibility diagnostic tool

This article describes how to set up and use the Inventory Visibility diagnostic tool, which helps identify and fix discrepancies between Dynamics 365 Supply Chain Management on-hand inventory records and Inventory Visibility on-hand inventory records in the `fno` data source.

## Set up Inventory Visibility diagnostic tool

The Inventory Visibility diagnostic tool requires that you have set up the integration and the data sync batch job, as described in [Set up Inventory Visibility in Supply Chain Management](inventory-visibility-setup.md#setup-dynamics-scm). The tool is otherwise turned on by default, so no extra steps are needed to make it available.

## Use Inventory Visibility diagnostic tool

1. Sign in to your Supply Chain Management environment.
1. Go to **Inventory Management \> Set up \> Inventory Visibility diagnostic tool**.
1. On the **Inventory Visibility diagnostic tool** page, select **Run diagnostic**.
1. The **Inventory Visibility on-hand diagnostic process** dialog opens. Make the following settings:
    - **Fix inventory discrepancy** – Set to *Yes* to immediately force synchronization and address mismatches. Allow around a minute for the synchronization process to complete. <!--KFM: What if I set this to No? Why would I set this to No? -->
    - **Only check warehouse items** – Set to *Yes* if you only need to review warehouse items. <!--KFM: What if I set this to No? What do we check then? -->
    - **Only check previous mismatched data** – Set to *Yes* to verify the effectiveness of the forced synchronization and confirm the resolution of prior discrepancies. <!--KFM: What if I set this to No? Why would I set this to No? What do we mean by "only"? --> If **Fix inventory discrepancy** is also set to *Yes*, the system synchronizes any remaining mismatches.
    - **Utilize filters to examine specific items or warehouses** – Additionally, you can select to check either open quantities or closed quantities by modifying the **No open quantities** field (by default the tool will only check open quantities).  <!--KFM: This isn't clear. I need to see this. -->
    - **Batch Processing** – You must set this option to *Yes* because the tool can only run in batch mode.

1. Select **OK** to apply your settings and return to the **Inventory Visibility diagnostic tool** page.
1. Select **Run diagnostic** again. The system shows the message, "The Inventory Visibility on-hand diagnostic process job is added to the batch queue." <!--KFM: No dialog this time? --> To monitor the batch job progress, go to **Inventory Management \> Workspaces \> Business process form test**.
1. When the job is finished, go back to the **Inventory Visibility diagnostic tool** page to view and compare the on-hand inventory records for each system.
    - To fix a discrepancy, select **Run diagnostic**, set **Fix inventory discrepancy** to *Yes*, and select **OK**. <!--KFM: Which kind of discrepancies are we fixing here, compared to the next bullet settings? -->
    - To fix a discrepancy that was found in previous run, select **Run diagnostic**, set both **Only check previous mismatched data** and **Fix inventory discrepancy** to *Yes*, and select **OK**. <!--KFM: How is this different from the previous bullet? -->

    <!--KFM: Looks like this time, when we selected **Run diagnostic**, we got the dialog again. Do I need to select **Run diagnostic** yet again to run the job with the new settings? -->

1. To monitor the batch job progress, go to **System Administrator \> Inquiries \> Batch Jobs**. <!--KFM: Why is this different than the path we used for this previously? -->
1. View batch job result once it's completed <!--KFM: How? Where? -->. Refresh the page <!--KFM: What page? How? --> to view the list of all resolved mismatched on-hand quantities.
