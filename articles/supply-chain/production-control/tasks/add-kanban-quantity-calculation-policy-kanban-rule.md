--- 
# required metadata 
 
title: Add a kanban quantity calculation policy to a kanban rule
description: This procedure focuses on creating a kanban quantity calculation policy and adding it to a kanban rule to optimize the kanban size and quantities. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: KanbanQuantityPolicy, KanbanRules, KanbanQuantityCalculation
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: johanho
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Add a kanban quantity calculation policy to a kanban rule

[!include [banner](../../includes/banner.md)]

This procedure focuses on creating a kanban quantity calculation policy and adding it to a kanban rule to optimize the kanban size and quantities. The demo data company used to create this procedure is USMF. This procedure is intended for the value stream manager. This procedure is a prerequisite for creating the procedure Calculate kanban quantity suggestions. 


## Create a kanban quantity calculation policy
1. Go to Production control > Periodic tasks > Kanban quantity calculation > Kanban quantity calculation policies.
2. Click New.
3. In the Name field, type a value.
    * For example, type Speaker2016.  
4. In the Master plan field, click the drop-down button to open the lookup.
5. In the list, find and select the desired record.
    * Select StaticPlan to calculate demand.  
6. In the list, click the link in the selected row.
7. Click Save.
8. In the Minimum kanban quantity field, enter '1'.
    * This is the additional number of kanbans that is included in the kanban quantity calculation.  
9. Set Safety factor to '1'.
    * This is the factor that is used to calculate additional quantity of safety stock.  
10. In the Days ahead field, enter '30'.
    * This is the number of days prior to the kanban quantity calculation date that is included in the demand calculation.  
11. In the Days behind field, enter '30'.
    * This is the number of days forward from the kanban quantity calculation date that is included in the demand calculation.  The formula used for the calculation is shown with the actual values. For example,  Kanban quantity = ((Average daily demand x lead time x 2.00) / Product quantity per handling unit) + 1  
12. Close the page.

## Add the kanban quantity calculation policy to a kanban rule
1. Go to Product information management > Lean manufacturing > Kanban rules.
2. In the list, find and select the desired record.
    * Select kanban rule 000020 for this procedure.  
3. In the list, click the link in the selected row.
4. Toggle the expansion of the Kanban quantity calculation policies section.
5. Click Add.
    * Add the kanban quantity calculation policy that you have just created in the previous sub-task.  
6. In the list, mark the selected row.
7. In the Name field, click the drop-down button to open the lookup.
8. In the list, click the link in the selected row.
    * Select the policy Speaker2016 that you have just created in the previous sub-task.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]