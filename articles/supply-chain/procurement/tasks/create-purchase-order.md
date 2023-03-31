--- 
# required metadata 
 
title: Create a purchase order
description: This article shows you how to create a purchase order manually. 
author: GalynaFedorova
ms.date: 07/18/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: PurchTable, PurchTablePart, PurchCreateOrder, InventDimParmFixed, InventItemIdLookupPurchase, InventProductDimensionLookup, PurchTotals   
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
# Create a purchase order

[!include [banner](../../includes/banner.md)]

This article shows you how to create a purchase order manually. It's more typical for purchase orders to be created automatically as result of master planning, direct delivery, and other processes. Purchase orders are typically created by a purchasing agent. The example shown here can be used in the USMF demo data company using the values that are suggested in the notes for various steps.


## Create the purchase order header
1. Go to **Procurement and sourcing > Purchase orders > All purchase orders**.
2. Select **New**.
3. Select vendor account **US-101**. When you select a vendor, details from the vendor record such as address, invoice account, delivery terms, and delivery mode will be copied as default values into the order header. You can change these values at any time.  
4. Expand the **General** section.

    - The **Site** field together with the **Warehouse** field specifies where the procured goods or services must be delivered to. The default delivery address is the site. Both fields can be populated with values set up for the selected vendor, or you can specify them manually.  
    - The **Delivery date** field is used to specify when procured goods and services need to be delivered. You can specify a single delivery date for the order, or the individual order lines can be given unique delivery dates. If the delivery date specified here cannot be met for specific products or services because they have longer lead times, then those lines will be created with a later delivery date to accommodate for this.  

5. Expand the **Administration** section. The **Orderer** field can be used to specify who is placing the order. This may be convenient to share with the vendor in case they need to contact that person. The field may be assigned a value automatically if the current user account is associated with a name on the **Users** page.  
6. Select **OK**. The order header has now been created. When you work with purchase order lines, only a summary of the header information is shown. If you need to view the rest of the information, select **Header**.  

## Add a purchase order line
1. Select **Purchase order line**.
2. Select **Dimensions**. Products can be in variants that are differentiated by dimensions, such as color, size, or style. Products can also be set up to use storage dimensions, such as site and warehouse. There are also optional tracking dimensions, such as batch and serial numbers. To improve the efficiency of order entry, you can add the dimension fields that you commonly use directly to the order grid.  
3. Select the **Color** check box. Optional: If you select the **Save setup** field, the dimensions you have chosen will also be shown on the order line grid the next time you open the purchase order page.  
4. Select **OK**.
5. In the **Item number** field, select **T0004**.

    - Order lines are created for products and services by specifying an item number, or as expenses by specifying a procurement category. 
    - The **Procurement** category field is used for adding lines where procured items are expensed directly, rather than going into inventory. This means that if you need to expense a purchase you can do this by creating a purchase order line that specifies a procurement category, rather than creating a line with an item number. Items can also be associated with a procurement category and in this case, the procurement category is shown as informational only.  

6. In the **Color** field, enter or select a value. The **Site** and **Warehouse** fields are typically populated with values from the order header, but it is possible to override the fields if some lines need to be delivered to different locations.  
7. In the **Quantity** field, enter a number.

    - Select the quantity that you want to purchase. The **Quantity** field is automatically populated with the minimum order quantity for the product if this is set up, or with the value of 1.  
    - The **Unit** field indicates the unit of measure for the ordered quantity. Typically, the unit is automatically provided from the purchasing unit on the product master data, but you can change this.  
    - The **Unit price** field typically contains a value from either a purchase agreement or a trade agreement. It's possible to change the unit price on individual order lines, for example if a unique price is negotiated with the vendor.  
    - The **Discount** field represents a discount amount per unit. This discount therefore reduces the unit price by the discount. This discount is commonly supplied automatically from purchase agreements or trade agreements, but it is possible to override on individual lines if unique discounts have been negotiated with the vendor.  
    - A discount percentage can be entered that reduces the net amount for the line accordingly. The discount percent is often supplied automatically from purchase agreements or trade agreements, but it is possible to override on individual lines if a unique discount percentage has been negotiated with the vendor.  
    - The value in the **Net Amount** field is calculated from other fields on the line including quantity, unit price, discount, and discount percent. It's possible to change the Net amount, but then the **Unit Price**, **Discount**, and **Discount percent** fields will be blank and when you post toward the line, the amount posted will be proportional to the net amount. Typically the **Net Amount** field is only used for displaying the net amount of the line.  

8. Expand the **Line details** section.
9. Select the **Delivery** tab. A unique delivery date can be assigned to each order line. The date is inherited from the field on the purchase order header, but you can change this.  

## Review order totals
1. Select **Totals**.

    - If you don't see the **Totals** action, select the **Purchase Order** tab on the Action Pane.  
    - This dialog box shows totals for the whole order.  
    - The **Selection** field allows you to change the basis of how totals are calculated. For example, you could choose **Product receipt quantity** to show totals that relate to the amount of the product(s) that have been received, or **Ordered quantity** to show the amount of product that was ordered.  

2. Select **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]