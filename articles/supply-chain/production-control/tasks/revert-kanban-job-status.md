--- 
# required metadata 
 
title: Revert kanban job status
description: This procedure focuses on reverting an incorrect kanban job status. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: KanbanBoardWorkCell, KanbanJobStatusUpdate   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: johanho
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Revert kanban job status

[!include [banner](../../includes/banner.md)]

This procedure focuses on reverting an incorrect kanban job status. This is useful in case the machine operator updates the wrong job, or sets the wrong status by mistake. In this procedure, a kanban job is registered as prepared by mistake, and the status is reverted. The demo data company used to create this procedure is USMF. This procedure is intended for the shop supervisor or machine operator working in a lean manufacturing company.


## Open process board for the work cell
1. Go to Kanban board for process jobs.
2. In the Work cell field, enter or select a value.
    * Select work cell 1260.  

## Prepare kanban job
1. Click Prepare.
    * If you can't click Prepare because it is grayed out, make sure that the selected kanban job has status Planned, which is indicated by the empty kanban icon. If Prepare fails, make sure that all materials in the Picking list are available.  
2. In the list, select the prepared job.
    * Select the first job that you have just prepared.  
    * Notice that the jobs status is prepared, which is indicated with a triangle inside the kanban icon.  

## Revert the status of the prepared kanban job
1. In the list, mark the selected row.
    * Select the first job that was prepared.  
2. On the Action Pane, click Manufacture.
3. Click Revert status.
    * You can use an alternative kanban rule when the following conditions are true:  - The replenishment strategy is the same for both rules.  - The version of the production flow is the same for both rules.  - The product that is supplied is the same for both rules.  - Any downstream activities that are configured for the last activity of the kanban rules must be the same for both rules.  - The same supplied inventory dimensions must be configured for both rules.  - The status of the handling unit must be Not assigned.  - The configuration for event kanbans must be the same.  
    * Ensure that the new status is Planned.  
4. Click OK.
5. In the list, unmark the selected row.
    * Select the same job.  
    * Notice that the job status for the kanban job is reverted to Planned, which is indicated by an empty kanban icon.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]