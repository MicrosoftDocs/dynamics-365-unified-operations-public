--- 
# required metadata 
 
title: Create routes (February 2016 only)
description: This task focuses on creating the production routes for a finished product and a semi-finished product. 
author: ShylaThompson
manager: AnnBe 
ms.date: 02/07/2017
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create routes (February 2016 only)

[!include [banner](../../includes/banner.md)]

This task focuses on creating the production routes for a finished product and a semi-finished product. It is the fifth task in the BOM calculation series. The demo data company used to create this task is USMF.


## Create a route for a semi-finished product
1. Go to Product information management > Products > Released products.
2. In the list, click the link in the selected row.
    * Select the item number BOM_2.  
3. On the Action Pane, click Engineer.
4. Click Route.
5. Click New.
6. Click Route and route version.
7. In the Description field, type a value.
    * For example, type ROUTE_2.  
8. In the Site field, enter or select a value.
    * For this example, enter or select Site 1.  
9. Click OK.
10. Click New.
11. In the Operation field, enter or select a value.
    * For this example, select Assembly.  
12. In the Run time field, enter a number.
    * For example, type 1. Run times are often part of the price that is calculated for an item.  
13. In the Route group field, enter or select a value.
    * For this example, select Std.  
14. Click the Setup tab.
15. In the Setup category field, enter or select a value.
    * For this example, select Assembly.  
16. Click the Times tab.
17. In the Setup time field, enter a number.
    * For this example, type 1. Setup times are often part of the price that is calculated for an item.  
18. On the Action Pane, click Route version.
19. Click Approve.
20. Select Yes in the Do you also want to approve the route? field.
21. Click OK.
22. On the Action Pane, click Route version.
23. Click Activate.
24. Close the page.
25. Close the page.

## Create a route for a finished product
1. In the list, click the link in the selected row.
    * Select the item number BOM_1.  
2. On the Action Pane, click Engineer.
3. Click Route.
4. Click New.
5. Click Route and route version.
6. In the Description field, type a value.
    * For this example, type ROUTE_1.  
7. In the Site field, enter or select a value.
    * For this example, enter or select Site 1.  
8. Click OK.
9. Click New.
10. In the Operation field, enter or select a value.
    * For this example, select Packing.  
11. In the Run time field, enter a number.
    * For this example, type 1.  
12. In the Route group field, enter or select a value.
    * For this example, select Std.  
13. Click the Setup tab.
14. In the Setup category field, enter or select a value.
    * For this example, select Packing.  
15. Click the Times tab.
16. In the Setup time field, enter a number.
    * For this example, type 1.  
17. On the Action Pane, click Route version.
18. Click Approve.
19. Click OK.
20. On the Action Pane, click Route version.
21. Click Activate.
22. Close the page.
23. Close the page.

## Enable automatic consumption of setup time
1. Go to Production control > Setup > Routes > Route groups.
2. In the list, find and select the desired record.
    * Select Std in the list.  
3. Click Edit.
4. Select Yes in the Setup time field.
    * Setup times are often part of the price that is calculated for an item.  
5. Click Save.
6. Close the page.

