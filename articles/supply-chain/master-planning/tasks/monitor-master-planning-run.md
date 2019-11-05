--- 
# required metadata 
 
title: Monitor a master planning run
description: The production planner wants to see if a master planning run is in progress. 
author: josaw1
manager: AnnBe 
ms.date: 11/04/2019
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, ReqCreatePlanWorkspace, ReqTransPlanCard, SysQueryForm, InventItemIdLookupSimple, ReqLog, ReqProcessTaskTrace   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---

# Monitor a master planning run

[!include [banner](../../includes/banner.md)]
[!include [banner](../../includes/preview-banner.md)]


## Gantt chart to visualize master planning progress

From **View master planning progress,** it is possible to view details from historical master planning runs presented as a Gantt chart. This is useful to understand the time spend on the various phases of master planning. For a current active planning job, **View master planning progress** can be used to track progress and view the estimated remaining time.

### Enable and use master plan progress visualization

To use this functionality, do the following.

1. Go to the **Feature management** workspace.
1. Select **Master planning progress visualization** in the list. If the option is not shown under **New**, select **Not enabled** or **All**.
1. Click **Enable now**, or click **Schedule** and pick a time to enable the feature.


To view historical planning jobs, do the following.

- To view master plans, go to **Master planning > Setup > Plans > Master plans > History > Inquiries > View progress**.
- To view the master planning workspace, go to **Master planning > Workspaces > Master planning tile: History > Inquiries > View progress**.

To view active planning jobs, go to **Master planning > Workspaces > Unfinished planning process > Inquiries > View progress**, or **Master planning > Workspaces > Master planning tile: View progress > Inquiries > View progress**. You can only view active jobs when a planning job is processing.


### Analyze a master planning job

In the Gantt chart, each of the following planning processes can be expanded to show additional details about the time spend.

- Initializing
- Deleting and inserting data
- Coverage planning
- Delays
- Action messages
- Finalization
- Auto-firming

This tool is useful if you want to view the impact of having action messages enabled.

#### Navigating in a Gantt chart

- To expand the selected group and show the details, click the plus sign **(+)** in the tree view.
- To collapse the selected group, click the minus sign **(-)** in the tree view.
- Keyboard navigation is possible using the arrow keys. Use the up and down arrows to navigate rows. Use the right and left arrows to expand and collapse groups.
- To open or close all levels in the Gantt chart, click **Expand all** or **Collapse all**.
- To see the related process time, hover over a task (lowest level in the Gantt).

#### Show additional master planning run

By selecting a master planning job in the drop-down menu, you can view an additional master planning run in the Gantt chart and compare the two jobs.

#### BOM-level display

BOM levels are displayed differently for coverage planning, delays, and firming.

- Coverage planning: BOM levels are shown as expected. They are calculated top down. For example, BOM level 0, 1, 2.
- Delays: Bom levels are shown as coverage planning BOM level times -1 (negative). For example, BOM level  -2, -1, 0.
- Action message: BOM levels are shown as expected. They are calculated top down. For example, BOM level 0, 1, 2.
- Auto-firming: BOM levels are shown as 999 minus coverage planning BOM level. For example, BOM level 999, 998, 997.

| Bom level example | End item | Sub component | Raw material |
| --- | --- | --- | --- |
| Coverage planning BOM level shown | 0 | 1 | 2 |
| Delays BOM level shown | 0 | -1 | -2 |
| Action message BOM level shown | 0 | 1 | 2 |
| Auto-firming BOM level shown | 999 | 998 | 997 |

#### Visualize progress

If you view a master planning job that is currently running, progress is shown with colors in the Gantt. The following colors apply to the blue theme, they will be different for other color themes.

- Dark blue: completed planning tasks.
- Orange: current task in progress.
- Light blue: estimate for remaining tasks.

The color is only indicated on the lowest level in the Gantt chart. Use **Expand all** to view all tasks in the master planning job. The estimate of remaining tasks is done based on historical master planning jobs.

## Run master planning with track processing time enabled

1. Click **Master planning** on the default dashboard.  
1. In the **Plan field**, enter or select a value.
1. Click **Run**.
1. Select **Yes** in the **Track processing time field**.
1. In the **Number of threads** field, enter a number.
1. Expand the **Records to include** section.
1. Click **Filter**.
1. In the list, mark the row where field = item number.  
1. In the **Criteria** field, enter a value.
1. Click **OK**.
