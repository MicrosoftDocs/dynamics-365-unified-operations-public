---
# required metadata

title: Master planning home page
description: Master planning allows companies to determine and balance the future need for raw materials and capacity to meet company goals. 
author: ShylaThompson
manager: AnnBe
ms.date: 12/03/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: roxanad
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

[!include [banner](../includes/preview-banner.md)]

# Plan filters

When Planning Optimization is used it is possible to apply filters to a plan. The plan filter will always be applied during master planning run.

The plan filter is useful when you want to limit a specific plan to a specific group of items and ensure that no other items are included as part of the resulting master planning.

If a plan filter is applied, and another filter is applied during the master planning run (runtime filter), only the intersection of the two filters will be included in the planning run.

### Example:

Plan filter is setup to include item A,B and C

4 master planning runs are then executed for the same plan, but with different runtime filters:

1. Runtime filter includes item D: No items are planned, as there is no intersection between the plan and runtime filter.
2. Runtime filter includes item A and D: Only item A is included in the planning run, as D is not part of the plan filer.
3. Runtime filter includes item B: Only item B is included in the planning run, previous planning output for item A are kept.
4. Runtime filter includes all items (Blank filter): Item A, B and C are included in the planning run, and previous planning output for item A and B will be overwritten.

**Note:** You should avoid plan filter on the plan selected as the dynamics plan, as it would limit the dynamic plan functionality to the filtered items. E.g. updating Net requirements for an item that is not part of the plan filter will not generate any result.
