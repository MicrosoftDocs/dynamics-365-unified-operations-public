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

This article describes how base price versions work in Pricing management. The primary purpose of a base price version is to maintain a list of *item base prices* for a specific period. The base price is a common price at the level of the stock keeping unit (SKU). Pricing management lets you build selling prices by using *cost-plus pricing*. When you use cost-plus pricing, you first build a price structure that starts with the base price.

The following tables shows an example of a [price structure](price-structure-overview.md) that can be used to build final selling prices based on base prices.

| Pricing sequence | Price component code | Price component type | Description | Price details on the sales order |
|---|---|---|---|---|
| 10 | BAS01 | Base price | <p>Price component code *BAS01* must be associated with one of the following price component code types:</p><ul><li>Base price – inventory price</li><li>Base price – purchase price</li><li>Base price – cost price</li></ul> | Base price |
| 20 | MAC01 | Margin component | Adjust the price up or down based on a fixed amount or percentage. | Price adjustments |
| 25 | MAC02 | Margin component | Adjust the price up or down based on a fixed amount or percentage. | Price adjustments |
| 30 | MAC03 | Margin component | Adjust the price up or down based on a fixed amount or percentage. | Price adjustments |

The selling price is calculated by using the following formula: *Selling price* = *Base price* &plusmn; *Margin component price adjustments*.

## Determining the base price

The cost-plus pricing model works by determining the product cost and then adding a markup to determine the selling price.

- In retail and distribution industries, many products are items that are procured and then sold to customers. For these industries, the base price is typically the procurement price for a product.
- In the manufacturing industries, the base price is typically based on the calculated total cost of the bill of materials (BOM) for a product.

Pricing management derives base prices from one of the following two sources:

- The primary source is the item base price that's listed for each product on the **Item base price** page. To open this page, go to **Pricing management \> Pre-sales pricing \> Base price versions** to open the **Base price versions** page, which lists the base price versions that you've created and shows the dates that each version is valid for. Select a version in the list, and then select **Price \> Base price** on the Action Pane to view and edit the prices that apply for that version.
- If an item doesn't have an active item base price, the system determines whether it has an active cost price in a [costing version](../cost-management/costing-versions.md). A costing version can support a standard cost inventory model for items, where the costing version contains a set of standard cost records about the items and their manufacturing processes.

The following table shows the rules for determining the base price.

| Product type | Industries | How base prices are determined |
|---|---|---|
| Traded items that you procure and then sell | Retail, distribution | <ul><li>Pricing management calculates item base prices based on prices that are found on the **Base price versions** page.</li><li>Item base prices are calculated by using the following formula: *Base price* = *Vendor list price* &plusmn; *Vendor price term agreement*.<li>If several calculated prices apply to the same item, the price engine always selects the *lowest* price as the item base price.</li><li>You can activate a calculated item base price. The price engine will then use that calculated price as the base price.</li></ul> |
| Manufactured items (with BOMs) that use the standard cost model | Manufacturing | <ul><li>Microsoft Dynamics 365 Supply Chain Management can calculate and activate item cost prices based on [costing versions](../cost-management/costing-versions.md).</li><li>Item base prices don't have to be maintained on the **Base price versions** page.</li><li>The price engine will use the active item cost price as the base price.</li><li>Item selling prices are calculated by using the following formula: *Selling price* = *Active calculated item cost (base price)* &plusmn; *Margin component price adjustments*.</li></ul> |
| Manufactured items (with BOMs) that don't use the standard cost model | Manufacturing | <ul><li>Item base prices are defined on the **Base price versions** page.</li><li>The price engine will use the active item base price as the base price.</li></ul> |

## Base price determination exception

As has been mentioned, the base price is a common price at the SKU level. A price differentiation strategy is often applied when a price manager negotiates with a customer to set up a special price for a specific group of products for a specific date range. These prices should be recorded as *sales trade agreement prices*. Sales trade agreement prices take priority over base prices.

The following table shows how sales trade agreements are related to selling prices.

| Do applicable margin component price adjustments exist? | Sales price calculation |
|---|----|
| No | *Selling price* = *Sales trade agreement price* |
| Yes | *Selling price* = *Sales trade agreement price* &plusmn; *Margin component price adjustments* |

> [!NOTE]
> To use sales trade agreement prices, your price structure must include a price component code where the **Price component** field is set to *Sales trade agreement*.

The following tables shows an example of a [price structure](price-structure-overview.md) that includes a sales trade agreement.

| Pricing sequence | Price component code | Price component type | Description | Price details on the sales order |
|---|---|---|---|---|
| 10 | BAS01 | Base price | Price component code *BAS01* must be associated with one of the following price component code types:<ul><li>Base price – inventory price</li><li>Base price – purchase price</li><li>Base price – cost price</li></ul> | Base price or Sales trade agreement price |
| 15 | TAM | Sales trade agreement | Sales trade agreement | Base price or Sales trade agreement price |
| 20 | MAC01 | Margin component | Adjust the price up or down based on a fixed amount or percentage. | Price adjustments |
| 25 | MAC02 | Margin component | Adjust the price up or down based on a fixed amount or percentage.| Price adjustments |
| 30 | MAC03 | Margin component | Adjust the price up or down based on a fixed amount or percentage. | Price adjustments |

For example, when this price structure is used, the price engine might find that the following pricing rules are applicable to item *EV0001* on a sales order line:

- Activated item base price (BAS01) = $5
- Posted sales trade agreement journal price (TAM) = $8
- Margin component price adjustment (MAC01) = $3
- Margin component price adjustment (MAC02) = $2
- Margin component price adjustment (MAC03) = -$1

Therefore, the selling price for the sales order line is 8 + 3 + 2 – 1 = $12.

## Next steps

- [Sales trade agreement prices](sales-trade-agreement-prices.md)
