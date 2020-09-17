---
# required metadata

title: Troubleshoot sales orders
description: This topic describes how to fix issues that you might encounter while working with sales orders.
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

This topic describes how to fix common issues that you might encounter while working with sales orders.

## Changing the location in a sales order header doesn't update the tax information

### Issue description

If the site, warehouse, or delivery address is changed on a sales order header or at the line level, the case tax information isn't updated for the lines automatically.

### Issue resolution

This is by design. The issue occurs because the delivery address, site, and warehouse aren't automatically changed at the line level either. You must to update them manually.

## When there are two trade agreements for the same or overlapping period, the same agreement line is always picked

### Issue description

If there are two trade agreements defined for the same/overlapping period, then when creating sales order lines with those items, the same trade agreement seems to be picked each time.

### Issue resolution

When there is more than one trade agreement for a given date, then the trade agreement with the lowest price will always be selected. For more information, download this white paper: [Trade agreements in Microsoft Dynamics AX 2012](https://www.axug.com/HigherLogic/System/DownloadDocumentFile.ashx?DocumentFileKey=3396a3a8-1f48-4d85-8cd6-5fa982f62e90).

## Is it possible to link a purchase order to a sales order to fulfil demand?

You can create purchase order from a sales order. For more information, see [Create a purchase order from a sales order](tasks/create-purchase-order-sales-order.md).

## Unable to cancel or delete a return order or a sales order

You can only cancel sales orders and return orders that are in the *Created* state. For more information, see [Cancel a return order](../service-management/cancel-return-order.md).

## The error "Reservations cannot be removed because there is work created which relies on the reservations" is shown when trying to cancel a sales order

If there is work associated to the sales order (even if the work is closed), you won't be able to cancel the sales order until the work is cancelled and reversed.

To solve this issue:

1. Go to the relevant load of the sales order and select either the **Reduce picked quantity** option on the load line or the **Reverse work** option on the Action Pane to cancel the work and put inventory back to desired location.
2. The work now has a status of *Cancelled* and new inventory movement work to put inventory back to location described at the time of reversing is created and processed automatically.
3. Delete the load, which will also delete the shipment.
4. It should now be possible to go to the sales order and cancel it.

## It isn't possible to cancel an intercompany purchase order that is linked to a sales order

### Issue description

If you try to cancel an intercompany purchase order that is linked to a sales order, you might see the error message "Quantity cannot be reduced because the remaining update quantity changes sign".

### Issue resolution

This issue was fixed in Supply Chain Management 10.0.13. Starting with that version, it is now possible to cancel an intercompany purchase order that is linked to a sales order.

## Is it possible to restore an invoiced sales order that was deleted?

### Issue description

An invoiced sales order was deleted by mistake. Is there a way to restore this or see the deleted sales order details?

### Issue resolution

If the deleted sales order has already been invoiced, you can find it by going to **Customer Account > Transactions > Original document > View details**. On this page, find the invoice you are looking for and select it to see the its details, including the sales order reference. You should also be able to access the sales order details from here.

## Deadline of sales order header can't be found in the data entity "SalesOrderHeaderV2Entity"

This field doesn't exist on the `SalesOrderHeaderV2Entity` entity.

## I need to delete orphaned sales order records

To clean up orphaned sales order records, run the *Sales order deletion periodic job*, which is available by going to either of the following:

- **Sales and marketing > Periodic tasks > Clean up > Delete sales orders**
- **Retail and commerce > Retail and commerce IT > Clean up > Delete sales orders**

## Is there a way of calculating commissions on already posted invoices?

Supply Chain Management does not currently support the calculation of commissions for posted invoices.

## Bundle item is not supported within intercompany process

### Reproduce the issue, scenario 1

One way to reproduce this issue is do the following:

1. Create a sales order in the legal entity of the subsidiary and add an item with **Bundle** set to *Yes*.
1. Confirm the sales order (**Sell > Generate > Confirm sales order**). On confirmation, the bundle is exploded on the sales order.
1. Go to **Sales order > Purchase order**.
1. Note that it isn't possible to select the bundle item. Only the components are visible.

### Reproduce the issue, scenario 2

Another way to reproduce this issue is do the following:

1. Create a sales order in the legal entity of the subsidiary and add an item with **Bundle** set to *Yes*.
2. Go to **Sales order > Purchase order** and create a purchase order by using the vendor of the main company (intercompany settings should be available). On confirmation, an intercompany purchase order and intercompany sales order are created.
3. Go to the intercompany sales order (**Manage > Intercompany tracing > Intercompany sales order**).
4. Confirm the sales order (**Sell > Generate > Confirm sales order**).
5. With confirmation, the bundle is exploded on the intercompany sales order, The intercompany purchase order and the original sales order are also updated, but in the original sales order, the bundle functionality isn't considered.

### Issue resolution

The bundle item is not available for the purchase order because if you check the sales order lines for the bundle item, the quantity will be 0 and status will be *Cancelled*. This is by design. The sales order is not buying the bundle item but only its components. If you need to buy a bundle, consider whether you need to mark it as bundle item because this functionality is actually designed for revenue recognition scenarios. For details on bundle items, see [Bundles](../../finance/accounts-receivable/revenue-recognition-setup.md#bundles)

## Additional resources

[Get started with sales orders](get-started.md)
