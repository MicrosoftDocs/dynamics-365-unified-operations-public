--- 
# required metadata 
 
title: Create a material plan for co-products
description: The production planner plans the material requirements for items that are formula co-products. 
author: YuyuScheller
manager: AnnBe 
ms.date: 11/14/2016
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
# Create a material plan for co-products

[!include[task guide banner](../../includes/task-guide-banner.md)]

The production planner plans the material requirements for items that are formula co-products. The demo data company used to create this procedure is USP2.


## Create requirement for a co-product
1. Go to Default dashboard.
2. Click Sales order processing and inquiry.
3. Click New.
4. Click Sales order.
5. In the Customer account field, type a value.
    * Example: US-001  
6. Click OK.
7. In the Item number field, type a value.
    * Example: P6003  
8. In the Quantity field, enter a number.
    * Example: 50000  
9. Click Save.

## Create a material plan for co-products
1. Click Master planning.
2. In the Plan field, click the drop-down button to open the lookup.
3. In the list, click the link in the selected row.
    * Example: MasterPlan  
4. Click Run.
5. Expand or collapse the Records to include section.
6. Click Filter.
7. In the list, select the row for Field = Item number.
8. In the Criteria field, type a value.
    * Example: P6003  
9. Click OK.
10. Click OK.
11. Click Planned orders.
12. Use the Quick Filter to find records. For example, filter on the Item number field with a value of 'P6000'.
    * Filter by the formula item that has as co-product of the item that you created a sales order for.  
13. In the list, mark the selected row.
    * Select any of the rows returned by the filter.  
14. In the list, click the link in the selected row.
15. Expand or collapse the Pegging section.
16. In the list, click the link in the selected row.
    * The planned order is pegged to the sales order for the co-product.  
17. Close the page.

