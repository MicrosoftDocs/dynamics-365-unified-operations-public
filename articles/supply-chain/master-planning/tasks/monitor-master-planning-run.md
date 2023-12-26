--- 
# required metadata 
 
title: Monitor a master planning run
description: This article explains how the production planner can see whether a master planning run is in progress. 
author: t-benebo
ms.date: 11/04/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, ReqCreatePlanWorkspace, ReqTransPlanCard, SysQueryForm, InventItemIdLookupSimple, ReqLog, ReqProcessTaskTrace
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: benebotg
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---

# Monitor a master planning run

[!include [banner](../../includes/banner.md)]

## Use a Gantt chart to visualize master planning progress

From the **View master planning progress** page, you can view details of historical master planning runs as a Gantt chart. This functionality can help you understand the time that is spent on the various phases of master planning. For a current active planning job, the **View master planning progress** page can be used to track progress and view the estimated remaining time.

### Turn the Master plan progress visualization feature on or off

As of Supply Chain Management version 10.0.21, this feature is turned on by default. As of Supply Chain Management 10.0.25, this feature is mandatory and can't be turned off. If you're running a version older than 10.0.25, then admins can turn this functionality on or off by searching for the *Master planning progress visualization* feature in the [Feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

### Use the Master plan progress visualization feature

The **View master planning progress** page can display both historical planning jobs and active planning jobs. 

To view historical planning jobs, there are two options. 

1. Go to **Master planning \> Setup \> Plans \> Master plans**, and then, on the Action Pane, select **History**. With the desired job selected, select **Inquiries**,  and then select **View progress**
1. Go to **Master planning \> Workspaces \> Master planning**, on the Master planning tile click **History**. With the desired job selected, select **Inquiries**,  and then select **View progress**

To view active planning jobs, there are two options. 
1. Go to **Master planning \> Workspaces \> Master planning**, on the Action Pane, select **Unfinished planning process**. With the desired job selected, select **Inquiries**,  and then select **View progress**.
1. Go to **Master planning \> Workspaces \> Master planning**, on the Master planning tile click **View progress**. With the desired job selected, select **Inquiries**,  and then select **View progress**

Note you can view active jobs only when a planning job is processing.

### Analyze a master planning job

In the Gantt chart, you can expand each of the following planning processes to view additional details about the time that is spent:

- Initializing
- Deleting and inserting data
- Coverage planning
- Delays
- Action messages
- Finalization
- Auto-firming

The Gantt chart is a useful tool if you want to view the impact of using action messages.

#### Navigation in the Gantt chart

- To expand the selected group and show the details, select the plus sign (**+**) in the tree view.
- To collapse the selected group, select the minus sign (**–**) in the tree view.
- You can use your keyboard for navigation. Use the **Up arrow** and **Down arrow** keys to move between rows. Use the **Right arrow** and **Left arrow** keys to expand and collapse groups.
- To open or close all levels in the Gantt chart, select **Expand all** or **Collapse all**.
- To view the related processing time, hover over a task. (Tasks are the lowest level in the Gantt chart.)

#### View an additional master planning run to compare jobs

By selecting a master planning job on field **Show additional master planning run**, you can view an additional master planning run in the Gantt chart and compare the two jobs.

#### BOM-level display

Bill of materials (BOM) levels are shown differently for coverage planning, delays, actions, and firming.

- **Coverage planning** – BOM levels are shown as expected. They are calculated from the top down.

    **Example:** BOM level 0, 1, 2

- **Delays** – BOM levels are shown as the coverage planning BOM levels multiplied by –1. (In other words, they have a negative sign.)

    **Example:** BOM level –2, –1, 0

- **Action message** – BOM levels are shown as expected. They are calculated from the top down.

    **Example:** BOM level 0, 1, 2

- **Auto-firming** – BOM levels are shown as 999 minus the coverage planning BOM level.

    **Example:** BOM level 999, 998, 997

The following table summarizes the behavior.

| BOM level that is shown | End item | Subcomponent | Raw material |
|---|---|---|---|
| Coverage planning | 0 | 1 | 2 |
| Delays | 0 | –1 | –2 |
| Action message | 0 | 1 | 2 |
| Auto-firming | 999 | 998 | 997 |

#### Visualize progress

If you view a master planning job that is currently running, progress is shown through colors in the Gantt chart. The following colors apply to the blue theme. For other color themes, the colors will differ.

- **Dark blue** – Completed planning tasks.
- **Orange** – The task that is currently in progress.
- **Light blue** – The estimate for remaining tasks.

The color is shown only on the lowest level in the Gantt chart. Select **Expand all** to view all tasks in the master planning job. The estimate of remaining tasks is based on historical master planning jobs.

## Run master planning and track processing time

1. On the default dashboard, select **Master planning**.
1. In the **Plan** field, enter or select a value.
1. Select **Run**.
1. Set the **Track processing time** option to **Yes**.
1. In the **Number of threads** field, enter a number.
1. On the **Records to include** FastTab, select **Filter**.
1. In the grid, select the row where the **Field** field is set to **Item number**.
1. In the **Criteria** field, enter a value.
1. Select **OK**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]