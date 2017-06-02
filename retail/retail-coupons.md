---
# required metadata

title: Creating coupons for retail sales
description: This topic provides and overview of retail coupons and how to set them up.
author: scott-tucker
manager: AnnBe
ms.date: 05/22/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: RetailCoupon
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope:
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
ms.search.industry: retail
ms.author: scotttuc
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: 

---

# Creating coupons for retail sales

[!include[banner](../includes/banner.md)]


## Overview of coupons

Coupons are codes and bar codes that are used add retail discounts to transactions. Each coupon can have multiple codes, and each code can have its own effective dates. 

Each coupon is related to one retail discount. The customers that can use a coupon, or the channels that a coupon is valid in, are defined by the price groups associated with the discount. 

Coupons are essentially additional validation on top of retail discounts. The coupon provides the coupon codes and bar codes that are required along with date ranges for those codes. The coupon also provides optional usage limit, and customer required properties. The discount provides the set of products the coupon is valid for. The price groups for the discount provide the set of customers, channels, or catalogs the coupon is valid for.

To create a coupon, you create the discount and the coupon separately and then link them by choosing the discount on the coupon page in Dynamics AX for Retail. 

#### Note
> Once a coupon is linked to a discount, several fields on the discount page in Dynamics become read-only because they are managed by the coupon’s settings. Those fields include status and standard date ranges.

### Limited use coupons

Coupons can also be configured to be limited use. The limit can be defined per customer, per channel, or for a global limit. For limited use coupons, the limit is enforced when the code or bar code is entered or scanned in POS or a sales order entry. The use of the coupon is recorded when an order is competed with a coupon associated with it. The limit is enforced per coupon code on each coupon. For example, a single use coupon with two coupon codes can be used twice, once for each coupon code. Each code on a coupon can be independently set to active.

## Managing coupons

You need to create the discount and the coupon independently and then link them by choosing the discount in the coupon form. Once you link a coupon to a discount, a number of fields on the discount become read only because they are managed by the coupon's settings. Fields such as status and standard date ranges.  

Coupons are now essentially additional validation on top of retail discounts. The coupon provides the coupon codes and bar codes with date ranges, the usage limits, and customer required property. The discount provides the set of products the coupon is valid for. The discount's price groups provide the set of customers, channels, or catalogs the coupon is valid for.


## System set up for coupons 

Before you can set up a coupon, you first need to set up the coupon bar code and two coupon number sequences. 

1.  On the **Mask characters** page, create a new mask character for the coupon code. You can select any unused character.
2.	On the **Bar code mask setup** page, create a new bar code mask with **Type** set to "Coupon".
3.	On the **Bar code setup** page, create a new bar code that uses the bar code mask you just created.
4.	On the **Number sequences** page, create two new number sequences. One sequence is for the coupon code ID and the other is for the coupon number. The coupon code ID is the unique identifier for each coupon code for a coupon. The coupon number is the unique identifier for a coupon. Each coupon can have multiple codes and bar codes that trigger the coupon.
#### Note
> For both number sequences, **Scope** must be set to “Company”. In most cases, you should automatically generate both sequence numbers.
5.	On the **Retail shared parameters** page, on the **Bar codes** tab, select the bar code you created earlier.
6.	On the **Retail parameters** page, on the **Number sequences** tab, select the corresponding number sequences you created earlier for the coupon number and coupon code ID.
7.	You can now open the **Coupons** page and create new coupons.

 
## Effect of partial updates on coupons

Coupon functionality comprises multiple distinct features in Dynamics 365 for Retail. Dynamics 365 for Retail headquarters (HQ) and channel can be updated partially across components. Because of this, it's important to understand how partial updates affect coupon functionality as a whole.

- HQ partially updated, Retail server and POS not updated: In an HQ update, coupon and discount pages are updated, as well as the retail price engine. If only one of those two components are updated, certain pages in Retail won’t match the price calculation data, resulting in unexpected discount calculations or errors during discount calculations.
- HQ updated, Retail server and POS not updated (N-1): Because not all retail stores can be updated at the same time, it’s recommended that HQ is updated before the retail stores. In the N-1 scenario, new functionality related to coupons won't be available in stores that haven’t been updated yet. For example, “exclude” lines have been introduced with coupon functionality. If you use exclude lines on a discount, they will not be applied in a retail store running a previous version.
- HQ not updated, Retail server and POS updated (N+1): Because the updated price engine in Retail server can handle legacy discount codes during price calculations, there should be no functional impact of the update in this scenario.
