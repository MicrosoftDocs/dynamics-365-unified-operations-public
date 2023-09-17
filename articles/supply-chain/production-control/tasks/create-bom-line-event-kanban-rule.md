--- 
# required metadata 
 
title: Create a BOM line event kanban rule
description: This task focuses on the setup needed to create an event kanban rule to ensure supply for production BOM lines in a mixed lean and classic production environment. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: KanbanRules, LeanProductionFlowActivityLookup, InventItemIdLookupSimple, ProdTableListPage, ProdTableCreate, InventItemIdLookupPurchase, ProdTable, ProdBOM, ProdParmCostEstimation   
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
# Create a BOM line event kanban rule

[!include [banner](../../includes/banner.md)]

This task focuses on the setup needed to create an event kanban rule to ensure supply for production BOM lines in a mixed lean and classic production environment. The demo data company used to create this task is USMF. This task is intended for the process engineer or the value stream manager, as they prepare production of a new or modified product.


## Create a new kanban rule
1. Go to Production control > Periodic tasks > Kanban quantity calculation > Kanban rules.
2. Click New.
3. In the Type field, select 'Withdrawal'.
    * The Withdrawal type is used to create transfer kanbans.  
4. In the Replenishment strategy field, select 'Event'.
    * The Event strategy is selected to create the transfer of kanbans based on an event. Later in the task guide, we will trigger it by estimating a production order.  
5. In the First plan activity field, enter or select a value.
    * Enter or select ReplenishSpeakerComponents. This transfer activity has receipt (output) warehouse and location 12, which means that material will be moved to location 12 in warehouse 12.  
6. Expand the Details section.
7. In the Product field, enter or select M0001.
8. Expand the Events section.
9. In the BOM line event field, select 'Automatic'.
    * With the BOM line event field set to Automatic, kanban will be created to fulfill material needs for production order BOM lines.  
10. Close the page.

## Create and modify a new production order
1. Go to Production control > Production orders > All production orders.
2. Click New production order.
3. In the Item number field, enter or select a value.
    * Enter or select 'L0001'. We use item L0001 because item M0001 is included in the BOM for item L0001.  
4. Click Create.
5. In the list, click the link in the row for L0001
6. Click BOM.
7. In the list, click the link in the selected row.
8. Click Edit.
9. In the Line type field, select 'Pegged supply'.
    * Pegged supply is selected to trigger the supply creation of a kanban.  
10. Select No in the Resource consumption field.
    * Clearing the check box of Resource consumption lets us change the warehouse.  
11. Expand the Inventory dimensions section.
12. In the Warehouse field, type '12'.
    * Warehouse is set to 12 because this is the output warehouse for the withdrawal activity.  
13. In the Location field, type '12'.
    * Location is set to 12 because this is the output location of the withdrawal activity.  
14. Close the page.
15. Close the page.

## Estimate the production order and view the kanban created
1. Click Estimate.
    * Estimating the production order will trigger the creation of the associated kanban to supply item M0001.  
2. Click OK.
3. Close the page.
4. Close the page.
5. Go to Product information management > Lean manufacturing > Kanban rules.
6. In the list, click the link in the selected row.
    * Select the event kanban rule created for item M0001.  
7. Expand the Kanbans section.
8. In the list, mark the selected row.
    * Notice the kanban created to supply M0001 for the estimated production order.  
    * This is the last step!  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]