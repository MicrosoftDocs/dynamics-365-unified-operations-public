---
title: Inventory Visibility diagnostic tool
description: This article describes how to set up and use the Inventory Visibility diagnostic tool to compare and fix in case the inventory discrepency happens between Dynamics 365 SCM onhand inventory and Inventory Visibility service's onhand inventory under datasource 'fno'
author: yufeihuang
ms.date: 10/16/2023
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yufeihuang
ms.search.validFrom: 2023-10-16
ms.dyn365.ops.version: 10.0.38
---

# Inventory Visibility diagnostic tool
This article describes how to set up and use the Inventory Visibility diagnostic tool to compare and fix in case the inventory discrepency happens between Dynamics 365 SCM onhand inventory and Inventory Visibility service's onhand inventory under datasource 'fno'

## Set up Inventory Visibility diagnostic tool
The feature is enable by default and there is no toggle to enable. You can use this feature as long as you have enabled the integration and data sync batch job between Dynamics 365 SCM and Inventory Visibility service. See [Set up Inventory Visibility in Supply Chain Management](https://learn.microsoft.com/en-us/dynamics365/supply-chain/inventory/inventory-visibility-setup#setup-dynamics-scm) for details

## Use Inventory Visibility diagnostic tool:
1. Log onto your Dynamics 365 SCM environment > Navigate to the company you are working with, for example **USMF**
1. Go to **Inventory Management** > Set up > Inventory Visibility Dignostic Tool
1. On the **Inventory Visibility diagnostic tool** page, you can start a new job by clicking **Run Diagnostic**
1. A side-car **Inventory Visibility on-hand diagnostic process** appears on the right which allows you to adjust parameters:
    - Fix Inventory Discrepancy: To immediately force synchronization and address mismatches, activate this option. Please allow around 1 minute for the synchronization process to complete.
    - Only Check Warehouse Items: If you only need to review warehouse items, enable this button.
    - Only Check Previous Mismatched Data: To verify the effectiveness of the forced synchronization and confirm the resolution of prior discrepancies, enable this button. If used concurrently with the "Fix inventory discrepancy" button, it will further synchronize any remaining mismatches
    - Utilize filters to examine specific items or warehouses. Additionally, you can select to check either open quantities or closed quantities by modifying the "No open quantities" field (by default the tool will only check open quantities)
    - Ensure you enable the "Batch Processing" option, as the tool needs to be run in batch mode


1. After setting up the parameters, click **Run Diagnostic** again. You will see message **The Inventory Visibility onhand diagnostic process job is added to the batch queue**. You can go to the workspace menu and navigate to **Business Process Form Test** to view the batch job process
1. Once the job is completed, you can go back to**Inventory Visibility diagnostic tool** pageview and compare the inventory onhand in Dynamics 365 SCM and Inventory Visibility's 'fno' datasource's inventory onhand
1. To fix discrepency of your click **Run Diagnostic** again and enable **Fix inventory discrepency** and click **OK**
1. Should you identified any discrepencies found in previous run that you wish to fix, click **Run Diagnostic** again and enable both **Only Check Previous Mismatched Data** and **Fix inventory discrepency** and click **OK**
1. Monitor the batch job progress via the **System Administrator** > **Inquiries** > **Batch Jobs**
1. View batch job result once it's completed. Refreshing the page and you will then be able to access the list of all resolved mismatched on-hand quantities