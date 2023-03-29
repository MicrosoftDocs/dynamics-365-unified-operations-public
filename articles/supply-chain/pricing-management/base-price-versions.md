---
title: Base price versions
description: This article describes how base price versions work in Pricing management.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form: GUPBasePriceVersion, GUPItemBasePrice
ms.topic: conceptual
ms.date: 04/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Base price versions

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

This article describes how base price versions work in Pricing management. The primary purpose of a base price version is to maintain a list of *item base prices* for a specific period. The base price is a common price at the SKU level. Pricing management allows you to build selling prices using *cost-plus pricing*. When you use cost-plus pricing, you start by building a pricing structure that starts with the base price.

The following tables shows an example of [pricing structure](price-structure-overview.md) that could be used to build final selling prices based on base prices.

| Pricing sequence | Price component code | Price component type | Descriptions | Price details in the sales order |
|---|---|---|---|---|
| 10 | BAS01 | Base price | BAS01 must be associated with any one of the following price component code types:<ul><li>Base price – inventory price</li><li>Base price – purchase price</li><li>Base price – cost price</li></ul> | Base price |
| 20 | MAC01 | Margin component | &plusmn; amount or % | Price adjustments |
| 25 | MAC02 | Margin component | &plusmn; amount or % | Price adjustments |
| 30 | MAC03 | Margin component | &plusmn; amount or % | Price adjustments |

The selling price is calculated as follows: *Selling price = Base price &plusmn; Margin component price adjustments*

## Determining the base price

The cost-plus pricing model works by determining the product cost and then adding a markup to determine the selling price.

- In retail and distribution industries, many products are items that are procured and then sold to customers. For these industries, the base price is typically the procurement price for a product.
- In the manufacturing industries, the base price is typically based on the calculated total cost of the bill of materials (BOM) for a product.

Pricing management derives base prices from one of the following two sources:

- The primary source is the price listed for each product on the **Item base price** page, which yo can open by going to **Pricing management \> Pre-sales pricing \> Base price versions** and selecting selecting **Price \> Base** price from on the Action Pane. <!-- KFM: I think this is what we mean here. Please confirm. More documentation is needed for these pages. -->
- If an item doesn't have an active Item base price, the system will check to see if it has an active cost price in a [costing version](../cost-management/costing-versions.md). A costing version can support a standard cost inventory model for items where the costing version contains a set of standard cost records about the items and their manufacturing processes.

The following tables illustrates the rules for determining the base price.

| Product type | Industries | How base prices are found |
|---|---|---|
| Traded items that you procure and then sell | Retail, distribution | <ul><li>Pricing management calculates item base prices based on prices found on the **Base price versions** page.</li><li>Item base prices are calculated as: *Vendor list price &plusmn; Vendor price term agreement*<li>If several calculated prices apply to the same item, the price engine always selects the *lowest* price as the item base price.</li><li>You can activate a calculated item base price and the price engine will use that as the base price.</li></ul> |
| Manufactured items (with BOM) that use the standard cost model | Manufacturing | <ul><li>Supply Chain Management can calculate and activate item cost prices based on [costing versions](../cost-management/costing-versions.md).</li><li>There is no need to maintain item base prices on the **Base price versions** page.</li><li>The price engine will use the active item cost price as the base price.</li><li>Item sell prices are calculated as: *Active calculated item cost (base price) &plusmn; margin component price adjustments*</li></ul> |
| Manufactured items (with BOM) that don't use the standard cost model | Manufacturing | <ul><li>Item base prices are defined on the **Base price versions** page.</li><li>The price engine will use the active item base price as the base price.</li></ul> |

## Base price determination exception

The base price is a common price at the SKU level. A price differentiation strategy is commonly applied when a price manager negotiates with a customer to set up a special price for a particular group of products for a specified date range. These prices should be recorded as *sales trade agreement prices*. Sales trade agreement prices take priority over base prices.

The following table shows how sales trade agreements relate to selling prices.

| Do applicable margin component price adjustments exist? | Sales price calculation |
|---|----|
| No | *Selling price = Sales trade agreement price* |
| Yes | *Selling price = Sales trade agreement price &plusmn; Margin component price adjustments* |

> [!NOTE]
> To use sales trade agreement prices, your pricing structure must include a price component code whose **Price component** is *Sales trade agreement*.

The following tables shows an example of [pricing structure](price-structure-overview.md) that includes a sales trade agreement.

| Pricing sequence | Price component code | Price component type | Descriptions | Price details in the sales order |
|---|---|---|---|---|
| 10 | BAS01 | Base price | BAS01 must be associated with any one of the following price component code types:<ul><li>Base price – inventory price</li><li>Base price – purchase price</li><li>Base price – cost price</li></ul> | Base price / Sales trade agreement price |
| 15 | TAM | Sales trade agreement | Sales trade agreement | Base price / Sales trade agreement price |
| 20 | MAC01 | Margin component | &plusmn; amount or % | Price adjustments |
| 25 | MAC02 | Margin component | &plusmn; amount or % | Price adjustments |
| 30 | MAC03 | Margin component | &plusmn; amount or % | Price adjustments |

So, for example, using this price structure, the price engine might find that item *EV0001* in a sales order line has following applicable pricing rules:

- Activated item base price (BAS01) = $5
- Posted sales trade agreement journal price (TAM) = $8
- Margin component price adjustment (MAC01) = $3
- Margin component price adjustment (MAC02) = $2
- Margin component price adjustment (MAC03) = -$1

Therefore, the selling price for the sales order line is: *8 &plus; 3 &plus; 2 &minus; 1 = 12*.

<!--KFM: I think the point of this example is that we ignore BAS01 because we have an applicable sales trade agreement. If this is right, we should point this out explicitly. -->

## Next steps

- [Sales trade agreement prices](sales-trade-agreement-prices.md)