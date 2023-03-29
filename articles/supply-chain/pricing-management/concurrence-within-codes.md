---
title: Resolving concurrency within price component codes
description: Concurrency rules let you establish what happens when multiple discounts and price adjustments apply to the same order and/or order line. This article explains how to manage within-price-component-code concurrency.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: conceptual
ms.date: 04/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Resolving concurrency within price component codes

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Concurrency rules let you establish what happens when multiple discounts and price adjustments apply to the same order and/or order line. You can set up concurrency rules to control whether the customer should receive just one of the matching price adjustments (and which one) or whether they should be combined (and how they should be combined). There are two types of concurrency:

- *Across-price-component-code concurrency* – Controls how the various [price component codes](price-component-code.md) included in a [pricing structure](price-structure-overview.md) combine with each other. Your pricing structure establishes a collection of various types of price component codes (including base price, sales agreement price, margin components, discounts, and/or charges), the sequence in which the codes are calculated, and how the price adjustments should be calculated and combined to find the final price.
- *Within-price-component-code concurrency* – Any number of [pricing rules](price-rules.md) can be associated with each of the component codes included in a pricing structure. This is especially true of discounts. This type of concurrency occurs when an order or order line qualifies for more than pricing rule that is associated with the same component code. For example, you could define a price component code called *Seasonal promotion events* and associate multiple discount rules with it, which means that multiple pricing rules might apply to the same order line. You would therefore set up concurrency rules to control whether the customer should receive just one of the matching discounts (and which one) or whether they should be combined (and how they should be combined) within the *Seasonal promotion events* price component code.

This article explains how to manage *within-price-component-code concurrency*. For details about how to manage *across-price-component-code concurrency*, see [Resolving concurrency across price component codes](concurrence-cross-codes.md).

## Types of within-price-component-code concurrency modes

The following types of within-price-component-code concurrency mode are available (depending on price component code type):

- **Exclusive** – The pricing rule can't be combined with other rules associated with the same price component code. If more than one of these rules is as exclusive, the price engine will apply the rule with the highest discount.
- **Best price** – Pricing rules of this concurrency mode will compete for the highest discount (lowest price).
- **Compounded** – All applicable pricing rules will be combined. You can set the system to make each calculation based on the original price or on a running total of all adjustments so far. The setting is on the **Pricing management parameters** page, as described in [System settings for discount concurrency control](concurrence-cross-codes.md#parameters).
- **Always apply** – The pricing rule always applies. This calculation is always applied last within a price component code.
- **Price attribute combination rank** – Pricing rules using this concurrency mode don't compete for price but instead compete based on which one has the highest *price attribute combination rank*. If multiple rules have the same highest rank within the same price component code, then those rules will be combined.

## Configure within-price-component-code concurrency modes

There are three places in the system where you can view and/or set within-price-component-code concurrency modes:

- **Price component code level** – Each relevant price component code holds a default within-price-component-code concurrency setting. The available modes vary by price component code type. This setting can be overwritten in any or all pricing rules if needed. See also [Price component codes](price-component-code.md).
- **Price structure level** – Each price component code included in a price structure shows its default concurrency mode, but you're not able to edit it here. See also [Arrange price component codes into a price structure](price-structure-details.md).
- **Pricing rule level** – The concurrency mode assigned to a pricing rule will override the default mode assigned by its associated price component code. See also [Pricing rules for discounts and margin price adjustments](price-rules.md).

## Discount determination flow

The following flow chart shows how pricing rules, price structure, and concurrency models work together to resolve within-price-component-code concurrency. <!-- KFM: We need to provide this information also in text.  -->

[<img src="media/concurrency-flowchart.png" alt="Flowchart for determining within-price-component-code concurrency." title="Flowchart for determining within-price-component-code concurrency" width="600" />](media/concurrency-flowchart.png#lightbox)

## Example

Here's an example of how concurrency determination works:

1. Suppose you have an item *BT023* with an item price of *$1565.00*. The concurrency mode is compounded. <!-- KFM: Where does this concurrency mode come from? -->
1. Your system includes the discount pricing rules shown in the following table. The pricing sequence comes from your price structure.

    | Price component code | Pricing sequence | Pricing rule ID | Concurrency mode | Calculation method | Value | Discount type |
    |---|---|---|---|---|---|---|
    | DIS 01 | 30 | DIS01-01 | Best price | Percentage | 10 | Simple |
    | DIS 01 | 30 | DIS01-02 | Always apply | Percentage | 5 | Simple |
    | DIS 02 | 40 | DIS02-01 | Compounded | Percentage | 10 | Simple |
    | DIS 02 | 40 | DIS02-02 | Always apply | Percentage | 8 | Simple |
    | DIS 03 | 50 | DIS03-01 | Compounded | Amount | 20 | Threshold |
    | DIS 03 | 50 | DIS03-02 | Always apply | Amount | 10 | Threshold |

1. An order is placed for one *BT023*, so the system applies the rules of the previous table to calculate the discount shown in the following table, resulting in a final price of $1080.45

    | Concurrency mode | Pricing sequence | Discount price component code | Pricing rule ID | Calculation method | Value | Discount amount | New unit price |
    |---|---|---|---|---|---|---|---|
    | Best price | 30 | DIS01 | DIS01-01 | Percentage | 10 | 156.50 | 1408.50 |
    | Compounded | 40 | DIS02 | DIS02-01 | Percentage | 10 | 140.85 | 1267.65 |
    | Threshold | 50 | DIS03 | DIS03-01 | Percentage | 20 | 20.00 | 1247.65 |
    | Always apply | 30 | DIS01 | DIS01-02 | Percentage | 5 | 62.38 | 1185.27 |
    | Always apply | 40 | DIS02 | DIS02-02 | Amount | 8 | 94.82 | 1090.45 |
    | Always apply | 50 | DIS 03 | DIS03-02 | Amount | 10 | 10.00 | 1080.45 |

## Resolving concurrency for sales trade agreements

The other sections of this article describe how within-price-component-code concurrency works for discounts and margin price components (which are similar). Sales trade agreements work differently and are set up using trade agreement journals where the pricing rules are established by the related journal lines. Concurrency rules for sales trade agreements are established on the **Pricing management parameters** page. For details about the options available and how to use them, see [Sales trade agreement prices](sales-trade-agreement-prices.md).
