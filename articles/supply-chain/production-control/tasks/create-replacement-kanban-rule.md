--- 
# required metadata 
 
title: Create a replacement kanban rule
description: This procedure focuses on replacing an existing kanban rule with a new kanban rule on a specific date. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: KanbanRules, KanbanRuleDuplicate   
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
# Create a replacement kanban rule

[!include [banner](../../includes/banner.md)]

This procedure focuses on replacing an existing kanban rule with a new kanban rule on a specific date. This is useful when changes in the production flow or replenishment rules need to be coordinated and scheduled. The demo data company used to create procedure is USMF. This procedure is intended for the process engineer or the value stream manager when they prepare production for a changed production flow or a new replenishment rule. This task replaces kanban rule 000022 with a new rule and increases the maximum quantity from 48 to 100 for the new rule.


## Select a kanban rule to replace
1. Go to Kanban rules.
2. In the list, find and select the desired record.
    * Select kanban rule 000022.  

## Create a replacement kanban rule
1. Click Replace kanban rule.
2. In the Effective date field, enter a date and time.
    * Select a date in the future, such as one week from now. This is the date and time when the new kanban rule becomes active and replaces the old kanban rule.  
    * If the kanban rule changes the path in the production flow,  another activity can be selected.  In this procedure, we will keep the activity untouched.  
3. Click OK.
    * Notice that a new kanban rule is created to replace kanban rule 000022.  
    * The effective date is set according to the date chosen when you replace the kanban rule.  
4. In the list, find and select the desired record.
    * Select the replaced kanban rule 000022.  
    * Notice that the replaced kanban rule has the same date as the Expiration date because this is the date when it will expire.  
5. In the list, select row 1.
    * Select the new kanban rule on top of the list. This is the kanban rule with the highest kanban rule number.  
6. In the list, click the link in the selected row.
    * Click the kanban rule number to open the kanban rule.  

## Modify maximum quantity for the replacement kanban rule
1. Set Maximum quantity to '100'.
    * Expand the Quantities FastTab to see the Maximum quantity field. Changing the maximum quantity to 100 will allow up to 100 kanbans to be processed.    This is the last step in this task.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]