--- 
# required metadata 
 
title: Add a predecessor to a production flow activity
description: In a production flow version, all activities must be sequenced. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: LeanProductionFlow, PlanActivity, PlanActivityRelationNew, PlanActivityLookup   
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
# Add a predecessor to a production flow activity

[!include [banner](../../includes/banner.md)]

In a production flow version, all activities must be sequenced. An activity can have one or multiple predecessors or successors. 

This procedure shows how to associate a predecessor to an activity. 

To perform this task, you need a production flow that has the Draft version with at least two activities that can be connected. 

To learn more, read the white paper "Production flows and activities in lean manufacturing."


## Find the production flow and version
1. Go to Production control > Setup > Lean production flow > Production flows.
2. In the list, find and select the desired record.
3. In the list, click the link in the selected row.
4. In the list, find and select the desired record.
5. Click Activities.

## Select an activity and add a predecessor
1. In the list, find and select the desired record.
2. Click Add predecessor.
3. In the Activity field, enter or select a value.
4. In the Cycle time ratio field, enter a number.
    * The default cycle time ratio of an activity relation is 1. This assumes that both activities run at the same pace or takt time. If the predecessor runs at a higher pace (lower takt time), the ratio should be lower than 1, if the predecessor runs at a slower pace (higher takt time) the cycle time ratio is greater than 1.  
5. Click OK.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]