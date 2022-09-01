---
# required metadata

title: Coupons
description: This article provides an overview of coupon related capabilities in Dynamics 365 Commerce.
author: boycez
ms.date: 08/29/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: RetailCoupon, RetailParameters, RetailSharedParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw

# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
ms.search.industry: retail
ms.author: josaw
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: July 2017 update

---

# Coupons

This article provides an overview of coupon related capabilities in Dynamics 365 Commerce.

## Overview

Coupons are codes and bar codes used to add discounts to transactions. Retailers distribute coupons to prospective or existing customers to help improve their brand recognition, drive conversion, retain customer base, boost sales and eventually increase revenue. Coupon has became one of the most popular marketing tools, and a new norm in e-commerce sales. 

In Commerce, coupons are linked to discounts and essentially considered as additional validation on top of discounts. Each coupon is related to one discount. The linked discount defines the set of products that the coupon is valid for. The price groups that are associated with the discount define the eligible conditions (such as customer groups, selling channels) the coupon can be used.  The coupon also provides **Usage limit** and **Customer required** properties as optional usage restriction. Each coupon can have multiple **coupon codes** and **coupon bar codes**, and each code can have its own effective date range and status. If the status of a code is set to **Inactive**, this code cannot be used in any channel.

## Set up coupon

Before you can set up a coupon, you must set up the coupon bar code and two coupon number sequences. 

1. On the **Mask characters** page, create a new mask character for **Coupon code** type. You can select any unused character.
1. On the **Bar code mask setup** page, create a new bar code mask for **Coupon** type.
1. On the **Bar code setup** page, create a new bar code that uses the bar code mask that you just created.
1. On the **Number sequences** page, create two new number sequences. One sequence for the **Coupon number**, which is the unique identifier of coupon, and the other for the **Coupon code ID**, which is the unique identifier of each coupon code for a coupon. For both number sequences, you must set the **Scope** field to **Company**. In most cases, you should automatically generate both sequence numbers.
1. On **Commerce parameters \> Prices and discounts > Coupons**, set the **Coupon bar code mask** field to the bar code you created earlier.
1. On **Commerce parameters \> Number sequences**, select the number sequences that you created earlier for the **Coupon number** and **Coupon code ID**.

To set up a coupon, you must create discount and coupon separately, and then link them by selecting the discount in **Discount** field of the coupon configuration. After a coupon is linked to a discount, the **Status**, **Effective date** and **Expiration date** fields on the linked discount become read-only, because they are managed by the coupon's status and validity period respectively. When a coupon status is set to **Active** or **Inactive**, the linked discount status becomes **Enabled** or **Disabled** systematically. 

## Use coupon

To add a coupon to a sales transaction in Commerce point of sale (POS), you can use coupon code or coupon bar code. To use coupon code, select the **Add coupon code** operation and enter the code. Alternatively, to use coupon bar code, you can scan the bar code using scanner device or enter the bar code using the numeric keyboard on the **Transaction** screen.

Retailers sometimes want to give cashiers authority to apply fixed-amount discounts to customers for appeasement or product defects reasons, but don’t want to print coupon codes and distribute them to the cashiers. To achieve it, they can set the **Apply without coupon code** option on coupon to **Yes**. With that, in POS, cashiers can use the **Apply coupon** function inside the **View available discounts** operation to add a coupon to the transaction without manually entering the code. If multiple coupon codes exist for a coupon, the system automatically selects the first active code and applies it to the transaction.

To add a coupon to a call center sales order, the call center user needs to use the **Coupons** function (located at **Manage \> Coupons**) on Action Pane of sales order form.

To add a coupon to an e-commerce order, the shopper can enter the coupon code in the **promo code** input box on the shopping bag.

After a coupon is added to a sales order, the pricing engine triggers recalculation for the entire order immediately, regardless of whether delayed calculation is enabled.

> [!NOTE] 
> In Commerce version **10.0.30** and earlier, after adding coupons to a call center sales order, the call center user must select the **Recalculate** button (located at **Sell \> Calculate \> Recalculate**) on Action Pane in order for the discount associated to the coupon to get applied.
## Coupon usage limit

Coupons can be configured for limited use. The usage limit can be defined per customer, channel, or global-wise. The limit is enforced per coupon code on a coupon. For example, a single-use coupon that has two coupon codes can be used two times: one time for each coupon code.

Coupons can be used across selling channels. However, for call center, the limited-use coupons can be applied only when the **Order completion** setting on the call center is enabled. If this is disabled, then only non-limited-use coupons can be applied.

[!INCLUDE[footer-include](../includes/footer-banner.md)]