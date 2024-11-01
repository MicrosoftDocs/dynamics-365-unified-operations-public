---
title: Create a purchase order from a sales order
description: Learn how to create a purchase order that is based on a sales order, including a step-by-step process for creating purchases orders from sales orders. 
author: adpattanaik
ms.author: adpattanaik
ms.reviewer: kamaybac
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable, PurchCreateFromSalesOrder, VendAccountItemLookup, SalesTableReferences, PurchTable, PurchTablePart
ms.topic: how-to
ms.date: 08/26/2024
ms.custom: 
  - bap-template
---

# Create a purchase order from a sales order

[!include [banner](../../includes/banner.md)]

This procedure shows you how to create a purchase order that is based on a sales order. The product's quantities on the purchase order are then designated to fulfill the demand of the originating sales order. Fulfilling sales demand this way is an alternative to a more comprehensive and optimized method of Distribution Requirements Planning. You can run this procedure in demo data company USMF or on your own data.

## Create a purchase order from a sales order

1. Go to **Sales and marketing > Sales orders > All sales orders**.
1. Select **New**.
1. In the **Customer account** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. Select **OK**.
1. In the **Item number** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record. If you're using USMF, you could select *D0001*.  
1. In the **Quantity** field, enter a number.
1. Select **Add line**.
1. In the **Item number** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record. If you're using USMF, you could select *T0020*.  
1. In the list, select the link in the selected row.
1. In the **Quantity** field, enter a number.
1. Select **Save**.
1. On the **Action Pane**, select **Sales order**.
1. Select **Purchase order**. The **Create purchase order** page lists all the open sales order lines that have been copied from the sales order. You can review the order details, and if necessary, you can modify selected details such purchase quantity and pricing terms, before you create the purchases.
1. Select the **Include all option**.
    - If you want to generate purchase orders for only a subset of the sales order lines, select these individually.  
    - The **Vendor account** field might or may might already be populated with a vendor number. If the default vendor is set up for the product (on the associated Item coverage), then this vendor will be copied  to the line. Otherwise, you must enter a vendor manually. In this article, regardless of whether the **Vendor account** field already contains a value or not, the following steps instruct you to select a new vendor that is different for each line.  
1. In the **Vendor account** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Select the second order line.
1. In the **Vendor account** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Select **Validate**.
1. Select **OK**. The message informs you that one or more purchase orders have been created. The system generates a separate purchase order for each vendor that you specified for the sales order lines. This means that if several sales order lines are to be supplied by the same vendor, a single purchase order with multiple lines will be generated.  

## Review purchase orders created from sales orders

1. On the **Action Pane**, select **General**.
1. Select **Related orders**. The **Related orders** page lists all the orders that were created from the sales order. In this example, there are two purchase orders generated for two different vendors respectively.
1. Select to follow the link in the **Purchase order** field. Each purchase order line is associated with the sales order line that led to the purchase. The relation to the sales order is indicated on the **Product tab** in the **Line details** FastTab, in the **Reference type**, **Reference number**, and **Reference lot** fields.  
1. Expand or collapse the **Line details** section.
1. Select the **Product** tab.
    - The **Reference lot** guarantees that the costs from the current purchase are charged on the attached sales order.  
    - You can navigate to the originating sales order by opening the link in the **Reference number** field.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
