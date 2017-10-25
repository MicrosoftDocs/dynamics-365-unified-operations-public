--- 
# required metadata 
 
title: Create sales orders
description: This procedure shows you how to create a sales order. 
author: omulvad
manager: AnnBe 
ms.date: 11/10/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: omulvad
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create sales orders

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows you how to create a sales order. You can use the procedure in demo data company USMF. Sales orders are typically created by a sales order processor. 




## Enter sales order header details
1. Go to Sales and marketing > Sales orders > All sales orders.
2. Click New.
3. In the Customer account field, click the drop-down button to open the lookup.
4. In the list, find and select the customer record.
    * For this example, select customer number US-004.  
5. In the list, click the link in the selected row.
6. Click OK.

## Enter sales order line details
    * The products sold by your organization may come in variants differentiated by dimensions, such as configuration, color, size, and style. Also, products may be set up to use storage dimensions, such as site, warehouse, and pallet, and racking dimensions, such as batch and serial numbers. When these dimensions are assigned, you must select the values for those dimensions on the order line. To improve order entry efficiency, you may want to add the respective dimension fields to the order grid.  
1. Click Sales order line.
2. Click Dimensions.
    * For this example, select the Color, Site and Warehouse dimensions. The dimensions you select here will appear in the sales order grid. If you want your selections to persist, set the Save setup option to Yes.   
3. Click OK.
4. In the Item number field, click the drop-down button to open the lookup.
5. For this example, select item number T0004.
6. In the list, click the link in the selected row.
    * If the item is part of a sales category, the item name will automatically appear in the Sales category field.  
    * If product dimension fields already contain a value, this is because the value was copied from the product record where it is defined as a default product dimension. You can change the default value at any time.   
7. In the Color field, click the drop-down button to open the lookup.
8. In the list, find and select the desired record.
9. In the list, click the link in the selected row.
10. In the Quantity field, enter a number.
    * If the item is sold in different units than when it’s purchased, produced, and stored, and a sales unit of measure is set on the product record, this value will be shown in the Unit field. You can change the value at any time.   
    * If the Site field already contains a value, the value was copied from the order header or from the order settings that are associated with the product. You can change the value at any time. If the field is empty, select a value.   
    * If the Unit price field already contains a value, the value was copied from a valid trade agreement, or from the product record. (The unit price can also originate from a sales agreement, but the process for creating sales orders from sales agreements is different to the one shown here.) If the field is empty, enter a value.   
    * The Discount field contains a discount amount per product unit. To calculate the total line discount amount, the discount value is multiplied by line quantity.    If the Discount field already contains a value, the value was copied from a valid trade agreement. If the field is empty, and you want to give the customer a line discount, enter a value.  
    * The Discount percent field contains a percentage value by which the total line gross amount is to be reduced.  If the Discount percent field already contains a value, it was copied from a valid trade agreement. If the field is empty, and you want to give the customer a line discount, enter a value.  
    * The Net amount field contains a value that is calculated based on the line's quantity and unit price adjusted by discounts.  You can override the calculated value to a different one.  

## Review the order totals
1. On the Action Pane, click Sales order.
2. Click Totals.
    * The Totals page displays details about the entire order. This includes the subtotal amount, which is a sum of all line net amounts adjusted for eventual line discounts, the total invoice amount, which is a subtotal amount adjusted for eventual order-level discount, charges, and sales tax, the customer credit limit situation, and more.  The invoice amount is the amount that will appear on the customer's invoice document.  
3. Click OK.

