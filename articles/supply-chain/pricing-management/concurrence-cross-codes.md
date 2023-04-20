---
title: Resolve concurrency across price component codes
description: Concurrency rules let you define what happens if multiple discounts and price adjustments apply to the same order and/or order line. This article explains how to manage across-price-component-code concurrency in a price structure. 
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form: GUPPricingTree, GUPParameters, GUPPriceComponentCodeSetup
ms.topic: conceptual
ms.date: 04/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Resolve concurrency across price component codes

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Concurrency rules let you define what happens if multiple pricing rules apply to the same order and/or order line. You can set up concurrency rules to control whether the customer receives just one of the matching rules (and if so, which one they receive), or whether the rules are combined (and if so, how they're combined). There are two types of concurrency:

- **Across-price-component-code concurrency** – This type of concurrency controls how the different [price component codes](price-component-code.md) that are included in a [price structure](price-structure-overview.md) combine with each other. A price structure defines a collection of different types of price component codes (including base price, sales agreement price, margin components, discounts, and/or charges), the order that the codes are calculated in, and the way that the price adjustments are calculated and combined to determine the final price.
- **Within-price-component-code concurrency** – Any number of [pricing rules](margin-discount-pricing-rules.md) can be associated with each price component code that's included in a price structure. This principle is especially true of discounts. This type of concurrency occurs when an order or order line qualifies for more than one pricing rule that's associated with the same component code. For example, if you define a price component code that's named *Seasonal promotion events*, and you associate multiple discount rules with it, multiple pricing rules might apply to the same order line. Therefore, in the *Seasonal promotion events* price component code, you'll set up concurrency rules to control whether the customer receives just one of the matching discounts (and if so, which one they receive), or whether the discounts are combined (and if so, how they're combined).

This article explains how to manage *across-price-component-code concurrency*. For information about how to manage *within-price-component-code concurrency*, see [Resolve concurrency within price component codes](concurrence-within-codes.md).

## Set across-price-component-code concurrency options for each price structure

Concurrency across price components codes affects only discounts and margin price adjustments. You configure the setting at the price structure level, by using the **Concurrency mode across priority** field on either the **Price component code setup** page or the **Price trees** page. The following values are available:

- *Compounded* – The system first computes the price adjustment or discount for each line in the price structure. It then calculates the final discount or adjustment by adding the value of every line. This value is available only for lines where the **Price component** field is set to *Discounts* or *Margin component*. (For margin components, this value is the only one that's available.)
- *Best price* – If the price structure includes more than one price component code that has this value, only one of the lines (the one that has the largest discount) will contribute to the final unit price. This value is available only for lines where the **Price component** field is set to *Discounts*.

The **Concurrency mode across priority** setting affects discount calculations only when the *Best price and compound within priority, best price and compound across priority* option is selected under **Best price and compound concurrency control model** on the **Pricing management parameters** page. For more information, see the [System settings for resolving discount concurrency across price component codes](#parameters) section of this article.

As was mentioned, margin components are always compounded across components (in other words, the **Concurrency mode across priority** field is always set to *Compounded* for margin components in your price structures). However, you must still set up each price structure to control whether each adjustment is calculated by using the base price or the compound price (that is, the running total). The option that you choose can have a significant effect on your final prices for margin price adjustments that are calculated as a percentage. For each margin component in your price structures, you can set the option by using the **Compound** checkbox. For an example that shows how the setting of this checkbox affects your final prices, see the [Example price calculation using a mix of compound and non-compound margin components](#margin-example) section of this article.

For information about how to set up price structures, see [Arrange price component codes into a price structure](price-structure-details.md).

## <a name="parameters"></a>System settings for resolving discount concurrency across price component codes

A setting on the **Pricing management parameters** page affects the way that concurrent discounts are calculated. The calculation method can, in turn, affect the way that some of your price structure settings work as they apply to discounts. Follow these steps to set up the calculation.

1. Go to **Pricing management \> Setup \> Pricing management parameters**.
1. On the **Prices and discounts** tab, on the **Discount concurrency control** FastTab, under **Best price and compound concurrency control model**, select one of the following options:

    - *Best price and compound within priority, never compound across priorities*
    - *Best price only within priority, always compound across priorities*
    - *Best price and compound within priority, best price and compound across priority*

## <a name="margin-example"></a>Example: Price calculation that uses a mix of compound and non-compound margin components

If your price structure includes multiple margin and/or discount components, the order that the components are calculated in and the method that's used to combine them can significantly affect the final price.

The following table shows an example of a price component code setup and its resulting calculations.

| Price component code | Description | Pricing sequence | Calculation method | Value | Compounded | Calculated line value | New unit price |
|---|---|---|---|---|---|---|---|
| Base | Base price - inventory Cost | 10 | | | | $1,000.00 | $1,000.00 |
| MC01 | Ullage | 20 | Percent | 5 | No | $50.00 | $1,050.00 |
| MC02 | Freight | 30 | Percent | -2 | Yes | -$21.00 | $1,029.00 |
| MC03 | Group Margin price adjustment | 40 | Amount | 10 | No | $10.00 | $1,039.00 |
| MC04 | Contract Margin price adjustment | 50 | Percent | 5 | Yes | $51.95 | $1,090.95 |
| MC05 | Pickup fee | 60 | Amount | 2 | Yes | $2.00 | $1,092.95 |
| MC06 | Other cost to sell | 70 | Percent | 5 | Yes | $54.65 | $1,147.60 |

The system applies the following rules to calculate the final unit price:

- A new unit price is calculated for each line, according to the pricing sequence.
- For non-compounded lines, the line value is calculated based on the original base price.
- For compound lines, the line value is calculated based on the previous line's new unit price.
- Each line's new unit price is found by adding its calculated line value to the new unit price from the previous line.
- Calculation continues until all lines have been processed. The result is the final unit price.

## Example: Price calculation that uses a mix of compound and best-price discount components

The following table shows an example of a price structure that uses a mix of best-price and compounded components.

| Price component code | Price sequence | Concurrency mode across priority | Price component | Computed line value |
|---|---|---|---|---|
| MAC01 | 10 | Compounded | Margin component | $50 |
| MAC02 | 20 | Compounded | Margin component | $20 |
| DIS 01 | 30 | Best price | Discounts | $10 |
| DIS 02 | 40 | Best price | Discounts | **$20** |
| DIS 03 | 50 | Compounded | Discounts | $30 |

In addition, on the **Pricing management parameters** page, the *Best price and compound within priority, best price and compound across priority* option under **Best price and compound concurrency control model** is selected. In the name of this option, *priority* refers to each price component code in the sequence. (This setting affects the way that the discount lines are interpreted.) Therefore, the following unit price modifications apply:

- The total price adjustment is the sum of the margin component lines: **$70**.
- The best price (largest discount) for the best-price lines is $20. The compounded discount is then added to this price. Therefore, the total discount is **$50**.
