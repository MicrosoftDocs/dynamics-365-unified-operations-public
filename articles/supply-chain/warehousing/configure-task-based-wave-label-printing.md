---
# required metadata

title: Schedule wave label printing during wave
description: This topic describes how to set up and use the task-based wave label printing functionality.
author: MSFTGarm
ms.date: 06/09/2021
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: WHSPostMethod, WHSWavePostMethodTaskConfig, WHSWaveTemplateTable, WHSParameters, WHSWaveTableListPage, WHSWorkTableListPage, WHSWorkTable, BatchJobEnhanced, WHSPlannedWorkOrder

audience: Application User
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
ms.search.region: Global
ms.author: kamaybac
ms.search.validFrom: 2021-06-09
ms.dyn365.ops.version: 10.0.16

---

# Schedule wave label printing during wave

[!include [banner](../../includes/banner.md)]

Use the *Task based wave label printing* feature as part of your waving process to improve efficiency and separate creation of wave labels and work by having the system create wave labels in a separate task.

When the functionality is enabled, work and work lines will get created, then wave labels created and printed, and then work and wave released for picking, if the wave label creation processed correctly.

Wave label printing configuration is a complex task and relies on accuracy of configuration and master data in many aspects. So, it is not uncommon to arrive at the situation when a wave label record generation fails, and then the entire wave processing is rolled back. So, in order to avoid re-creating work and work lines each time a wave label was not printed correctly, the new *Task based wave label printing* feature is introduced.

## Turn on the Task based wave label printing feature in feature management

To use the features described in this topic, they must be turned on for your system. Use [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace to turn on the following features in the following order:

1. **Wave label printing** - Required to enable wave label printing wave process method.
1. **Organization-wide work blocking** - Required for both manual and automatic configuration of scheduled work creation.
1. **Task based wave label printing** - Required for splitting wave label printing to a separate transaction scope.

## Manually enable the new wave step method

Start by creating the new wave step method and enabling it for parallel asynchronous task processing.

1. Go to **Warehouse management \> Setup \> Waves \> Wave process methods**.
1. Select **Regenerate method** and note that *waveLabelPrinting* has been added to the list of wave process methods you can use in your shipping wave templates.
1. Select the record with the **Method name** *waveLabelPrinting* and select **Task configuration**.
1. To add a new row to the grid, select **New** on the Action Pane and use the following settings:

    - **Warehouse** - Select the warehouse you will use to schedule work creation processing.
    - **Maximum number of batch tasks** - Specify a maximum number of batch tasks. In most cases, this value should be in the range from 8-16, however we recommend that you experiment with the optimal setting based on your scenarios.
    - **Wave processing batch group** - Select a dedicated wave processing batch group to optimize your batch queue processing.

Now you are ready to update an existing wave template (or create a new one) to use the *Wave label printing* wave processing method.

1. Go to **Warehouse management \> Setup \> Waves \> Wave templates**.
1. Select **Edit** on the Action Pane.
1. In the list pane, select the wave template you would like to update (if you are testing using demo data, then you could use *24 Shipping default*).
1. Expand the **Methods** FastTab and select the row with the **Name** *waveLabelPrinting* in the **Remaining methods** grid.
1. Select the arrow pointing to the **Selected methods** column to move the selected row to that column.
1. Add a **Wave step code** that will be used to connect the wave template with wave label template.

## Set wave task processing threshold data

The system will create default wave task processing threshold data the first time a wave process runs using any task-based processing. The data is used to control when wave processing will run asynchronously and be task-based, which enables it to process and create wave labels in parallel.

The default data will initially use a threshold value of 1 for the minimum number of works (`MinimumWorkThresholdForLabelPrinting`). This means that when the system processes a wave with more than 1 work, it will use task based processing of wave labels in a separate transaction. You can manually insert/update this data in the `WHSWaveTaskProcessingThresholdParameters` table in your test environments. If you need to change this setting in a production environment, you must contact Microsoft Support to request the update.

## Changes to the wave processing logic with the task based wave label printing

If the wave label processing exceeds the threshold described above, the task based processing is initiated. Starting with the next wave processing that fits this wave template, wave label printing will run in a standalone *ttsbegin*/*ttscommit* transaction right after work creation. Work release (unblocking), if configured on the wave template to run automatically, happens only after wave label printing process completed successfully. 

If wave label generation fails (for example, conversion of work quantity to wave label quantity fails and throws an error), only the appropriate transaction fails, while the work created in the previous step stays frozen. The errors can be corrected, and wave labels printed by activating the **Print \> Wave labels** button on the **Warehouse management \> Outbound waves \> Shipment waves \> All waves** page. After that, the work under the wave can be released manually by activating the **Wave \> Release** button on the same page.

## Additional resources

- [Wave label printing](configure-wave-label-printing.md)
- [Schedule work creation during wave](configure-wave-schedule-work-createion.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
