---
# required metadata

title: Schedule work creation during wave
description: This topic describes how to set up and use the Schedule work creation wave processing method.
author: perlynne
manager: mirzaab
ms.date: 01/14/2021
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: WHSPostMethod, WHSWavePostMethodTaskConfig, WHSWaveTemplateTable, WHSParameters, WHSWaveTableListPage, WHSWorkTableListPage, WHSWorkTable, BatchJobEnhanced, WHSPlannedWorkOrder

# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: 
ms.search.scope: Core, Operations
# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: kamaybac
ms.search.validFrom: 2021-01-14
ms.dyn365.ops.version: 10.0.17

---

# Schedule work creation during wave

[!include [banner](../../includes/banner.md)]

Use the *Schedule work creation* feature as part of your waving process to help increase wave processing throughput by having the system create work using parallel processing.

When the functionality is enabled, planned work will automatically get created, which the system will eventually process to create actual work. If the number of wave load lines reaches a predetermined threshold, the system will create actual work more quickly by applying parallel, asynchronous processing.

## Enable the Schedule work creation feature

### Enable the feature in feature management

Before you can use the *Schedule work creation* feature, it must be turned on in your system. Admins can use the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace to check the status of the feature and turn it on if it's required. There, the feature is listed in the following way:

- **Module:** *Warehouse management*
- **Feature name:** *Schedule work creation*

> [!NOTE]
> The *Organization-wide work blocking* feature must be enabled before you can enable *Schedule work creation*.

### Manually enable batch processing of waves

To take advantage of a parallel asynchronous method to create warehouse work, your wave process must be running in batch. To set this up:

1. Go to **Warehouse management \> Setup \> Warehouse management parameters**.

1. On the **General** tab, set **Process waves in batch** to *Yes*. Optionally, you can also select a dedicated **Wave processing batch group** to prevent your batch queue processing from running at the same time as other processes.

1. Set the **Wait for lock (ms) time**, which applies when the system is processing several waves at the same time. For most larger waving processes, we recommend a value of *60000*.

### Manually enable the new wave step method for existing wave templates

Start by creating the new wave step method and enabling it for parallel asynchronous task processing.

1. Go to **Warehouse management \> Setup \> Waves \> Wave process methods**.

1. Select **Regenerate method** and note that *WHSScheduleWorkCreationWaveStepMethod* has been added to the list of wave process methods you can use in your shipping wave templates.

1. Select the record with the **Method name** *WHSScheduleWorkCreationWaveStepMethod* and select **Task configuration**.

1. To add a new row to the grid, select **New** on the Action Pane and use the following settings:

    - **Warehouse** - Select the warehouse you will use to schedule work creation processing.

    - **Maximum number of batch tasks** - Specify a maximum number of batch tasks. In most cases, this value should be in the range from 8-16, however we recommend that you experiment with the optimal setting based on your scenarios.

    - **Wave processing batch group** - Select a dedicated wave processing batch group to optimize your batch queue processing.

Now you are ready to update an existing wave template (or create a new one) to use the *Schedule work creation* wave processing method.

1. Go to **Warehouse management \> Setup \> Waves \> Wave templates**.

1. Select **Edit** on the Action Pane.

1. In the list pane, select the wave template you would like to update (if you are testing using demo data, then you could use *24 Shipping default*).

1. Expand the **Methods** FastTab and select the row with the **Name** *Schedule work creation* in the **Remaining methods** grid.

1. Select the arrow pointing to the **Selected methods** column to move the selected row to that column. (You can only have one selected method at a time that uses either *WHSScheduleWorkCreationWaveStepMethod* or *createWork*, so the existing row with **Method name** *createWork* is automatically moved to the **Remaining methods** grid.)

## Set wave task processing threshold data

The system will create default wave task processing threshold data the first time a wave process runs using any task-based processing. The data is used to control when wave processing will run asynchronously and be task-based, which enables it to process and create work in parallel.

The default data will initially use a threshold value of 15 for the minimum number of load lines (MINIMUMWAVELOADLINES). This means that when the system processes a wave with more than 15 loads lines, it will use asynchronous task processing. You can manually insert/update this data in the **WHSWaveTaskProcessingThresholdParameters** table in your test environments, but if you need to change this setting in a production environment, you must contact Microsoft Support to request the update.

## Work with the feature

When the *Schedule work creation* functionality is enabled, wave processing will create planned work, which will eventually be used by the new work creation process. During work creation, the work will be blocked using the *Organization-wide work blocking* feature.

The following flowchart shows how planned work is created during wave processing.

![Schedule work creation](media/schedule-work-creation-process.png)

### Planned work

The **Planned work details** page (**Warehouse management \> Work \> Planned work details**) shows information about the planned work, which is initially created during wave processing. The following **Process status** values are available:

- **Queued** - The planned work is waiting to be used to create work.
- **Completed** - The planned work has been used to create work.
- **Failed** – The wave processing has failed. Note that the planned work can be in a **Failed** state with or without related actual work. When the actual work creation process fails, the actual work remains in status *Cancelled*.

### Batch job for the work creation process

To view the batch jobs for processing waves, select **Batch jobs** on the Action Pane on the **All waves** page.

From here, you can view all the batch task details for each of the batch job IDs.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]