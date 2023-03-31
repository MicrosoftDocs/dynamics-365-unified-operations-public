--- 
# required metadata 
 
title: Create a purchase order from a sales order
description: This procedure shows you how to create a purchase order that is based on a sales order. 
author: Henrikan
ms.date: 06/26/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable, PurchCreateFromSalesOrder, VendAccountItemLookup, SalesTableReferences, PurchTable, PurchTablePart   
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
# Create a purchase order from a sales order

[!include [banner](../../includes/banner.md)]

This procedure shows you how to create a purchase order that is based on a sales order. The product's quantities on the purchase order are then designated to fulfill the demand of the originating sales order. Fulfilling sales demand this way is an alternative to a more comprehensive and optimized method of Distribution Requirements Planning. You can run this procedure in demo data company USMF or on your own data.


## Create a purchase order from a sales order
1. Go to **Sales and marketing > Sales orders > All sales orders**.
2. Click **New**.
3. In the **Customer account** field, click the drop-down button to open the lookup.
4. In the list, find and select the desired record.
5. Click **OK**.
6. In the **Item number** field, click the drop-down button to open the lookup.
7. In the list, find and select the desired record. If you're using USMF, you could select D0001.  
8. In the **Quantity** field, enter a number.
9. Click **Add line**.
10. In the **Item number** field, click the drop-down button to open the lookup.
11. In the list, find and select the desired record. If you're using USMF, you could select T0020.  
12. In the list, click the link in the selected row.
13. In the **Quantity** field, enter a number.
14. Click **Save**.
15. On the **Action Pane**, click **Sales order**.
16. Click **Purchase order**. The **Create purchase order** page lists all the open sales order lines which have been copied from the sales order. You can review the order details, and if required, you can modify selected details such purchase quantity and pricing terms, before you create the purchases. 
17. Select the **Include all option**.
    - If you want to generate purchase orders for only a subset of the sales order lines, select these individually.  
    - The **Vendor account** field may or may not already be populated with a vendor number. If the default vendor is set up for the product (on the associated Item coverage) then this vendor will be copied  to the line. Otherwise, you must enter a vendor manually.  In this guide, regardless of whether the **Vendor account** field already contains a value or not, the following steps instruct you to select a new vendor which is different for each line.  
18. In the **Vendor account** field, click the drop-down button to open the lookup.
19. In the list, find and select the desired record.
20. In the list, click the link in the selected row.
21. Select the second order line.
22. In the **Vendor account** field, click the drop-down button to open the lookup.
23. In the list, find and select the desired record.
24. In the list, click the link in the selected row.
25. Click **Validate**.
26. Click **OK**. The message informs you that one or more purchase orders have been created. The system generates a separate purchase order for each vendor that you specified for the sales order lines. This means that if several sales order lines are to be supplied by the same vendor, a single purchase order with multiple lines will be generated.  

## Review purchase orders created from sales orders
1. On the **Action Pane**, click **General**.
2. Click **Related orders**. The **Related orders** page lists all the orders that were created from the sales order. In this example, there are two purchase orders generated for two different vendors respectively. 
3. Click to follow the link in the **Purchase order** field. Each purchase order line is associated with the sales order line that led to the purchase. The relation to the sales order is indicated on the **Product tab** in the **Line details** Fasttab, in the **Reference type**, **Reference number**, and **Reference lot** fields.  
4. Expand or collapse the **Line details** section.
5. Click the **Product** tab.
    - The **Reference lot** guarantees that the costs from the current purchase are charged on the attached sales order.  
    - You can navigate to the originating sales order by opening the link in the **Reference number** field.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]