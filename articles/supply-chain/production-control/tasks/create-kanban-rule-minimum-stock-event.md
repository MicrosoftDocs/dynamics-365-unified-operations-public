--- 
# required metadata 
 
title: Create a kanban rule using a minimum stock event
description: This procedure focuses on the setup needed to create a kanban rule using a minimum stock event to ensure that a specific product is always available at a specific location. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: KanbanRules, LeanProductionFlowActivityLookup, InventItemIdLookupSimple, EcoResProductInformationDialog, EcoResProductDetailsExtended, ReqItemTable, InventLocationIdLookup   
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
# Create a kanban rule using a minimum stock event

[!include [banner](../../includes/banner.md)]

This procedure focuses on the setup needed to create a kanban rule using a minimum stock event to ensure that a specific product is always available at a specific location. A kanban rule is created to transfer material to the location when the inventory level drops below 200 pieces. By running the Pegging event processing, the needed kanbans are created. The demo data company used to create this task is USMF. This task is intended for the process engineer or the value stream manager, as they prepare production of a new or modified product in a lean environment.


## Create a new kanban rule
1. Go to Product information management > Lean manufacturing > Kanban rules.
2. Click New.
3. In the Type field, select 'Withdrawal'.
    * This type is used to create transfer kanbans.  
4. In the Replenishment strategy field, select 'Event'.
    * The Event strategy is used to create the transfer kanbans based on an event. Later in the procedure, you will trigger transfer kanbans by using stock replenishment.  
5. In the First plan activity field, enter or select a value.
    * Enter or select ReplenishSpeakerComponents. This transfer activity has receipt (output) warehouse and location 12, which means that materials will be moved to location 12 in warehouse 12.  
6. Expand the Details section.
7. In the Product field, enter or select a value.
    * Select M0007.  
8. Expand the Events section.
9. In the Stock replenishment event field, select 'Batch'.
    * This creates kanbans to fulfill material needs at the related location during Pegging event processing.  

## Set the minimum quantity for the item
1. Click to follow the link in the Product field.
2. Click to follow the link in the Item number field.
3. Expand the Product image FactBox.
4. On the Action Pane, click Plan.
5. Click Item coverage.
6. Click New.
7. In the list, mark the selected row.
8. In the Warehouse field, enter or select a value.
    * Set Warehouse to 12.  
9. Set Minimum to '200'.

## Run the batch event creation job
1. Go to Production control > Periodic tasks > Kanban job batch processing > Pegging event processing.
2. Click OK.
3. Go to Product information management > Lean manufacturing > Kanban rules.
4. In the list, click the link in the selected row.
    * Select the kanban rule that you created earlier.  
5. Expand the Kanbans section.
    * Notice that a kanban was created to transfer the needed material to warehouse 12.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]