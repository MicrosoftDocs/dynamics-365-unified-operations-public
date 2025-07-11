---
title: Exclude products that have specific product lifecycle states
description: Learn how to exclude products based on their lifecycle state, including an outline on the Is active for planning option being toggled.
author: Henrikan
ms.author: henrikan
ms.topic: article
ms.date: 11/13/2020
ms.custom: 
ms.reviewer: kamaybac
ms.search.form: ReqCreatePlanWorkspace
---

# Exclude products that have specific product lifecycle states

[!include [banner](../../includes/banner.md)]

Released products and released product versions include a **Product lifecycle state** field. This field lets you control, among other things, which products are included during master planning. You can add, remove, and edit lifecycle states as required by going to **Product information management \> Setup \> Product lifecycle state**. For each product lifecycle state, set the **Is active for planning** option to *Yes* if products that have that state should be included during master planning. When the option is set to *No*, the associated products and variants will be excluded from all master planning and all calculations at the bill of materials (BOM) level.

Released products and variants where the **Product lifecycle state** field is left blank are treated as though they have a product lifecycle state where the **Is active for planning** option is set to *Yes*. In other words, they will be included during master planning.

> [!NOTE]
> To help avoid unnecessary supply suggestions, we strongly recommend that you associate all obsolete released products and variants with a product lifecycle state where the **Is active for planning** option is set to *No*. This approach is especially important when you work with product configuration variants that aren't reusable, because it will help prevent waste.

## Related resources

For more information about product lifecycle states, see [Product lifecycle state overview](../../pim/product-lifecycle.md).

For detailed information that includes steps for using product lifecycle states to exclude products from master planning and BOM-level calculations, see [Create a product lifecycle state to exclude products from Master planning](../../pim/tasks/exclude-products-master-planning.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]