---
title: Options for including physical value in cost calculations
description: Learn how to use the "Include physical value" and "Include physical value in weighted average recalculation" options for cost calculations.
author: prasungoel
ms.author: prasungoel
ms.reviewer: kamaybac
ms.search.form: InventModelGroup
ms.topic: how-to
ms.date: 07/29/2024
ms.custom: 
  - bap-template
---

# Options for including physical value in cost calculations

Supply Chain Management provides two options for including physical value in cost calculations:

- Include physical value
- Include physical value in weighted average recalculation

You can also choose not to include physical value in cost calculations.

This article explains these options and how to set them up.

## Include physical value

[!include [banner](../includes/banner.md)]

You can choose whether the system should consider physically updated transactions when calculating the average cost price for items belonging to a given item model group. To set this option, follow these steps:

1. Go to **Cost management** \> **Inventory accounting policies setup** \> **Item model groups**.
1. On the list pane, select the item model group that you want to configure (or create a new one).
1. Expand the **Costing method & cost recognition** FastTab.
1. Set the **Include physical value** check box to one of the following values:
    - *Selected* – Both physically updated transactions and financially updated transactions are used to calculate the running average cost price.
    - *Cleared* – Only financially updated transactions are used to calculate the running average cost price.

The check box has slightly different effects, depending on the inventory model that you use.

- If you select the **Include physical value** check box when using the *FIFO* (first in, first out), *LIFO* (last in, first out), or *LIFO date* inventory model, inventory close also makes adjustments to physically updated transactions.
- If you don't select the **Include physical value** check box when using the *FIFO* (first in, first out), *LIFO* (last in, first out), or *LIFO date* inventory model, inventory close makes settlements only to financially updated transactions.
- When you use the *weighted average* or *weighted average date* inventory model, inventory close settles only financially updated transactions, regardless of whether you select the **Include physical value** check box.

### Include physical value example 1

The **Include physical value** check box is selected and you receive the following purchase orders:

- A purchase order for a quantity of 2 and a cost price of USD 10.00 that has been packing slip–updated.
- A purchase order for a quantity of 3 and a cost price of USD 12.00 that has been invoice-updated.

In this case, the running average cost price is USD 11.20 = (2x10+3x12)/(2+3), because both physically updated transactions and financially updated transactions are used to calculate the cost price.

### Include physical value example 2

The **Include physical value** check box isn't selected, and the cost price on the item setup is USD 10.00.

- You receive a purchase order for a quantity of 20 and a cost price of USD 12.00 that has been packing slip–updated.

When a sales order is posted, the posted cost amount is USD 10.00, because the running average cost price doesn't include physically posted transactions.

> [!NOTE]
> For comparison, if you select the **Include physical value** check box for this item, when a sales order is posted, the posted cost amount will be USD 12.00.

## Include physical value in weighted average recalculation (preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.43 GA -->

This feature lets you choose whether to include physically updated transactions that haven't yet been financially updated when recalculating weighted average.

> [!IMPORTANT]
> This capability is only available during recalculation and isn't used during inventory close. If you would like to check the results including physical value after inventory closing, you should run a new recalculation.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

### Prerequisites

To use the feature described in this section, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.41 or later.
- The feature that is named *Recalculation for Weighted Average Cost including Physical Transaction* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

### Choose whether to include physical value in weighted average recalculation

To choose whether the system should include physically updated transactions that haven't yet been financially updated when recalculating weighted average, follow these steps:

1. Go to **Cost management** \> **Inventory accounting policies setup** \> **Item model groups**.
1. On the list pane, select the item model group that you want to configure (or create a new one).
1. Expand the **Costing method & cost recognition** FastTab.
1. Set the **Include physical value in weighted average recalculation** check box to one of the following values:
    - *Selected* – Both physically updated transactions and financially updated transactions are used to calculate the running average cost price.
    - *Cleared* – Only financially updated transactions are used to calculate the running average cost price.

> [!NOTE]
>
> - This check box is only visible for item model groups where **Inventory model** is set to *Weighted avg.* or *Weighted avg. date*.
> - This option is only available during recalculation and isn't used during inventory close. To ensure accurate results, we recommend that you perform the recalculation immediately after inventory closing.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
