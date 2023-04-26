--- 
# required metadata 
 
title: Create a purchase order with a delivery schedule
description: This article demonstrates how to create a delivery schedule for a purchase order. 
author: GalynaFedorova
ms.date: 08/01/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: PurchTable, PurchTablePart, PurchCreateOrder, InventItemIdLookupPurchase, PurchDeliverySchedule, PurchEditLines   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: gfedorova
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a purchase order with a delivery schedule

[!include [banner](../../includes/banner.md)]

This article demonstrates how to create a delivery schedule for a purchase order. A delivery schedule is used when a quantity on an order or a journal is requested to be delivered in multiple shipments. The example shown in this guide can be used in the USMF demo data company. This procedure would typically be done by a purchasing agent.

## Create a delivery schedule
1. Go to **Procurement and sourcing > Purchase orders > All purchase orders**.
2. On the Action Pane, select **New**.
3. In the **Vendor account** field, enter `US-101`.
4. Select **OK**.
5. In the **Item number** field, enter `M0001`.
6. In the **Quantity** field, enter `10`.
7. Select **Purchase order line**.
8. Select **Delivery schedule**.
- The **Delivery schedule** page allows you to specify the number of shipments in which the total quantity of the order line will be delivered from the vendor.  
- By default, the system copies the total quantity and other delivery details of the original purchase line into the first delivery schedule line. In this example, we'll create a schedule for two shipments, with the second shipment's date offset by a week from the first shipment.  
9. In the **Quantity** field, change the quantity to `4`.
10. Select **New**.
11. In the **Quantity** field, enter `6` as the remaining quantity.
- In the delivery date field, select a date that's one week after the date on the first delivery line.  
- You can keep track of the total quantity that's allocated to the delivery schedule lines by looking at the **Total** and **Remaining** fields. When the remaining quantity is zero, the full quantity from the original line has been allocated to the schedule.  
12. Expand the **Charges conversion** section.
- The options here allow you to control how you want charges to be distributed across the delivery schedule lines. If you select **Copy gross amounts**, the charge amount on the original order line is copied to each delivery line. The **Allocate to delivery lines** option divides the original line charge according to the quantity on each delivery line.  
13. Collapse the **Charges conversion** section.
14. Select **OK**.
- The delivery schedule has now been applied to the order.  
- The original order line, now referred to as a Commercial line, has been converted to an Order line with multiple deliveries. It is marked with a distinct icon and acts as a header for the delivery lines.  
15. Select the second order line, which is the first of the two delivery lines.
- The two new lines, referred to as Delivery lines, make up one delivery schedule. The order will be processed against these lines and not the original line. If documents such as confirmations, product receipt journals, or invoices are printed, only the delivery lines are shown.  

## Change the delivery schedule
You can change the quantity on delivery lines. If you do this, the commercial line is automatically updated to the total quantity in the delivery lines.  
1. In the **Quantity** field of the first delivery line, change the quantity from `4` to `5`.
2. Select the first order line (the commercial line).  
- The quantity on the commercial line has been changed to 11.  

## Process product receipt using delivery schedules
The purchase order must be confirmed before the product receipt can be processed. In this example, receipt is recorded directly on the purchase order. The receipt could also have been recorded when the goods arrived in the warehouse.  
1. On the Action Pane, select **Purchase**.
2. Select **Confirm**.
3. On the Action Pane, select **Receive**.
4. Select **Product receipt**. In the **Product receipt** field, type any value.
- This field is used to enter a reference that will be used as voucher for the product receipt journal.  
- In the **Quantity** field, select **Ordered quantity**. This option means that the receipt will process for the quantity that the order lines were created with.  
- Make sure that the **Print product receipt** field is set to **No**. Printing isn't needed in this example.  
5. Expand the **Lines** section.
- Notice how the product receipt is created for the two delivery lines and not the original order line. If the receipt had been recorded in the warehouse, it would also have been recorded on the delivery schedule lines.  
6. Collapse the **Lines** section.
7. Select **OK** to post the receipt.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]