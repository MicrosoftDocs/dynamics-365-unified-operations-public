---
title: Schedule wave label printing during wave
description: This topic describes how to set up and use the task-based wave label printing functionality.
author: MSFTGarm
ms.date: 06/09/2021
ms.topic: article
ms.search.form: WHSPostMethod, WHSWavePostMethodTaskConfig, WHSWaveTemplateTable, WHSParameters, WHSWaveTableListPage, WHSWorkTableListPage, WHSWorkTable, BatchJobEnhanced, WHSPlannedWorkOrder
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: v-obaranov
ms.search.validFrom: 2021-06-09
ms.dyn365.ops.version: 10.0.16
---

# Schedule wave label printing during wave

[!include [banner](../../includes/banner.md)]

Use the *Task based wave label printing* feature as part of your waving process to improve efficiency and separate creation of wave labels and work by having the system create wave labels in a separate task.

Wave label printing configuration is a complex task and relies on accuracy of configuration and master data in many aspects. It isn't uncommon for wave label record generation to fail, which results in the entire wave processing being rolled back. The *Task based wave label printing* feature helps you to avoid recreating work and work lines each time a wave label isn't printed correctly.

When you use *Task based wave label printing*, the system first creates work and work lines, then creates and prints wave labels, and then releases the work and wave for picking, provided wave label creation completed correctly.

## Turn on the Task based wave label printing feature in feature management

To use the features described in this topic, they must be turned on for your system. Use [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace to turn on the following features in the following order:

1. *Wave label printing* - Required to enable wave label printing wave process method.
1. *Organization-wide work blocking* - Required for both manual and automatic configuration of scheduled work creation.
1. *Task based wave label printing* - Required for splitting wave label printing to a separate transaction scope.

## Manually enable the new wave step method

Start by creating the new wave step method and enabling it for parallel asynchronous task processing.

1. Go to **Warehouse management \> Setup \> Waves \> Wave process methods**.
1. On the Action Pane, select **Regenerate method** and note that *waveLabelPrinting* has been added to the list of wave process methods you can use in your shipping wave templates.
1. Select the record with the **Method name** *waveLabelPrinting* and, on the Action Pane, select **Task configuration**.
1. To add a new row to the grid, select **New** on the Action Pane and make the following settings for the new row:

    - **Warehouse** - Select the warehouse you will use to schedule work creation processing (if you are testing using demo data, then you could use warehouse *24*).
    - **Maximum number of batch tasks** - Specify a maximum number of batch tasks. In most cases, this value should be in the range from 8-16, however we recommend that you experiment with the optimal setting based on your scenarios.
    - **Wave processing batch group** - Select a dedicated wave processing batch group to optimize your batch queue processing.

Now you are ready to update an existing wave template (or create a new one) to use the *Wave label printing* wave processing method.

1. Go to **Warehouse management \> Setup \> Waves \> Wave templates**.
1. Select **Edit** on the Action Pane.
1. In the list pane, select the wave template you would like to update (if you are testing using demo data, then you could use *24 Shipping default*).
1. Expand the **Methods** FastTab and select the row with the **Name** *waveLabelPrinting* in the **Remaining methods** grid.
1. Select the arrow pointing to the **Selected methods** column to move the selected row to that column.
1. Enter a **Wave step code**, which will be used to connect the wave template with a wave label template.

## Set wave task processing threshold data

The first time a wave process runs using any task-based processing, the system will create default wave task processing threshold data. This data is used to control when wave processing will run asynchronously and be task-based, which enables it to process and create wave labels in parallel.

The default data will initially use a threshold value of 1 for the minimum number of work IDs (`MinimumWorkThresholdForLabelPrinting`). This means that when the system processes a wave with more than 1 work ID, it will use task-based processing of wave labels in a separate transaction. You can manually insert/update this data in the `WHSWaveTaskProcessingThresholdParameters` table in your test environments. If you need to change this setting in a production environment, you must contact Microsoft Support to request the update.

## Changes to the wave processing logic with the task based wave label printing

If the wave label processing exceeds the threshold described previously, task-based processing is initiated. Starting with the next wave processing that fits this wave template, wave label printing will run in a standalone *ttsbegin*/*ttscommit* transaction right after work creation. Work release (unblocking), if configured on the wave template to run automatically, happens only after wave label printing process completed successfully.

If wave label generation fails (for example, if conversion of work quantity to wave label quantity fails and throws an error), only the appropriate transaction fails, while the work created in the previous step stays frozen. To correct errors and print the wave labels, do the following steps:

1. Go to **Warehouse management \> Outbound waves \> Shipment waves \> All waves**.
1. Select the relevant wave on the grid.
1. On the Action Pane, open the **Wave** tab and, from the **Print** group, select **Wave labels**.
1. Follow the instructions on your screen to send the labels for print.
1. On the Action Pane, open the **Wave** tab and, from the **Wave** group, select **Release**. This manually releases the work for the selected wave.

## Additional resources

- [Wave label printing](configure-wave-label-printing.md)
- [Schedule work creation during wave](configure-wave-schedule-work-createion.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
