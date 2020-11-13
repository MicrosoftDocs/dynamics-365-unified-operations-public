---
# required metadata

title: Exclude products with certain product lifecycle states
description: This topic explains how to exclude products based on their lifecycle state when Planning Optimization functionality is used. 
author: ChristianRytt
manager: tfehr
ms.date: 11/13/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: crytt
ms.search.validFrom: 2019-11-13
ms.dyn365.ops.version: 10.0.15

---
# Exclude products with certain product lifecycle states

[!include [banner](../../includes/banner.md)]

Released products (and released product versions) include a **Product lifecycle state** setting, which you can use to control (among other things) which products are included during master planning. You can add, remove, and edit lifecycle states as needed by going to **Product information management \> Setup \> Product lifecycle state**. For each product lifecycle state, set **Is active for planning** to *Yes* to include products that have that state during master planning. When set to *No*, the associated products and variants will be excluded from all master planning and BOM-level calculations.

Released products and variants where **Product lifecycle state** is left blank are treated as though they belong to a lifecycle state where **Is active for planning** is set to *Yes*, which means that they will be covered during master planning.

> [!NOTE]
> To avoid unnecessary supply suggestions, we strongly recommend that you associate all obsolete released products (and product variants) with a product lifecycle state that is deactivated for master planning. To avoid waste, this is especially important when working with non-reusable product configuration variants.

## Related resources

For more information related to product the life cycle state, see [Product lifecycle state overview](../../pim/product-lifecycle.md).

For detailed information with steps for how to use the product lifecycle state to exclude products from master planning and BOM-level calculation, see [Create a product lifecycle state to exclude products from Master planning](../../pim/tasks/exclude-products-master-planning.md).
