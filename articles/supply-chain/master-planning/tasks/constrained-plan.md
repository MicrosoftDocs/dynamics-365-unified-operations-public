--- 
# required metadata 
 
title: Generate a constrained plan
description: This procedure shows how to create a plan that takes into account both material and capacity constraints. 
author: YuyuScheller
manager: AnnBe 
ms.date: 03/02/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: yuyus
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: yuyus
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Generate a constrained plan

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows how to create a plan that takes into account both material and capacity constraints. The plan ensures that manufacturing doesn't start before materials are available and resources are not overbooked. 

The demo data company used to create this procedure is USMF. This procedure is intended for the production planner.


## Set up a constrained plan
1. Click Master planning.
2. Click Master plans.
3. In the list, find and select the desired record.
    * Example: StaticPlan  
4. Select Yes in the Finite capacity field.
5. In the Finite capacity time fence field, enter '30'.
6. Expand the Time fences in days section.
7. Select Yes in the Capacity field.
8. In the Capacity scheduling time fence (days) field, enter a number.
    * Example: 60  
9. Select Yes in the Calculated delays field.
10. In the Calculate delays time fence (days) field, enter a number.
    * Example: 60  
11. Expand the Calculated delays section.
12. Select Yes in the Add the calculated delay to the requirement date field.
13. Select Yes in the Add the calculated delay to the requirement date field.
14. Select Yes in the Add the calculated delay to the requirement date field.
15. Close the page.

## Create a constrained plan
1. Click Run.
2. In the Master plan field, enter or select a value.
    * Select the plan for which you have set up constraints.  
3. Click OK.
    * This may take a while.  
4. Click Planned orders.

