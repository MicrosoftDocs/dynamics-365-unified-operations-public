--- 
# required metadata 
 
title: Schedule a production order with operations and job scheduling
description: This procedure focuses on scheduling a production order with operations scheduling and job scheduling. 
author: ChristianRytt
manager: AnnBe 
ms.date: 10/27/2016
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
# Schedule a production order with operations and job scheduling

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure focuses on scheduling a production order with operations scheduling and job scheduling. No jobs are created with operations scheduling whereas jobs are created with job scheduling. The demo data company used to create this task is USMF. This procedure is intended for the production manager, production planner, or shop floor supervisor working in a discrete manufacturing environment.


## Create a production order
1. Go to Production control > Production orders > All production orders.
2. Click New production order.
3. In the Item number field, enter or select a value.
    * Select Item number D0001.  
4. Click Create.

## Schedule operations for the production order
1. In the list, mark the selected row.
    * Select the production order that you have just created. It should be at the top of the list.      
2. On the Action Pane, click Schedule.
3. Click Schedule operations.
4. In the Scheduling direction field, select 'Forward from scheduling date'.
5. In the Scheduling date field, enter a date.
    * Select a future date, for example, today plus one week. With the selected Scheduling direction, the production order will be scheduled forward from this date.  
6. Click OK.
7. In the list, mark the selected row.
    * Note that the status is changed to Scheduled.  
8. In the list, click the link in the selected row.
9. Click All jobs.
    * Note that no jobs are created with operations scheduling.  
10. Close the page.

## Schedule jobs for the production order
1. On the Action Pane, click Schedule.
2. Click Schedule jobs.
3. In the Scheduling direction field, select 'Forward from scheduling date'.
4. In the Scheduling date field, enter a date.
    * Select a date in the future, for example, today plus one week. With the selected Scheduling direction, the production order will be scheduled forward from this date.  
5. Click OK.
6. On the Action Pane, click Production order.
7. Click All jobs.
    * Note that based on the active route, 5 jobs are created with job scheduling.  

