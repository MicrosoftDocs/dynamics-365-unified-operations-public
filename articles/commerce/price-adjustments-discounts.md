---
# required metadata

title: Price adjustments and discounts
description: This article provides information about price adjustments and discounts in Dynamics 365 Commerce.
author: scott-tucker
ms.date: 11/16/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: RetailParameters, RetailPeriodicDiscount
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 15891
ms.assetid: bab5adf3-ddf0-4c22-a2eb-b4d25b88de99
ms.search.region: global
ms.search.industry: Retail
ms.author: scotttuc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update


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
> The Mix and Match discount and Threshold discount have a property named "Count non-discountable products" and "Count non-discountable products towards threshold" respectively. If this is turned ON, then an item which is not eligible for any discount (or any further discount) can still help in qualifying for the Mix and match or Threshold discount, but this item will not get the discount. For e.g. Assuming you create a Mix and match discount with two lines A and B such that the customer should get 10% off on both items. But there is already an Exclusive 5% discount applied on item A, which would ideally stop item A from participating in this Mix and match discount. But, if this is configuration is turned ON, then item A can be used to qualify for this Mix and Match discount, but the 10% discount will be applied only on item B. The similar logic is extended for the Threshold discount.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
