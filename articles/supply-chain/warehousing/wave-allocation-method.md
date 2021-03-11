---
# required metadata

title: Wave allocation
description:
manager: tfehr
ms.date: 03/08/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2021-03-08
ms.dyn365.ops.version: Release 10.0.18
---

# Wave allocation

[!include [banner](../includes/banner.md)]

Wave processing can be time consuming, and majority of the processing time is spent in the allocation step and in the work creation step.

It is now possible to run each of these steps in parallel, which can improve the performance of the wave processing, and allow for a larger throughput of waves in the same warehouse. This topic explains how to set up the wave allocation method to run in parallel. For more information about how to set up work creation to run in parallel, see [Schedule work creation during wave](configure-wave-schedule-work-creation.md).

Previously it was only possible to allocate one wave at a warehouse at a time. This constraint has now been removed and replaced by a new constraint that only locks the item and dimensions that are above location in the reservation hierarchy. Dimensions above the location always include product dimensions, so for example if an item is configured using *Color*, then variants for *Red*, *Blue*, and *Yellow* could each be processed in parallel.

This means that if the same item with the same dimensions above the location is being allocated by one wave, other waves will have to wait to acquire a lock on the same item and dimensions. If the lock can't be acquired in a timely manner, an error will be thrown and the wave processing will fail.

In order to utilize parallel processing, the wave must run in batch.

## Performance improvements

Performance benefits of parallel processing fall in two categories:

- **Improved throughput**: The throughput of waves will typically improve even if parallel processing isn't configured, especially for scenarios where there is no overlap of items within the waves.
- **Improvement of the allocation for a single wave**: Testing on customer data on a 4 core environment using 8 tasks resulted in a near 50% improvement of the overall processing for larger waves with more than 700 different items and variants. The parallel processing is done per items and dimensions above the location, so the improvements depends on how many different items a wave contains, the infrastructure available, and the duration of the allocation vs. the duration of the work creation.

## Configure parallel allocation

### Warehouse management parameters

To use parallel allocation processing, go to **Warehouse management > Setup > Warehouse management parameters** and make the following settings:

- **Wave processing batch group** - Select the batch group that the initial processing of the waves should use. The subsequent processing of allocation can be done using different batch groups.
- **Process waves in batch** - Choose whether the waves are processed in batch. You must set this to *Yes* to use parallel processing.
- **Create wave progress log** - Choose whether to automatically save information about a wave in a log file after the wave is processed, including during the parallel processing of pending allocations. You should normally only enable this during troubleshooting because it adds an extra overhead.
- **Wait for lock (ms)** - Enter the time, in milliseconds, that an allocation step will wait for a system resource that is locked by another allocation step. When this time is exceeded, the wave is not processed and an error message is displayed. We recommend that you allow at least a few seconds, since it allows for allocation of one logical unit to finish.

<!-- KFM: This repeats info already available in [Warehouse parameters for wave processing](wave-warehouse-parameters.md). We should synchronize these description and maybe even just link to the other topic instead of repeat everything here. -->

## Wave process methods

To set up parallel processing:\

1. Go to **Warehouse Management > Setup > Waves > Wave process methods**.
1. Select the `allocateWave` method in the grid.
1. On the Action Pane, select **Task configuration**.
1. The **Wave post method task configuration** page opens. This grid lists each warehouse where you have configured the `allocateWave` method. Parallel processing will only be used for warehouses that are listed here. Use the Action Pane buttons to add or remove warehouses from the grid as needed. 
1. For each warehouse, make the following settings:
    - **Maximum number of batch tasks** - Specify the number of batch tasks that should be used for the allocation for the selected warehouse. The optimal number of batch tasks depends on the infrastructure available and what other batch jobs are being processed on the server. Tests done on a 4 core environment that was dedicated to wave processing showed that using 8 tasks lead to good results.
    - **Wave processing batch group** - Specific batch groups can be used for different warehouses in order to allow the allocation processing to scale out per warehouse.

## Enable parallelization across all legal entities
<!-- KFM: I still need to review this section -->
Having the AllocateWave method configured to run in parallel helps the performance of the wave processing.

- The *Wave parallelization for Allocate Wave method* feature is enabled by default and configures wave templates to be run in parallel for all the warehouses from all legal entities.
- The **allocateWave** method has a task configuration setting that lets you use the **Wave process methods** page to define the number of tasks that will run simultaneously equivalent to the number of parallel processes. Roughly, the time used on the allocate wave step that is between 30 to 60% is reduced by a factor equivalent to the number of tasks. It’s also possible to define which batch that will be assigned to process these tasks. It’s important to notice that all the legal entities will be configured to process waves in batch. For the warehouse management that are already configured to process waves in batch and for the warehouses that are already configured to use **allocateWave** method in parallel, the existing configuration will be kept. 
- All the new legal entities will be configured by default to process waves in Batch and all the new warehouses with the configuration **Warehouse Management Processes** enabled would have the **allocateWave** method configured to run in parallel by default. Furthermore the waves will be enable to be executed in batch and configure a default 15 seconds wave lock wait time. When a wave is running, it acquires a lock on the item and dimensions above location during allocation step. When a subsequent concurrent wave processing tries to acquire the same lock for the identical record, it is blocked. The value represents how long it is - as a maximum - acceptable to wait before the lock is released and can be acquired.
- Disabling the wave processing to be run in batch can have an impact of the performance of the wave processing, especially if the wave processing is using a parallelization process defined at the task configuration at relevant wave methods.

Each of the above defaulting can be reverted manually after enabling the *Wave parallelization for Allocate Wave method* feature.

- Warehouse parameters go to **Warehouse management \> Setup \> Warehouse management parameters** on the **Wave processing** tab, apply new values for *Process waves in batch* and *Wait for lock (ms)*
- Wave methods go to **Warehouse management \> Setup \> Waves \> Wave process methods**, select *allocateWave*, on the Action Pane, select **Task configuration**, modify or delete the batch tasks and group for each warehouse.

## Troubleshooting

### Troubleshoot using the Infolog

Because the batch framework is used, errors that occur during wave processing will be captured as part of the batch jobs Infologs. The batch jobs related to a wave can be viewed using the **Batch jobs** button. <!-- KFM: Where is this button? -->

Wave processing is self-correcting, so any error detected during processing should be handled gracefully and reported using the Infolog.

A typical error related to parallel processing could be that two waves try to allocate the same item at the same time and one does not complete so that the other wave is unable to acquire a lock within the specified time. If this situation occurs, the batch jobs log will contain information stating that the lock for the item could not be acquired, in which case the wave that failed must be processed again.

Because the processing is happening in parallel, data must be maintained in different tables to track the state of the processing. This means that the logs for the batch jobs might contain errors such as duplicate key errors.

The errors from the batch tasks are also part of the batch jobs log. The most important information is typically at the bottom.

In rare cases, for example if the SQL connection ended, it is possible for the wave processing to end up in an inconsistent state where the batch job appears to be running but the processing is stopped. The wave can't handle errors like this, so an attempt to clean up failed waves is done when the next wave runs. Alternatively, you can use the **Clean up wave data** button to clean up the current wave if it is in an inconsistent state. <!-- KFM: Where is this button? -->

### Troubleshoot using the wave progress log

If the **Create wave progress log** option is enabled on the **Warehouse management parameters** page, then a log record is created every time allocation for an item and its dimensions begins and ends. Logging should only be enabled if you need it, for example, during initial testing or for troubleshooting. <!-- KFM: Where do we find this log? -->
