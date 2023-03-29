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
| Item base price | The **Item base price** page lets you set prices for each item using either calculated or manually entered values. Calculated prices use the following formula: *Item base price = Vendor list price &plusmn; Vendor term agreements* | Can be any of the following: <ul><li>Base price - purchase price</li><li>Base price - inventory price</li><li>Base price - sales price</li></ul> |
| Standard cost | The cost version of an item calculated using standard cost model. | Base price - inventory price |
| Margin component price adjustments | You can set up layers of margin components to adjust the base price up (positive) or down (negative). Margin component price adjustments have a calculation sequence and can be compounded to get the total adjustment price. | Margin component |
| Sales agreement | The Pricing management module respects [sales agreement rules](../sales-marketing/sales-agreements.md), but the sales agreement feature is not otherwise integrated with the Pricing management module. |  |

The following flowchart illustrates the sales order base price determination rules.

[<img src="media/base-price-determination-chart.png" alt="Sales order base price determination rule diagram." title="Sales order base price determination rule diagram" width="720" />](media/base-price-determination-chart.png#lightbox)

## Next steps

- [Base price versions](base-price-versions.md)
- [Sales trade agreement prices](sales-trade-agreement-prices.md)