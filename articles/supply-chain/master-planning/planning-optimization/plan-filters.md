---
title: Run planning for a subset of items
description: This article explains how to run planning for a subset of items (plan filter and filtered runs). 
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: ReqCreatePlanWorkspace, ReqPlanSched
ms.topic: how-to
ms.date: 10/14/2022
ms.custom: bap-template
---

# Run planning for a subset of items

[!include [banner](../../includes/banner.md)]

With Planning Optimization, you can set up various filters to limit the set of items to include in a planning run so that not all items are planned. There are two ways to limit the set of items that are planned:

- *Plan filters*, which are set up on the master plan itself.
- *Runtime filters*, where you use options in the **Planning Optimization** run dialog to select items and BOM levels to include in the run.

## Apply a plan filter

Plan filters are useful when you want to limit a plan to a specific group of items and make sure that no other items are included as part of the resulting master planning. When defined, the plan filter is always applied during a master planning run that uses that plan.

> [!IMPORTANT]
> Plan filters are only available on systems where [Planning Optimization is enabled](get-started.md).

Follow these steps to set up a plan filter:

1. Go to **Master planning \> Setup \> Plans \> Master plans**.
1. Select a plan on the list pane (or create a new on).
1. On the Action Pane, select **Plan filter**.
1. The standard query editor dialog opens, where you can make settings that will limit the set of products to include when running the current plan. This is the *plan filter* mentioned elsewhere in this topic.
1. Select OK when you are done setting up your filters.

> [!NOTE]
> If you set a plan filter on the plan that is selected as the **Current dynamic master plan** on the **Master planning parameters** page, then that filter will apply each time the dynamic plan runs. For example, if the net requirements are updated for an item that isn't part of the plan filter, no result will be generated.

## Apply a runtime filter and set BOM levels to include

You set up the *runtime filter* for a job from the **Planning Optimization** run dialog. The runtime filter applies just to the job that you launch or schedule from the dialog and is combined with the plan filter using intersection logic (see examples later in this article). You also use the **Planning Optimization** run dialog to control the number levels of BOM components and subcomponents to include for manufactured items that pass the combined filters. For recurring jobs, the runtime filter and BOM levels defined when you set up the job are applied each time it runs.

Use the following procedure to set up the runtime filter and BOM levels for a master planning batch job.

1. Go to **Master planning \> Master planning \> Run**.
1. The **Planning Optimization** dialog opens.
1. Expand the **Parameters** FastTab and make the following settings:
    - **Master plan** – Select the master plan you want to run.
    - **Track processing time** – Choose wether to record the processing time required to complete each task.
    - **Number of threads** – Enter the number of child threads to use to parallelize and speed up master planning. Numbers greater than 0 are only allowed when running with batch processing.
    - **Comment** – Add a comment to describe the purpose of this job.
1. Expand the **Records to include** FastTab and make the following settings:
    - **Filter** – Select this link to open the standard query editor, where you can make settings that will limit the set of products to include in the current planning job. This is the *runtime filter* mentioned elsewhere in this topic.
    - **Include all BOM levels** – For manufactured items that have a bill of material (BOM), it's often convenient to plan all BOM components together with the main item to ensure that all the required components are available when production begins. Set this to *Yes* to include all BOM levels for items that pass both the runtime filter and plan filter. Set this to *No* to limit the number of BOM levels to include and then use the **BOM levels to include** setting to specify the maximum number of BOM levels to include.
    - **BOM levels to include** – When **Include all BOM levels** is set to *No*, use this setting to establish the number of BOM levels to include. For example:
        - Set this field to zero to ignore all BOM components.
        - Set this field to one to include supply for BOM components.
        - Set this field to two to include supply for BOM components and their derived BOM components.
1. Expand the **Run in the background** FastTab and set recurrence and other batch options as usual. The fields work just as they do for other types of [background jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.

## Combine plan filters and runtime filters

If you apply both a plan filter and a runtime filter during a master planning run, then only the intersection of the two filters will be included in the run.

To see how the plan and runtime filters combine, consider this example. You have a plan with a plan filter is set up to include items A, B, and C. You then run master planning run several times using the same plan, but with a different runtime filter each time. The results are as follows:

- **Run 1: Runtime filter includes item D** – No items are planned because there is no intersection between the plan filter and the runtime filter.
- **Run 2: Runtime filter includes items A and D** – Only item A is included because item D isn't part of the plan filter.
- **Run 3: Runtime filter includes item B** – Only item B is included and the previous planning output for item A is kept.
- **Run 4: Runtime filter includes all items (blank filter)** – Items A, B, and C are included and the previous planning output for items A and B is overwritten.

The system will also include all the relevant BOM components and subcomponents for the manufactured products found by the combined filters, as specified by the BOM level settings made in the **Planning Optimization** run dialog when you set up the job.

## Related resources

- [Planning Optimization overview](planning-optimization-overview.md)
- [Get started with Planning Optimization](get-started.md)
- [Planning Optimization fit analysis](planning-optimization-fit-analysis.md)
- [View plan history and planning logs](plan-history-logs.md)
- [Cancel a planning job](cancel-planning-job.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
