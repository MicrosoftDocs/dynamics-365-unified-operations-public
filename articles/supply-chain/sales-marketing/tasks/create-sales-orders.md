--- 
# required metadata 
 
title: Create sales orders
description: This procedure shows you how to create a sales order. 
author: Henrikan
ms.date: 04/06/2022
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable, InventDimParmFixed, InventProductDimensionLookup, SalesTotals   
audience: Application User, SalesTableDelete, SalesTableListPagePreviewPage, SalesUpdateRemain
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
# Create sales orders

[!include [banner](../../includes/banner.md)]

This procedure shows you how to create a sales order. You can use the procedure in demo data company USMF. Sales orders are typically created by a sales order processor. 

## Enter sales order header details
1. Go to **Sales and marketing > Sales orders > All sales orders**.
2. Select **New**.
3. In the **Customer account** field, select the drop-down button to open the lookup.
4. In the list, find and select the customer record.
    - For this example, select customer number US-004.  
5. Select **OK**.

## Enter sales order line details
    
The products sold by your organization may come in variants differentiated by dimensions, such as configuration, color, size, and style. Also, products may be set up to use storage dimensions, such as site, warehouse, and pallet, and tracking dimensions, such as batch and serial numbers. When these dimensions are assigned, you must select the values for those dimensions on the order line. To improve order entry efficiency, you may want to add the respective dimension fields to the order grid.
    
1. Under the **Sales order lines** section, select the **Sales order line**.
2. Select **Dimensions**.
    
    For this example, select the Color, Site and Warehouse dimensions. The dimensions you select here will appear in the sales order grid. If you want your selections to persist, set the **Save setup** option to Yes.
    
3. Select **OK**.
4. In the **Item number** field, select the drop-down button to open the lookup.
5. For this example, select item number T0004.
    - If the item is part of a sales category, the item name will automatically appear in the Sales category field.  
    - If product dimension fields already contain a value, this is because the value was copied from the product record where it is defined as a default product dimension. You can change the default value at any time.   
6. In the **Color** field, select the drop-down button to open the lookup.
7. In the list, find and select the desired record.
8. In the **Quantity** field, enter a number.
    - If the item is sold in different units than when it's purchased, produced, and stored, and a sales unit of measure is set on the product record, this value will be shown in the **Unit** field. You can change the value at any time.   
    - If the **Site** field already contains a value, the value was copied from the order header or from the order settings that are associated with the product. You can change the value at any time. If the field is empty, select a value.   
    - If the **Unit price** field already contains a value, the value was copied from a valid trade agreement, or from the product record. (The unit price can also originate from a sales agreement, but the process for creating sales orders from sales agreements is different to the one shown here.) If the field is empty, enter a value.   
    - The **Discount** field contains a discount amount per product unit. To calculate the total line discount amount, the discount value is multiplied by line quantity. If the **Discount** field already contains a value, the value was copied from a valid trade agreement. If the field is empty, and you want to give the customer a line discount, enter a value.  
    - The **Discount percent** field contains a percentage value by which the total line gross amount is to be reduced.  If the **Discount percent** field already contains a value, it was copied from a valid trade agreement. If the field is empty, and you want to give the customer a line discount, enter a value. 
    - The **Net** amount field contains a value that is calculated based on the line's quantity and unit price adjusted by discounts.  You can override the calculated value to a different one.  

## Review the order totals
1. On the **Action Pane**, select **Sales order**.
2. Select **Totals**.
    
    The **Totals** page displays details about the entire order. This includes the subtotal amount, which is a sum of all line net amounts adjusted for eventual line discounts, the total invoice amount, which is a subtotal amount adjusted for eventual order-level discount, charges, and sales tax, the customer credit limit situation, and more. The invoice amount is the amount that will appear on the customer's invoice document.  
    
3. Select **OK**.

## Sales order creation performance enhancement
The new feature introduced with application 10.0.26 version reduces the extra record creation for tables **SourceDocumentHeader** and **SourceDocumentLine**. Performance is improved and storage size is reduced because these records aren't created. These underlying source document framework tables aren't used for sales orders in the product at this time and there are no scheduled plans to utilize them. Enabling this feature is considered a safe change for improved performance. 

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
