---
title: Resolving concurrency across price component codes
description: Concurrency rules let you establish what happens when multiple discounts and price adjustments apply to the same order and/or order line. This article explains how to manage across-price-component-code concurrency within a price structure. 
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

# Resolving concurrency across price component codes

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Concurrency rules let you establish what happens when multiple pricing rules apply to the same order and/or order line. You can set up concurrency rules to control whether the customer should receive just one of the matching rules (and which one) or whether they should be combined (and how they should be combined). There are two types of concurrency:

- *Across-price-component-code concurrency* – Controls how the various [price component codes](price-component-code.md) included in a [pricing structure](price-structure-overview.md) combine with each other. Your pricing structure establishes a collection of various types of price component codes (including base price, sales agreement price, margin components, discounts, and/or charges), the sequence in which the codes are calculated, and how the price adjustments should be calculated and combined to find the final price.
- *Within-price-component-code concurrency* – Any number of [pricing rules](margin-discount-pricing-rules.md) can be associated with each of the component codes included in a pricing structure. This is especially true of discounts. This type of concurrency occurs when an order or order line qualifies for more than pricing rule that is associated with the same component code. For example, you could define a price component code called *Seasonal promotion events* and associate multiple discount rules with it, which means that multiple pricing rules might apply to the same order line. You would therefore set up concurrency rules to control whether the customer should receive just one of the matching discounts (and which one) or whether they should be combined (and how they should be combined) within the *Seasonal promotion events* price component code.

This article explains how to manage *across-price-component-code concurrency*. For details about how to manage *within-price-component-code concurrency*, see [Resolving concurrency within price component codes](concurrence-within-codes.md).

## Set across-price-component-code concurrency options for each price structure

Concurrency across price components codes only affects discounts and margin price adjustments. You make the setting at the price structure level, using the **Concurrency mode across priority** column on either the **Price component code setup** or **Price trees** page. The following options are available:

- *Compounded* – The system will first compute the price adjustment or discount for each line in the structure and then will calculate the final discount or adjustment by adding up the value for each line. This value is only available for lines with a **Price component** of *Discounts* or *Margin component* (For margin components, this is the only available setting).
- *Best price* – If the price structure includes more than one price component code with this setting, then  only one of those lines will contribute to the final unit price (the one with the highest discount).  This value is only available for lines with a **Price component** of *Discounts*.

This setting only affects discount calculations when the **Best price and compound concurrency control model** is set to *Best price and compound within priority, best price and compound across priority* on the **Pricing management parameters** page. See the [System settings for resolving discount concurrency across price component codes](#parameters) for details.

As mentioned, margin components are always compounded across components (in other words, **Concurrency mode across priority** is always *Compounded* for margin components in your price structures). However, you still need to set up each price structure to control whether each adjustment is calculated using the base price or the compound price (running total). This can have a significant effect on your final prices for margin price adjustments that are calculated as a percentage. For each margin component in your price structure(s), you can set this option using the **Compound** check box. For an example of how this setting affects your final prices, see [Example price calculation using a mix of compound and non-compound margin components](#margin-example).

For details about how to set up price structures, see [Arrange price component codes into a price structure](price-structure-details.md).

## <a name="parameters"></a>System settings for resolving discount concurrency across price component codes

A setting on the **Pricing management parameters** page affect the way concurrent discounts are calculated, which can also affect the way some of your price structure settings work as they apply to discounts. Follow these steps to set it up.

1. Go to **Pricing management \> Setup \> Pricing management parameters**.
1. Open the **Prices and discounts** tab.
1. Expand the **Discount concurrency control** FastTab.
1. Choose one of the following options under the **Best price and compound concurrency control model** heading:
    - *Best price and compound within priority, never compound across priorities*
    - *Best price only within priority, always compound across priorities*
    - *Best price and compound within priority, best price and compound across priority*

## <a name="margin-example"></a>Example price calculation using a mix of compound and non-compound margin components

When your price structure includes multiple margin and/or discount components, then the order in which they are calculated and the method used to combine them can significantly affect the final price.

The following table shows an example price component code setup and its resulting calculations.

| Price component code | Description | Pricing sequence | Calculation method | Value | Compounded | Calculated line value | New unit price |
|---|---|---|---|---|---|---|---|
| Base | Base price - inventory Cost | 10 |  |  |  | $1,000.00 | $1,000.00 |
| MC01 | Ullage | 20 | Percent | 5 | No | $50.00 | $1,050.00 |
| MC02 | Freight | 30 | Percent | -2 | Yes | -$21.00 | $1,029.00 |
| MC03 | Group Margin price adjustment | 40 | Amount | 10 | No | $10.00 | $1,039.00 |
| MC04 | Contract Margin price adjustment | 50 | Percent | 5 | Yes | $51.95 | $1,090.95 |
| MC05 | Pickup fee | 60 | Amount | 2 | Yes | $2.00 | $1,092.95 |
| MC06 | Other cost to sell | 70 | Percent | 5 | Yes | $54.65 | $1,147.60 |

The system applies the following rules to calculate the final unit price:

- The calculation proceeds by calculating a new unit price for each line following the pricing sequence.
- For non-compounded lines, the line value is calculated based on the original base price.
- For compound lines, the line value is calculated based on the previous line's new unit price.
- Each line's new unit price is found by adding its calculated line value to the new unit price from the previous line.
- Calculation continues until all lines have been processed, resulting in the final unit price.

## Example price calculation using a mix of compound and best-price discount components

The following table shows a price structure that uses a mix of best-price and compounded components.

| Price component code | Price sequence | Concurrency mode across priority | Price component | Computed line value |
|---|---|---|---|---|
| MAC01 | 10 | Compounded | Margin component | $50 |
| MAC02 | 20 | Compounded | Margin component | $20 |
| DIS 01 | 30 | Best price | Discounts | $10 |
| DIS 02 | 40 | Best price | Discounts | **$20** |
| DIS 03 | 50 | Compounded | Discounts | $30 |

In addition, the **Pricing management parameters** are set with a **Best price and compound concurrency control model** of *Best price and compound within priority, best price and compound across priority*, where *priority* refers to each price component code in the sequence (this setting affects the way the discount lines are interpreted). Therefore, the following unit price modifications apply:

- The total price adjustment is the sum of the margin component lines: **$70**.
- The best price (largest discount) for the best price lines is $20, to which is added to the compounded discount so the total discount is: **$50**.
