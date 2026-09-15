---
title: Item where used
description: Learn how to get an overview of where an item is used in Asset Management, including a step-by-step process for making an item-where-used calculation.
author: jodahlMSFT
ms.author: jodahl
ms.topic: article
ms.date: 09/15/2026
ms.custom:
ms.reviewer: kamaybac
ms.search.form: EntAssetItemWhereUsed, EntAssetItemWhereUsedCalculate
---

# Item where used

[!INCLUDE [banner](../../includes/banner.md)]

You can calculate where a specific item is used in Asset Management. The results show the context in which the item is used during its lifetime. You can open the **Item where used** page from the main Asset Management menu. You can also access it from the following pages:

- [Asset BOMs](../objects/object-bom.md)
- [Asset spare parts](../setup-for-objects/spare-parts.md)
- [Maintenance job type categories and maintenance job types, maintenance job type variants, maintenance job trades, and maintenance checklists](../setup-for-work-orders/job-groups-and-job-types-variants-trades-and-checklists.md)
- [Maintenance forecast](../work-orders/maintenance-forecasts.md)
- [Procurement](../work-orders/procurement.md)
- [Work order purchase](../work-orders/procurement.md)

To see where an item is used, follow these steps:

1. Select **Asset management** > **Inquiries** > **Item where used**, or select the **Item where used** button on one of the pages mentioned earlier.
1. In the **Item where used** dialog, select the item for which you want to perform the calculation in the **Item number** field.
1. Use the **Level** field to indicate how detailed you want the item lines to be regarding functional locations.

    For example, if you enter *1* in the field and you have a multilevel functional location structure, all item lines for a functional location appear at the top level. Therefore, relation and quantity on a line might be summed from functional locations at a lower level.

    If you enter *0* in the **Level** field, you see a detailed result that shows all item lines on all the functional location levels to which they're related.

1. In the **Include** section, set filtering options to control which types of items that you want to include in the calculation.
1. Select **OK** to start the calculation.
1. On the Action Pane, open the **Item where used** tab, select the various **Group by** buttons to show the required detail level of the calculation. The selected buttons are highlighted. Select a button to activate or deactivate it.
1. To choose which dimensions to display in the grid, open the **Item where used** tab on the Action Panel and then select **Display dimensions**.

The following screenshot shows an example of an item-where-used calculation for item number *1000*.

:::image type="content" source="media/12-controlling-and-reporting.png" alt-text="Example of item where used calculation." lightbox="media/12-controlling-and-reporting.png":::
