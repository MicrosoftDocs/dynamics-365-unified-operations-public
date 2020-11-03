---
# required metadata

title: Exclude products with certain product lifecycle states
description: This topic explains how to exclude products with product lifecycle state when Planning Optimization functionality is used. 
author: ChristianRytt
manager: tfehr
ms.date: 11/02/2020
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
ms.search.validFrom: 2019-11-03
ms.dyn365.ops.version: AX 10.0.12

---
# Exclude products with certain product lifecycle states

[!include [banner](../../includes/banner.md)]
<!-- KFM: We should orient the reader a bit more here. Where are these settings? -->
Use the **Product lifecycle state** to control the released products (or released product variants) that are included during master planning. The user-defined product lifecycle state has a control **Is active for planning**. By default, this is set to *Yes* for all created product lifecycle states, but it can be changed to *No*. When set to *No*, the associated released products (or released product variants) are:

- Excluded from master planning.
- Excluded from BOM-level calculation.

When **Product lifecycle state** is left blank, the released product (or released product variant) is considered **Is active for planning** <!-- KFM: Is this a setting I can see somewhere? -->, which means that it will be covered during master planning.

> [!NOTE]
> To avoid unnecessary supply suggestions, we strongly recommend that you associate all obsolete released products (and product variants) with a product lifecycle state that is deactivated for master planning. To avoid waste, this is especially important when working with non-reusable product configuration variants.

## Related resources

For more information related to product the life cycle state, see [Product lifecycle state overview](../../pim/product-lifecycle.md).

For detailed information with steps for how to use the product lifecycle state to exclude products from master planning and BOM-level calculation, see [Create a product lifecycle state to exclude products from Master planning](../../pim/tasks/exclude-products-master-planning.md).
