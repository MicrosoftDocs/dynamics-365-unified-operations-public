--- 
# required metadata 
 
title: Move scheduled kanban jobs
description: This procedure focuses on moving planned process kanban jobs to a different period. 
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
# Move scheduled kanban jobs

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure focuses on moving planned process kanban jobs to a different period. The demo data company used to create this procedure is USMF. This procedure is intended for the shop floor supervisor or production planner working with kanbans.


## Select scheduled kanban jobs
1. Gå til Produktionsstyring > Kanban > Tidsplanlægning af kanban-job.
2. !MtCMR!In the Work cell field, click the drop-down button to open the lookup. áçêìõý !
3. Markér den valgte række på listen.
    * Select work cell 1250.  
4. Klik på Select.
5. Vælg 'Planlagt' i feltet Display job status.
    * This filters the job list to display only the scheduled kanban jobs.  

## Move kanban jobs to a different period
1. Find og vælg den ønskede post på listen.
    * Select a job that has the Planned job status, for example, a job scheduled on December 20, 2012  in the Planned period field. Then move the job to the previous period.  
2. Klik på Previous period.
3. Klik på End.
    * This will move the job to the end of the job list as the last job in the previous period.  
4. Find og vælg den ønskede post på listen.
    * Select a job that has the Planned job status, for example, a job scheduled on December 18, 2012 in the Planned period field. Then move the job to the next period.  
5. Klik på Next period.
6. Klik på Start.
    * This will move the job to the start of the job list as the first job in the previous period.  

## Task: Move a job within a period
1. Find og vælg den ønskede post på listen.
    * Select a job that has the Planned job status, for example, the second job scheduled on December 19, 2012 in the Planned period field. Then move the job within the planned period.  
2. Klik på Forward.
    * Notice that the job is moved one line down on the list.  
3. Klik på Backward.
    * Notice that the job is moved one line up on the list.  

