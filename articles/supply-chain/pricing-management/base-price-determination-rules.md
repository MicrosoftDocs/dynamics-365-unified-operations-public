---
title: Sales order base price determination rules
description: This article describes the price determination rules for calculating an item base price.
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

# Sales order base price price determination rules

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

This article describes the price determination rules for calculating the sales order base price.

<!-- KFM: Introduce the following table. What does it show? Why isn't unit price affected by discounts? -->

| Terms | Definition, usage, and notes | Price component type |
|-------------------------|-------------------------|-------------------------|
| Unit price | The price calculated for each unit in a sales order. It's calculated as: *Unit price = Base price &plusmn; Margin component price adjustments* |  |
| Base price | The basis for the price adjustments. It's intended for all customers and is the standard rate for general purposes.<ul><li>If there is applicable sales trade agreement price, then the base price is the *sales trade agreement price*</li><li>If there is no applicable sales trade agreement price, the base price is the *item base price*.</li></ul> |  |
| Sales trade agreement price | Reflects a negotiated pricing strategy for a collection of customers and a group of specific products. You can configure the system to calculate the unit price based on it by applying one of the following formulas:<ul><li>*Unit price = Sales trade agreement price* (when no margin component price adjustment applies)</li><li>*Unit price = Sales trade agreement price &plusmn; Margin component price adjustments*</li></ul> | Sales trade agreement |
| Item base price | The **Item base price** page lets you set prices for each item using either calculated or manually entered values. Calculated prices use the following formula: *Item base price = Vendor list price &plusmn; Vendor term agreements* | Can be any of the following: <ul><li>Base price - purchaser price</li><li>Base price - inventory price</li><li>Base price - sales price</li></ul> |
| Standard cost | The cost version of an item calculated using standard cost model. | Base price - inventory price |
| Margin component price adjustments | You can set up layers of margin components to adjust the base price up (positive) or down (negative). Margin component price adjustments have a calculation sequence and can be compounded to get the total adjustment price. | Margin component |
| Sales agreement | The Pricing management module respects [sales agreement rules](../sales-marketing/sales-agreements.md), but the sales agreement feature is not otherwise integrated with the Pricing management module. |  |

## Base price determination flowchart

The following flowchart illustrates the sales order base price determination rules.

[<img src="media/base-price-determination-chart.png" alt="Sales order base price determination rule diagram." title="Sales order base price determination rule diagram" width="720" />](media/base-price-determination-chart.png#lightbox)

## Concurrency model for sales trade agreement prices

<!--KFM: This section, the ranking rules, and the examples are unclear so I can't edit them. It's not clear where these various "ranks" come from. Please revise and add more details. -->

Follow these steps to set the concurrency model to use for sales trade agreement prices:

1. Go to **Pricing management \> Setup \> Pricing management parameters**.
1. Open the **Prices and discounts** tab.
1. Expand the **Trade agreements** FastTab.
1. Set **Enable default find next** to one of the following values:
    - *Yes* – The price engine will check all applicable trade agreement prices and apply the *cheapest* price.
    - *No* – The price engine will use the *price attribute combination rank* to determine the price by applying the following rules: <!-- KFM: It isn't clear where the various ranks in this table come from or what "records" we are referring to. -->
        - Apply the record with the highest *price attribute combination rank*.
        - If two or more records have an equal and highest *price attribute combination rank*, the price engine will check the *header price attribute* and apply the highest ranked record price group.
        - If two or more records have an equal and highest *header price attribute*, the price engine will check the *line price attribute* and apply the highest ranked record in the price attribute group.
        - If multiple price records are found with the same rank, the price engine will apply the cheapest price.

The following table shows an example of price component code attribute combinations. <!-- KFM: The table has two columns with the same heading. What does that mean?  -->

| Price attribute combination | Price attribute combination | Header price attribute | Rank | Line price attribute | Rank |
|---|---|---|---|---|---|
| Target customer segments + Vehicle product | 2003 | Customer account | 4 | Interior Upholstery | 4 |
| Target customer segments + Vehicle product | 2003 | Customer group | 3 | Exterior color | 3 |
| Target customer segments + Vehicle product | 2003 | Price group | 2 | Fuel type | 2 |
| Target customer segments + Vehicle product | 2003 | Sales group | 1 | Drive type | 1 |

Assuming there are two posted records for sales trade agreement price lines with the same date range. <!-- KFM: What does this mean?  -->

Because the price attribute combination is the same, the price attribute combination ranks are the same. The price engine will apply the RID0002 price.

<!-- KFM: We should introduce the following table. What does it mean? -->

| IDs | Price attribute combination | Header price attribute criteria | Line price attribute criteria | Price | Applicable |
|---|---|---|---|---|---|
| RID0001 | Target customer segments + Product segments | Price group= 01 | Interior Upholstery= Package B | $1500 | No |
| RID0002 | Target customer segments + Product segments | Customer account= US-003 | Interior Upholstery= Package B | $1550 | Yes |

## Next steps

- [Base price versions](base-price-versions.md)
- [Sales trade agreement prices](sales-trade-agreement-prices.md)