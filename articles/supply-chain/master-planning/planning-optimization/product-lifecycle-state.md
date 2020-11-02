---
# required metadata

title: Exclude products with product lifecycle state
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
# Exclude products with product lifecycle state

[!include [banner](../../includes/banner.md)]

The **Product lifecycle state** can be used to control the released products or released product variants that are included during master planning. 
The user defined product lifecycle state has a control **Is active for planning**. By default, this is set to **Yes** for all created product lifecycle states, but it can be changed to **No**. When set to **No**, the associated released products or released product variants are:

- Excluded from master planning.
- Excluded from BOM-level calculation.

When **Product lifecycle state** is left blank the released product or released product variant is considered **Is active for planning** meaning that it will be covered during master planning.

> [!NOTE]
> To avoid unnecessary supply suggestions, it is highly recommended to associate all obsolete released products, and product variants, with a product lifecycle state that is deactivated for master planning. This is especially important when working with non-reusable product configuration variants, to avoid waist.

## Related resources

For more information related to product life cycle state, see [Product lifecycle state overview]( https://docs.microsoft.com/en-us/dynamics365/supply-chain/pim/product-lifecycle)

For detailed information with steps for how to use product lifecycle state to exclude products from master planning and BOM-level calculation, see [Create a product lifecycle state to exclude products from Master planning](https://docs.microsoft.com/en-us/dynamics365/supply-chain/pim/tasks/product-lifecycle-state-released-product)
