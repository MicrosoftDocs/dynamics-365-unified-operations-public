--- 
# required metadata 
 
title: Create a withdrawal kanban rule
description: This procedure shows the setup that is needed to create a withdrawal kanban rule for transferring material in a lean environment. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: KanbanRules, LeanProductionFlowActivityLookup, InventItemIdLookupSimple, UnitOfMeasureLookup, KanbanCreate   
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
# Create a withdrawal kanban rule

[!include [banner](../../includes/banner.md)]

This procedure shows the setup that is needed to create a withdrawal kanban rule for transferring material in a lean environment. The demo data company used to create this procedure is USMF. This procedure is intended for the Process Engineer or the Value Stream Manager, as they prepare replenishment of new or modified material.


## Create new kanban rule
1. Go to Kanban rules.
2. Click New.
3. In the Type field, select 'Withdrawal'.
    * The Withdrawal type is used for kanban rules to transfer material or goods.  
4. In the First plan activity field, enter or select a value.
    * Select ReplenishSpeakerComponents.   This activity is set up to move components from warehouse 11, location 11 to warehouse 12, and location 12.  
5. In the Product field, enter or select a value.
    * Select M0007.  
6. In the Lead time field, enter a number.
    * For example, 60.  
7. In the Unit of measure field, enter or select a value.
    * For example, Minutes.  

## Set quantities for kanban
1. Set Default quantity to '5'.
    * This is the quantity that will be transferred for each kanban.  
2. In the Fixed kanban quantity field, enter '2'.
    * This is the amount of kanbans that should be active. In this case, 2 kanbans transferring 5 each.  
3. In the Alert boundary minimum field, enter '1'.
    * Used to keep track of the minimum amount of full kanbans that should be at the destination. For example, this is used on the kanban quantity overview.  
4. In the Alert boundary maximum field, enter '2'.
    * Used to keep track of the maximum amount of full kanbans that should be at the destination. For example, this is used on the kanban quantity overview.  

## Create kanbans
1. Click Save.
    * The kanban rule needs to be saved before kanbans can be created.  
2. Click Add.
    * Note that there are no active kanbans because the suggested 'Number of new kanbans' is 2, which is equal to the 'Fixed kanban quantity'.  
3. Click Create.
    * This will create two kanbans.  
    * Note that 2 kanbans, for 5 each, was created for this withdrawal kanban rule.  This is the last step in this procedure.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]