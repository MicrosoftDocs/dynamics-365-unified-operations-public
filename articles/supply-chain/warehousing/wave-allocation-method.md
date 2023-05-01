---
# required metadata

title: Wave allocation
description: This article describes how to set up the wave allocation step, including how to enable parallel processing for it.
author: Mirzaab
ms.date: 03/08/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this article to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac

# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2021-03-08
ms.dyn365.ops.version: 10.0.18
---

# Wave allocation

[!include [banner](../includes/banner.md)]

Wave processing can be time consuming, and most of the processing time is spent in the allocation step and in the work creation step.

It is now possible to run each of these steps in parallel, which can improve the performance of the wave processing, and allow for a larger throughput of waves in the same warehouse. This article explains how to set up the wave allocation method to run in parallel. For more information about how to set up work creation to run in parallel, see [Schedule work creation during wave](configure-wave-schedule-work-creation.md).

Previously it was only possible to allocate one wave at a warehouse at a time. This constraint has been removed and replaced by a new constraint that only locks the item and dimensions that are above location in the reservation hierarchy. Dimensions above the location always include product dimensions. For example, if an item is configured using *Color*, then variants for *Red*, *Blue*, and *Yellow* could each be processed in parallel.

This means that if the same item with the same dimensions above the location is being allocated by one wave, other waves will have to wait to acquire a lock on the same item and dimensions. If the lock can't be acquired in a timely manner, an error will occur and the wave processing will fail.

In order to utilize parallel processing, the wave must run in batch.

## Performance improvements

Performance benefits of parallel processing fall in two categories:

- **Improved throughput** - The throughput of waves will typically improve even if parallel processing isn't configured, especially for scenarios where there is no overlap of items within the waves.
- **Improvement of the allocation for a single wave** - Testing on customer data has shown a near 50% performance improvement after switching to parallel allocation. The parallel processing is done per items and dimensions above the location, so the improvements depend on how many different items a wave contains, the infrastructure available, and the duration of the allocation versus the duration of the work creation.

## Configure parallel allocation

### Warehouse management parameters

To use parallel allocation processing, go to **Warehouse management > Setup > Warehouse management parameters**, open the **Wave processing** tab, and make the following settings:

- **Wave processing batch group** - Select the batch group that the initial processing of the waves should use. The subsequent processing of allocation can be done using different batch groups.
- **Process waves in batch** - Set this to *Yes* to use parallel processing.
- **Wait for lock (ms)** - Enter the time, in milliseconds, that an allocation step will wait for a system resource that is locked by another allocation step. When this time is exceeded, the wave is not processed and an error message is displayed. We recommend that you allow at least a few seconds to allow for allocation of one logical unit to finish.

For information about these and other wave processing options on the **Warehouse management parameters** page, see [Warehouse parameters for wave processing](wave-warehouse-parameters.md).

## Wave process methods

To set up parallel processing:

1. Go to **Warehouse Management > Setup > Waves > Wave process methods**.
1. Select the `allocateWave` method in the grid.
1. On the Action Pane, select **Task configuration**.
1. The **Wave post method task configuration** page opens. This grid lists each warehouse where you have configured the `allocateWave` method. Parallel processing will only be used for warehouses that are listed. Use the Action Pane buttons to add or remove warehouses from the grid as needed. 
1. For each warehouse, make the following settings:
    - **Maximum number of batch tasks** - Specify the number of batch tasks that should be used for the allocation for the selected warehouse. The optimal number of batch tasks depends on the infrastructure available and what other batch jobs are being processed on the server. Tests done on a four core environment that was dedicated to wave processing showed that using eight tasks produced good results.
    - **Wave processing batch group** - Specific batch groups can be used for different warehouses to allow the allocation processing to scale out per warehouse.

## Enable or disable parallelization across all legal entities

We recommend that you set the `allocateWave` method to run in parallel across all legal entities because this helps to improve the performance of the wave processing. Starting in Supply Chain Management version 10.0.17, the *Wave parallelization for Allocate Wave method* feature is turned on by default for all new and updated installations, and can't be turned off again. After enabling this feature, the following occurs:

- The `allocateWave` method is updated to include a task configuration setting that lets you use the **Wave process methods** page to define the number of tasks that will run simultaneously, equivalent to the number of parallel processes. As a result, the time used on the allocate-wave step (which is typically 30% to 60% of the total processing time) is reduced by a factor roughly equivalent to the number of tasks. It's also possible to select which batch will be assigned to process these tasks. It's important to note that all of your legal entities will be configured to process waves in batch. For the warehouses that are already configured to process waves in batch, and for the warehouses that are already configured to use the `allocateWave` method in parallel, the existing configuration will be kept.
- By default, all the new legal entities are configured to process waves in batch. All new warehouses with the **Warehouse management processes** option enabled will have the `allocateWave` method configured to run in parallel by default.
- On the **Warehouse management parameters** page, **Process saves in batch** is set to *Yes* and  **Wait for lock (ms)** set to a default 15 seconds. This means that all waves will be executed in batch. When a wave is running, it acquires a lock on the item and dimensions above location during the allocation step. When another wave processing task tries to acquire the same lock for the identical record, it is blocked until the current process is finished. The **Wait for lock (ms)** settings establishes the maximum time the system will wait before the lock is released.

Parallel allocation processing requires wave processing to run in batch. Therefore, you will reduce your wave processing performance if you turn off the **Process saves in batch** setting, especially if wave processing is using a parallel process as defined by the task configuration for the relevant wave methods.

If necessary, you can undo each of the settings made by default when the *Wave parallelization for Allocate Wave method* feature is automatically enabled for your instance. To do this:

- Go to **Warehouse management \> Setup \> Warehouse management parameters**. On the **Wave processing** tab, apply your preferred values for **Process waves in batch** and **Wait for lock (ms)**.
- Go to **Warehouse management \> Setup \> Waves \> Wave process methods**. Select the `allocateWave` method. On the Action Pane, select **Task configuration** to open a page that lists each warehouse where the method is set to run in parallel. Modify or delete the number of batch tasks and the assigned wave group for each listed warehouse as needed.

## Troubleshooting

### Troubleshoot using the Action center

Because the batch framework is used, errors that occur during wave processing will be captured in Action center messages generated by each batch job. To read the batch jobs related to a wave:

1. Go to **Warehouse management \> Outbound waves \> Shipment waves \> All waves**.
1. Select the wave you want to inspect.
1. On the Action Pane, open the **Wave** tab and, from the **Wave** group, select **Batch jobs**.

Wave processing is self-correcting, so any error detected during processing should be reported using the Action center.

A typical error related to parallel processing could be that two waves try to allocate the same item at the same time and one does not complete so that the other wave is unable to acquire a lock within the specified time. If this situation occurs, the batch jobs log will contain information stating that the lock for the item could not be acquired, in which case the wave that failed must be processed again.

Because the processing is happening in parallel, data must be maintained in different tables to track the state of the processing. This means that the logs for the batch jobs might contain errors such as duplicate key errors.

The errors from the batch tasks are also part of the batch jobs log. The most important information is typically at the bottom.

In rare cases, for example if the SQL connection ended, it is possible for the wave processing to end in an inconsistent state where the batch job appears to be running but the processing is stopped. The wave can't handle errors like this, so an attempt to clean up failed waves is done when the next wave runs. Alternatively, if the current wave is in an inconsistent state, perform the following steps:

1. Go to **Warehouse management \> Outbound waves \> Shipment waves \> All waves**.
1. Select the wave you need to clean up.
1. On the Action Pane, open the **Wave** tab and, in the **Wave** group, select **Cleanup wave data**.

### Troubleshoot using the wave progress log

If the **Create wave progress log** option is enabled on the **Warehouse management parameters** page, then a log record is created every time allocation for an item and its dimensions begins and ends. You should only enable this log when you need it, for example, during initial testing or for troubleshooting. When this option is enabled, you can view the log by taking the following steps:

1. Go to **Warehouse management \> Outbound waves \> Shipment waves \> All waves**.
1. Select the wave you want to inspect.
1. On the Action Pane, open the **Wave** tab and, in the **Wave** group, select **Progress**.
