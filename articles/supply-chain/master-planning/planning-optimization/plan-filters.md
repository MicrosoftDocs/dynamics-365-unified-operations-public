---
# required metadata

title: Apply filters to a plan
description: This topic explains how to use filters on a plan with Planning Optimization. 
author: ChristianRytt
manager: AnnBe
ms.date: 10/30/2019
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
ms.author: crytt
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: AX 10.0.5

---

[!include [banner](../../includes/preview-banner.md)]
[!include [banner](../../includes/banner.md)]


# Apply filters to a plan

When Planning Optimization is used, it is possible to apply filters to a plan. The plan filter will always be applied during a master planning run.

A plan filter is useful when you want to limit a plan to a specific group of items and ensure that no other items are included as part of the resulting master planning.

If a plan filter is applied, and a runtime filter is also applied during the master planning run, only the intersection of the two filters will be included in the planning run.

## Example scenario

A plan filter is setup to include item A, B, and C. Master planning runs are then executed for the same plan, but with different runtime filters, as below.

- Runtime filter includes item D: No items are planned, as there is no intersection between the plan filter and runtime filter.
- Runtime filter includes item A and D: Only item A is included in the planning run, as D is not part of the plan filter.
- Runtime filter includes item B: Only item B is included in the planning run, previous planning output for item A is kept.
- Runtime filter includes all items (blank filter): Item A, B, and C are included in the planning run, and previous planning output for item A and B will be overwritten.

> [!NOTE]
> You should avoid plan filter on the plan selected as the dynamics plan, as it would limit the dynamic plan functionality to the filtered items. E.g. updating Net requirements for an item that is not part of the plan filter will not generate any result.
