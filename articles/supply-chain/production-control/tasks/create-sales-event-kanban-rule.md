--- 
# required metadata 
 
title: Create a sales event kanban rule
description: This procedure focuses on the setup needed to create a kanban rule that is triggered during sales order creation. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: KanbanRules, LeanProductionFlowActivityLookup, InventItemIdLookupSimple, SalesTableListPage, SalesCreateOrder, SalesTable, LeanPeggingTree   
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
# Create a sales event kanban rule

[!include [banner](../../includes/banner.md)]

This procedure focuses on the setup needed to create a kanban rule that is triggered during sales order creation. The event kanban rule replenishes requirements that originate from sales order lines. The demo data company used to create this procedure is USMF. It is intended for the process engineer or the value stream manager as they prepare production of a new or modified product.




## Create a new kanban rule
1. Go to Kanban rules.
2. Click New.
3. In the Replenishment strategy field, select 'Event'.
    * Selecting Event means that the kanban rule is triggered by an event, for example, creation of a sales order line.   This is applied to areas where each kanban should cover a specific demand.  
4. In the First plan activity field, enter or select a value.
    * Select Final assembly.  
5. Expand the Details section.
6. In the Product field, enter or select a value.
    * Select L0050.  

## Define an event
1. Expand the Events section.
2. In the Sales event field, select 'Automatic'.
    * By selecting the sales event Automatic, this kanban rule will be triggered automatically when a sales line matches the product and receipt location. In this procedure, it is product L0050 on warehouse 13.  
3. Set Minimum event quantity to '50'.
    * With a minimum event quantity of 50, the kanban rule will only be triggered by events with a quantity of 50 or more.  
4. Expand the Production flow section.
    * Notice that the Receipt location is warehouse 13. This means that this kanban rule will be triggered for this location.  
    * In this example, a sales line for product L0050, with a quantity of 50 or more, on warehouse 13, will trigger this kanban rule.  

## Create sales line to trigger event kanban rule
1. Go to All sales orders.
    * A warning is shown when the kanban rule is saved, which means that kanbans will be created in real-time during sales order creation.  
2. Click New.
3. In the Customer account field, enter or select a value.
    * For example, select US-003.  
4. Click OK.
5. In the Item number field, type 'L0050'.
6. In the Site field, type '1'.
    * Select Site 1 because Warehouse 13 is on Site 1.  
7. In the Warehouse field, enter or select a value.
    * Set Warehouse to 13.  
8. Set Quantity to '75'.
    * Enter a quantity of 50 or greater, to trigger the created kanban rule.  

## Verify that kanban is created
1. Click Product and supply.
2. Click View pegging tree.
    * Notice that a kanban with the same quantity as the sales line is created. You can also see the material issues needed to produce L0050. This is the last step in this procedure.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]