---
title: Price structure overview
description: This article provides an overview of how price structures work in Pricing management
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form: GUPPricingTree, GUPPriceComponentCodeSetup
ms.topic: overview
ms.date: 04/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Price structure overview

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

You can check the detailed price breakdown including the price component when a sales order is placed. The breakdown corresponds to the price structure that you have configured. The price details that are shown give an audit record of how the price was determined and serve as a starting point for future price investigation. <!-- KFM: This seems like an intro to a different topic. We should instead tell what price trees are and what they are for.  -->

The following two methods are available for building the price structure:

- **Price component code setup** – Provides a single, uniform price structure for each company.
- **Price trees** – Enables multiple price structures based on order attribute values for each company.

<!-- KFM: We should introduce the following image. What are we showing here?  -->

[<img src="media/price-trees-block-diagram.png" alt="Price tree and price component code setup elements." title="Price tree and price component code setup elements" width="720" />](media/price-trees-block-diagram.png#lightbox)

## Price component types

The following table summarizes the principle component types that can be included in a price structure.

| Price component | Price position | Details |
|---|---|---|
| Base price | Unit Price | <p>The *[base price](base-price-versions.md)* (which is at the SKU level) represents the common price for general use. You can only have *one* price component code of this type in each price structure, which can be of any of the following base price types:</p><ul><li>Base price - inventory price</li><li>Base price - purchase price</li><li>Base price - sales price</li></ul><p>The base price comes from the **Item base price** page and can be calculated or entered manually.</p><p>If you set up the base price using a price structure (price component code setup or price tress), and no matching record exists on the **Item base price** page, then the system will check whether the item is a standard cost item and source the base price from the activate item standard cost.</p> |
| Sales trade agreement price | Unit Price | <p>When available, the *[sales trade agreement price](sales-trade-agreement-prices.md)* takes precedence over the base price because it represents a special price arrangement with a particular group of consumers for a certain set of products.</p><p>You can only have *one* price component code of this type, but any number of sales trade agreement prices may apply for that code in various situations.</p> |
| Margin component price adjustment | Unit Price | <p>*[Margin component price adjustments](margin-price-adjustments.md)* move item prices up or down from the base price. Margin component price adjustments can be associated with many different types of agreements, promotions, and events. They make it easy for you to adjust price without changing the base price.</p><p>You can have *multiple* price component codes of this type, and you can associate any number of [pricing rules](margin-discount-pricing-rules.md) with each of these price component codes.  Across price component codes, price adjustment are compounded and add up to the total price adjustment. |
| Discounts | On-invoice discounts | <p>*[Discounts](discounts.md)* let you adjust prices based on a wide variety of calculation methods designed to encourage the purchase of certain products, volumes, packages, and so on. You can have *multiple* price component codes of this type, and you can associate any number of [pricing rules](margin-discount-pricing-rules.md) with each of these price component codes.</p> |
| Rebate management | Off-invoice discounts | <!-- KFM: Description needed. --> You can have *multiple* price component codes of this type. <!-- KFM: We need a topic about this. --> |
| Auto charges | <!-- KFM: Value needed --> | <!-- KFM: Description needed. --> |

## Concurrency rules

If your price structure has multiple price rules that apply to the same price component code and/or multiple price component codes of the same type, then the system will apply concurrency rules to resolve them.

- If more than one pricing rule applies to the same price component code in a price structure, then *within-price-component-code concurrency* rules will be applied to decide which rules apply and how to combine them. See also [Resolving concurrency within price component codes](concurrence-within-codes.md).
- If your price structure includes more than one price component code of the same type, then *Across-price-component-code concurrency* rules will be applied to decide how to combine them. See also [Resolving concurrency across price component codes](concurrence-cross-codes.md).

## Next steps

- [Set up company to use a multiple price structures](price-structure-multiple.md)
- [Set up company to use a single price structure](price-structure-single.md)
- [Arrange price component codes into a price structure](price-structure-details.md)
