--- 
# required metadata 
 
title: Execute kanban process jobs
description: This procedure focuses on executing kanban process jobs. 
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
# Execute kanban process jobs

[!include [banner](../../includes/banner.md)]

This procedure focuses on executing kanban process jobs. The first job is completed with the expected quantity and has no errors. The second job is completed with errors. The demo data company used to create this procedure is USMF. This procedure is intended for the machine operator.


## Select a kanban job
1. Go to Production control > Kanban > Kanban board for process jobs.
2. In the Work cell field, click the drop-down button to open the lookup.
3. Click the row with resource group 1250. This filters the Jobs list to display only the jobs for work cell 1250.
    * Mark the row that has the Planned job status.  

## Complete a job with expected quantity
1. Expand or collapse the Details section.
    * This section displays important information about card number, item number, quantity ordered, and activity name.  
2. Expand or collapse the Production instructions section.
    * This section displays production instructions for the activity. The instructions can be text, pictures, drawings, and other documents.  
3. Click Start.
    * Select a job that is not completed. Use status icons in the Job status field to view job status.      
4. Click Complete.
    * The job is completed with the expected quality.  

## Complete a job with errors
1. Click Start.
    * When a job is completed, the next job on the list is selected automatically. This is why you don't need to select a job before you click Start.  
2. On the Action Pane, click Manufacture.
3. Click Complete (details).
4. In the list, mark the selected row.
5. In the Error quantity field, enter a number.
6. In the Good quantity field, enter a number.
7. Click OK.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]