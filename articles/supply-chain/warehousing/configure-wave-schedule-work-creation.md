---
# required metadata

title: Schedule work creation during wave
description: This article describes how to set up and use the Schedule work creation wave processing method.
author: Mirzaab
ms.date: 01/14/2021
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: WHSPostMethod, WHSWavePostMethodTaskConfig, WHSWaveTemplateTable, WHSParameters, WHSWaveTableListPage, WHSWorkTableListPage, WHSWorkTable, BatchJobEnhanced, WHSPlannedWorkOrder

# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac

# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2021-01-14
ms.dyn365.ops.version: 10.0.17

---

# Schedule work creation during wave

[!include [banner](../../includes/banner.md)]

Use the *Schedule work creation* feature as part of your waving process to help increase wave processing throughput by having the system create work using parallel processing.

When the functionality is enabled, planned work will automatically get created, which the system will eventually process to create actual work. If the number of wave load lines reaches a predetermined threshold, the system will create actual work more quickly by applying parallel, asynchronous processing.

## Turn on the scheduled work creation features in feature management

To use the features described in this article, they must be turned on for your system. Use [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace to turn on the following features in the following order:

1. *Organization-wide work blocking* – Required for both manual and automatic configuration of scheduled work creation. (As of Supply Chain Management version 10.0.21, this feature is mandatory and can't be turned off.)
1. *Schedule work creation* – Required for both manual and automatic configuration of scheduled work creation. (As of Supply Chain Management version 10.0.32, this feature is mandatory and can't be turned off.)
1. *Organization-wide "Schedule work creation" wave method* – Required for automatic configuration of scheduled work creation. You don't need this feature if you will only use manual configuration. (As of Supply Chain Management version 10.0.32, this feature is mandatory and can't be turned off.)

<a name="Auto-enable-schedule-work-creation"></a>

## Automatically configure scheduled work creation

If you enable the *Organization-wide "Schedule work creation" wave method* feature, the following automatically occurs on your system:

- The *Schedule work creation* wave method (`WHSScheduleWorkCreationWaveStepMethod`) is added and configured to run in parallel across all legal entities.
- Wave templates from all legal entities that have **Wave template type** set to *Shipping* and **Template status** set to *Valid* will have the *Create work* method replaced by the *Schedule work creation* method. However, wave templates from legal entities where the *Create work* method is allowed to be repeatable will not be modified.
- Task configurations for the *Schedule work creation* method will be created for all warehouses from all legal entities that have **Use warehouse management processes** enabled. This means that the *Schedule work creation* method will now run in parallel by default. Existing warehouses for which you change **Use warehouse management processes** from *No* to *Yes* will also run this method in parallel by default.
- All legal entities will process waves in batches and **Wait for lock (ms)** will be set to a default value of *60,000* ms if it was previously set to *0* ms.
- All the new wave templates that you create will have the *Schedule work creation* wave method instead of the *Create Work* method.

The existing task and wave processing configurations will also be kept for all legal entities that are already configured to process waves in batches, and for all warehouses that are already configured to use the *Schedule work creation* method in parallel.

If necessary, you can manually revert any or all of the settings made automatically when you enabled the *Organization-wide Schedule work creation wave method* feature by doing the following:

- For wave templates, go to **Warehouse management \> Setup \> Waves \> Wave templates**. Replace *Schedule work creation* method with *Create work*.
- For warehouse parameters, go to **Warehouse management \> Setup \> Warehouse management parameters**. On the **Wave processing** tab, apply your preferred values for **Process waves in batch** and **Wait for lock (ms)**.
- For the wave methods, go to **Warehouse management \> Setup \> Waves \> Wave process methods**. Select `WHSScheduleWorkCreationWaveStepMethod` and, on the Action Pane, select **Task configuration**. Modify or delete the number of batch tasks and the assigned wave group for each listed warehouse as needed.

## Manually configure scheduled work creation

If you didn't enable the [*Organization-wide "Schedule work creation" wave method* feature](#Auto-enable-schedule-work-creation), then you can use the procedures provided in this section to manually configure scheduled work creation as needed.

### Manually enable batch processing of waves

To take advantage of a parallel asynchronous method to create warehouse work, your wave process must be running in batch. To set this up:

1. Go to **Warehouse management \> Setup \> Warehouse management parameters**.
1. On the **General** tab, set **Process waves in batch** to *Yes*. Optionally, you can also select a dedicated **Wave processing batch group** to prevent your batch queue processing from running at the same time as other processes.
1. Set the **Wait for lock (ms) time**, which applies when the system is processing several waves at the same time. For most larger waving processes, we recommend a value of *60000*.

### Manually enable the new wave step method for existing wave templates

Start by creating the new wave step method and enabling it for parallel asynchronous task processing.

1. Go to **Warehouse management \> Setup \> Waves \> Wave process methods**.
1. Select **Regenerate method** and note that *WHSScheduleWorkCreationWaveStepMethod* has been added to the list of wave process methods you can use in your shipping wave templates.
1. Select the record with the **Method name** *WHSScheduleWorkCreationWaveStepMethod* and select **Task configuration**.
1. To add a new row to the grid, select **New** on the Action Pane and use the following settings:

    - **Warehouse** - Select the warehouse you will use to schedule work creation processing.
    - **Maximum number of batch tasks** - Specify a maximum number of batch tasks. In most cases, this value should be in the range from 8-16, however we recommend that you experiment with the optimal setting based on your scenarios.
    - **Wave processing batch group** - Select a dedicated wave processing batch group to optimize your batch queue processing.

Now you are ready to update an existing wave template (or create a new one) to use the *Schedule work creation* wave processing method.

1. Go to **Warehouse management \> Setup \> Waves \> Wave templates**.
1. Select **Edit** on the Action Pane.
1. In the list pane, select the wave template you would like to update (if you are testing using demo data, then you could use *24 Shipping default*).
1. Expand the **Methods** FastTab and select the row with the **Name** *Schedule work creation* in the **Remaining methods** grid.
1. Select the arrow pointing to the **Selected methods** column to move the selected row to that column. (You can only have one selected method at a time that uses either `WHSScheduleWorkCreationWaveStepMethod` or `createWork`, so the existing row with **Method name** `createWork` is automatically moved to the **Remaining methods** grid.)

## Set wave task processing threshold data

The system will create default wave task processing threshold data the first time a wave process runs using any task-based processing. The data is used to control when wave processing will run asynchronously and be task-based, which enables it to process and create work in parallel.

The default data will initially use a threshold value of 15 for the minimum number of load lines (`MINIMUMWAVELOADLINES`). This means that when the system processes a wave with more than 15 loads lines, it will use asynchronous task processing. You can manually insert/update this data in the `WHSWaveTaskProcessingThresholdParameters` table in your test environments. If you need to change this setting in a production environment, you must contact Microsoft Support to request the update.

## Work with the scheduled work creation

For details about how to work with scheduled work creation, see [Wave creation and processing](wave-processing.md). 


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
