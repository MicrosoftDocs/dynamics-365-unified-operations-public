--- 
title: Schedule a production order with operations and job scheduling
description: Learn about scheduling a production order with operations scheduling and job scheduling, including a step-by-step process for creating production orders. 
author: johanhoffmann
ms.author: johanho
ms.topic: how-to
ms.date: 08/19/2019
ms.custom:
ms.reviewer: kamaybac   
ms.search.form: ProdTableListPage, ProdTableCreate, InventItemIdLookupPurchase, ProdSchedule, ProdTable, ProdRouteJob
---

# Schedule a production order with operations and job scheduling

[!include [banner](../../includes/banner.md)]

This article focuses on scheduling a production order with operations scheduling and job scheduling. No jobs are created with operations scheduling whereas jobs are created with job scheduling. The demo data company used to create this task is USMF. This procedure is intended for the production manager, production planner, or shop floor supervisor working in a discrete manufacturing environment.


## Create a production order
1. Go to **Production control > Production orders > All production orders**.
2. Select **New production order**.
3. In the **Item number** field, enter or select a value. Select Item number **D0001**.  
4. Select **Create**.

## Schedule operations for the production order
1. Mark the newly created row.      
2. On the Action Pane, select **Schedule**.
3. Select **Schedule operations**.
4. In the **Scheduling direction** field, select **Forward from scheduling date**.
5. In the **Scheduling date** field, enter a date. Select a future date, for example, today plus one week. With the selected Scheduling direction, the production order will be scheduled forward from this date.  
6. Select **OK**.
7. In the list, mark the selected row. Note that the status is changed to **Scheduled**. 
8. Select **All jobs**. Note that no jobs are created with operations scheduling.  
9. Close the page.

## Schedule jobs for the production order
1. On the Action Pane, select **Schedule**.
2. Select **Schedule jobs**.
3. In the **Scheduling direction** field, select **Forward from scheduling date**.
4. In the **Scheduling date** field, enter a date. Select a date in the future, for example, today plus one week. With the selected Scheduling direction, the production order will be scheduled forward from this date.  
5. Select **OK**.
6. On the Action Pane, select **Production order**.
7. Select **All jobs**. Note that based on the active route, 5 jobs are created with job scheduling.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]