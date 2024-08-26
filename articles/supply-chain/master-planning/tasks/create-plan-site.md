--- 
title: Create a plan for a site
description: The production planner calculates the material and capacity requirements for the production of a specific item. 
author: t-benebo
ms.date: 08/29/2018
ms.topic: how-to 
ms.search.form: DefaultDashboard, ReqCreatePlanWorkspace, ReqTransPlanCard, ReqTransPOUrgentFormPart, SysQueryForm   
ms.reviewer: kamaybac
ms.author: benebotg
---
# Create a plan for a site

[!include [banner](../../includes/banner.md)]

The production planner calculates the material and capacity requirements for the production of a specific item. After the sourcing suggestions are created, they find the orders at the site for which they are planning and firms the orders, starting from the urgent ones. The most urgent orders are the ones that need to be firmed on the current date. Use the demo data company USMF to perform these tasks.


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



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]