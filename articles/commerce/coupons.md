---

# required metadata
title: Coupons
description: This article provides an overview of coupon-related capabilities in Microsoft Dynamics 365 Commerce.
author: boycez
ms.date: 11/09/2023
ms.topic: article
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2017-06-30

---

# Coupons

[!include [banner](../includes/banner.md)]

This article provides an overview of coupon-related capabilities in Microsoft Dynamics 365 Commerce.

Coupons are codes and bar codes that are used to add discounts to transactions. Retailers distribute coupons to prospective or existing customers to help improve their brand recognition, drive conversion, retain their customer base, boost sales, and eventually increase revenue. Coupons have become one of the most popular marketing tools and are a new norm in e-commerce sales.

In Dynamics 365 Commerce, coupons are linked to discounts and are considered additional validation on top of discounts. Each coupon is related to one discount, and the linked discount defines the set of products that the coupon is valid for.

Price groups that are associated with a discount define the eligible conditions that a coupon can be used for. Those conditions include customer groups and selling channels. Coupons also provide **Usage limit** and **Customer required** properties that can be used to configure optional usage restrictions.

Each coupon can have multiple coupon codes and coupon bar codes, and each code can have its own effective date range and status. If the status of a code is set to **Inactive**, the code can't be used in any channel.

## Set up a coupon

Before you can set up a coupon, you must set up the coupon bar code and two coupon number sequences.

To set up a coupon in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Inventory management \> Bar codes and labels \> Mask characters**.
1. Select **Add** to create a mask character of the **Coupon code** type. In the **Character** field, you can select any unused character.
1. Go to **Retail and Commerce \> Inventory management \> Bar codes and labels \> Bar code mask setup**.
1. Select **New** to create a bar code mask of the **Coupon** type.
1. Go to **Retail and Commerce \> Inventory management \> Bar codes and labels \> Bar code setup**.
1. Select **New** to create a bar code that uses the bar code mask that you created.
1. Go to **Organization administration \> Number sequences**.
1. Create two number sequences:

    1. One sequence for the **Coupon number** reference. This sequence defines the unique identifier of coupon.
    1. One sequence for the **Coupon code ID** reference. This sequence defines the unique identifier of each coupon code for a coupon.

    For both number sequences, you must set the **Scope** field to **Company**. In most cases, both sequence numbers should be automatically generated.

1. Go to **Commerce parameters \> Prices and discounts \> Coupons**.
1. Set the **Coupon bar code mask** field to the bar code that you created earlier.
1. Go to **Commerce parameters \> Number sequences**.
1. Select the number sequences that you created earlier for the **Coupon number** and **Coupon code ID** references.

To set up a coupon, you must create the discount and the coupon separately, and then link them by selecting the discount in the **Discount** field of the coupon configuration. After a coupon is linked to a discount, the **Status**, **Effective date**, and **Expiration date** fields of the linked discount become read-only, because the values are determined by the coupon's status and validity period. When a coupon's status is set to **Active**, the status of the linked discount is automatically updated to **Enabled**. Likewise, when a coupon's status is set to **Inactive**, status of the linked discount status is automatically updated to **Disabled**.

## Use a coupon

To add a coupon to a sales transaction in Commerce point of sale (POS), you can use a coupon code or a coupon bar code. To use a coupon code, select the **Add coupon code** operation, and then enter the code. To use a coupon bar code, you can either scan the bar code by using a scanning device or enter it by using the numeric keyboard on the **Transaction** screen.

Retailers sometimes want cashiers to be able to give fixed-amount discounts to customers for appeasement reasons or because of product defects, but they don't want to print coupon codes and distribute them to the cashiers. In this case, you can set the **Apply without coupon code** option for the coupon to **Yes**. POS cashiers can then use the **Apply coupon** function inside the **View available discounts** operation to add a coupon to a transaction without manually entering the code. If multiple coupon codes exist for a coupon, the system automatically selects the first active code and applies it to the transaction.

To add a coupon to a call center sales order, a call center user must select **Coupons** on the **Manage** tab of the Action Pane on the sales order page.

To add a coupon to an e-commerce order, the shopper can enter the coupon code in the **promo code** field in the shopping cart.

After a coupon is added to a sales order, the pricing engine immediately triggers recalculation for the whole order, regardless of whether delayed calculation is enabled.

> [!NOTE]
> In Commerce version 10.0.30 and earlier, after call center users add a coupon to a call center sales order, they must select **Recalculate** in the **Calculate** group on the **Sell** tab of the Action Pane to apply the discount that is associated with that coupon.

## Coupon usage limit

Coupons can be configured for limited use. The usage limit can be defined per customer, per channel, or globally. The usage limit is enforced per coupon code on a coupon. For example, a single-use coupon that has two coupon codes can be used two times, one time for each coupon code.

Coupons can be used across selling channels. However, for call center, limited-use coupons can be applied only when the **Enable order completion** setting for the call center channel is enabled. If the **Enable order completion** setting is disabled, only non-limited-use coupons can be applied.

## Other considerations

If a coupon has a large number of coupon codes, activating all the coupon codes by setting the coupon status to **Active** can be time-consuming. For such cases, the following best practices are recommended:

- Split large groups of coupon codes into multiple coupons, with each coupon linked to the same discount.
- If you create a large number of coupon codes by data import, if you import them as **Active** and with the **From date** value set as the desired effective date, you don't need to manually activate the coupon codes.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
