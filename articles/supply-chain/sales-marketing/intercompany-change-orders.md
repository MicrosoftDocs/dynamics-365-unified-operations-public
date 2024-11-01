---
title: Change intercompany orders
description: Learn about changing intercompany orders functionality, including outlines on adding new lines and changing prices and discounts.
author: adpattanaik
ms.author: adpattanaik
ms.topic: article
ms.date: 09/01/2021
ms.reviewer: kamaybac
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable
---

# Change intercompany orders

[!include [banner](../../includes/banner.md)]

If you change an intercompany sales order or purchase order, the corresponding sales order or purchase order in the corresponding company also reflects that change.

## Adding new lines

You can add new lines to an intercompany sales order and purchase order if the original sales order is part of the intercompany order chain. You can also add new lines if the original sales order is not a direct delivery. If the original sales order is a direct delivery, you can add new order lines to the intercompany sales order and purchase order only if the **Allow indirect creation** field is selected on the **Intercompany settings** FastTab on the original sales order.

## Changing prices and discounts

You can change the prices and discounts if the **Allow price edit** and **Allow discount edit** check boxes are selected on the **Intercompany** page.

If you change the unit price of one of the existing lines on the intercompany sales order line, the unit price on the intercompany purchase order is also changed.

If you change any of the discount fields on the intercompany sales order line, the relevant discount fields on the intercompany purchase order are updated.

## Changing and adding new charges

You can change charges if the **Allow price edit** and **Allow discount edit** check boxes are selected on the **Intercompany** page.

If you add a new charge to the intercompany sales order header and a new charge to the intercompany sales line, both charges are copied to the intercompany purchase order. Therefore, the intercompany sales order and the intercompany purchase order have the same total amount. The charges are never copied to the original sales order.

## Copying a fee

To copy a fee to the original sales order, create it as a new sales line that has an item of type **Service**.

## Changing quantities, and deleting intercompany purchases and sales order lines

You can change the quantity or delete an intercompany purchase order line or sales order line only if the line has been created directly from the **Sales order** or **Purchase order** form. This change makes either the intercompany purchase order or sales order or order lines the source.

## Origins of orders and order lines

Intercompany orders and order lines can have one of two origins:

- **Derived** – The order was created automatically from an intercompany order chain.
- **Source** – The order was created manually by a user.

The origin is indicated on the order header of intercompany purchase orders and sales orders in the **Origin** field. This field is located on the **Intercompany settings** FastTab on the sales order and on the **Setup** FastTab on the purchase order.

The **Derived** and **Source** origins apply only to intercompany orders. The **Origin** field is blank for all other sales orders, purchase orders, and order lines. This field is also blank on the original sales order.

## Example: Derived origin

You create an original sales order for an external customer. This sales order contains one order line. This original sales order creates an intercompany purchase order that contains one order line, which creates an intercompany sales order that contains one order line. The intercompany purchase order header and the order line are created automatically from the original sales order.

The value of the **Origin** field on the **Setup** FastTab of the intercompany purchase order and the **Intercompany settings** FastTab of the intercompany sales order headers is **Derived**. The value of the **Origin** field on the **Line details** tab of the purchase order and sales order lines is also **Derived**.

If an order line has an origin of **Derived**, you cannot delete the order line directly. You can delete the order line only from the source that created the order line. Also, you can change the ordered quantity only from the source that created the order line.

If an original sales order and original sales order line is part of the intercompany order chain, you can change ordered quantities from the original sales order, and you can delete order lines from the original sales order.

## Example: Source origin

You create a purchase order for an intercompany vendor. The intercompany purchase order and order line both have an origin of **Source**. Therefore, this intercompany purchase order is the controller, and the intercompany sales order that is created automatically in the vendor company has an origin of **Derived**.

Additionally, the ordered quantities of an order line that is created on the intercompany purchase order cannot be changed on the intercompany sales order. The order line can be deleted only from the intercompany purchase order. If a new line is added to the intercompany sales order, the intercompany sales order line then has an origin of **Source**.

When an original sales order is part of the intercompany order chain, you can always control the intercompany orders and intercompany order lines from the original sales order.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
