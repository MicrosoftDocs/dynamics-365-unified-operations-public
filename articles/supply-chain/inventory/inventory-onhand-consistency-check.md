---
title: Actions need to take before running Consistency Check when IV batch job is enabled
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

# Actions need to take before running Inventory On-hand Consistency Check when IV batch job is enabled

[!include [banner](../includes/banner.md)]

FnO provides On-hand Consistency Check tool, which allows you to check/fix On-hand data on all items or specific items. On-hand consistency check will reconsutruct InventSum table by analyzing InvetTrans table. By doing this, IV batch job will resync changes on the InventTrans table to Inventory service.
While you're trying to perform On-hand Consistency Check on **all items**, please be aware that: 1. running On-hand Consistency Check on all items will usually take long time. 2. It will take longer time than the standard use case when Inventory Visibility batch is not enabled. 3. On-hand Consistency Check will involve API calls to Inventory Visbility to sync InventSum data if you have batch job enabled and you might experience check failure if the external calls encounter errors.  
so it is recommended to disable the Inventory Visibility Integration batch job.

## There are two different cases, please will take different actions:

### Case 1: You want to initiate On-hand Consistency Check on all items when IV batch job is enabled

As it is mentioned above, enabling Inventory Integration batch job will cause consistency check fail unexpectedly. So before you run consistency check, please do the following:

1. Disable Inventory Visibility Integration batch job: go to **Inventory Management** > **Periodic Tasks** > **Inventory Visibility Integration** and disable batch job.
2. Run consistency check.
3. Re-enable IV batch job by clicking *Enabling **IV integration batch job with check the Resync button**. This action will clean up some legacy FnO data in Inventory Visibility and start initial push to resync InventSum table to IV service. 
 
* Please be aware: Inventory Visibility service will return empty on-hand query result. Service will return the correct result after the re-enabled bath job is completed.

### Case 2: You want to initiate On-hand Consistency Check on several items.

You don't have to do any extra steps as described in Case 1. You can perform On-hand Consistency Check on the desired items. 

