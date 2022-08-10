---
title: Run planning for a subset of items
description: This article explains how to run planning for a subset of items (plan filter and filtered runs). 
author: t-benebo
ms.date: 08/10/2022
ms.topic: article
ms.search.form: ReqCreatePlanWorkspace
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: AX 10.0.5
---

# Run planning for a subset of items

With Planning Optimization, you can set up various filters to limit the set of items to include in a planning run so that not all items are planned. There are two ways to limit the set of items that are planned:

- Plan filters, which are set up on the master plan itself.
- Runtime filters, where you use runtime options in the Planning Optimization run dialog the select a set of items and BOM levels to include in the run.

<!-- KFM: Do we now have a third way? (Select manufactured items) -->

## Apply a plan filter

[!include [banner](../../includes/banner.md)]

*Plan filters* are useful when you want to limit a plan to a specific group of items and make sure that no other items are included as part of the resulting master planning. When defined, the plan filter is always be applied during a master planning run.

If you apply both a plan filter and a runtime filter during a master planning run, then only the intersection of the two filters will be included in the run.

You access the plan filter from the **Master plans** page when you are using Planning Optimization.

<!-- KFM: How can I set a plan filter? Instructions needed. -->

## Apply a runtime filter

<!-- KFM: How do I set the runtime filter? Instructions needed. -->

## Example of combining plan and runtime filters

To see how the plan and runtime filters combine, consider this example. You have a plan with a plan filter is set up to include items A, B, and C. You then run master planning run several times using the same plan, but with a different runtime filter each time. The results are as follows:

- **Run 1: Runtime filter includes item D** – No items are planned because there is no intersection between the plan filter and the runtime filter.
- **Run 2: Runtime filter includes items A and D** – Only item A is included because item D isn't part of the plan filter.
- **Run 3: Runtime filter includes item B** – Only item B is included and the previous planning output for item A is kept.
- **Run 4: Runtime filter includes all items (blank filter)** – Items A, B, and C are included and the previous planning output for items A and B is overwritten.

> [!NOTE]
> If you set a plan filter on the plan that is selected as the **Current dynamic master plan** on the **Master planning parameters** page, then that filter will apply each time the dynamic plan runs. For example, if the net requirements are updated for an item that isn't part of the plan filter, no result will be generated.

## Run planning for select manufactured items

For manufactured items that have a bill of material (BOM), it's often convenient to plan all BOM components together with the main item to ensure that all the required components are available when production begins.

Use options on the Planning Optimization run dialog <!-- KFM: How do I open this dialog? What is its name? How is this different from the built-in engine run dialog? Does this work only with PO? What are the options called? --> to select which items should be added <!--KFM: Is this referring to the runtime filter? --> and choose whether the BOM components should be included in the plan.

- To include all components, set **Include all BOM levels** to *Yes*.
- To limit the set of components to plan, set **Include all BOM levels** to *No* and then use the **BOM levels to include** setting to specify the maximum number of BOM levels to include (in addition to items included in the filters). For example:
  - Set **BOM levels to include** to zero to ignore all BOM components that are not part of the filter;
  - Set **BOM levels to include** to one to include supply for BOM components
  - Set **BOM levels to include** to two to include supply for BOM components and their derived BOM components.

## Use plan filters in combination with selected manufactured items

When a plan filter has been defined on the plan and a set of items has been added on the Planning Optimization run dialog, Planning Optimization will create supply for the combination of both sets of items. In other words, planning will be done both for the items specified in the plan filter and the items specified in the run filter. <!-- KFM: So, unlike with the runtime filter, the "selected manufacturing items" add to the plan (we have union rather than intersection). Is that right? Can we have a runtime filter too? -->

## Related resources

- [Planning Optimization overview](planning-optimization-overview.md)
- [Get started with Planning Optimization](get-started.md)
- [Planning Optimization fit analysis](planning-optimization-fit-analysis.md)
- [View plan history and planning logs](plan-history-logs.md)
- [Cancel a planning job](cancel-planning-job.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
