---
title: Price adjustments and discounts
description: Learn about price adjustments and discounts in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 01/27/2026
ms.topic: overview
ms.reviewer: v-griffinc
ms.search.region: global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.assetid: bab5adf3-ddf0-4c22-a2eb-b4d25b88de99
ms.search.form: RetailParameters, RetailPeriodicDiscount
ms.custom: 
  - bap-template
---

# Price adjustments and discounts

[!include [banner](includes/banner.md)]

This article provides information about price adjustments and discounts in Dynamics 365 Commerce.

In Commerce, you can make price adjustments to products, and you can also set up discounts that apply to a line item or a transaction at the point of sale (POS), in a call center sales order, or in an online order. You can link both price adjustments and discounts to price groups. For both price adjustments and discounts, you can specify a single start date and end date or a recurring period, a discount code, and a few other attributes. 

You can apply price adjustments and discounts to products, variants, or categories. If more than one discount applies to a product, a customer might receive either one of the discounts or a combined discount, depending on the configuration of the discount. Commerce automatically applies the discount or combination of discounts that gives the best price to the customer. When you set up a price adjustment or a discount, confirm that you assign price groups to the correct channels, catalogs, affiliations, or loyalty programs that you want the discount to apply to. If you want to automatically generate the discount ID, set up number sequences on the **Commerce parameters** page before you define a new price adjustment or discount.

> [!NOTE]
> You can delete a price adjustment or a discount. However, statistical information is lost.

## Types of discounts

You can use many types of discounts:

- **Simple discount** – A single percentage or amount.
- **Quantity discount** – A discount that you apply when two or more products are purchased.
- **Mix and match discount** – A discount that you apply when a specific combination of products is purchased.
- **Threshold discount** – A discount that you apply when the transaction total is more than a specified amount.
- **Tender-based discount** – A discount that you apply when the transaction total is more than a specified amount and a specific payment type (for example, cash, credit, or debit card) is used for payment.
- **Shipping discount** – A discount that you apply when the transaction total is more than a specified amount and a specific mode of delivery (for example, two day shipping or overnight shipping) is used on the order.

You can associate both price adjustments and discounts with price groups. Then, you can associate price groups with channels, catalogs, affiliations, and loyalty programs.

> [!NOTE]
> The mix and match discount and the threshold discount have properties named **Count non-discountable products** and **Count non-discountable products towards threshold**, respectively. If you enable these properties, an item that isn't eligible for any discount can still help qualify a transaction for the discount, but the ineligible item doesn't get the discount.  
> 
> For example, if you create a mix and match discount with two lines, A and B, where a customer gets 10% off on both items, but item A has the configuration "Prevent all discounts" checked, then this configuration typically stops item A from being included in the discount. However, if you enable the **Count non-discountable products** property, item A can be used to qualify for the mix and match discount, but the 10% discount applies only to item B. Similar logic applies to the threshold discount.  
>
> However, the **Count non-discountable products towards threshold** property has an additional capability when compared to the "Count nondiscountable products" property of the mix and match discounts. If you enable the threshold discount, and if there's an item that has an existing discount that prevents the item from any other discounts, the price paid for this item qualifies towards meeting the threshold, but this item doesn't get the additional discount.

## Best practices

Follow these best practices when you create price adjustments and discounts.

### Mix and match discounts

To achieve optimal pricing calculation performance, don't configure mix and match discount line groups with a *number of products needed* that exceeds 20. Use a different unit to reduce the quantity. For example, if you're setting a mix and match discount for 200 *capsules* of coffee, use *pack* or *sleeve* as the unit of measure instead.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
