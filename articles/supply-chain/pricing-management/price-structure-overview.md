---
title: Price structure overview
description: This article provides an overview of how price structures work in Pricing management
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form: GUPPricingTree, GUPPriceComponentCodeSetup
ms.topic: overview
ms.date: 03/24/2023
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

## Price components

The following table summarizes the principle components of the price structure used by Pricing management.

| Price component | Price position | Details |
|---|---|---|
| Base price | Unit Price | <p>The *base price* (which is at the SKU level) represents the common price for general use. You can choose *one* of the base price types:</p><ul><li>Base price - inventory price</li><li>Base price - purchase price</li><li>Base price - sales price</li></ul><p>The base price comes from **Item base price** page <!-- KFM: Where is this page?--> and can be calculated or entered manually.</p><p>If you set up the base price using the price structure (price component code setup or price tress), and no matching record exists on the **Item base price** page, then the system will check whether the item is a standard cost item and source the base price from the activate item standard cost.</p> |
| Sales trade agreement price | Unit Price | <p>The *sales trade agreement price* takes precedence over the base price because it represents a special price arrangement with a particular group of consumers for a certain set of products.</p><p>You can only have *one* price component code that use this price component. Within that price component code, you can define multiple pricing rule records <!-- KFM: What do we mean by "pricing rule records"? I don't see those here.-->. The concurrency models (parameter level configuration<!--KFM: Are you referencing a setting on the **Pricing management parameters** page? I couldn't find a relevant setting there. -->) are:<ul><li>**Find next** – Find the all the applicable records and apply the one with the cheapest price.</li><li>**Price attribute combination rank** – Find the record that has the highest price attribute combination rank and apply that price</li></ul> |
| Margin component price adjustment | Unit Price | <p>The *margin component price adjustment* is a set of price adjustments applied to the base price or sales trade agreement price. The system applies the following calculation:</p><p>Unit price = (\[Base price\] or \[Sales trade agreement price\]) &plusmn; \[Margin component price adjustment\].</p><p>You can have *multiple* price component codes that use this price component. Within the price component code, you can define multiple pricing rule records<!-- KFM: What do we mean by "pricing rule records"? I don't see those here.-->. The concurrency models are <!--KFM: Is there just one, or did we forget the others? -->:<ul><li>**Price attribute combination rank** – Find the record that has the highest price attribute combination rank and apply that price.</li></ul><p>The system will find the applicable rule records in each price component code, and then *compound* the result into price adjustments.<!--KFM: Is this actually another concurrency model? --></p> |
| Discounts | On-invoice discounts | <p>Depending on your business needs, you can group various discount rule records into various discount types of price component codes. This differs from the discount type, the later one is calculation method relevant.<!--KFM: I'm not sure what this paragraph is referring to. --></p><p>You can have *multiple* price component codes that use this price component. Within the price component code, you can define multiple pricing rule records <!-- KFM: What do we mean by "pricing rule records"? I don't see those here.-->. The concurrency models are <!--KFM: Maybe we should describe each of the following, like we do in the sections above. -->:<ul><li>Best price</li><li>Compounded</li><li>Exclusive</li><li>Always apply</li><li>Price attribute combination rank</li></ul> |
| Rebate | Off-invoice discounts | <p>Depending on your business needs, you can group various rebate rule records into various rebate types of price component codes<!--KFM: I'm not sure what this paragraph is referring to. -->.</p><p>You can have *multiple* price component codes that use this price component. Within the price component code, you can define multiple pricing rule records <!-- KFM: What do we mean by "pricing rule records"? I don't see those here.-->. The concurrency models are<!--KFM: Is there just one, or did we forget the others? -->:<ul><li>**Price attribute combination rank:** Find the records that have the highest price attribute combination rank and apply the price.</li></ul> |

<!--KFM: Why aren't we including the following note as part of the table? This appears to be a "price component", but it's otherwise missing from the table. -->

> [!NOTE]
> The auto charge for sales is another distinction between the price component code setup (single price tree) and price trees (multiple price trees).
>
> - **Price component code setup:** You can add the price component code for auto charge in the price tree structure configuration.
> - **Price trees**: Auto charges are not included in the price tree structure. The system will apply the standard Supply Chain Management auto-charge logic, which means that when a rule record is applicable, the auto charge will apply to the sales order.

## Next steps

- [Set up company to use a multiple price structures](price-structure-multiple.md)
- [Set up company to use a single price structure](price-structure-single.md)
- 