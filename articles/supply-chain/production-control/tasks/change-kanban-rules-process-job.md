--- 
title: Change kanban rules for a process job
description: Learn about changing the used kanban rule for a given kanban, including step-by-step processes for copy and changing kanban rules.
author: johanhoffmann
ms.author: johanho
ms.topic: how-to
ms.date: 08/29/2018
ms.custom:
ms.reviewer: kamaybac   
ms.search.form: KanbanRules, KanbanRuleDuplicate, KanbanJobSchedulingListPage, LeanRuleReassignmentWizard, KanbanReassignRuleLookup  
---

# Change kanban rules for a process job

[!include [banner](../../includes/banner.md)]

This procedure focuses on changing the used kanban rule for a given kanban. This is useful to level load resources or in case of breakdown. The demo data company used to create this procedure is USMF. This procedure is intended for the planner, working at a lean manufacturing company, responsible for the value stream.


## Copy kanban rule
1. Go to Kanban rules.
2. In the list, find and select the desired record.
    * Select Event Kanban rule 000022 for L0001.  
3. Click Duplicate kanban rule.
4. Click OK.

## Change kanban rule
1. Close the page.
2. Go to Kanban job scheduling.
3. In the list, mark the selected row.
    * Select line with Kanban 000177.  
4. Click Use alternative kanban rule.
5. Click Next.
6. In the Kanban rule field, enter or select a value.
    * Select the kanban rule that was created earlier. This is the kanban rule with the highest number.  
7. Click Finish.
    * Now the kanban job is using an another kanban rule. This can be useful to level load work cells.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]