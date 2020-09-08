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
Only sales orders and return orders in the state 'Created' can be cancelled. 

## Getting the error 'Reservations cannot be removed because there is work created which relies on the reservations.' when trying to cancel a sales order.
If there is work associated to the sales order (even if the work is closed), it will not allow to cancel the sales order until the work is cancelled and reversed.

**Resolution**
1. Navigate to the load of the sales order and either use "Reduce picked quantity" options in the load line or "Reverse work" option in action pane of the load to cancel the work and put back inventory to desired location.
2. Once you have done the above step you can see the work will get a status of cancelled and an inventory movement work will be created and processed automatically to put back inventory to location described at the time of reversing.
3. Then delete the load which will delete the shipment as well.
4. It should then be possible to go to the sales order and cancel the sales order.


## Additional resources

[Get started with Sales Orders](get-started.md)

