--- 
# required metadata 
 
title: Create a plan for a site
description: The production planner calculates the material and capacity requirements for the production of a specific item. 
author: YuyuScheller
manager: AnnBe 
ms.date: 06/10/2016
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
# Create a plan for a site

[!include[task guide banner](../../includes/task-guide-banner.md)]

The production planner calculates the material and capacity requirements for the production of a specific item. After the sourcing suggestions are created, he finds the orders at the site for which he is planning and firms the orders, starting from the urgent ones. The most urgent orders are the ones that need to be firmed on the current date. Use the demo data company USMF to perform these tasks.


## Create a materials and capacity plan for an item
1. Click Master planning.
    * You need to navigate to the default Dashboard.  
2. Click Run.
3. Expand the Records to include section.
4. Click Filter.
5. In the list, mark the selected row.
6. In the Criteria field, type a value.
    * Example: D0001  
7. Click OK.
8. Click OK.
    * This may take a few minutes.  
9. Refresh the page.

## Identify the urgent planned orders for the item
1. Open Item number column filter.
2. Apply a filter on the "Item number" field, with a value of "D0001", using the "begins with" filter operator.
3. Open Order date column filter.
4. Apply a filter on the "Order date" field, with a value of current date, using the "is exactly" filter operator.

## Firm all the urgent orders for the item
1. In the list, mark or unmark all rows.
2. Click Firm.
3. Click OK.

