---
# required metadata

title: Run planning for a subset of items
description: This article explains how to run planning for a subset of items (plan filter + filtered runs). 
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
# Run planning for a subset of items

When running Planning Optimization it is possible to plan for a subset of items, so not all items are planned. There are two options to do so. First is by using plan filters, second is when selecting a set of items and BOM levels to include in the Planning Optimization run dialog. 

## Apply filters to a plan

[!include [banner](../../includes/banner.md)]

When the Planning Optimization functionality is used, you can apply a filter to a plan. The **Plan filter** will always be applied during a master planning run. A **Plan filter** is useful when you want to limit a plan to a specific group of items and make sure that no other items are included as part of the resulting master planning.

If a **Plan filter** is applied, and a runtime filter is also applied during the master planning run, only the intersection of the two filters is included in the planning run.

The **Plan filter** can be accessed from **Master plans** when Planning Optimization is used.

### Example scenario

A plan filter is set up that includes items A, B, and C. Master planning runs are then run for the same plan, but different runtime filters are applied:

- **Runtime filter that includes item D:** No items are planned, because there is no intersection between the plan filter and the runtime filter.
- **Runtime filter that includes item A and D:** Only item A is included in the planning run, because item D isn't part of the plan filter.
- **Runtime filter that includes item B:** Only item B is included in the planning run, and the previous planning output for item A is kept.
- **Runtime filter that includes all items (blank filter):** Items A, B, and C are included in the planning run, and the previous planning output for items A and B is overwritten.

> [!NOTE]
> If you set a plan filter on the plan that is selected as the **Current dynamic master plan** on the **Master planning parameters** page, then the dynamic master plan functionality will be limited to the filtered items. For example, if the net requirements are updated for an item that isn't part of the plan filter, no result will be generated.

## Run planning for select manufactured items

For manufactured items with BOM it may be convenient to plan them as well as its components to ensure that all subcomponents are ready to produce the end item. 
For this case, from the Planning Optimization run dialog it is possible to select which items should be added as well as if its components should be included. To include all components, the setting **Include all BOM levels** must be set to Yes. If it is set to No, it is possible to define how many levels should be included in the master planning run in the parameter **BOM levels to include**. 
In this parameter you must specify the maximum number of Bill of material (BOM) levels to include during master planning (in addition to items included in the filter). For example, set this to zero to ignore all BOM components that are not part of the filter; set to one to include supply for BOM components; set to two to include supply for BOM components and their derived BOM components. This setting is only used when “Include all BOM levels” is set to No. 

## Use plan filters in combination with selected manufactured items

When a plan filter has been defined on the plan and a set of items have been added on the Planning Optimization run dialog, Planning optimization will create supply for the combination of both sets of items, in other words, for the items specified in the plan filter and the ones specified in the run filter. 

## Related resources

[Planning Optimization overview](planning-optimization-overview.md)

[Get started with Planning Optimization](get-started.md)

[Planning Optimization fit analysis](planning-optimization-fit-analysis.md)

[View plan history and planning logs](plan-history-logs.md)

[Cancel a planning job](cancel-planning-job.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
