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
  - **Unit** – Select the unit of measurement for the sample size (such as *Pieces* or *Milliliters*).
  - **One sample every** – Specify how often samples should be taken and then choose whether to count batches or license plates (for example, enter *10* and select *Batch* to take a sample from every tenth batch that's reported as finished).
  - **Number of samples per quality order generated** – Specify how often samples should be tested (for example, enter *4* to test every fourth sample).

    





- Define a sample association and make the following selections:
  - **Item code** – Select which products should be included in the rule. Choose one of the following values:
    - *Table* – A specific product.
    - *Group* – A group of products.
    - *All* – All products.
    - **Item** – Depending on what you selected for **Item code**, choose the specific product or product group for which this rule should apply. Leave blank if **Item code** is set to *All*.
  - **Inline sample type** – Select the sample type that defines how the inline sample should be inspected, including its applicable lifecycle states. This sample type governs the inspection method used for inline sampling and ensures that the correct procedures and validations are applied throughout the sample's lifecycle.
  - **Inline sample scrap in days** – Specify how many days inline samples should be retained before being automatically scrapped. This setting helps manage sample lifecycle and storage by defining the retention period for inline samples associated with the item.
  - **Default item sampling for inline** – Specifies the default item sampling method applied to inline samples during production. When initiating inline sampling from the production orders list or details page, this value is pre-filled in the create dialog but can be adjusted as needed.
  - **Default inline test group** – Specify the default test group used for inline samples from production. When initiating inline sampling from the production orders list or details page, thsi value is pre/filled in the create dialog but can be adjusted as needed

- to specify for which product or products the inline samples should be applicable for. Note that the inline sample process is only applicable for batch-controlled products. Learn more in [admin topic](quality-sample-management-admin.md).