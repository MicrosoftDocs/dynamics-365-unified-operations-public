--- 
# required metadata 
 
title: Create activity relation - Successor
description: The flow of activities in a lean production flow is documented through activity relations. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: LeanProductionFlow, PlanActivity, PlanActivityRelationNew, PlanActivityLookup, DefaultDashboard   
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
# Create activity relation - Successor

[!include [banner](../../includes/banner.md)]

The flow of activities in a lean production flow is documented through activity relations. This recording shows how to create an activity relation.

Prerequisites:

- A production flow and version in draft mode. 

- Two activities that follow each other in the production flow are created but not related.


## Find the production flow version 
1. Go to Production control > Setup > Lean production flow > Production flows.
2. In the list, find and select the desired record.
3. In the list, click the link in the selected row.
4. In the list, mark the selected row.
5. In the list, select a draft version.
    * Activity relations can be added to both draft or active versions of a production flow.  

## Open the activity overview
1. Click Activities.
    * Note that the form shows all activities of the production flow that are allocated to the Version of the production flows that you are working in.  

## Add a Successor
1. Click Add successor.
2. In the Activity field, click the drop-down button to open the lookup.
3. In the list, find and select the desired record.
4. In the list, click the link in the selected row.
5. Select the Constraint check box.
6. In the Constraint value field, enter a number.
    * The constraint time is the time to be scheduled between the scheduled end of the predecessor (due date and time) and the scheduled start of the successor.  
7. In the Units field, type a value.
8. In the Cycle time ratio field, enter a number.
    * If both activities run at the same takt, the cycle time ratio should be 1. If the predecessor runs at the double speed of the successor, the ratio should be 2.   The cycle time ratios are used to calculate the individual cycle times of the production flow activities.  
9. Click OK.
10. Close the page.
11. Click the GridPanel tab.
12. Close the page.
13. Refresh the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]