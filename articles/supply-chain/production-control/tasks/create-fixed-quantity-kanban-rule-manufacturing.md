--- 
# required metadata 
 
title: Create a fixed quantity kanban rule for manufacturing
description: This procedure focuses on the setup needed to create a fixed manufacturing kanban rule for triggering transforming activities, at a work cell, in a lean environment. 
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
# Create a fixed quantity kanban rule for manufacturing

[!include [banner](../../includes/banner.md)]

This procedure focuses on the setup needed to create a fixed manufacturing kanban rule for triggering transforming activities, at a work cell, in a lean environment. The demo data company used to create this procedure is USMF. This procedure is intended for the Process Engineer or the Value Stream Manager, as they prepare production of a new or modified product.


## Create new kanban rule
1. Go to Kanban rules.
2. Click New.
    * Notice that the default Type is Manufacturing and Replenishment strategy is Fixed. You do not have to change these parameters.  
3. In the First plan activity field, enter or select a value.
    * This is the activity that will be performed for kanbans created based on this kanban rule.  Select 'SpeakerTestAndPackaging'.  
4. Expand the Details section.
5. In the Product field, enter or select a value.
    * Select L0050.  
6. In the Unit of measure field, enter or select a value.
    * Select minutes.  
7. In the Lead time field, enter a number.
    * Enter 5.  

## Set quantities
1. Expand the Quantities section.
2. Set Default quantity to '10'.
    * This is the quantity that will be transferred for each kanban.  
3. Select the Product quantity variance check box.
    * With this, selected kanbans can be completed with a variance from the default quantity.  To allow kanbans to be completed with a quantity from 8 to 12, set both variances to 2.  
4. Set Variance below to '2'.
    * This will allow completing down to 10 - 2 = 8  
5. Set Variance above to '2'.
    * This will allow completing up to 10 + 2 = 12  
6. In the Fixed kanban quantity field, enter a number.
    * This is the amount of kanbans that should be active. In this case, 5 kanbans processing 10 each.  
7. In the Alert boundary minimum field, enter '2'.
    * Used to keep track of the minimum amount of full kanbans that should be at the destination. For example, this is used on the kanban quantity overview.  
8. In the Alert boundary maximum field, enter '4'.
    * Used to keep track of the maximum amount of full kanbans that should be at the destination. For example, this is used on the kanban quantity overview.  
9. In the Automatic planning quantity field, enter '1'.
    * Setting this to 1 means that every kanban will be automatically planned.   If we entered 3, the kanbans would not be planned until 3 empty kanbans are ready for planning. This is useful for grouping work and avoiding too much setup.  

## Create Kanbans
1. Expand the Kanbans section.
2. Click Save.
    * The kanban rule needs to be saved before kanbans can be created.  
3. Click Add.
    * Note that there are no active kanbans, due to this the suggested 'Number of new kanbans' are 5. This is equal to the 'Fixed kanban quantity'.  
4. Click Create.
    * This will create 5 kanbans.  
    * Note that 5 kanbans, for 10 each, was created for this manufacturing kanban rule. This is the last step in this procedure.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]