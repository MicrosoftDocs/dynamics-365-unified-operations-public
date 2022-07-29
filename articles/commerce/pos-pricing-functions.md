---
# required metadata

title: Pricing functions in POS 
description: This article explains various price and discount functions in Commerce point of sale application.
author: boycez
ms.date: 07/14/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail, Commerce
ms.author: boycez
ms.search.validFrom: 2022-07-14
ms.dyn365.ops.version: Application update 10.0.29

---

# Pricing functions in POS

[!include [banner](includes/banner.md)]

## Overview

Dynamics 365 Commerce point of sale (POS) application provides rich capabilities for first-line workers to perform store commerce operations. The following price and discount functions are currently available in the application.

| Function                       	| POS operations                                                                                                                                                           	|
|--------------------------------	|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| View prices                    	| [Price check](#price-check)                                                                                                                                                              	|
| View discounts                 	| [View all discounts](#view-all-discounts)<br>[View available discounts](#view-available-discounts)                                                                                                                           	|
| Override prices                	| [Price override](#price-override)                                                                                                                                                           	|
| Apply or remove discounts      	| [Line discount amount](#line-discount-amount)<br>[Line discount percent](#line-discount-percent)<br>[Total discount amount](#total-discount-amount)<br>[Total discount percent](#total-discount-percent)<br>[Remove system discounts from transaction](#remove-system-discounts-from-transaction)<br>[Reapply system discounts](#reapply-system-discounts) 	|
| Apply or remove coupons        	| [Add coupon code](#add-coupon-code)<br>[Remove coupon code](#remove-coupon-code)                                                                                                                                    	|
| Calculate prices and discounts 	| [Calculate total](#calculate-total)                                                                                                                                                          	|

For more details about how those operations can be configured in the application and whether they support offline mode, please check [Online and offline point of sale (POS) operations](https://docs.microsoft.com/dynamics365/commerce/pos-operations).

## Price check

The **Price check** operation allows POS users to look up pre-configured prices for a specific product.

## View all discounts

The **View all discounts** operation allows POS users to look up all effective promotions that are currently running in the store channel. More specifically, this operation lists all discounts that match any of the following conditions:

- The price group of the discount matches the price group of the store.
- The price group of the discount is mapped to an affiliation or loyalty program.
- The price group of the discount is mapped to a catalog that is associated with the store.

This operation shows only discounts that don't compete with any of the applied discounts. This behavior helps ensure that, if a sales associate informs a customer about a discount, and the customer takes the required action (for example, the customer buys one more item to get 10% off), the discount is applied to the transaction. The coupon-based discounts are shown only when the **Apply without coupon code** parameter is turned on.

Inside this operation, POS users can search discounts by discount name or discount description, as well as filter discounts based on whether the discount requires coupon.

## View available discounts

The **View available discounts** operation allows POS users to view all discounts that are applicable to a selected line in the transaction, or to the whole transaction. The applicable discounts to a selected line include the ones that are already applied, as well as ones not yet but could potentially be applied, for example, mix & match discounts that require additional items. If the applicable discount is linked to a coupon with **Apply without coupon code** parameter turned on, the POS user can also use the **Apply coupon** function inside this operation to directly redeem the coupon without having to enter or scan any coupon code or coupon bar code.

## Price override

The **Price override** operation allows POS users to override the sales price of a product in the transaction. This operation only works for products configured to allow price overrides.

## Line discount amount

The **Line discount amount** operation allows POS users to enter a discount amount for a line item in the transaction. This operation only applies to discountable items and respects the **Maximum line discount amount** specified in the POS permission group for the user.

## Line discount percent

The **Line discount percent** operation allows POS users to enter a discount percentage for a line item in the transaction. This operation only applies to discountable items and respects the **Maximum line discount percentage** specified in the POS permission group for the user.

## Total discount amount

The **Total discount amount** operation allows POS users to enter a discount amount for a transaction. This operation only applies to discountable items and respects the **Maximum total discount amount** specified in the POS permission group for the user. When the entered value exceeds the limit, the operation is blocked, and no permission override flow is triggered. Applying a total discount amount to a cart mixed of sales and return items is not yet supported.

## Total discount percent

The **Total discount percent** operation allows POS users to enter a discount percentage for a transaction. This operation only applies to discountable items and respects the **Maximum discount total percentage** specified in the POS permission group for the user. When the entered value exceeds the limit, the operation is blocked, and no permission override flow is triggered. Applying a total discount percentage to a cart mixed of sales and return items is not yet supported.

## Remove system discounts from transaction

The **Remove system discounts from transaction** operation allows POS users to clear all applied system discounts (including coupon-based discounts) from the transaction. After performing this operation, pricing engine starts excluding system discounts from discount calculation scope. This operation does not remove manual discounts.

## Reapply system discounts

The **Reapply system discounts** operation allows POS users to reapply system calculated discounts on the transaction if they were removed using the Remove system discounts from transaction operation. After performing this operation, the pricing engine starts including all system discounts in discount calculation scope.

## Add coupon code

The **Add coupon code** operation allows POS users to add a coupon to the transaction by entering the **coupon code**. Alternatively, POS users can scan or enter a **coupon bar code** using the numeric keyboard on the Transactions screen to add a coupon to the transaction.

## Remove coupon code

The **Remove coupon code** operation allows POS users to select and remove one or more coupons that are currently applied to the transaction.

## Calculate total

The **Calculate total** operation allows POS users to trigger on-demand pricing calculation. This operation is needed when price lock and/or delayed price calculation is enabled, and the POS user wants to recalculate prices and discounts after cart / order changes.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
