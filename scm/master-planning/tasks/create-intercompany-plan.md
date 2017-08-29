--- 
# required metadata 
 
title: Create an intercompany plan
description: This procedure shows how to create an intercompany plan. 
author: YuyuScheller
manager: AnnBe 
ms.date: 11/11/2016
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
# Create an intercompany plan

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows how to create an intercompany plan. The demo data company used to create this procedure is USMF.


## Set up an intercompany planning group 
1. Go to Intercompany planning groups.
    * Master planning > Setup > Intercompany planning groups  
2. Use the Quick Filter to find records. For example, filter on the Name field with a value of '10'.
3. In the list, mark the selected row.
4. Click Delete.
    * This step is necessary in order to shorten the intercompany planning run.   Intercompany planning will run master planning in all the companies in a planning group, starting from the lowest scheduling sequence.  
5. Click Yes.
6. Close the page.

## Create an intercompany plan
1. Click Intercompany master planning.
    * This is on the Master planning workspace.  
2. In the Intercompany planning group field, click the drop-down button to open the lookup.
3. In the list, click the link in the selected row.
    * Select intercompany planning group 10.  
4. In the Number of intercompany planning iterations field, enter '2'.
    * Intercompany planning group 10 has two members. In order to propagate the delays from the source company (USMF) to the customer company (DEMF), you will need to run intercompany in both companies two times. The first iteration will propagate the demand and identify the delays in the source company (USMF). The second iteration will propagate the delays from USMF to DEMF.  
5. In the First iteration field, select an option.
6. In the First iteration field, select 'Regeneration'.
7. In the Subsequent iterations field, select 'Regeneration'.
8. In the Number of threads field, enter a number.
    * This represents the number of parallel threads used for planning.  
9. Click OK.

## View the result of the plan
1. In the Plan field, click the drop-down button to open the lookup.
2. In the list, click the link in the selected row.
    * Click the link for StaticPlan. You need to be in company USMF.  
3. Click Planned orders.

