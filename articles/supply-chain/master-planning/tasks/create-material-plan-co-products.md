--- 
# required metadata 
 
title: Create a material plan for co products
description: The production planner plans the material requirements for items that are formula co-products. 
author: ShylaThompson
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, SalesOrderProcessingWorkspace, SalesCreateOrder, SalesTable, ReqCreatePlanWorkspace, ReqTransPlanCard, SysQueryForm, ReqTransPo   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create a material plan for co products

[!include [banner](../../includes/banner.md)]

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
1. Close the page.
2. Close the page.
3. Click Master planning.
4. In the Plan field, click the drop-down button to open the lookup.
5. In the list, click the link in the selected row.
    * Example: MasterPlan  
6. Click Run.
7. Expand or collapse the Records to include section.
8. Click Filter.
9. In the list, select the row for Field = Item number.
10. In the Criteria field, type a value.
    * Example: P6003  
11. Click OK.
12. Click OK.
13. Click Planned orders.
14. Use the Quick Filter to find records. For example, filter on the Item number field with a value of 'P6000'.
    * Filter by the formula item that has as co-product of the item that you created a sales order for.  
15. In the list, mark the selected row.
    * Select any of the rows returned by the filter.  
16. In the list, click the link in the selected row.
17. Expand or collapse the Pegging section.
18. In the list, click the link in the selected row.
    * The planned order is pegged to the sales order for the co-product.  
19. Close the page.

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
1. In the Plan field, click the drop-down button to open the lookup.
2. In the list, click the link in the selected row.
    * Example: MasterPlan  
3. Click Run.
4. Expand or collapse the Records to include section.
5. Click Filter.
6. In the list, select the row for Field = Item number.
7. In the Criteria field, type a value.
    * Example: P6003  
8. Click OK.
9. Click OK.
10. Click Planned orders.
11. Use the Quick Filter to find records. For example, filter on the Item number field with a value of 'P6000'.
    * Filter by the formula item that has as co-product of the item that you created a sales order for.  
12. In the list, mark the selected row.
    * Select any of the rows returned by the filter.  
13. In the list, click the link in the selected row.
14. Expand or collapse the Pegging section.
15. In the list, click the link in the selected row.
    * The planned order is pegged to the sales order for the co-product.  
16. Close the page.
17. Click Master planning.
18. Go to Master planning > Setup > Master planning parameters.
19. Select No in the Disable all planning processes field.
20. Close the page.

