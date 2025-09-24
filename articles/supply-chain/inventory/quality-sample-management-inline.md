---
title: Initiate an inline sample (preview)
description: Learn how to initiate an inline sample, including how to create a sample from a production order or batch order.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 10/24/2025
ms.custom: 
  - bap-template
---

# Initiate an inline sample (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.45 GA -->

## Prerequisites

To initiate the inline sampling process follow these steps. 

Make sure to set up the following elements as described in [Enable and configure sample management (preview)](quality-sample-management-admin.md)

- Add number sequence for generating sample-ID's.
- Define the sample life cycle states.
- Define the sample type used for inline sampling and add the applicable life cycle states. 
- Define the sample procedures and sample procedure types as needed.
- Define an [item sampling](quality-item-sampling.md) for inline sampling. In the sample management FastTab, make the following selections:
    **Sample inspection method** - Select *Inline process*.
    **Sample size** - Set to the amount of material you want to sample.
    **Unit** - Set the unit that applies to the selected sample size.
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

1. With the relevant row still selected in the top section, add each of the [sample procedures](#configure-sample-procedures) that workers should follow when handling samples for this association. Use the toolbar buttons to add or remove procedures as needed.
1. On the Action Pane, select **Save**.

## Initiate the sample

To initiate an inline sample follow these steps:

1. Create a production or batch order for a batch-controlled product that is configured for continuous sampling. 
1. Bring the production or batch order into status *Started*
1. On the action pane, under the **View** tab, select **Initiate inline sample management** to open the dialog for creating the inline sample. Select values for **Item sampling** and **Test group** if they are not defaulted, based on configuration in the **Sample associations**.
1. Confirm the dialog with **OK**

## Work with samples in the sample management workbench

To manage the inline samples follow these steps:

1. On the production order details page, create a production or batch order and initiate an inline sample as described in previous section.
1. On the action pane, under **View** tab, select **Sample management workbench**
1. On the action pane, under the **Sample** tab, use the different options to update the sample and view related information. Learn more in: [Manage and process samples (preview)](quality-sample-management-use.md) 

