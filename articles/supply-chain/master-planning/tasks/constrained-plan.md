--- 
# required metadata 
 
title: Generate a constrained plan
description: This article explains how to create a plan that takes into account both material and capacity constraints. 
author: t-benebo
ms.date: 08/02/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, ReqCreatePlanWorkspace, ReqTransPlanCard, ReqPlanSched   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: benebotg
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Generate a constrained plan

[!include [banner](../../includes/banner.md)]

This article explains how to create a plan that takes into account both material and capacity constraints. The plan ensures that manufacturing doesn't start before materials are available and resources are not overbooked. 

The demo data company used to create this procedure is USMF. This procedure is intended for the production planner.


## Set up a constrained plan
1. In the home page, select the **Master planning** workspace.
2. Select **Master plans** in the list of links on the far right side of the workspace.
3. In the list, find and select the desired record. Example: **StaticPlan**  
4. Select **Yes** in the **Finite capacity** field.
5. In the **Finite capacity time fence** field, enter `30`.
6. Expand the **Time fences in days** section.
7. Select **Yes** in the **Capacity** field.
8. In the **Capacity scheduling time fence (days)** field, enter a number. Example: `60`  
9. Select **Yes** in the **Calculated delays** field.
10. In the **Calculate delays time fence (days)** field, enter a number. Example: `60` 
11. Expand the **Calculated delays** section.
12. Select **Yes** in all **Add the calculated delay to the requirement date** fields.
13. Close the page.

## Create a constrained plan
1. Select **Run**.
2. In the **Master plan** field, enter or select the plan for which you have set up constraints.  
3. Select **OK**.
4. Select **Planned orders**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]