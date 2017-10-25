---
# required metadata

title: Create coupons for retail sales
description: This topic provides an overview of retail coupons and explains how to set them up.
author: scott-tucker
manager: AnnBe
ms.date: 05/22/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: RetailCoupon
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
ms.search.industry: retail
ms.author: scotttuc
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: July 2017 update

---

# Create coupons for retail sales

[!include[banner](includes/banner.md)]


## Overview of coupons

Coupons are codes and bar codes that are used to add retail discounts to transactions. Each coupon can have multiple codes, and each code can have its own effective dates. 

Each coupon is related to one retail discount. The price groups that are associated with the discount define the customers that can use a coupon or the channels where a coupon is valid. 

Essentially, coupons are additional validation on top of retail discounts. The coupon provides the coupon codes and bar codes that are required, together with date ranges for those codes. The coupon also provides optional usage limits and customer required properties. The discount provides the set of products that the coupon is valid for. The price groups for the discount provide the set of customers, channels, or catalogs that the coupon is valid for.

To create a coupon, you create the discount and the coupon separately. You then link them by selecting the discount on the coupon page in Microsoft Dynamics 365 for Retail. 

> [!NOTE]
> After a coupon is linked to a discount, several fields on the discount page in Microsoft Dynamics 365 for Retail become read-only, because they are managed by the coupon’s settings. These fields include the fields for the status and standard date ranges.

### Limited-use coupons

Coupons can be configured as limited-use coupons. The usage limit can be defined per customer or channel, or as a global limit. This limit is enforced when the code or bar code is entered or scanned in POS or during sales order entry. A coupon is recorded as used when an order is completed that has the coupon associated with it.

The limit is enforced per coupon code on a coupon. For example, a single-use coupon that has two coupon codes can be used two times: one time for each coupon code. Each code on a coupon can be independently set to active.

## Managing coupons

You must create the discount and the coupon separately. You then link them by selecting the discount on the coupon page. After you link a coupon to a discount, several fields for the discount become read-only, because they are managed by the coupon's settings. These fields include the fields for the status and standard date ranges.  

Essentially, coupons are now additional validation on top of retail discounts. The coupon provides the coupon codes and bar codes, together with date ranges, the usage limits, and the customer required property. The discount provides the set of products that the coupon is valid for. The discount's price groups provide the set of customers, channels, or catalogs that the coupon is valid for.

## System setup for coupons 

Before you can set up a coupon, you must set up the coupon bar code and two coupon number sequences. 

1.  On the **Mask characters** page, create a new mask character for the coupon code. You can select any unused character.
2.	On the **Bar code mask setup** page, create a new bar code mask. Set the **Type** field to **Coupon**.
3.	On the **Bar code setup** page, create a new bar code that uses the bar code mask that you just created.
4.	On the **Number sequences** page, create two new number sequences. One sequence is for the coupon code ID, and the other sequence is for the coupon number. The coupon code ID is the unique identifier for each coupon code for a coupon. The coupon number is the unique identifier for a coupon. Each coupon can have multiple codes and bar codes that trigger the coupon.

    > [!NOTE]
    > For both number sequences, you must set the **Scope** field to **Company**. In most cases, you should automatically generate both sequence numbers.

5.	On the **Retail shared parameters** page, on the **Bar codes** tab, select the bar code that you created earlier.
6.	On the **Retail parameters** page, on the **Number sequences** tab, select the number sequences that you created for the coupon number and coupon code ID.
7.	You can now open the **Coupons** page and create new coupons.

## The effect of partial updates on coupons

Coupon functionality comprises multiple distinct features in Dynamics 365 for Retail. Microsoft Dynamics 365 for Retail headquarters (HQ) and the channel can be partially updated across components. Therefore, it's important that you understand how partial updates affect coupon functionality as a whole.

- **HQ is partially updated, but Retail server and POS aren't updated.** In an HQ update, the coupon and discount pages are updated, and the retail price engine is also updated. If only one of those two components is updated, some pages in Retail won’t match the price calculation data. Therefore, unexpected discount calculations or errors might occur during discount calculations.
- **HQ is updated, but Retail server and POS aren't updated (N-1).** Because not all retail stores can be updated at the same time, we recommend that you update HQ before you update retail stores. In the N-1 scenario, new functionality that is related to coupons won't be available in stores that haven’t been updated yet. For example, the coupon functionality introduces “exclude” lines. If you use exclude lines on a discount, they won't be applied in a retail store that is running an earlier version.
- **HQ isn't updated, but Retail server and POS are updated (N+1).** Because the updated price engine in Retail server can handle legacy discount codes during price calculations, the update should have no functional impact in this scenario.
