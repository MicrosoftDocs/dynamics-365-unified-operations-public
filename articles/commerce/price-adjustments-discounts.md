---
title: Price adjustments and discounts
description: This article provides information about price adjustments and discounts in Dynamics 365 Commerce.
author: josaw1
ms.date: 06/11/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: josaw
ms.search.region: global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update
ms.assetid: bab5adf3-ddf0-4c22-a2eb-b4d25b88de99
ms.search.industry: Retail
ms.search.form: RetailParameters, RetailPeriodicDiscount
---

# Price adjustments and discounts

[!include [banner](includes/banner.md)]

This article provides information about price adjustments and discounts in Dynamics 365 Commerce.

In Commerce, you can make price adjustments to products, and can also set up discounts that are applied to a line item or a transaction at the point of sale (POS), in a call center sales order, or in an online order. Both price adjustments and discounts can be linked to price groups. For both price adjustments and discounts, you can specify a single start date and end date or a reoccurring period, a discount code, and a few additional attributes. 

Price adjustments and discounts can be applied to products, variants, or categories. If more than one discount applies to a product, a customer might receive either one of the discounts or a combined discount, depending on the configuration of the discount. Commerce automatically applies the discount or combination of discounts that gives the best price to the customer. When you set up a price adjustment or a discount, be sure to confirm that price groups are assigned to the correct channels, catalogs, affiliations, or loyalty programs that you want the discount to apply to. Additionally, if you want to automatically generate the discount ID, set up number sequences on the **Commerce parameters** page before you define a new price adjustment or discount.

> [!NOTE]
> You can delete a price adjustment or a discount. However, statistical information will be lost.

## Types of discounts

There are many types of discounts:

- **Simple discount** – A single percentage or amount.
- **Quantity discount** – A discount that is applied when two or more products are purchased.
- **Mix and match discount** – A discount that is applied when a specific combination of products is purchased.
- **Threshold discount** – A discount that is applied when the transaction total is more than a specified amount.
- **Tender-based discount** – A discount that is applied when the transaction total is more than a specified amount and a specific payment type (for example, cash, credit, or debit card) is used for payment.
- **Shipping discount** – A discount that is applied when the transaction total is more than a specified amount and a specific mode of delivery (for example, two day shipping or overnight shipping) is used on the order.

Both price adjustments and discounts can be associated with price groups. Price groups can then be associated with channels, catalogs, affiliations, and loyalty programs.

> [!NOTE]
> The mix and match discount and the threshold discount have properties named "Count non-discountable products" and "Count non-discountable products towards threshold", respectively. If these properties are enabled, an item that is not eligible for any discount can still help qualify a transaction for the discount, but the ineligible item will not get the discount. 
> 
> For example, if you create a mix and match discount with two lines, A and B, where a customer should get 10% off on both items, but item A has the configuration "Prevent all discounts" checked, then this would typically stop item A from being included in the discount. However, if the "Count non-discountable products" property is enabled, then item A can be used to qualify for the mix and match discount, but the 10% discount will only be applied to item B. Similar logic applies to the threshold discount. 
>
> However, the property "Count non-discountable products towards threshold" has an additional capability when compared to the "Count non-discountable products" property of the mix and match discounts. If the threshold discount is enabled, and if there is an item that has an existing discount which would prevent the item from any other discounts, then  the price paid for this item would qualify towards meeting the threshold, but this item will not get the additional discount.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
