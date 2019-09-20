--- 
# required metadata 
 
title: Monitor a master planning run
description: The production planner wants to see if a master planning run is in progress. 
author: ShylaThompson
manager: AnnBe 
ms.date: 08/29/2018
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

[!include [task guide banner](../../includes/task-guide-banner.md)]


## Gantt chart to view master planning progress

From **View master planning progress,** it is possible to view details from historical master planning runs presented as a Gantt chart. This is useful to understand the time spend on the various phases of master planning. For a current active planning job **View master planning progress** can be used to track progress and view the estimated remaining time.

### Get started

To use this feature, you need to enable the following feature flag. Note the feature is available from version 10.0.7.

- Go to **Feature management**
- Select **Master planning progress visualization** in the list (If not shown under **New** select **Not enabled** or **All** )
- Click **Enable now,** r use **Schedule** to pick a time to enable the feature

You can access **View master planning progress** to view both historical planning jobs and active planning jobs.

Historical planning jobs:

- Master plans: Master planning \&gt; Setup \&gt; Plans \&gt; Master plans \&gt; History \&gt; Inquiries \&gt; View progress
- Master planning workspace: Master planning \&gt; Workspaces \&gt; Master planning Tile: History \&gt; Inquiries \&gt; View progress

Active planning jobs (only possible when a planning job is processing):

- Master planning workspace: Master planning \&gt; Workspaces \&gt; Unfinished planning process \&gt; Inquiries \&gt; View progress
- Master planning workspace: Master planning \&gt; Workspaces \&gt; Master planning Tile: View progress \&gt; Inquiries \&gt; View progress

### Analyzing a master planning job

From the Gantt chart each of the following planning processes can be expanded to show additional details about the time spend.

- Initializing
- Deleting and inserting data
- Coverage planning
- Delays
- Action messages
- Finalization
- Auto-firming

This can be a great tool to see the impact of i.e. having **Action messages** enabled

**Navigating in the Gantt chart**

- Click a plus **(+)** sign in the tree view, to expand the selected group and show the details.
- Click a minus **(-)** sign in the tree view to collapse the selected group.
- Keyboard navigation is possible with arrows. Up and down to navigate rows. Right and left to expand and collapse groups.
- **Expand all** and **Collapse all** allows you to open or close all levels in the Gantt chart.
- Hover over a task (lowest level in the Gantt) to see the related process time.

**Show additional master planning run**

By selecting a master planning job in the dropdown, you can view an additional master planning run in the Gantt chart and compare the two.

### Visualize progress

If you view a master planning job that is currently running the progress is shown with colors in the Gantt. The colors listed below apply to the blue theme, they will be different for other color themes.

- Dark blue: Completed planning tasks
- Orange: Current task in progress
- Light blue: Estimate for remaining tasks

The color is only indicated on the lowest level in the Gantt chart. You can use **Expand all** to view all tasks in the master planning job. The estimate of remaining tasks is done based on historical master planning jobs.

## Run master planning with Track processing time enabled

The production planner wants to see if a master planning run is in progress. Use the demo data company USMF to complete this procedure.

1. Click Master planning.
    * You'll find this on the default dashboard.  
2. In the Plan field, enter or select a value.
    * Example: StaticPlan  
3. Click Run.
4. Select Yes in the Track processing time field.
    * If the field is already selected, skip this step.  
5. In the Number of threads field, enter a number.
6. Expand the Records to include section.
7. Click Filter.
8. In the list, mark the selected row.
    * Mark the row where Field = Item number.  
9. In the Criteria field, enter or select a value.
    * Example: T0001  
10. Click OK.
11. Click OK.

## Monitor the master planning run
1. Click History.
2. Click Inquiries.
3. Click Process task duration.
4. In the list, find and select the desired record.
    * For each item you can get an overview of how long it took to complete each planning step.  

