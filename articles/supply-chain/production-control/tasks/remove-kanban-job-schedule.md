--- 
title: Remove a kanban job from the schedule
description: Learn about removing a planned process kanban job from the schedule by reverting the job status to Not planned, including a step-by-step process.
author: johanhoffmann
ms.author: johanho
ms.topic: how-to
ms.date: 08/29/2018
ms.custom:
ms.reviewer: kamaybac   
audience: Application User 
ms.search.form: KanbanJobSchedulingListPage, SysLookupMultiSelectGrid, KanbanJobStatusUpdate
---

# Remove a kanban job from the schedule

[!include [banner](../../includes/banner.md)]

This procedure focuses on removing a planned process kanban job from the schedule by reverting the job status to Not planned. The demo data company used to create this procedure is USMF. This procedure is intended for the shop floor supervisor or production planner.


## Find a planned kanban job
1. Go to Production control > Kanban > Kanban job scheduling.
2. In the Work cell field, click the drop-down button to open the lookup.
3. In the list, click the link in the selected row.
    * Select work cell 1250.  
4. Click Select.
5. In the Display job status field, select 'Scheduled'.

## Remove the planned kanban job from the schedule
1. In the list, find and select the desired record.
    * Select a job that has the Planned status, for example, a job from December 19, 2012.  
2. On the Action Pane, click Plan.
3. Click Revert job status.
4. Click OK.
    * This will revert the current job status from 'Planned' to 'Not planned' and remove it from the process board.   



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]