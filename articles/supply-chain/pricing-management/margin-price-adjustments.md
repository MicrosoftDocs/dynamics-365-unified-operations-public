---
title: Margin price adjustments
description: This article describes how to set up and use margin price adjustments.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form: GUPPriceComponentCode, GUPPriceComponentCodeSetup, GUPPricingTree, RetailPeriodicDiscount, GUPParameters
ms.topic: how-to
ms.date: 04/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Margin price adjustments

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article describes how to set up and use margin price adjustments.

Pricing management enables you to use *margin price adjustments* to move item prices up or down from the base price. You can set this up by including one or price component codes of type *Margin component price adjustment* in your price structures. Across price component codes, price adjustment are compounded and add up to the total price adjustment. <!-- KFM: Do we *always* compound these? -->

In scenarios where you build your selling price based on the inventory standard cost or purchased price, it represents the layers of the margin components that add up to those base price. <!-- KFM: This isn't clear. Please revise. -->

Margin component price adjustments can be associated with many different types of agreements, promotions, and events. They make it easy for you to adjust price without changing the base price.

## Set up margin price adjustments

To use margin component price adjustments you must make the following configurations:

- Create one or more [price component codes](price-component-code.md) to set up various types of margin price adjustments that you can include in your price structures.
- Create one or more [price structures](price-structure-overview.md) to establish how your margin price adjustments combine with other price elements (such as base price and discounts) to find the final unit price.
- Set up one or more [margin price adjustment pricing rules](margin-discount-pricing-rules.md) to configure the margin price adjustments you need, which customers and items they apply to, and how they are calculated. You'll associate each price adjustment with a specific price component code and then define the details of the calculation.

For details about how to create pricing rules for each margin price adjustment (and discount), see [Pricing rules for discounts and margin price adjustments](margin-discount-pricing-rules.md).

For example, the following screenshot shows a price structure that contains two sequential margin component price adjustments (*General price adjustments* and *Seasonal price adjustments*).

[<img src="media/price-component-code-setup.png" alt="The Price component code setup page." title="The Price component code setup page" width="720" />](media/price-component-code-setup.png#lightbox)

## Margin component price adjustment determine rule

### Within the same price component code

Pricing management allows multiple rule records within the same price component code. The concurrency modes within the price component code for Margin component adjustments are displayed in the Margin component price adjustments records.

Go to **Pricing management \> During-sales pricing \> Price adjustments \> Margin component price adjustments**.

The concurrency models within the Price component code for Margin component price adjustments are Price attribute combination rank, and display only, non-modifiable.

### Across the price component codes

In the Price component code setup\\Price trees, you can build multiple price component codes for Margin component price adjustments. The **Concurrency model across priority** (price component codes) are set in the form:

- Price component code setup (single tree) or,
- Price trees (multiple trees)

- **Concurrency model across priority** – 'Compounded' is the default setting, and it cannot be modified. This implies that all price component codes for Margin component price adjustments will be added together. The pricing sequence will determine the calculation sequence.
- **Compounded** – It decides whether the Margin component price adjustment of this price component code's calculation basis is Base price or compounded value. When the calculation method is set to "Percent," the compounded setting affects the computation's outcome.

| Price Component Code | Description | Pricing Sequence | Calculation Method | Value | Compounded | Calculated Value |
|---|---|---|---|---|---|---|
| Base Price | Base Price- Inventory Cost | 10 |   |   |   | 1000.00 |
| MC01 | Ullage | 20 | Percent | 5 | No | 50.00 |
| MC02 | Freight | 30 | Percent | -2 | Yes | -21.00 |
| MC03 | Group Margin price adjustment | 40 | Amount | 10 | No | 10.00 |
| MC04 | Contract Margin price adjustment | 50 | Percent | 5 | Yes | 51.95 |
| MC05 | Pickup fee | 60 | Amount | 2 | Yes | 2.00 |
| MC06 | Other cost to sell | 70 | Percent | 5 | Yes | 54.64 |
| Unit price | 1147.59 |  |  |  |  |  |
