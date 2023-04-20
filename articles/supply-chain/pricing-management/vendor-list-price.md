---
title: Vendor list prices and price adjustments
description: This article provides information about vendor list prices, which come from a vendor price catalogue and can be used as the foundation for calculating the sales price of an item.
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

# Vendor list prices and price adjustments

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

In some cases, Pricing management can derive a product's sales price from the vendor's list price or procurement price. For example, this functionality can be used for the trade of items in the retail and distribution industry, where products are procured from vendors and sold to customers.

Vendor list prices come from a vendor price catalogue and can be used as the foundation for calculating the sales price of an item.

The vendor list price features have three core elements:

- **Vendor list price** – The vendor list price lets you record the general vendor price catalog and specify a valid date period. The vendor list price is on the *item and inventory dimensions* level.
- **Vendor price term codes** – Vendor price term codes establish a list of price adjustment codes that you can use when you define vendor price term agreements. For calculations where the **Compound** option is set to *Yes*, pricing calculations will apply price term codes together with the pricing sequence.
- **Vendor price term agreements** – Vendor price term agreements keep track of the contracts that you have with vendors for price adjustments for each site. The valid periods, vendors, calculation methods for price adjustments, and values are all recorded. You can use price attributes to specify the applicable items and sales order lines, because vendor price term agreements use the line price attribute group.

Pricing management lets you define the selling price as *Item base price* &plusmn; *Margin component price adjustments*.

For the items that will be sold, the system can determine the item base price based on the vendor list price. The item base price is calculated as *Vendor list price* + *Vendor price term agreement price*. During the calculation, the system evaluates each vendor's item base price for each site. Because the item base price has just one unique active value per site, if multiple calculated prices exist, the system will use only the lowest calculated price.

## Next steps

- [Base price determination rules](base-price-determination-rules.md)
- [Base price versions](base-price-versions.md)
- [Sales trade agreement prices](sales-trade-agreement-prices.md)
