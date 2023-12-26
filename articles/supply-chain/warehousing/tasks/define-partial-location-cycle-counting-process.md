--- 
# required metadata 
 
title: Define partial location cycle counting process 
description: When you use cycle count plans to create counting work, you can guide the actual counting operations by requesting that only specific products and product variants be counted instead of all on-hand inventory at the location. 
author: Mirzaab
ms.date: 06/23/2017
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
ms.search.form: WHSRFMenuItemCycleCount, WHSCycleCountPlan, WHSCycleCountPlanListPage, WHSWorkTemplateTable
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: mirzaab
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Define partial location cycle counting process 

[!include [banner](../../includes/banner.md)]

When you use cycle count plans to create counting work, you can guide the actual counting operations by requesting that only specific products and product variants be counted instead of all on-hand inventory at the location. By filtering on specific products, the warehouse manager can reduce review overhead, help prevent consolidation mistakes, and save time. Typically, a warehouse manager performs the setup tasks. You can go through this procedure in the USMF demo data company or in your own data.


## Create a cycle counting work template
1. Go to Warehouse management > Setup > Work > Work templates.
2. In the Work order type field, select 'Cycle counting'.
3. Click New.
4. In the Sequence number field, enter a number.
    * The sort order is from the smallest number to the largest number. The value must be more than 0 (zero).  
5. In the list, mark the selected row.
6. In the Work template field, type a value.
7. In the Work template description field, type a value.
8. In the Work pool ID field, enter or select a value.
9. In the Work priority field, enter a number.
10. Click Save.
11. Click New.
12. In the list, mark the selected row.
13. In the Work type field, select 'Counting'.
14. In the Work class ID field, enter or select a value.
15. Click Save.
16. Click Work line breaks.
17. Click New.
18. In the Sequence number field, enter a number.
    * The sort order is from the smallest number to the largest number. The value must be more than 0 (zero).  
19. Click Save.
20. Close the page.
21. Close the page.

## Create a cycle counting plan
1. Go to Warehouse management > Setup > Cycle counting > Cycle count plans.
2. Click New.
3. In the Cycle counting plan ID field, type a value.
4. In the Description field, type a value.
5. In the Maximum number of cycle counts field, enter a number.
6. In the Work template field, enter or select a value.
7. Click New.
8. In the Sequence number field, enter a number.
    * The sort order is from the smallest number to the largest number. The value must be more than 0 (zero).  
9. In the Description field, type a value.
10. Click Save.
11. Click Define product query.
12. In the list, mark the selected row.
13. In the Criteria field, enter or select a value.
14. Click OK.
15. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]