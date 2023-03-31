--- 
# required metadata 
 
title: Schedule kanban jobs
description: This procedure focuses on scheduling process kanban jobs for a specific work cell. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: KanbanJobSchedulingListPage, KanbanPeriodCapacityPart, SysLookupMultiSelectGrid, KanbanBoardScheduleJobForward   
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
# Schedule kanban jobs

[!include [banner](../../includes/banner.md)]

This procedure focuses on scheduling process kanban jobs for a specific work cell. The procedure "Prepare a process kanban job when materials are not available" is a prerequisite for creating this procedure. The demo data company used to create this procedure is USMF. This task is intended for the shop floor supervisor and production planner working with kanbans.


## Select kanban jobs for a work cell
1. Go to Production control > Kanban > Kanban job scheduling.
2. Expand the Period capacity fact box
    * Expand the Kanban FactBox.  
3. In the Work cell field, click the drop-down button to open the lookup.
4. In the list, mark the selected row.
    * Select work cell 1250. This will filter the view to display only the jobs for work cell 1250.  
5. In the list, click the link in the selected row.
6. Click Select.

## Schedule a kanban job in the first available period
1. In the list, mark the selected row.
    * Select the first row in the list that has the Not planned status. The dotted icon in the Job status field indicates not planned.  
2. Click Schedule.
    * This will schedule the kanban job in the first available period.  
    * Notice that the kanban job is moved to the end of the list because it has been added to the period starting from today.  
    * If the period starting from today is fully booked, the job will be moved to the first available period.  

## Schedule two kanban jobs for a specific day
1. In the list, select row 1.
    * You should see that the first row has the Not planned status in the Job status field.  
2. In the list, select row 2.
    * You should see that the second row has the Not planned status in the Job status field. Now you have the first two jobs selected.  
3. Click Schedule from date to open the drop dialog.
4. Check or uncheck the Override capacity shortage reaction box.
    * This option allows you to override the default capacity shortage reaction.  
5. In the Capacity shortage reaction field, select 'Add to the requested period'.
    * This option will ensure that the job is added to the requested period, regardless if the work cell might be overloaded.  
6. Click Schedule.
    * Notice that both jobs are added to the desired period.  
    * In the Period capacity section, you can see the load for each period. The Consumption field shows the scheduled consumption in this period. If the scheduled consumption is higher than the available capacity in this period, the overloaded consumption will be selected.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]