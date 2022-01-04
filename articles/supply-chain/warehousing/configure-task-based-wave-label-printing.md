---
title: Schedule wave label printing during wave
description: This topic describes how to set up and use the functionality for task-based wave label printing.
author: perlynne
ms.date: 06/09/2021
ms.topic: article
ms.search.form: WHSPostMethod, WHSWavePostMethodTaskConfig, WHSWaveTemplateTable, WHSParameters, WHSWaveTableListPage, WHSWorkTableListPage, WHSWorkTable, BatchJobEnhanced, WHSPlannedWorkOrder
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: perlynne
ms.search.validFrom: 2021-06-09
ms.dyn365.ops.version: 10.0.16
---

# Schedule wave label printing during wave

[!include [banner](../../includes/banner.md)]

Use the *Task based wave label printing* feature as part of your waving process to help improve efficiency, and to have the system create wave labels and work in separate tasks.

The process of configuring wave label printing is complex and relies on accurate configuration and master data. It isn't uncommon for the generation of wave label records to fail, and when it does, the whole wave processing is rolled back. The *Task based wave label printing* feature helps you avoid having to re-create work and work lines every time that a wave label is incorrectly printed.

When you use the *Task based wave label printing* feature, the system first creates work and work lines. It then creates and prints wave labels. Finally, if the wave labels are correctly created, it releases the work and wave for picking.

## Turn on the Task based wave label printing feature in feature management

To use the features that are described in this topic, they must be turned on for your system. Use [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace to turn on the features in the following order:

1. *Wave label printing* – This feature is required to enable the wave process method for wave label printing.
1. *Organization-wide work blocking* – This feature is required for both manual and automatic configuration of scheduled work creation. (As of Supply Chain Management version 10.0.21, this feature is mandatory, so it is turned on by default and can't be turned off again.)
1. *Task based wave label printing* – This feature is required to split off wave label printing to a separate transaction scope.

## Manually enable the new wave step method

You must first create the new wave step method and enable it for parallel, asynchronous task processing.

1. Go to **Warehouse management \> Setup \> Waves \> Wave process methods**.
1. On the Action Pane, select **Regenerate method**. Notice that *waveLabelPrinting* is added to the list of wave process methods that you can use in your shipping wave templates.
1. Select the record where the **Method name** field is set to *waveLabelPrinting*, and then, on the Action Pane, select **Task configuration**.
1. On the Action Pane, select **New** to add a row to the grid. Then set the following fields for the new row:

    - **Warehouse** – Select the warehouse that you will use to schedule work creation processing. (If you're using demo data for testing purposes, you can select warehouse *24*.)
    - **Maximum number of batch tasks** – Specify a maximum number of batch tasks. In most cases, the value should be from *8* through *16*. However, we recommend that you experiment to find the optimal setting for your scenarios.
    - **Wave processing batch group** – Select a dedicated wave processing batch group to optimize batch queue processing.

You can now update an existing wave template so that it uses the *Wave label printing* wave processing method. Alternatively, you can create a new wave template that uses it.

1. Go to **Warehouse management \> Setup \> Waves \> Wave templates**.
1. On the Action Pane, select **Edit**.
1. In the list pane, select the wave template to update. (If you're using demo data for testing purposes, you can select *24 Shipping default*.)
1. On the **Methods** FastTab, in the **Remaining methods** column, select the row where the **Name** field is set to *waveLabelPrinting*.
1. Select **add** (right arrow button) to move the selected row to the **Selected methods** column.
1. In the **Wave step code** field, enter a wave step code that will be used to connect the wave template with a wave label template.

## Set wave task processing threshold data

The first time that a wave process runs by using any task-based processing, the system creates default wave task processing threshold data. This data is used to control whether wave processing will run asynchronously and be task-based, so that it can process and create wave labels in parallel.

The default data initially uses a threshold value of *1* for the minimum number of work IDs (`MinimumWorkThresholdForLabelPrinting`). Therefore, when the system processes a wave that has more than one work ID, it will use task-based processing of wave labels in a separate transaction. You can manually insert or update this data in the `WHSWaveTaskProcessingThresholdParameters` table in your test environments. To change the setting in a production environment, you must contact Microsoft Support to request the update.

## Changes to the wave processing logic when task-based wave label printing is used

If the wave label processing exceeds the wave task processing threshold, task-based processing is initiated. In the next wave processing that fits the wave template, wave label printing will run in a standalone *ttsbegin*/*ttscommit* transaction immediately after work creation. If work release (unblocking) is configured on the wave template to run automatically, it occurs only after the wave label printing process is successfully completed.

If wave label generation fails (for example, if conversion of the work quantity to the wave label quantity fails and throws an error), only the appropriate transaction fails. The work that was previously created remains frozen. To correct errors and print the wave labels, follow these steps.

1. Go to **Warehouse management \> Outbound waves \> Shipment waves \> All waves**.
1. Select the relevant wave in the grid.
1. On the Action Pane, on the **Wave** tab, in the **Print** group, select **Wave labels**.
1. Follow the on-screen instructions to send the labels for printing.
1. On the Action Pane, on the **Wave** tab, in the **Wave** group, select **Release** to manually release the work for the selected wave.

## Additional resources

- [Wave label printing](configure-wave-label-printing.md)
- [Schedule work creation during wave](configure-wave-schedule-work-creation.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
