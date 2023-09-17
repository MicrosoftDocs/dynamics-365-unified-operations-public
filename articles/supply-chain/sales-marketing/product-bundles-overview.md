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

Product bundles enable businesses to group multiple items so that they can be priced and sold together. They provide an easy way to ensure that the correct items are always sold and priced together, but that the individual items in the bundle can also be shipped individually and revenue can be recognized against the shipped items.

A product bundle consists of a parent item and multiple component items. Order entry is quick and efficient, because users can add the whole bundle to a sales order just by adding the parent item. Picking lists and packing slips list the component items of a product bundle, but sales confirmations and sales invoices show only the parent item.

Each product bundle is represented by a physical item. However, when the sales order is confirmed, the bundle is exploded into its component items, and the selling price is allocated proportionally from the parent item to the individual component items that make up the bundle. After the bundle is exploded into its component items, the product bundle construct ensures that the sum of the component items equals the bundle net amount, so that the customer is always invoiced the correct amount for the product bundle.

This product bundle feature replaces the [previous bundle feature](../../finance/accounts-receivable/rev-rec-bundles.md) that was part of the revenue recognition module and was deprecated in April 2023.

> [!NOTE]
> Product bundles aren't supported in channels that are managed by Microsoft Dynamics 365 Commerce. These channels include e-commerce, point of sale (POS), and call centers. Items that are configured as product bundles shouldn't be added to orders or transactions that were created in Dynamics 365 Commerce channels.

## Next steps

- [Enable and set up product bundles](product-bundles-setup.md)
- [Sell and allocate product bundles](product-bundles-use.md)
