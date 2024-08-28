---
title: Create an item replacement order   
description: Learn how to create an item replacement order, including a step-by-step process for creating a replacement order after receiving a returned item.
author: Henrikan
ms.author: henrikan
ms.topic: article
ms.date: 05/01/2018
ms.custom:
ms.reviewer: kamaybac
ms.search.form: ReturnTableListPage, ReturnReplaceItem
---

# Create an item replacement order

[!include [banner](../includes/banner.md)]

Item replacement orders are usually created after a product is returned and inspected. However, when an item must be replaced before it has been returned, or when the original item won't be returned, you can create an item replacement order immediately after you create a return order.

## Create a replacement order after you receive an item that is returned

1. Go to **Sales and marketing** \> **Sales returns** \> **All return orders**.

1. Create a new return order, or select a returned order from the list to open the **Return order - RMA number: %1, %2** form.

1. Select **Return line**, and then select **Replacement item**.

1. Select the item to replace the returned item with. Enter the item specifications, and then select **Apply**.

1. Select **Packing slip** to generate the packing slip for the return order. A sales order is generated for the replacement item that you selected.

    After the sales order is created for the replacement item, sales agreements are automatically searched and if there's an applicable sales agreement, it's applied to the sales order.

## Create a replacement order before you receive an item that will be returned

1. Go to **Sales and marketing** \> **Sales returns** \> **All return orders**.

1. Create a new return order, or select a return order from the list to open the **Return order - RMA number: %1, %2** form.

1. Select **Find sales order** if you want to identify the sales order for the returned item. Complete the **Find sales order** form and then select **OK** to close the form and return to the **Return order - RMA number: %1, %2** form. The sales order line for the returned item is copied to the return order.

1. Select **Replacement order** to open the **Create sales order** form.

1. Select the **Copy return order lines** check box to transfer details from the return order you selected on the **Return order - RMA number: %1, %2** form to this sales order.

1. Enter or modify details, as required.

    If you identified the sales order in step 3, and if the sales order line for the returned item is linked to a sales agreement, the identifier of the applicable sales agreement for the item replacement order will be automatically displayed in the **Sales agreement ID** field.

1. Select **OK** to close the **Create sales order** form and open the **Sales order** form, where you can continue to enter information for the new sales order. Any applicable return order lines will be copied to the new sales order.

    If the identifier of the sales agreement is automatically displayed in the **Sales agreement ID** field, then the sales agreement has been linked to the sales order header for the item replacement order. If there's an applicable commitment in the sales agreement that hasn't been fulfilled yet, and the sales order is created before the sales agreement expires, a link is established between the sales agreement line and the sales order line. Therefore, information from the sales agreement, such as item price, is copied to the new sales order line.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]