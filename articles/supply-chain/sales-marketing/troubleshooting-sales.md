---
# required metadata

title: Troubleshoot Sales orders
description: This topic describes how to fix issues that you might encounter while working with Sales Orders.
author: SmithaNataraj
manager: tfehr
ms.date: 05/07/2020
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
ms.search.validFrom: 2020-5-7
ms.dyn365.ops.version: AX 10.0.14

---
# Troubleshoot Sales Orders 

This topic describes how to fix common issues that you might encounter while working with Sales Orders.

##  Changing the location in a sales order header does not update the tax information 
If site or warehouse or delivery address is being changed on a sales order header or at the line level, the case tax information is not getting updated for the lines automatically.
		
**Resolution/Fix**
That's because the delivery address, site and warehouse doesn't automatically get changed at the line level either - you'll need to update that yourself

##  When there are two trade agreements for the same/overlapping period, then the same agreement line is always picked.
If there are two trade agreements defined for the same/overlapping period, then when creating sales order lines with those items, the same trade agreement seems to be picked each time.
		
**Resolution/Fix**
When there is more than one trade agreement for a given date, then the trade agreement with the lowest price will always be picked up. Read more on trade agreements [here] (https://www.axug.com/HigherLogic/System/DownloadDocumentFile.ashx?DocumentFileKey=3396a3a8-1f48-4d85-8cd6-5fa982f62e90).

## Is it possible to link a Purchase order to a Sales Order to fulfil demand? 
A purchase order can be created from a sales order. For more details see [Create a purchase order from a sales order](https://docs.microsoft.com/en-us/dynamics365/supply-chain/sales-marketing/tasks/create-purchase-order-sales-order).

## Unable to cancel or delete a return order or a sales order
Only sales orders and return orders in the state 'Created' can be cancelled. See more [Cancel a return order](https://docs.microsoft.com/en-us/dynamics365/supply-chain/service-management/cancel-return-order)

## Getting the error 'Reservations cannot be removed because there is work created which relies on the reservations.' when trying to cancel a sales order.
If there is work associated to the sales order (even if the work is closed), it will not allow to cancel the sales order until the work is cancelled and reversed.

**Resolution**
1. Navigate to the load of the sales order and either use "Reduce picked quantity" options in the load line or "Reverse work" option in action pane of the load to cancel the work and put back inventory to desired location.
2. Once you have done the above step you can see the work will get a status of cancelled and an inventory movement work will be created and processed automatically to put back inventory to location described at the time of reversing.
3. Then delete the load which will delete the shipment as well.
4. It should then be possible to go to the sales order and cancel the sales order.

## It is not possible to cancel an intercompany PO that is linked to a sales order. Error message: Quantity cannot be reduced because the remaining update quantity changes sign
This issue has been fixed in 10.0.13. It is possible to cancel an intercompany PO that is linked to a sales order from 10.0.13.

## Is it possible to restore an invoiced sales order that was deleted?
An invoiced sales order was deleted by mistake. Is there a way to restore this or see the deleted sales order details?

**Resolution**
If the deleted Sales Order has already been invoiced, it can be found via:  Customer Account > Transactions > Original document > View details. On this screen, find the corresponding invoice you are looking for and click on the invoice to see the actual invoice details along with the sales order reference. You should be able to access the sales order details as well from here.

## Deadline of SO header cannot be found in the data entity "SalesOrderHeaderV2Entity"

This field does not exist on the SalesOrderHeaderV2Entity.

## Need to delete orphaned sales order records
If the system ended up with orphaned sales order records and those need to be cleaned up, use the 'Sales Order Deletion Periodic Jobs' to achieve that. It can be accessed from  Sales and marketing > Periodic > Clean Up Or Retail and commerce > Retail and commerce IT > Clean Up

## Is there a way of calculating commissions on already posted invoices?
If commissions need to be calculated for posted invoices, that is not supported currently. 

##  Bundle Item is not supported within Intercompany Process
**Scenario**
Variant 1:
1. Create a sales order in the legal entity of the subsidiary and add an item marked as bundle=yes
2. Create Sales order confirmation (Sell > Generate > Confirm sales order)
3. With confirmation the bundle is exploded on the sales order
4. Go to menu Sales order > Purchase order: it is not possible to select the bundle item. Only the components are visible

Variant 2:
1. Create a sales order in the legal entity of the subsidiary and add an item marked as bundle=yes
2. Go to menu Sales order > Purchase order and create a purchase order by using the vendor of the main company (IC settings should be available) - with confirmation IC purchase order and IC sales order are created
3. Go to IC sales order (Manage > Intercompany tracing > Intercompany sales order)
4. Create Sales order confirmation (Sell > Generate > Confirm sales order)
5. With confirmation the bundle is exploded on the IC sales order; IC purchase order and Original sales order is updated as well. But in the original sales order the bundle functionality is not considered.

**Resolution**
Bundle item is not available for the purchase order, because if you check the sales order lines for the bundle item, the quantity will be 0 and status = Cancelled. This is by design. The sales order is not buying the Bundle item but only its components. If you need to buy a bundle, consider whether you need to mark it as Bundle item, as it is designed for Revenue recognition scenarios. For details on bundle items, see (here)[https://docs.microsoft.com/en-us/dynamics365/finance/accounts-receivable/revenue-recognition-setup#bundles].

## Additional resources

[Get started with Sales Orders](get-started.md)

