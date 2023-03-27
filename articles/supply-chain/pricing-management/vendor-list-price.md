---
title: Vendor list price and price adjustments overview
description: Vendor list prices come from a vendor price catalogue and can be used as the foundation to calculate the sales price of an item.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 04/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

<!-- KFM: Is this topic in the right place? What are we talking about here, base prices, sales prices, or something else? -->

# Vendor list price and price adjustments overview

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

In some cases, Pricing management can derive a product's sales price from the vendor's list price or procurement price, such as when trading items in the retail and distribution industry where products are procured from vendors and sold to customers.

Vendor list prices come from a vendor price catalogue and can be used as the foundation to calculate the sales price of an item.

The vendor list price features have three core elements:

- **Vendor list price** – Provides the capability to record the general vendor price catalog with a valid date period. The vendor list price is on the *Item + inventory dimensions* level.
- **Vendor price term codes** – Establish a list of price adjustment codes, which you can use when defining vendor price term agreements. For calculations with **Compound** set to *Yes*, pricing calculations will apply price term codes together with the pricing sequence.
- **Vendor price term agreements** – Keep track of your contracts for price adjustments with vendors for each site. The valid periods, vendors, methods of calculating price adjustments, and values are all recorded. You can use price attributes to specify the applicable items and sales order lines because the vendor price term agreements make use of the line price attribute group.

Pricing management lets you define the selling price as the item base price &plusmn; margin component price adjustments.

For the items to be sold, the system can find the item base price based on the vendor list price. The item base price is calculated as the vendor list price plus the price term agreement. In the calculation, the system will evaluate each vendor's item base price for each site. Because the item base price has just one unique active value per site, if multiple calculated prices exist, the system will only use the lowest calculated price.

## Next steps

- [Base price determination rules](base-price-determination-rules.md)
- [Base price versions](base-price-versions.md)
- [Sales trade agreement prices](sales-trade-agreement-prices.md)