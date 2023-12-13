---
title: Pricing examples
description: This article provides examples of typical usages of pricing and discounts in Microsoft Dynamics 365 Commerce.
author: zhizhen
ms.date: 12/08/2023
ms.topic: article
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: zhizhen
ms.search.validFrom:

---

# Pricing examples

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article provides examples of typical usages of pricing and discounts in Microsoft Dynamics 365 Commerce.

## Purchase product A, and receive a discount on product B when both items are in the cart

To configure a mix and match discount where when a user purchases product A, they receive a discount on product B when both items are in their cart, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Pricing and discounts \> Mix and match discounts**.
1. Select **New**.
1. Configure general settings for the new mix and match discount, such as price groups, discount name, priority, and validation period.
1. On the **Price/discount** FastTab, for **Calculation type**, select **Line spec**.
1. Add product A as **Line group** "A", with a **Discount value** of "0" (zero).
1. Add product B as **Line group** "B", with the **Discount value** of the offer.

The following example screenshot shows:
- When there are two quantities of items under category "Apparel and Footwear" and one quantity of item "0103" in the cart, the discount is applicable.
- When the discount is applied, the item "0103" in the cart gets 100% off.

![Purchase product A, and receive a discount on product B when both items are in your cart](./media/mix-and-match-sample-1.png)

## Receive a discount on a specific item when your cart totals a certain amount

To receive a discount on a specific item when your cart totals a certain amount, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Pricing and discounts \> Threshold discounts**.
1. Select **New** to create a new threshold discount.
1. Configure general settings for the new threshold discounts such as price groups, discount name, priority, and validation period.
1. Under **Threshold discount tiers** FastTab, add a new tier and fill the amount the customers get discount on.
1. Select **Discount lines** in the **Calculation type** column.
1. Add items that are qualified for cart totals calculation to the **Lines** FastTab.
1. Add items that need to be discounted to the **Threshold discount lines** FastTab.

The following example screenshot shows:
- When the total amount for the items under "Fashion" category reaches $100, the discount is applicable.
- When the discount is applied, the item "0029" in the cart gets 30% off.

![threshold sample 1](./media/threshold-sample-1.png)

[!INCLUDE[footer-include](../includes/footer-banner.md)]