---
# required metadata

title: Apply filters to a plan
description: This topic explains how to use filters on a plan when the Planning Optimization functionality is used. 
author: t-benebo
ms.date: 01/08/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: benebotg
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: AX 10.0.5

---
# Apply filters to a plan

[!include [banner](../../includes/banner.md)]

When the Planning Optimization functionality is used, you can apply a filter to a plan. The **Plan filter** will always be applied during a master planning run. A **Plan filter** is useful when you want to limit a plan to a specific group of items and make sure that no other items are included as part of the resulting master planning.

If a **Plan filter** is applied, and a runtime filter is also applied during the master planning run, only the intersection of the two filters is included in the planning run.

The **Plan filter** can be accessed from **Master plans** when Planning Optimization is used.

## Example scenario

A plan filter is set up that includes items A, B, and C. Master planning runs are then run for the same plan, but different runtime filters are applied:

- **Runtime filter that includes item D:** No items are planned, because there is no intersection between the plan filter and the runtime filter.
- **Runtime filter that includes item A and D:** Only item A is included in the planning run, because item D isn't part of the plan filter.
- **Runtime filter that includes item B:** Only item B is included in the planning run, and the previous planning output for item A is kept.
- **Runtime filter that includes all items (blank filter):** Items A, B, and C are included in the planning run, and the previous planning output for items A and B is overwritten.

> [!NOTE]
> If you set a plan filter on the plan that is selected as the **Current dynamic master plan** on the **Master planning parameters** page, then the dynamic master plan functionality will be limited to the filtered items. For example, if the net requirements are updated for an item that isn't part of the plan filter, no result will be generated.

## Related resources

[Planning Optimization overview](planning-optimization-overview.md)

[Get started with Planning Optimization](get-started.md)

[Planning Optimization fit analysis](planning-optimization-fit-analysis.md)

[View plan history and planning logs](plan-history-logs.md)

[Cancel a planning job](cancel-planning-job.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
