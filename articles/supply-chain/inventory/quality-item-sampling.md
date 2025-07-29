---
title: Quality management item sampling
description: Learn how to set up item sampling and how it's used as part of a quality association, including an outline and step-by-step process for setting up item sampling.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: InventItemSampling
ms.topic: how-to
ms.date: 07/28/2025
ms.custom: 
  - bap-template
---

# Quality management item sampling

[!include [banner](../includes/banner.md)]

Item sampling is used as part of a quality association. It defines the amount of current physical inventory that must be inspected. Sampling can be based on fixed quantities, a percentage, or a full license plate.

## Set up item sampling

Follow these steps to set up item sampling.

1. Go to **Inventory management \> Setup \> Quality control \> Item sampling**.
1. Select **New**.
1. Make the following settings in the header of your new record:
    - **Item sampling**: Enter a name for the record.
    - **Description**: Enter a short description of the record.
    - **Sampling scope**: Select the scope to use when evaluating if quality work should be created. When set to *Shipment* or *Load*, those entities are used if available. If not, the *Order* is used.
    - **Use acceptance sampling charts**: Choose whether to use acceptance sampling with this record. Learn more in [Acceptance sampling (preview)](quality-acceptance-sampling.md).

1. If you're using acceptance sampling, then fill out the settings provided on the **Acceptance sampling** FastTab. Learn more about how to use these settings in [Acceptance sampling (preview)](quality-acceptance-sampling.md).
1. On the **Sampling quantity** FastTab, in the **Value** field, enter a number. This value is related to the quantity specification value that is selected in the adjacent field.
1. On the **Process** FastTab, make the following settings:
    - **Full blocking**: Set to *Yes* if the entire lot or order line quantity should be blocked when a test fails. Set this option to *No* if only the items in the quality order should be blocked when a test fails.
    - For each dimension (such as **License plate** or **Batch number**) that should be automatically populated on the **Inventory dimensions** tab of a quality order, set it's option to *Yes*.
1. Select **Save**.
1. Close the page.

> [!NOTE]
> The *Quality management for warehouse processes* feature provides additional item sampling capabilities. It adds the concept of *item sampling scope* and lets you define a full license plate as the quantity specification. If you've turned on this feature, go to [Quality management for warehouse processes](quality-management-for-warehouses-processes.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
