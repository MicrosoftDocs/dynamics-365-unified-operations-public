---
title: Margin price adjustments
description: Learn how to set up and use margin price adjustments, including a list of configuration you must complete to use margin component price adjustments.
author: sherry-zheng
ms.author: chuzheng
ms.topic: how-to
ms.date: 5/28/2026
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: GUPPriceComponentCode, GUPPriceComponentCodeSetup, GUPPricingTree, RetailPeriodicDiscount, GUPParameters
---

# Margin price adjustments

[!include [banner](../includes/banner.md)]

This article describes how to set up and use margin price adjustments.

Unified pricing management lets you use *margin price adjustments* to move item prices up or down from the base price. Set up these adjustments by including one or more price component codes of the *Margin component price adjustment* type in your price structures. Price adjustments are compounded across price component codes and add up to the total price adjustment.

In scenarios where you build your selling price based on the inventory standard cost or purchase price, it represents the layers of the margin components that add up to those base prices.

You can associate margin component price adjustments with many types of agreements, promotions, and events. They let you easily adjust prices without changing the base price.

To use margin component price adjustments, complete the following configuration steps:

- Create one or more [price component codes](upm-price-component-code.md) to set up the different types of margin price adjustments that you can include in your price structures.
- Create one or more [price structures](upm-price-structure-overview.md) to define how your margin price adjustments combine with other price elements (such as base prices and discounts) to determine the final unit price.
- Set up one or more [margin price adjustment pricing rules](upm-margin-discount-pricing-rules.md) to configure the margin price adjustments that you need, and to define which customers and items they apply to, and how they're calculated. Associate each price adjustment with a specific price component code and then define the details of the calculation.

For information about how to create pricing rules for each margin price adjustment (and discount), see [Pricing rules for discounts and margin price adjustments](upm-margin-discount-pricing-rules.md).

For example, the following illustration shows a price structure that contains two sequential margin component price adjustments (*General price adjustments* and *Seasonal price adjustments*).

:::image type="content" source="media/price-component-code-setup.png" alt-text="Screenshot of price structure on the Price tree page." lightbox="media/price-component-code-setup.png":::
