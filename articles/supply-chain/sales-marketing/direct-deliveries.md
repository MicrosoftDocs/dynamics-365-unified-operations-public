---
title: Direct deliveries
description: Learn about direct deliveries, which are deliveries that are sent directly from the vendor to your customer with outlines on delivery dates and order lines.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: PurchCreateFromSalesOrder, SalesTable
ms.topic: how-to
ms.date: 07/31/2024
ms.custom: 
  - bap-template
---

# Direct deliveries

[!include [banner](../includes/banner.md)]

This article provides information about direct deliveries. Direct deliveries are deliveries that are sent directly from the vendor to your customer.

Direct deliveries save delivery time and reduce the costs that are associated with carrying inventory, because you don't hold the products in your warehouse before you ship them to the customer.  

You can create direct deliveries from the **Sales order** page. First, create a sales order and order lines. Then, on the Action Pane, on the **Sales order** tab, select **Direct delivery**. Finally, specify the lines that must be handled as a direct delivery. A link is now created between the sales order lines for the direct delivery and the corresponding purchase order lines.  

> [!NOTE]
> If part of the ordered quantity has already been delivered, you must split the remaining quantity. Create a new line for the quantity that must be directly delivered, and subtract that quantity from the quantity on the original line. For example, if the original quantity was 15, and five have been delivered, you must create a new line for the remaining quantity, 10, and then reduce the original quantity by that amount.  

After you create the direct delivery link between the sales order lines and the purchase order lines, the sales order line packing slip is updated automatically through the purchase order line product receipt and can only be updated from the purchase order line product receipt update. Run either a product receipt update or an invoice update from the purchase order. If the invoice update is done on from the purchase order without a previous product receipt, then no automatic packing slip update happens for the sales order, however the sales order line is still updated to *delivered*. It's then possible to invoice-update the sales order, but don't do a packing slip update because this is triggered automatically. The invoice update for the sales order can be done from the **Sales order** page. An invoice update can't cause the quantity on the sales order to exceed the quantity that has been delivered. For example, a sales order line has ten pieces, but only five pieces from the sales order line have been updated to *delivered*. If you select *All* in the **Quantity** list when you invoice-update the sales order, only the quantities that have been delivered and not yet invoiced are invoice-updated.

## Delivery date

When you update the **Requested receipt date** field on the sales order line, the **Delivery date** field on the corresponding purchase order line is also updated. Similarly, when you update the **Confirmed** field on the purchase order line, the **Confirmed receipt date** and **Confirmed ship date** fields on the corresponding sales order line are also updated.

## Delivery address

Typically, the delivery address for a purchase order is the company's address. However, when you create a direct delivery, you enter the customer's address as the delivery address. If you change the delivery address on a purchase order line that has a delivery type of **Direct delivery**, the delivery address on the corresponding sales order line is also updated. Similarly, if you change the delivery address on the sales order line, the delivery address on the purchase order line is also updated.

## Deleting order lines

If you try to delete a sales order line that has a delivery type of **Direct delivery**, a message box states that purchase order lines are attached to the line. If the sales order line has been partially delivered, you can't delete the sales order line or the purchase order lines that are attached to it.

## Warehouse

When you create a direct delivery, the items that you sell never physically arrive at your warehouse. However, you must still specify a warehouse on the sales order line. Similarly, picking requirements might be specified on the item model group for the item. However, because the items never physically arrive at your warehouse, these requirements are ignored when the sales order is a direct delivery.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
