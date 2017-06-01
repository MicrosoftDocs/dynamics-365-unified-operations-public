---
# required metadata

title: Retail coupons
description: Retail coupons overview. Discount codes and call center coupons have been merged into a one feature set.
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

# Coupons for retail sales

[!include[banner](includes/banner.md)]


## Creating coupons

Coupons are codes and bar codes that are required to get some retail discounts. You can have multiple codes per coupon and each code can have it's effective dates. Coupons can be configured to be limited use. When creating limited use coupons the limit can be defined per customer, per channel, or global limit. When coupons are limited use the limit is enforced when the code or bar code is entered or scanned in POS or sales order entry. The usage of the coupon is recorded when an order is competed with a coupon on it. The limit is enforced per coupon code on a coupon.  For example, a single use coupon with two coupon codes can be used twice, once for each coupon code.  Each code on a coupon can be independently set to active.

Each coupon is related to one retail discount. The customers, or channels that a coupon is valid in are defined by price groups associated to discount. A coupon can be configured require a customer. 

When a discount is related to one or more coupons, some of the properties of the discount become disabled in the discount form because they are managed by properties on the coupon. These are the discount status, the start and end dates of the discount and the coupon code required flag.

## Managing coupons

You need to create the discount and the coupon independently and then link them by choosing the discount in the coupon form. Once you link a coupon to a discount, a number of fields on the discount become read only because they are managed by the coupon's settings. Fields such as status and standard date ranges.  

Coupons are now essentially additional validation on top of retail discounts. The coupon provides the coupon codes and bar codes with date ranges, the usage limits, and customer required property. The discount provides the set of products the coupon is valid for. The discount's price groups provide the set of customers, channels, or catalogs the coupon is valid for.


## Required set up for coupons 
Before you can use retail coupons you need to set up a coupon bar code and two number sequences. These are the steps for set up. Each step starts with the form name for the step.
- **Mask characters**: Create a new mask character for coupon code. Any unused character is fine.
- **Bar code mask setup**: Create a new bar code mask with **Type = Coupon**.
- **Bar code setup**: Create a new bar code that uses the bar code mask you just created.
- **Number sequences**: Create 2 new number sequences. One for Coupon code ID and one for Coupon number. Coupon number is the unique identifier for a coupon. Coupon code ID is the unique identifier for each coupon code for a coupon. Each coupon can have multiple codes / bar codes that trigger the coupon.
    - For both number sequences the **scope** must be company
    - Most likely you will want both to automatically generate sequence numbers.
- **Retail shared parameters**: In the **Bar codes** tab, select the bar code you created earlier.
- **Retail parameters**: In the **Number sequences** tab, select the corresponding number sequences you created earlier for **Coupon number** and **Coupon code ID**
- You should now be able to open the **Coupons** form and create new coupons.
 
### Partial updates and upgrades

Dynamics 365 servicing does not enforce applying updates for all components together. In addition, the retail solution is a distributed solution which also means updates may not be applied completely across the solution. The coupon feature because it is a merge of two existing features and involves discount calculation it is important to understand the impact of a partial update. 
- **Headquarters only partial update**: There are forms and binary updates that are applied in HQ. The retail price engine is updated with the binary update. It is used to calculate price in sales order and price simulator. The coupon and discount forms are updated with the HQ forms update. If only one of the two update parts are applied, you will get forms that do not match the price calculation data. This will cause either unexpected discount calculation or errors during discount calculation. 
- **HQ updated, Retail server and POS not updated(N-1)**: Retail server handles price calculation with the price engine. We always support updating HQ before updating retail stores. This is because not all stores can be updated at the same time. In this scenario, new functionality related to coupons won't be available in non-updated retail stores. For example, 'exclude' lines have been introduced with coupons. However, if you use exclude lines on a discount they will not be applied in a retail store running a previous version.
- **HQ not updated, Retail server and POS updated(N+1)**: The updated price engine in retail server knows how to handle legacy discount codes during price calculation so in this you should see no functional impact of the update.
