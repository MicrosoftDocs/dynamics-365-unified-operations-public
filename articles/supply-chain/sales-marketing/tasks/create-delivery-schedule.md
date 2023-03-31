--- 
# required metadata 
 
title: Create delivery schedule
description: This procedure demonstrates how to create a delivery schedule for a sales order. 
author: Henrikan
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable, SalesDeliverySchedule, SalesEditLines,  SrsReportViewerForm   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: henrikan
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create delivery schedule

[!include [banner](../../includes/banner.md)]

This procedure demonstrates how to create a delivery schedule for a sales order. A delivery schedule is used when a quantity on an order or a quotation is requested to be delivered in multiple shipments. You can run this procedure in demo data company USMF or on your own data.


## Create delivery schedule
1. Go to All sales orders.
2. Click New.
3. In the Customer account field, enter or select a value.
4. Click OK.
5. In the Item number field, enter or select a value.
6. In the Quantity field, enter a number that is bigger than 1.
7. Click Sales order line.
8. Click Delivery schedule.
    * The Delivery schedule page is the place where you can specify the number of shipments in which the total quantity of the order line will be delivered to the customer.    
    * By default, the system copies the total quantity and other delivery details of the original sales line into the first delivery schedule line. In this example, we'll create a schedule for two shipments, with the second shipment's date offset by a week from the first one.  
9. In the Quantity field, enter a number that is part of the total quantity.
10. Click New.
11. In the Quantity field, enter the remaining quantity.
12. In the Requested ship date field, enter a date a date that is one week ahead from the date of the first delivery line.
    * The two options on the Charges conversion FastTab control how you want the charges to be distributed across the delivery schedule lines, once they've been assigned to the original order line. If you select Copy gross amounts, the same charge amount is copied to each line. The Allocate to delivery lines option divides the charge equally across the delivery lines.  
    * Only fixed charges can be divided, whereas variable charges will still be copied to the lines.  
13. Move the cursor away from the second delivery line to update the page.
    * You can keep track of the total quantity that's allocated to the delivery schedule lines by looking at the Total and Remaining fields. When the remaining quantity is zero, the full quantity from the original line has been allocated to the schedule.   
14. Click OK.
    * The delivery schedule has now been copied to the order lines.   
    * The original order line, referred to as a Commercial line, has been converted to an Order line with multiple deliveries. It is marked with a distinct icon and acts as a header for the delivery lines.  
    * The two new lines, referred to as delivery lines, make up one delivery schedule. The order will be processed against these lines and not the original line. If documents such as confirmation slips, picking lists, packing slips, or invoices are printed, only the delivery lines are shown.   
    * The delivery lines can have different delivery dates, quantities, modes of delivery, and storage dimensions, such as site and warehouse. However, the product dimensions must always match the ones on the commercial line and can't be changed.  
15. In the Quantity field, enter a number that's bigger than the current one.
16. Select the commercial line to see the effect of the quantity recalculation.
17. On the Action Pane, click Pick and pack.
18. Click Post packing slip.
19. Expand the Parameters section.
20. In the Quantity field, select 'All'.
    * Note that the packing slip will be created for the two delivery schedule lines and not the original order line.  
21. Select Yes in the Print packing slip field.
22. Click OK.
23. Click Yes.
24. Close the page.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]