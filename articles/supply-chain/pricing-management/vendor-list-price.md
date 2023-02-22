---
title: Vendor list prices
description: Vendor list prices are typically used for products that are procured from vendors and sold to customers.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form:
ms.topic: conceptual
ms.date: 03/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Vendor list prices

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.33 GA -->

Vendor list prices are typically used for products that are procured from vendors and sold to customers.

Vendor list price functionality has three core elements:

- **Vendor list price** – Provides the capability to record the general vendor price catalogue with a valid date period. The vendor list price is on the *Item + inventory dimensions* level.
- **Vendor price term codes** – Allow you to set up a list of price adjustment codes, which can be used when defining vendor price term agreements. FOr calculations with **Compound** set to *Yes*, the price term codes will be applied along with the pricing sequence.
- **Vendor price term agreements** – Let you keep track of your contracts for price adjustments with vendors for each site. The valid periods, vendors, methods of calculating price adjustments, and values are all recorded. You can use price attributes to specify the applicable items and sales order lines because the vendor price term agreements make use of the line price attribute group.

Pricing management lets you define the selling price as the item base price &plusmn; margin component price adjustments.

For the items sold, the basis for determining the item base price can be provided by vendor list price features. The item base price is calculated as the vendor list price plus the price term agreement. In the calculation, the system will evaluate each vendor's item base price for each site. Because the item base price has just one unique active price per site, if there are multiple calculated prices, the system will only use the lowest calculated price.
