--- 
# required metadata 
 
title: Remove a kanban job from the schedule
description: This procedure focuses on removing a planned process kanban job from the schedule by reverting the job status to Not planned. 
author: ChristianRytt
manager: AnnBe 
ms.date: 11/11/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: yuyus
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: crytt
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Remove a kanban job from the schedule

[!include[task guide banner](../../includes/task-guide-banner.md)]

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

