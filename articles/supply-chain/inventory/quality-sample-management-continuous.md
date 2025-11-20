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

To prepare your environment for inline sampling, set up the following elements as described in [Enable and configure sample management (preview)](quality-sample-management-admin.md):

- A number sequence for generating sample IDs.
- Sample lifecycle states.
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

This section illustrates how to configure and use continuous sampling. The example assumes the following setup for generating samples and quality orders:
    - A sample is created for every second license plate that is reported as finished.
    - A quality order is created for every second sample that is generated.

To work through a scenario that shows how to set up and use continuous sampling, follow these steps:

1. Create a batch-controlled product with the following characteristics:
    - **Enabled for advanced warehouse processes** – Associate the product with a **Storage dimension group** that has **Use warehouse management processes** set to *Yes*.
    - **Batch enabled** – Associate the product with a **Tracking dimension group** that has the **Batch number** dimension enabled.
    - **Automatic batch numbering** – Associate the product with a **Batch number group** that automatically generates a batch number from a number sequence when quantities are reported as finished from a production or batch order.
1. Set up a sample association for a batch-controlled product as described in [Enable and configure sample management](quality-sample-management-admin.md).
1. Create a production or batch order for the product with the following information:
    - Choose a warehouse that is enabled for the advanced warehouse processes. Make sure that **Use warehouse management processes** is set to *Yes* for the selected warehouse.
    - Set the quantity for the order to *2,000 pieces*.
1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Item sampling**. Set up an item sampling policy as described in [Quality management item sampling](../inventory/quality-item-sampling.md). On the **Sample management** FastTab, make the following settings to set up continuous sampling:
    - **Sample inspection method** – Set to *Continuous process*.
    - **Sample size** – Set to *1*.
    - **Unit** – Set to *Sp* (spoonful).
    - **One sample per every** – Set to *2* and *License plate*.
    - **Number of samples per quality order generated** – Set to *2*.

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Test groups**. Set up a test group as described in [Quality management test groups](../inventory/quality-test-groups.md). Make sure at least one test is assigned in the bottom section. On the **General** tab in the top section, make the following settings to set up the test group for continuous sampling:
    - **Update inventory status** – Set to *Yes* to enable inventory status updates based on test results.
    - **Failed quality order status** – Specify the inventory status to apply to the license plate when a quality order fails.
    - **Passed quality order status** – Specify the inventory status to apply to the license plate when a quality order passes.

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Quality associations**. Set up a quality association as described in [Quality associations](../inventory/quality-associations.md). Make the following settings:
    - **Reference type** – Select **Production*.
    - **Item code** – Select *Table*.
    - **Item** – Select the item from the production or batch order you created for this scenario.
    - **Event type** – Select *Report as finished*
    - **Execution** – Select *After*.
    - **Item sampling** – Select the item sampling policy that you created for this exercise.
    - **Test group** – Select the test group that you created for this exercise.

1. Return to the production or batch order that you created for this scenario.
1. Bring the order into status *Started*.
1. Report four license plates as finish by following these steps:
    1. On the Action Pane, open the **Production order** tab and, from the **Process** group, select **Report as finished**.
    1. The **Report as finished** dialog opens. Check that the **License plate** dimension is visible in the grid. If it's not visible, select **Inventory** \> **Display dimensions** from the toolbar and then select the **License plate** check box in the **Display dimensions** dialog.
    1. Create four new license plates by following these steps:
        - Right-click on the right side of the **License plate** field. Then select **View details** from the context menu to open the **License plates** page.
        - On the Action Pane, select **New** to create a new license plate.
        - In the **License plate** field, enter a unique and recognizable ID for the license plate.
        - Repeat the last two steps until you have created four license plates.
        - On the Action Pane, select the **Back** button to return to the **Report as finished** dialog.
    1. Complete the report-as-finished operation by providing the following information in the **Report as finished** dialog:
        - In the **Good quantity** field, set the value to *20*.
        - In the **License plate** field, select the first license plate you created in the previous step.
        - Make sure that the **End job** checkbox isn't selected.
        - Select **OK** to confirm report as finished of the first license plate.
    1. Complete three more report-as-finished operations for this production order—one for each of the remaining three license plates. Make sure to set the **Good quantity** field to *20* for each license plate.
    1. Verify that two samples and one quality order were created by following these steps:
        - On the Action Pane, open the **View** tab and, from the **Manage quality** group, select **Sample management workbench**.
        - Verify that two samples were created for separate license plates, and that these license plates are blocked according to their default inventory status. Learn more about configuring the default item status in [Enable and configure sample management](quality-sample-management-admin.md). <!-- KFM: Where do we check these? On the **Dimensions** tab? Status shows available, so I tried to set a default status that blocks, But the system doesn't let me set a default status that blocks (see comment in admin topic). -->
        - Select the last sample and open the **References** tab in the bottom section to confirm that the sample has an associated **Quality order**.
