--- 
title: Transfer materials with kanban jobs
description: Learn about executing a withdrawal kanban job to transfer materials, including processes for displaying transfer jobs and starting transfer jobs. 
author: johanhoffmann
ms.author: johanho
ms.topic: how-to
ms.date: 08/29/2018
ms.custom:
ms.reviewer: kamaybac  
ms.search.form: KanbanBoardTransferJob 
---

# Transfer materials with kanban jobs

[!include [banner](../../includes/banner.md)]

This procedure focuses on executing a withdrawal kanban job to transfer materials. The demo data company used to create this procedure is USMF. This procedure is intended for the warehouse worker.


## Display transfer jobs
1. Go to Production control > Kanban > Kanban board for transfer jobs.
2. Expand or collapse the Filters section.
    * In the Filters section, you can specify what jobs you want to see by filtering on Production flow, Activity name, From warehouse and location, and To warehouse and location.  
3. In the From warehouse field, type '11'.
4. In the To location field, type '12'.

## Start a transfer job
1. In the list, deselect the selected row - if any.
2. In the list, select row 4.
    * Select the first job with status Not planned. Make sure this is the only job selected.  
3. Click Start.
    * Notice that an icon indicates that the job is started.  

## Select a second transfer job and change quantity
1. In the list, find and select the desired record.
    * You can have multiple jobs selected, but for now select row 5.  
2. In the list, find and select the desired record.
    * Make sure the job in the previous step is the only one selected. Deselect all other jobs.  
3. Note the value in the Job quantity field to reference later
4. Set Job quantity to '30'.
    * Notice the warning! You are not allowed to transfer 30. According to the setup of the kanban rule, you can only transfer the original quantity.  
5. Use the value noted previously in the Job quantity field
    * Set the Job quantity to the previous value.  

## Start the second transfer job
1. Click Start.
    * This will start the transfer of the job in row 5.  

## Complete both transfer jobs
1. In the list, select row 4.
    * Now two transfer jobs are selected on row 4 and row 5.  
2. Click Complete.
    * This will complete the transfer of both jobs.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]