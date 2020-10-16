---
# required metadata

title: Troubleshoot sales orders
description: This topic describes how to fix issues that you might encounter while you work with sales orders.
author: SmithaNataraj
manager: tfehr
ms.date: 09/16/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: SalesTable, SalesTableListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: smnatara
ms.search.validFrom: 2020-9-16
ms.dyn365.ops.version: Release 10.0.14

---
# Troubleshoot sales orders

This topic describes how to fix issues that you might encounter while you work with sales orders.

## The tax information isn't updated if I change the location on a sales order header.

### Issue description

If the site, warehouse, or delivery address is changed either on a sales order header or at the line level, the case tax information isn't automatically updated for the lines.

### Issue resolution

This behavior is by design. The issue occurs because the delivery address, site, and warehouse aren't automatically changed at the line level either. You must update them manually.

## If there are two trade agreements for the same period or overlapping periods, the same agreement line is always selected.

### Issue description

If two trade agreements are defined for the same period or overlapping periods, the same trade agreement seems to be selected every time when you create sales order lines that contain those items.

### Issue resolution

If there is more than one trade agreement for a given date, the trade agreement that has the lowest price is always selected. For more information, download the following white paper: [Trade agreements in Microsoft Dynamics AX 2012](https://www.axug.com/HigherLogic/System/DownloadDocumentFile.ashx?DocumentFileKey=3396a3a8-1f48-4d85-8cd6-5fa982f62e90).

## Can I link a purchase order to a sales order to fulfill demand?

You can create a purchase order from a sales order. For more information, see [Create a purchase order from a sales order](tasks/create-purchase-order-sales-order.md).

## I can't cancel or delete a return order or a sales order.

You can cancel only sales orders and return orders that are in a *Created* state. For more information, see [Cancel a return order](../service-management/cancel-return-order.md).

## When I try to cancel a sales order, I receive a "Reservations cannot be removed because there is work created which relies on the reservations" error.

If work is associated with a sales order, you can't cancel the sales order until the work is canceled and reversed. This requirement applies even if the work that is associated with the sales order is closed.

To fix this issue, follow these steps.

1. Cancel the work, and put inventory back into the desired location. Go to the relevant load of the sales order, and select either **Reduce picked quantity** on the load line or **Reverse work** on the Action Pane.

    The work now has a status of *Canceled*, and new inventory movement work is automatically created and processed to put inventory back into the location that was described at the time of reversal.

2. Delete the load. The shipment is also deleted.
3. You should now be able to go to the sales order and cancel it.

## I can't cancel an intercompany purchase order that is linked to a sales order.

### Issue description

If you try to cancel an intercompany purchase order that is linked to a sales order, you might receive the following error message: "Quantity cannot be reduced because the remaining update quantity changes sign."

### Issue resolution

This issue was fixed in Microsoft Dynamics 365 Supply Chain Management version 10.0.13. In that version and later versions, you can now cancel an intercompany purchase order that is linked to a sales order.

## Can I restore an invoiced sales order that was deleted?

### Issue description

An invoiced sales order was deleted by mistake, and you want to restore it or view its details.

### Issue resolution

If the deleted sales order has already been invoiced, go to **Customer account \> Transactions \> Original document \> View details**. Find the invoice that you're looking for, and select it to view its details. These details include the sales order reference. You should also be able to access the sales order details from that page.

## The deadline of a sales order header can't be found in the SalesOrderHeaderV2Entity data entity.

The deadline field doesn't exist on the *SalesOrderHeaderV2Entity* entity.

## I must delete orphaned sales order records.

To clean up orphaned sales order records, run the *Sales order deletion* periodic job by going to either of the following places:

- Sales and marketing \> Periodic tasks \> Clean up \> Delete sales orders
- Retail and commerce \> Retail and commerce IT \> Clean up \> Delete sales orders

## Is there a way to calculate commissions on invoices that have already been posted?

Supply Chain Management doesn't currently support the calculation of commissions for posted invoices.

## A bundle item isn't supported in an intercompany process.

### Reproduce the issue – Scenario 1

The following procedure shows one way to reproduce the issue.

1. In the legal entity of the subsidiary, create a sales order, and add an item where the **Bundle** option is set to *Yes*.
1. Go to **Sell \> Generate \> Confirm sales order** to confirm the sales order.

    After confirmation, the bundle is exploded on the sales order.

1. Go to **Sales order \> Purchase order**.
1. Notice that you can't select the bundle item. Only the components are visible.

### Reproduce the issue – Scenario 2

The following procedure shows another way to reproduce the issue.

1. In the legal entity of the subsidiary, create a sales order, and add an item where the **Bundle** option is set to *Yes*.
2. Go to **Sales order \> Purchase order**, and create a purchase order by using the vendor of the main company. (Intercompany settings should be available.) 

    After confirmation, an intercompany purchase order and an intercompany sales order are created.

3. Go to **Manage \> Intercompany tracing \> Intercompany sales order** to go to the intercompany sales order.
4. Go to **Sell \> Generate \> Confirm sales order** to confirm the sales order.

    After confirmation, the bundle is exploded on the intercompany sales order. The intercompany purchase order and the original sales order are also updated. However, the bundle functionality isn't considered on the original sales order.

### Issue resolution

The bundle item isn't available for the purchase order because, if you examine the sales order lines for the bundle item, you will notice that the quantity is *0* (zero) and the status is *Cancelled*. This behavior is by design. The sales order buys only the components of the bundle item. It doesn't buy the bundle item itself.

If you must buy a bundle, consider whether you have to mark it as bundle item, because this functionality is actually designed for revenue recognition scenarios. For more information about bundle items, see [Bundles](../../finance/accounts-receivable/revenue-recognition-setup.md#bundles).
