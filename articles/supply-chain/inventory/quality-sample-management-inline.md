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
<!-- KFM: Preview until further notice -->

## Prerequisites

To prepare your environment for inline sampling, be sure to set up the following elements as described in [Enable and configure sample management (preview)](quality-sample-management-admin.md)

- A number sequence for generating sample IDs.
- Sample life cycle states.
- Sample type used for inline sampling.
- Sample procedures and sample procedure types.
- An [item sampling](quality-item-sampling.md) policy set up for inline sampling. It must have the following settings on the **Sample management** FastTab:
    - **Sample inspection method** – Select *Inline process*.
    - **Sample size** – Set to the amount of material you want to sample.
    - **Unit** – Set the unit that applies to the selected sample size.
- Sample associations configured to link the inline sample type, inline item sampling, and inline sample procedures to the relevant products.

## Initiate the sample

To initiate an inline sample follow these steps:

1. Open or create a production or batch order for a batch-controlled product that is configured for inline sampling.
1. Bring the production or batch order into status *Started*.
1. On the Action Pane, open the **View** tab and, from the **Manage quality** group, select **Initiate inline sample management**.
1. The **Initiate inline sample management** dialog opens. Review and adjust the following settings:
    - **Item number** – The product for which you want to take a sample. This field is defaulted based on the production or batch order that you had open.
    - **Product name** – The name of the product for which you want to take a sample. This field is read-only and comes from the selected **Item number**.
    - **Sample type** – Set to *Inline*.
    - **Item sampling** – [Item samplings](quality-item-sampling.md) define the criteria for selecting samples. This field is defaulted based on the product that you selected, but you choose a new one if necessary.
    - **Test group** – [Test groups](quality-test-groups.md) define the set of tests applied while processing quality orders. Select the test group that defines the tests that need to be performed on this sample. This field is defaulted based on the selected item sampling.
    - **Sample size** – The amount of material that you want to sample. This field is read-only and comes from the selected item sampling.
    - **Unit** – The unit that applies to the selected sample size. This field is read-only and comes from the selected item sampling.

1. Select **OK**.

## Work with samples in the sample management workbench

To manage the inline samples related to a production or batch order, follow these steps:

1. Open or create a production or batch order for a batch-controlled product that is configured for inline sampling.
1. Initiate an inline sample as described in previous section.
1. On the Action Pane, open the **View** tab and, from the **Manage quality** group, select **Sample management workbench**.
1. On the Action Pane, open the **Sample** tab. Select the various actions here to update the sample and view related information. Learn more in [Manage and process samples (preview)](quality-sample-management-use.md).
