---
title: Fixed receipt price
description: Learn how you can configure and use fixed receipt prices in Microsoft Dynamics 365 Supply Chain Management with an outline on fixed receipt prices. 
author: rachel-profitt
ms.author: raprofit
ms.reviewer: kamaybac
ms.search.form: InventPosting, InventItemGroup, InventModelGroup
ms.topic: how-to
ms.date: 06/07/2024
ms.custom: 
  - bap-template
  - evergreen
---

# Fixed receipt price

[!include [banner](../includes/banner.md)]

**Fixed receipt price** is an option that you can select on an item model group when you use an inventory model other than *Standard cost* or *Moving weighted average*. In early versions of Microsoft Dynamics AX, this option was named **Standard cost**. It was renamed **Fixed receipt price** when the new standard cost inventory model was introduced in Dynamics AX 2012. This article explains how you can configure and use fixed receipt prices in Dynamics 365 Supply Chain Management.

## About fixed receipt prices

When you select the **Fixed receipt price** checkbox on the **Item model group** page for an item, the system uses the receipt price as a standard cost for the inventory receipt. If the purchase price and the default item cost price that is configured for a product differ, the difference is posted to the **Fixed receipt price profit** or **Fixed receipt price loss** account and offset to the **Fixed receipt price offset** account that you specify on the **Inventory posting profile** page.

Because the **Fixed receipt price** option is used with different inventory models (such as first in, first out (FIFO); last in, first out (LIFO); and weighted average), the *Inventory close and adjustment* process will still create settlements and adjustments according to the inventory principle that you select on the **Item model group** page. However, adjustments are made only to issues from inventory.

For example, you've configured a product with an item model group where the **Inventory model** field is set to *FIFO* and the **Fixed receipt price** option is selected. When you receive inventory through a purchase order, the inventory value is set to the value of the item's default cost price at the time of product receipt. When you invoice the purchase order, if the invoice price is different, the system posts the default cost price on the released product to the inventory account. It posts the difference to the fixed receipt price profit or loss account. Later, when you sell or consume the product, the system uses the running average for the item at the time when the sales order invoice was posted (unless you use marking).

When you run the *Inventory close and adjustment* process, the system creates a settlement with the first issue against the first receipt. The difference between the receipt price that was used on the receipt and the running average that was used on the issue is posted in a new voucher.

## Enable fixed receipt prices

To enable fixed receipt prices for an item, follow these steps.

1. Go to **Inventory management \> Setup \> Inventory \> Item model groups**.
2. Create a new item model group, or select an existing model group.
3. On the **Costing method & cost recognition** FastTab, select the **Fixed receipt price** checkbox.

    > [!NOTE]
    > You can't select the **Fixed receipt price** checkbox if the **Inventory model** field is set to *Standard cost* or *Moving average*.

4. Close the page.

After you enable the **Fixed receipt price** option, you must update your inventory posting profile by following these steps.

1. Go to **Inventory management \> Setup \> Posting \> Posting**.
1. On the **Purchase order** tab, in the **Select** column, select **Fixed receipt price profit**.
1. On the Action Pane, select **New** to add a row to the grid.
1. Set up the new row so that it applies to the item model group that you enabled fixed receipt pricing for, and specify the main account that is used to record fixed receipt price profits for purchase orders. Configure other settings as you require.
1. In the **Select** column, select **Fixed receipt price loss**. Add a new row that applies to the item model group that you enabled fixed receipt pricing for, and specify the main account that is used to record fixed receipt price losses for purchase orders. Configure other settings as you require.
1. In the **Select** column, select **Fixed receipt price offset**. Add a new row that applies to the item model group that you enabled fixed receipt pricing for, and specify the main account that is used to record fixed receipt price offsets for purchase orders. Configure other settings as you require.
1. On the **Inventory** tab, in the **Select** column, select **Fixed receipt price profit**. Add a new row that applies to the item model group that you enabled fixed receipt pricing for, and specify the main account that is used to record fixed receipt price profits for inventory. Configure other settings as you require.
1. In the **Select** column, select **Fixed receipt price loss**. Add a new row that applies to the item model group that you enabled fixed receipt pricing for, and specify the main account that is used to record fixed receipt price losses for inventory. Configure other settings as you require.

> [!NOTE]
> We usually recommend that the **Fixed receipt price profit** and **Fixed receipt price loss** fields use the same main account for both purchase orders and inventory.

> [!IMPORTANT]
> When you change the value in the **Price** field on the **Manage costs** FastTab of the **Released products** page, the system doesn't automatically revalue the inventory that is on hand. As a manual workaround, open the **Closing and adjustment** page, and select **Adjustment \> On-hand** on the Action Pane. Then select the items that are on hand, and adjust them to the current price. One clear advantage of using the standard cost inventory model is that it causes the system to automatically revalue the on-hand inventory.
