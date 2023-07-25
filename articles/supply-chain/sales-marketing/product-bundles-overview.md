---
title: Product bundles overview 
description: This article provides an overview of what product bundles are.
author: henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: Customer
ms.topic: how-to
ms.date: 07/31/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Product bundles overview

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

Product bundles allow businesses to group multiple items into product bundles to price and sell them together. It's an easy way to enable and ensure that the correct items are always sold and priced together while allowing the individual items included in the bundle to be shipped individually with revenue recognized against the shipped items.

A product bundle comprises a parent item and multiple component items. Order entry is quick and efficient because users can add the whole bundle to a sales order by adding the parent item. Picking lists and packing slips will list the component items of a product bundle, but sales confirmations and sales invoices will show only the parent item.

Each product bundle is represented by a physical item, but on sales order confirmation, the bundle is exploded into its component items, and the selling price is allocated proportionally from the parent item to the individual component items making up the bundle. Once exploded into its component items, the product bundle construct ensures that the sum of the component items equals the bundle net amount, so the customer is always invoiced the correct amount for the product bundle.

This product bundle feature replaces the [previous bundle feature](../../finance/accounts-receivable/rev-rec-bundles.md) (deprecated in April 2023), which was part of the revenue recognition module.

> [!NOTE]
> Product bundles aren't supported in channels managed by Dynamics 365 Commerce (including e-commerce, point of sale (POS), and call center). Items that are configured as product bundles shouldn't be added to orders or transactions that were created in Dynamics 365 Commerce channels.

## Next steps

- [Enable and set up product bundles](product-bundles-setup.md)
- [Sell and allocate product bundles](product-bundles-use.md)
