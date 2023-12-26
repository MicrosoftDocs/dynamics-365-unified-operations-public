---
# required metadata

title: Kanban job scheduling for lean manufacturing
description: This article provides information about visual control over kanban job scheduling and various ways to schedule kanban jobs.  
author: johanhoffmann
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: KanbanBoardScheduleJobForward, KanbanBoardShowJobs, KanbanJobSchedulingListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: fe3b4822-6140-4b02-bebb-1fc17be2bce8
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: johanho
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Kanban job scheduling for lean manufacturing

[!include [banner](../includes/banner.md)]

This article provides information about visual control over kanban job scheduling and various ways to schedule kanban jobs.  

The **Kanban job scheduling** page provides visual control over the schedules of lean manufacturing work cells. It gives an overview of all kanban jobs and provides multiple filtering capabilities. From this page, you can move to all other pages that are related to kanban configuration and execution.

## Automatic scheduling of kanban jobs
Scheduling can be triggered automatically if you set the **Automatic planning quantity** parameter on the kanban rule. If you set **Automatic planning quantity** to **1**, each kanban job is planned immediately when it's created. The result is a series of first pull, first serve operations. If you set **Automatic planning quantity** to a value that is more than 1, kanban jobs are grouped before they are planned. 

This concept enables kanban sizes to be reduced below the actual economic batch sizes. For example, the economic batch size for a specific item (or item family) is 30. Instead of creating kanbans that use the product quantity, 30, you can configure the kanban rule so that it has a product quantity of 10 and an **Automatic planning quantity** value of **3**. Although automatic planning schedules the kanban jobs for the work cell only when three unplanned jobs exist, it's fully transparent to the planner and the shop floor supervisor that two unplanned jobs might be awaiting execution. The planner or shop floor manager can then take those two jobs into production by manually planning them or creating additional kanbans.

## Manual scheduling
For manual scheduling, Microsoft Dynamics AX 2012 introduced the kanban scheduling board. Manual scheduling can be combined with automatic scheduling. The kanban scheduling board lets you plan and unplan jobs, moved them in sequence, or move them from period to period. Jobs that are based on a kanban rule where the **Automatic planning** value is more than **0** can be manually unplanned. However, these jobs will be replanned when the next automatic planning event occurs (that is, when a new kanban is created). The following options are available for manual scheduling:

-   **Schedule** schedules the selected jobs according to their due date. (This option resembles automatic planning.)
-   **Schedule forward from date** tries to schedule the selected jobs according to their due date but constrains the result by using the specified earliest start date.
-   **Backward** moves the selected scheduled jobs back in the sequence within the period.
-   **Forward** moves the selected scheduled jobs forward in the sequence with the period.
-   **Previous period** moves the selected scheduled jobs to the start or end of the previous period.
-   **Next period** moves the selected scheduled jobs to the start or end of the next period.
-   **Plan** &gt; **Revert job status** lets you unschedule a scheduled job.

## Lean scheduling groups
Each color represents a lean scheduling group. Lean scheduling groups can be freely defined as generic groups or as groups that belong to a single work cell. Items and dimensions can be freely assigned to the scheduling groups. For example, in a Painting cell, a schedule group can represent a color of the product. In work that is driven by specific tooling requirements, items might be grouped by tool requirement, and a packaging work cell might group items by packaging template. The use of colors for lean scheduling groups is optional but recommended. It improves visibility into the status of the plan. For example, it's very easy to see which colors are produced on which day, and you can tell at a glance how this work can be optimized.

## Work cell capacity and period capacity
The capacity of a lean work cell is always concurrent capacity. In other words, multiple jobs can be active in a work cell at the same time. The capacity can be tracked in two modes: throughput and hours.

### Throughput

The capacity of a work cell is defined by the average throughput quantity of a reference period (standard workday, week, or month). The actual capacity per day or week is then calculated based on the working times of the calendar that is assigned to the work cell. The capacity that is loaded by job is the quantity of the job, adjusted by the throughput ratio of the item in the work cell.

### Hours

The available capacity by day or week is defined by the calendar that is assigned to the work cell. The capacity that is loaded by job is the cycle time of the activity, adjusted by the quantity (default activity quantity versus actual job quantity) and the throughput ratio of the item in the work cell.

#### Period capacity FactBox

The **Kanban job scheduling** list page contains a FactBox that shows the available and booked period capacity for the selected work cell. Depending on the selected schedule periods in the production flow model, the periods show days or weeks.

## Additional resources





[!INCLUDE[footer-include](../../includes/footer-banner.md)]