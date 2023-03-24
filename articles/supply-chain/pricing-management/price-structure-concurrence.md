---
title: Resolving concurrent price codes within a price structure
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

# Resolving concurrent price codes within a price structure

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Concurrency rules let you establish what happens when multiple discounts and price adjustments apply to the same order and/or order line. You can set up concurrency rules to control whether the customer should receive just one of the matching price adjustments (and which one) or whether they should be combined (and how they should be combined). There are two types of concurrency:

- *Across-price-component-code concurrency* – Controls how the various [price component codes](price-component-code.md) included in a [pricing structure](price-structure-overview.md) combine with each other. Your pricing structure establishes a collection of various types of price component codes (including base price, sales agreement price, margin components, discounts, and/or charges), the sequence in which the codes are calculated, and how the price adjustments should be calculated and combined to find the final price.
- *Within-price-component-code concurrency* – Any number of [pricing rules](price-rules.md) can be associated with each of the component codes included in a pricing structure. This is especially true of discounts. This type of concurrency occurs when an order or order line qualifies for more than pricing rule that is associated with the same component code. For example, you could define a price component code called *Seasonal promotion events* and associate multiple discount rules with it, which means that multiple pricing rules might apply to the same order line. You would therefore set up concurrency rules to control whether the customer should receive just one of the matching discounts (and which one) or whether they should be combined (and how they should be combined) within the *Seasonal promotion events* price component code.

This article explains how to manage *across-price-component-code concurrency*. For details about how to manage *within-price-component-code concurrency*, see [Resolving concurrent pricing rules within a price code](concurrent-pricing-rules.md).

## <a name="parameters"></a>System settings for discount concurrency control

A few settings on the **Pricing management parameters** page affect the way concurrent discounts are calculated, which can also affect the way some of your price structure settings work as they apply to discounts. Follow these steps to set it up.

1. Go to **Pricing management \> Setup \> Pricing management parameters**.
1. Open the **Prices and discounts** tab.
1. Expand the **Discount concurrency control** FastTab.
1. Choose one of the following options under the **Best price and compound concurrency control model** heading:
    - *Best price and compound within priority, never compound across priorities* – <!-- KFM: Description needed -->
    - *Best price only within priority, always compound across priorities* – <!-- KFM: Description needed -->
    - *Best price and compound within priority, best price and compound across priority* – <!-- KFM: Description needed. Mention that the **Concurrency mode across priority** option in the **Price component code** setup only has an effect when this option is selected.  -->
1. Choose one of the following options under the **Discount compound behavior** heading.
    - *Compound* – <!-- KFM: Description needed -->
    - *Compound on the original price* – <!-- KFM: Description needed -->
1. Set **Enable competition between exclusive threshold and other periodic discounts** to one of the following values:
    - *Yes* – Exclusive threshold discounts will compete with the exclusive non-threshold discounts while priority still applies. The best price and compounded threshold discounts behavior will remain unchanged (they won't compete with the non-threshold discounts).
    - *No* – <!-- KFM: Description needed -->

## Example price calculation using a mix of compound and non-compound margin components

When your price structure includes multiple margin and/or discount components, then the order in which they are calculated and the method used to combine them can significantly affect the final price.

The following table shows an example price component code setup and its resulting calculations. <!-- KFM: What is the context here (where do the value and calc method values come from)? -->

| Price component code | Description | Pricing sequence | Calculation method | Value | Compounded | Calculated line value | New unit price |
|---|---|---|---|---|---|---|---|
| Base | Base price - inventory Cost | 10 |  |  |  | $1,000.00 | $1,000.00 |
| MC01 | Ullage | 20 | Percent | 5 | No | $50.00 | $1,050.00 |
| MC02 | Freight | 30 | Percent | -2 | Yes | -$21.00 | $1,029.00 |
| MC03 | Group Margin adjustment | 40 | Amount | 10 | No | $10.00 | $1,039.00 |
| MC04 | Contract Margin adjustment | 50 | Percent | 5 | Yes | $51.95 | $1,090.95 |
| MC05 | Pickup fee | 60 | Amount | 2 | Yes | $2.00 | $1,092.95 |
| MC06 | Other cost to sell | 70 | Percent | 5 | Yes | $54.65 | $1,147.60 |

The system applies the following rules to calculate the final unit price: <!-- KFM: I wrote these based on my best understanding/guesses. Please review and confirm. -->

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
