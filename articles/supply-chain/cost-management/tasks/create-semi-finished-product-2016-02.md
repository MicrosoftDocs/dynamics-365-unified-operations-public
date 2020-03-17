--- 
# required metadata 
 
title: Create a semi-finished product (February 2016 only)
description: This task focuses on creating a semi-finished product. 
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
# Create a semi-finished product (February 2016 only)

[!include [banner](../../includes/banner.md)]

This task focuses on creating a semi-finished product. It is the second task in the BOM calculation series. The demo data company used to create this task is USMF.

1. Go to Product information management > Products > Released products.
2. Click New.
3. In the Product number field, type a value.
    * For this example, type BOM_2.  
4. In the Item model group field, enter or select a value.
    * Select STD. STD stands for standard cost and is the most commonly used model when working with cost calculations.  
5. In the Item group field, enter or select a value.
    * For example, select Audio. This has no impact on cost calculations.  
6. In the Storage dimension group field, enter or select a value.
    * Select SiteWH. Only Site and Warehouse will be used for this example.  
7. In the Tracking dimension group field, enter or select a value.
    * Tracking dimensions will not be used for this example, select None.  
8. Click OK.
9. On the Action Pane, click Manage inventory.
10. Click Default order settings.
11. In the Default order type field, select 'Production'.
    * Because this is a semi-finished product that will be produced, select Production.  
12. In the Purchase site field, enter or select a value.
    * For this example, select Site 1.  
13. In the Inventory site field, enter or select a value.
    * For this example, select Site 1.  
14. In the Sales site field, enter or select a value.
    * For this example, select Site 1.  
15. Close the page.
16. On the Action Pane, click Manage costs.
17. Click Item price.
18. Click New.
19. In the list, mark the selected row.
20. In the Version field, enter or select a value.
    * For this example, select Version 10.  
21. In the Site field, enter or select a value.
    * For this example, select Site 1.  
22. Set Price to '10'.
    * For this example, type a cost price of 10.  
23. Click Save.
24. Click Activate pending price(s).
25. Close the page.
26. Close the page.
27. Click BOM_2 to open it.
28. Expand the Manage costs section.
29. In the Cost group field, enter or select a value.
    * For this example, select Cost group M1.  
30. Use the shortcut for saving a record.
31. Close the page.

