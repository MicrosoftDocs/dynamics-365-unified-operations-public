---
title: Return cost price and return lot ID    
description: Learn about the cost price and return lot IDs, including outline on manually entering return cost prices and automatically generating cost prices.
author: AditiPattanaik
ms.author: adpattanaik
ms.topic: article
ms.date: 04/30/2018
ms.custom:
ms.reviewer: kamaybac
ms.search.region: Global 
ms.search.form: ReturnTableListPage, ReturnInventTransIdLookup, ReturnItemNumLookup
---

# Return cost price and return lot ID

[!include [banner](../includes/banner.md)]

The cost of products that are returned to inventory is calculated by using the current cost of the products. However, you might want the cost of the returned products to equal the cost of the products at the time when you sold the products to the customer. You can do this by using the **Return lot ID** field on the **Line details** FastTab in the **Sales order** form.

For example, consider the following scenario. You invoice a customer. Then, the customer returns the delivered products to you. You return the products to stock. In this case, when you credit the customer for the returned products, the cost of those products is calculated by using the current cost of the products. However, if you use the **Return lot ID** field, the cost of the returned products is calculated by using the cost on the invoice of the original sale to the customer.

To use a cost other than the current cost for returns from a customer, use one of the following methods.

## Method 1: Manually enter the return cost price

By default, when you add items to a return order, the items are returned to inventory at the current cost price. To specify a different return cost price, follow these steps.

1. Go to **Sales and marketing** \> **Sales returns** \> **All return orders**.

1. On the **Action Pane**, in the **New** group, select **Return order**.

1. In the **Create return order** form, select a customer account, and then select **OK**.

1. In the **Return order - RMA number: %1, %2** form, select an item, and then enter a negative quantity in the **Quantity** field.

1. Select the **Line details** FastTab.

1. On the **General** tab, enter a value in the **Return cost price** field. This value is used when the goods are returned to inventory. If you do not enter a value, the current cost price is used when the goods are returned to inventory.

## Method 2: Automatically generate the cost price based on the customer invoice line

This is the preferred method to use to create return lines. To use the cost of the products at the time when you sold the products to the customer, create a return order and specify a sales line to return.

1. Go to **Sales and marketing** \> **Sales returns** \> **All return orders**.

1. On the **Action Pane**, in the **New** group, select **Return order**.

1. In the **Create return order** form, select a customer account, and then select **OK**.

1. In the **Return order - RMA number: %1, %2** form, on the **Action Pane**, select **Find sales order**.

1. In the **Find sales order** form, select the invoice line to return, and then select **OK**.

    On the **Line details** FastTab, on the **General** tab, the **Return lot ID** field displays the value from the original sales line. Additionally, the **Return cost price** field displays the cost value from the original sales line.

## Cost calculation example

When you use the **Return lot ID** field on a return order line to specify the return cost price, the cost on the return order line is used. If you run the inventory close or recalculation functionality, the cost is adjusted on the original sales line. The cost on the return order line is automatically adjusted to reflect the same cost per piece.

1. Create and release a product that is named Test. In the **Released product details** form, specify the following information:

    1. On the **Manage costs** FastTab, in the **Item group** field, select the **Parts** group.

    1. On the **General** FastTab, in the **Item model group** field, select **DEF**.

    1. On the **Purchase** FastTab, in the **Price** field, type 10.00 as the cost price of the item.

    1. On the **Action Pane**, select **Dimension groups**. In the **Storage dimension group** field, select **Site and Warehouse only**. In the **Tracking dimension group** field, select **No active tracking dimensions**.

1. Create a purchase order for 10 pieces of the Test item at 6.00 per piece, and then post an invoice for the purchase order.

    Create a second purchase order for 10 pieces of the Test item at 8.00 per piece, and then post an invoice for the purchase order.

1. Post an invoice for a sales order to sell five pieces of the Test item.

    In this case, the sales order line is costed at 35.00 (5 pieces \* 7.00 average cost per piece).

1. Create a return order for the customer. In the **Find sales order** form, select the invoice line, and then select **OK**.

1. In the **Return order - RMA number: %1, %2** form, verify that a return order is generated to return the Test item. The quantity of the return order is set to -5.00.

    The **Return lot ID** field displays a lot ID. This lot ID is taken from the original sales order of the item that was sold to the customer. The **Return cost price** field displays the cost price from the original sales line.

1. Register the receipt of the returned items.

1. Post a packing slip for the returned items.

1. Post an invoice for the return order. On the **All sales orders** list page, select a sales order for which **Returned order** is the order type.

1. Open the **Inventory transactions** form. Verify that the return is costed at 7.00 per piece by using the value in the **Return cost price** field, for a total of 35.00 in the **Cost amount** field. You can open the **Inventory transactions** form from the **Return order - RMA number: %1, %2** form. In the **Lines** grid, select **Inventory** \> **Transactions**.

1. In Inventory and warehouse management, use the **Closing and adjustment** form to run the **3. Close** procedure.

    This action adjusts the cost on the original sales line that was costed at -35.00 (5 pieces \* 7.00) to -30.00 (5 pieces \* 6.00). This is because the inventory model group uses First in, First out (FIFO), and 6.00 per piece is the FIFO cost from the first purchase order. Additionally, the action adjusts the cost on the return sales line to match the cost per piece on the original sales line. Therefore, the cost of the return line is adjusted from 35.00 to 30.00.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]