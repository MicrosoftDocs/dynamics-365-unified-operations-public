---
title: Set up continuous sampling (preview)
description: Learn how to set up continuous sampling for specific products.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 10/24/2025
ms.custom: 
  - bap-template
---

# Set up continuous sampling (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

## Prerequisites

To prepare your environment for inline sampling, be sure to set up the following elements as described in [Enable and configure sample management (preview)](quality-sample-management-admin.md)

- A number sequence for generating sample IDs.
- Sample life cycle states.
- Sample type used for continuous sampling.
- Sample procedures and sample procedure types.
- An [item sampling](quality-item-sampling.md) policy set up for continuous sampling. It must have the following settings on the **Sample management** FastTab:
    - **Sample inspection method** – Select *Continuous process*.
    - **Sample size** – Set to the amount of material you want to sample.
    - **Unit** – Set the unit that applies to the selected sample size.
    - **One sample every** – Specify how often samples should be taken and then choose whether to count batches or license plates.
    - **Number of samples per quality order generated** – Specify how often samples should be tested.
- Sample associations configured to link the continuous sample type, continuous item sampling, and continuous sample procedures to the relevant products. Each sample association also defines how long samples can be kept before being scrapped.

## Continuous sampling example scenario

This section provides an example of how to set up and use continuous sampling.

### Setup and generate continuous samples

The following procedure provides an example of how to set up continuous sampling. <!-- KFM: Should we have a step to set up the sample association? -->

1. Create a production or batch order for a batch-controlled product.
1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Item sampling**. Set up an item sampling policy as described in [Quality management item sampling](../inventory/quality-item-sampling.md). On the **Sample management** FastTab, be sure to make the following settings to set up continuous sampling:
    - **Sample inspection method** - Set to *Continuous process*.
    - **Sample size** - Set to *1*.
    - **Unit** - Set to *Sp* (spoonful).
    - **One sample per every** - Set to *2* and *License plate*.
    - **Number of samples per quality order generated** - Set to *2*.

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Test groups**. Set up a test group as described in [Quality management test groups](../inventory/quality-test-groups.md). Make sure at least one test is assigned in the bottom section. On the **General** tab in the top section, be sure to make the following settings to set up the test group for continuous sampling:
    - **Update inventory status** - Set to *Yes* to enable inventory status updates based on test results.
    - **Failed quality order status** - Specify the inventory status to apply to the license plate when a quality order fails.
    - **Passed quality order status** - Specify the inventory status to apply to the license plate when a quality order passes.

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Quality associations**. Set up a quality association as described in [Quality associations](../inventory/quality-associations.md). Be sure to make the following settings: <!-- KFM: Maybe we should recommend more settings here (e.g., reference type, event type and execution) -->
    - **Item** – Select the item from the production or batch order you created in the first step.
    - **Item sampling** – Select the item sampling policy that you created for this exercise.
    - **Test group** – Select the test group that you created for this exercise.

1. Return to the production or batch order that you created in the first step. Bring the order into status *Started*. Then report four license plates as finished to generate the continuous samples according to your item sampling policy. <!-- KFM: I didn't get any samples. Maybe I reported as finished wrong? -->

### Work with the samples in the sample management workbench

<!-- KFM: This information should probably be in [Manage and process samples (preview)](quality-sample-management-use.md), either repeated or instead of here. -->

The following procedure provides an example of how to use the sample management workbench to work with the continuous samples you created in the previous procedure.

1. Open the production or batch order that you created in the previous procedure.
1. On the Action Pane, open the **View** tab and, from the **Manage quality** group, select **Sample management workbench**.
1. Verify that two samples have been created for separate license plates, and that these license plates are blocked by their default inventory status. Learn more about configuring the default item status in [Enable and configure sample management (preview)](quality-sample-management-admin.md).
1. Select the last sample and verify that a quality order has been created for that sample. <!-- KFM: How can I verify this? -->
1. On the Action Pane, open the **Sample** tab and select **Quality orders**.
1. On the Action Pane of the quality order, select **Quick results entry**
1. Register a test result for the test that is within a range that makes the test pass. <!-- KFM: Do I need to select **Validate** here? -->
1. Close the **Quick results entry** dialog. <!-- KFM: Select the **Back** button? -->
1. On the Action Pane of the quality order, select **Validate**.
1. In the grid on the **Sample management** FastTab, verify that four records exists for the four license plates that have been produced. <!-- KFM: Where are we now? How did we get here? -->
1. Verify that the field **Update inventory status to** is set to *Available* because the quality order for the last sample passed. <!-- KFM: Where are we now? How did we get here? -->
1. Set the field **Update inventory status** to *Yes*. <!-- KFM: Where are we now? How did we get here? -->
1. Select **OK** to confirm the dialog. <!-- KFM: Where are we now? How did we get here? -->
1. In the **Sample management workbench** verify that the inventory status of the two samples are now available by the values shown in their **Current inventory status** column<!-- KFM: Why *Current* inventory status? -->. If the inventory status isn't visible in the grid, select **Display dimensions** from the Action Pane and select **Inventory status** in the **Dimension display** dialog.
