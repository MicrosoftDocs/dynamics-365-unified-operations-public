---
title: Run planning for a subset of items
description: This article explains how to run planning for a subset of items by using plan filters and runtime filters. 
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: ReqCreatePlanWorkspace, ReqPlanSched
ms.topic: how-to
ms.date: 01/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Run planning for a subset of items

[!include [banner](../../includes/banner.md)]

Master planning lets you set up filters to limit the set of items that are included in a planning run, so that not all items are planned. 

You can use two types of filters to limit the set of items that is planned:

- *Plan filters*, which are set up on the master plan itself
- *Runtime filters*, where you use options in the **Planning Optimization** run dialog box to select the items and bill of materials (BOM) levels to include in the run

## Apply a plan filter

Plan filters are useful when you want to limit a plan to a specific group of items and ensure that no other items are included as part of the resulting master planning. When a plan filter is defined, it's always applied during a master planning run that uses the plan.

> [!IMPORTANT]
> Plan filters are available only in systems where [Planning Optimization is enabled](get-started.md).

Follow these steps to set up a plan filter.

1. Go to **Master planning \> Setup \> Plans \> Master plans**.
1. Select a plan in the list pane, or create a new one.
1. On the Action Pane, select **Plan filter**.
1. A standard query editor dialog box appears. There, you can enter settings to limit the set of products that are included when the current plan runs. These settings define the plan filter.
1. When you've finished setting up your filter, select **OK**.

> [!NOTE]
> If you set up a plan filter on the plan that is selected as the **Current dynamic master plan** on the **Master planning parameters** page, that filter will be applied each time that the dynamic plan runs. For example, if the net requirements are updated for an item that isn't part of the plan filter, no result will be generated.

## Apply a runtime filter and set the BOM levels to include

You set up the runtime filter for a job from the **Planning Optimization** run dialog box. The runtime filter applies only to the job that you start or schedule from the dialog box. If you both a plan filter and a runtime filter are set up, intersection logic is used to combine them. (See the example later in this article.)

You also use the **Planning Optimization** run dialog box to control the number of levels of BOM components and subcomponents that are included for manufactured items that pass the combined filters.

For a recurring job, the runtime filter and BOM levels that you define when you set up the job are applied each time that it runs.

Follow these steps to set up the runtime filter and BOM levels for a master planning batch job.

1. Go to **Master planning \> Master planning \> Run**.
1. In the **Planning Optimization** dialog box, on the **Parameters** FastTab, set the following settings fields:

    - **Master plan** – Select the master plan to run.
    - **Track processing time** – Select whether you want to record the processing time that is required to complete each task.
    - **Number of threads** – Enter the number of child threads to use to parallelize and help speed up master planning. Numbers above 0 (zero) are allowed only when you use batch processing to run the job.
    - **Comment** – Add a comment to describe the purpose of the job.

1. On the **Records to include** FastTab, set the following fields:

    - **Filter** – Select this link to open a standard query editor dialog box where you can enter settings to limit the set of products that are included in the current planning job. These settings define the runtime filter.
    - **Include all BOM levels** – For manufactured items that have a BOM, it's often convenient to plan all BOM components together with the main item, to ensure that all the required components are available when production begins. Set this option to *Yes* to include all BOM levels for items that pass both the runtime filter and the plan filter. Set it to *No* to limit the number of BOM levels that are included. Then use the **BOM levels to include** field to specify the maximum number of BOM levels to include.
    - **BOM levels to include** – If **Include all BOM levels** is set to *No*, use this field to specify the number of BOM levels to include. Here are some examples:

        - Set this field to *0* (zero) to ignore all BOM components.
        - Set this field to *1* to include supply for BOM components.
        - Set this field to *2* to include supply for BOM components and their derived BOM components.

1. On the **Run in the background** FastTab, set recurrence and other batch options in the usual way. The fields work just as they do for other types of [background jobs](../../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Microsoft Dynamics 365 Supply Chain Management.

> [!NOTE]
> The following limitations apply when you use a runtime filter with BOM levels:
>
> - If you run auto-firming or another post-processing job using [the current extensibility point](/dynamics365/supply-chain/master-planning/planning-optimization/extensibility), then the system will only apply the auto-firming and other actions to the items specified directly on the filter (not to the subcomponents).
> - Delays from subcomponents are not propagated to their respective parent items.
> - The requirement date of a subcomponent may fall on a date closed by the calendar of the subcomponent. To update the date to an open date on the subcomponent calendar, you must make a full or filtered run that includes the subcomponent directly on the filter.
>
> If any of these issues are critical for you, then add the relevant subcomponents to the filter manually.

## Combine plan filters and runtime filters

If you apply both a plan filter and a runtime filter during a master planning run, only the intersection of the two filters will be included in the run.

To see how the plan and runtime filters are combined, consider this example. You have a plan where a plan filter is set up to include items A, B, and C. You then run master planning run several times. Each run uses the same plan but a different runtime filter. The results are as follows:

- **Run 1: The runtime filter includes item D** – No items are planned, because there is no intersection between the plan filter and the runtime filter.
- **Run 2: The runtime filter includes items A and D** – Only item A is included, because item D isn't part of the plan filter.
- **Run 3: The runtime filter includes item B** – Only item B is included, and the previous planning output for item A is kept.
- **Run 4: The runtime filter includes all items (blank filter)** – Items A, B, and C are included, and the previous planning output for items A and B is overwritten.

The system will also include all the relevant BOM components and subcomponents for the manufactured products that are found by the combined filters, as specified by the BOM level settings that you entered in the **Planning Optimization** run dialog box when you set up the job.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
