---
title: Actions need to take before running Inventory On-hand Consistency Check when Inventory Visibility Integration batch job is enabled
description: This article provides some warning when you want to run consistency check. 
author: yuhuiyou
ms.date: 08/02/2021
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yuhuiyou
ms.search.validFrom: 2022-01-17
ms.dyn365.ops.version: 10.0.21
---

# Actions need to take before running Inventory On-hand Consistency Check when Inventory Visibility Integration batch job is enabled

[!include [banner](../includes/banner.md)]

Supply Chain Management provides an On-hand Consistency Check tool, which allows you to check/fix On-hand data on all items or specific items. On-hand consistency check will reconstruct On-hand list by analyzing Transactions table. 
While you're trying to perform On-hand Consistency Check on **all items**, please be aware that: 
1. running an On-hand Consistency Check on all items (with Inventory Visibility batch enabled) will usually take long time than the standard use case when the Inventory Visibility batch is not enabled. 
2. On-hand Consistency Check will involve API calls to sync the changes in the `InventSum` and `WHSInventReserve` tables to Inventory Visibility service if you have batch job enabled. You might experience failure on consistency check if the external calls have unexpected errors.  
As stated above, it is recommended to disable the Inventory Visibility Integration batch job when you want to run On-hand Consistency Check on **all items**.

## There are two different cases, please take different actions:

### Case 1: You want to initiate On-hand Consistency Check on all items.
0. Before you run an On-hand consistency check, please check if your Inventory Visibility Integration batch job is enabled. If it is enabled, please follow the below steps to disable batch job, otherwise, you can start consistency check directly. 
1. Disable Inventory Visibility Integration batch job: go to **Inventory Management** > **Periodic Tasks** > **Inventory Visibility integration** and disable the job.
2. Run consistency check.
3. Re-enable the Inventory Visibility Integration batch job. 
1. Go to **Inventory Management** > **Setup** and check *Resync before initial push* toggle. 
2. Re-enable the Inventory Visibility Integration batch job and start the initial push. 
- The Initial push with `Resync` action will clean up legacy fno data in Inventory Visibility service and resync the `InventSum` and `WHSInventReserve` tables to Inventory Visibility Service.
* Please be aware: Inventory Visibility Service will return the correct result after the re-enabled bath job is completed.

### Case 2: You want to initiate On-hand Consistency Check on several items.
You don't have to take any extra steps as described in Case 1. You can directly perform an On-hand Consistency Check on the desired items.
