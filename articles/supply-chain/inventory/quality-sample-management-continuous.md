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

<!-- KFM: 

Summarize all of the settings required to make continuous sampling work. Refer to the [admin topic](quality-sample-management-admin.md) for most settings. Add any extra configurations that are required. (We might not need this topic, but I think it would be nice)

-->

# Set up continuous sampling (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.45 GA -->

## Prerequisites

To initiate the continuous sampling process follow these steps. 

Make sure to set up the following elements as described in [Enable and configure sample management (preview)](quality-sample-management-admin.md)

- Add number sequence for generating sample-ID's.
- Define the sample life cycle states.
- Define the sample type used for continuous sampling and add the applicable life cycle states. 
- Define the sample procedures and sample procedure types as needed.
- Define an [item sampling](quality-item-sampling.md) for continuous sampling. In the sample management FastTab, make the following selections:
  - **Sample inspections method** – Select *Continuous process*.
  - **Sample size** – Enter the desired sample size.
  - **Unit** – Select the unit of measurement for the sample size.
  - **One sample every** – Specify how often samples should be taken and then choose whether to count batches or license plates (for example, enter *10* and select *Batch* to take a sample from every tenth batch that's reported as finished).
  - **Number of samples per quality order generated** – Specify how often samples should be tested (for example, enter *4* to test every fourth sample).

- Define a sample association and make the following selections:
  - **Item code** – Select which products should be included in the rule. Choose one of the following values:
    - *Table* – A specific product.
    - *Group* – A group of products.
    - *All* – All products.
    - **Item** – Depending on what you selected for **Item code**, choose the specific product or product group for which this rule should apply. Leave blank if **Item code** is set to *All*.
 - **Continuous sample type** – Select the sample type that defines how the continuous sample should be inspected, including its applicable lifecycle states. This sample type governs the inspection method used for continuous sampling and ensures that the correct procedures and validations are applied throughout the sample's lifecycle.
 - **Continuous sample scrap in days** – Select the number of days that continuous samples for this item should be saved before being scrapped.

1. With the relevant row still selected in the top section, add each of the [sample procedures](#configure-sample-procedures) that workers should follow when handling samples for this association. Use the toolbar buttons to add or remove procedures as needed.
1. On the Action Pane, select **Save**.


## Initiate the sample

To initiate continuous samples follow these steps:

1. Create a production or batch order for a batch-controlled product using following basic configuration for continuous sampling:
    - On item sampling make the following settings:
        - **Sample inspection method** - Set to *Continuous process*.
        - **Sample size** - Set to *1*.
        - **Unit** - Set to *Sp* (spoonful)-
        - **One sample per every** - Set to *2* and *License plate*.
        - **Number fo samples per quality order generated** - Set to *2*.
    - On the test group, make the following settings:
        - **Inventory status** - Set to *Yes*.
        - **Failed quality order status** - Set to an inventory status where **Inventory blocking** is set to *Yes*. 
        - **Passed quality order status** select an inventory status where **Inventory blocking** is set to *No*.
        - Make sure that the test group has one test defined.
    - On the **Quality association**, make sure that the **Item sampling** and **Test group** is associated.
1. Bring the production or batch order into status *Started*
1. From the production or batch order, report as finish four license plates. 
1. On the action pane, under the **View** tab, select **Sample management workbench** 
1. Verify that two samples have been created for separate license plates, and that these license plates are in inventory status **On-hold*.
1. Select the last sample and verify that a quality order has been created for that sample.
1. On the action pane, select **Quality order**
1. On the action pane of the quality order, select **Quick results entry**
1. Register a test result for the test that is within a range that makes the test pass.
1. Close the **Quick results entry** dialog.
1. On the action pane of the quality order, select **Validate**.

## Work with samples in the sample management workbench

To manage the inline samples follow these steps:

1. On the production order details page, create a production or batch order and initiate an inline sample as described in previous section.
1. On the action pane, under **View** tab, select **Sample management workbench**
1. On the action pane, under the **Sample** tab, use the different options to update the sample and view related information. Learn more in: [Manage and process samples (preview)](quality-sample-management-use.md) 
