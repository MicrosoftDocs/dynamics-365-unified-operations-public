---
# required metadata

title: Direct deliveries
description: This article provides information about direct deliveries. Direct deliveries are deliveries that are sent directly from the vendor to your customer.
author: YuyuScheller
manager: AnnBe
ms.date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: PurchCreateFromSalesOrder, SalesTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: YuyuScheller
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 9704
ms.assetid: 64c51384-8a4e-45d0-83c1-12cea22902f9
ms.search.region: Global
# ms.search.industry: 
ms.author: omulvad
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Direct deliveries

This article provides information about direct deliveries. Direct deliveries are deliveries that are sent directly from the vendor to your customer.

Direct deliveries save delivery time and reduce the costs that are associated with carrying inventory, because you don't hold the products in your warehouse before you ship them to the customer.  

You can create direct deliveries from the **Sales order** page. First, create a sales order and order lines. Then, on the Action Pane, on the **Sales order** tab, select **Direct delivery**. Finally, specify the lines that must be handled as a direct delivery. A link is now created between the sales order lines for the direct delivery and the corresponding purchase order lines.  

**Note:** If part of the ordered quantity has already been delivered, you must split the remaining quantity. Create a new line for the quantity that must be directly delivered, and subtract that quantity from the quantity on the original line. For example, if the original quantity was 15, and five have been delivered, you must create a new line for the remaining quantity, 10, and then reduce the original quantity by that amount.  

After you create the direct delivery link between the sales order lines and the purchase order lines, you can update the sales order by using a packing slip. Run either a packing slip update or an invoice update from the purchase order. You must invoice-update the sales order from the **Sales order** page. An invoice update can't cause the quantity on the sales order to exceed the quantity that has been registered as received. For example, a sales order line has 10 pieces, but only five pieces from the sales order line have been updated by using a packing slip. If you select **All** in the **Quantity** list when you invoice-update the sales order, only those items that have been physically received, or updated by using a packing slip, are invoice-updated. The whole sales order line isn't updated.

## Delivery date
When you update the **Requested receipt date** field on the sales order line, the **Delivery date** field on the corresponding purchase order line is also updated. Similarly, when you update the **Confirmed** field on the purchase order line, the **Confirmed receipt date** and **Confirmed ship date** fields on the corresponding sales order line are also updated.

## Delivery address
Typically, the delivery address for a purchase order is the company's address. However, when you create a direct delivery, you enter the customer's address as the delivery address. If you change the delivery address on a purchase order line that has a delivery type of **Direct delivery**, the delivery address on the corresponding sales order line is also updated. Similarly, if you change the delivery address on the sales order line, the delivery address on the purchase order line is also updated.

## Deleting order lines
If you try to delete a sales order line that has a delivery type of **Direct delivery**, a message box states that purchase order lines are attached to the line. If the sales order line has been partially delivered, you can't delete the sales order line or the purchase order lines that are attached to it.

## Warehouse
When you create a direct delivery, the items that you sell never physically arrive at your warehouse. However, you must still specify a warehouse on the sales order line. Similarly, picking requirements might be specified on the item model group for the item. However, because the items never physically arrive at your warehouse, these requirements are ignored when the sales order is a direct delivery.

