---
title: Create a purchase order
description: Learn how to create a purchase order manually, including a step-by-step process for creating purchase order headers using the USMF demo data company. 
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: PurchTable, PurchTablePart, PurchCreateOrder, InventDimParmFixed, InventItemIdLookupPurchase, InventProductDimensionLookup, PurchTotals
ms.topic: how-to
ms.date: 06/10/2026
ms.custom:
  - bap-template
---

# Create a purchase order

[!include [banner](../../includes/banner.md)]

This article shows you how to create a purchase order manually. The system often creates purchase orders automatically as a result of master planning, direct delivery, and other processes. A purchasing agents also create purchase orders. This procedure includes sample values based on the USMF demo data company.

## Create the purchase order header

The purchase order header captures information that applies to the entire order, such as the vendor, delivery location, receipt date, and the person placing the order. Follow these steps to start a new purchase order and set the header values that will act as defaults for the order lines you add later.

1. Go to **Procurement and sourcing** \> **Purchase orders** \> **All purchase orders**.
1. Select **New**.
1. Select vendor account *US-101*. When you select a vendor, the system copies details from the vendor record, such as address, invoice account, delivery terms, and delivery mode, as default values into the order header. You can change these values at any time.  
1. Expand the **General** section.

    - The **Site** field together with the **Warehouse** field specifies where the procured goods or services must be delivered. The default delivery address is the site. You can populate both fields with values set up for the selected vendor, or you can specify them manually.  
    - Use the **Receipt date** field to specify when procured goods and services need to be delivered. You can specify a single receipt date for the order, or you can give the individual order lines unique receipt dates. If the receipt date you specify here can't be met for specific products or services because they have longer lead times, the system creates those lines with a later receipt date to accommodate for this.  

1. Expand the **Administration** section. Use the **Orderer** field to specify who is placing the order. This information might be convenient to share with the vendor in case they need to contact that person. The system might automatically assign the field a value if the current user account is associated with a name on the **Users** page.  
1. Select **OK**. The order header is created. When you work with purchase order lines, you see only a summary of the header information. If you need to view the rest of the information, select **Header**.  

## Add a purchase order line

Purchase order lines specify the individual products, services, or expense categories that you are buying, along with quantities, prices, discounts, and delivery details. Follow these steps to add a line to the order, choose the product dimensions that you want to track, and enter the pricing and quantity information that will be sent to the vendor.

1. Select **Purchase order line**.
1. Select **Dimensions**. Products can be in variants that are differentiated by dimensions, such as color, size, or style. You can also set up products to use storage dimensions, such as site and warehouse. There are also optional tracking dimensions, such as batch and serial numbers. To improve the efficiency of order entry, add the dimension fields that you commonly use directly to the order grid.  
1. Select the **Color** check box. If you select the **Save setup** option, the selected dimensions appear by default the next time you open the purchase order page.      
1. Select **OK**.
1. In the **Item number** field, select *T0004*.

    - Create order lines for products and services by specifying an item number. Create order lines for expenses by specifying a procurement category.
    - Use the **Procurement** category field for adding lines where procured items are expensed directly, rather than going into inventory. This means that if you need to expense a purchase, you can create a purchase order line that specifies a procurement category, rather than creating a line with an item number. You can also associate items with a procurement category. In this case, the procurement category is shown as informational only.  

1. In the **Color** field, enter or select a value. The **Site** and **Warehouse** fields typically populate with values from the order header, but you can override the fields if some lines need to be delivered to different locations.  
1. In the **Quantity** field, enter a number.

    - Select the quantity that you want to purchase. The **Quantity** field automatically populates with the minimum order quantity for the product if this is set up, or with the value of 1.  
    - The **Unit** field indicates the unit of measure for the ordered quantity. Typically, the unit is automatically provided from the purchasing unit on the product master data, but you can change this.  
    - The **Unit price** field typically contains a value from either a purchase agreement or a trade agreement. You can change the unit price on individual order lines, for example if a unique price is negotiated with the vendor.  
    - The **Discount** field represents a discount amount per unit. This discount therefore reduces the unit price by the discount. This discount is commonly supplied automatically from purchase agreements or trade agreements, but you can override on individual lines if unique discounts are negotiated with the vendor.  
    - Enter a discount percentage that reduces the net amount for the line accordingly. The discount percent is often supplied automatically from purchase agreements or trade agreements, but you can override on individual lines if a unique discount percentage is negotiated with the vendor.  
    - The value in the **Net Amount** field is calculated from other fields on the line including quantity, unit price, discount, and discount percent. You can change the net amount, but then the **Unit Price**, **Discount**, and **Discount percent** fields are blank. When you post toward the line, the amount posted is proportional to the net amount. Typically the **Net Amount** field is only used for displaying the net amount of the line.  

1. Expand the **Line details** section.
1. Select the **Delivery** tab. You can assign a unique receipt date to each order line. The date is inherited from the field on the purchase order header, but you can change this.  

## Review order totals

Before you submit a purchase order, it's a good idea to verify the totals so that you can confirm the overall cost, taxes, charges, and discounts that apply to the order. Follow these steps to open the totals dialog box and review the calculated amounts for the whole order.

1. Select **Totals**.

    - If you don't see the **Totals** action, select the **Purchase Order** tab on the Action Pane.  
    - This dialog box shows totals for the whole order.  
    - The **Selection** field allows you to change the basis of how totals are calculated. For example, you could choose **Product receipt quantity** to show totals that relate to the amount of the products that are received, or **Ordered quantity** to show the amount of product that you ordered.  

1. Select **OK**.

## Default financial dimensions for purchase orders created from purchase requisitions

When you create a purchase order from a purchase requisition, the system initializes financial dimensions on the purchase order based on the following rules:

- **Purchase order header dimensions** – The system always initializes the financial dimensions on the purchase order header based on the vendor setup. This setup includes dimensions such as *Business unit*, *Cost center*, and any other mandatory financial dimensions configured on the vendor.  
- **Purchase order line dimensions** – If you create the purchase order from a purchase requisition, the system copies line-level financial dimensions from the corresponding purchase requisition lines.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
