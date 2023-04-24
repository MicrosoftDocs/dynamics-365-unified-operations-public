--- 
# required metadata 
 
title: Move scheduled kanban jobs
description: This procedure focuses on moving planned process kanban jobs to a different period. 
author: johanhoffmann
ms.date: 11/07/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: KanbanJobSchedulingListPage   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: johanho
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---

# Move scheduled kanban jobs

[!include [banner](../../includes/banner.md)]

This procedure focuses on moving planned process kanban jobs to a different period. The demo data company used to create this procedure is USMF. This procedure is intended for the shop floor supervisor or production planner working with kanbans.

## Select scheduled kanban jobs. 

1. Go to **Production control > Kanban > Kanban job scheduling**. 

2. In the **Work cell** field, click the drop-down button to open the lookup. 

3. In the list, mark the selected row. 
   - Select work cell 1250. 
4. Click **Select**. 

5. In the **Display job status** field, select **Scheduled**. This filters the job list to display only the scheduled kanban jobs. 

## Move kanban jobs to a different period. 

1. In the list, find and select the desired record. Select a job that has the **Planned job** status, for example, a job scheduled on December 20, 2012 in the **Planned period** field. Then move the job to the previous period. 

2. Click **Previous period**. 

3. Click **End** to move the job to the end of the job list as the last job in the previous period. 

4. In the list, find and select the desired record. Select a job that has the **Planned job** status, for example, a job scheduled on December 18, 2012 in the **Planned period** field. Then move the job to the next period. 

5. Click **Next period**. 

6. Click **Start** to move the job to the start of the job list as the first job in the previous period. 

## Move a job within a period. 

1. In the list, find and select the desired record. Select a job that has the Planned job status, for example, the second job scheduled on December 19, 2012 in the **Planned period** field. Then move the job within the planned period. 

2. Click **Forward**. Notice that the job is moved one line down on the list. 

3. Click **Backward**. Notice that the job is moved one line up on the list.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]