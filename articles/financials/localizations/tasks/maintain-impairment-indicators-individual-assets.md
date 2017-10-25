--- 
# required metadata 
 
title: Maintain impairment indicators on individual assets (Japan)
description: Use this task to learn how to maintain impairment indicators on individual assets. 
author: ShylaThompson
manager: AnnBe 
ms.date: 09/22/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: shylaw
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Japan
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Maintain impairment indicators on individual assets (Japan)

[!include[task guide banner](../../includes/task-guide-banner.md)]

Use this task to learn how to maintain impairment indicators on individual assets.



Run the task 'Setup impairment accounting common parameters' prior to this running this procedure. 



This task uses the JPMF demo company data.


## Update impairment indicator on a single fixed asset
1. Go to Fixed assets > Fixed assets > Fixed assets.
2. In the list, find and select the desired record.
    * Example: TOOLM-000006  
3. Click Books.
4. Click Functions.
5. Click Update impairment indicators.
6. Click New.
7. In the Modify date field, enter a date.
    * Example: 2013-04-01  
8. In the Description field, type a value.
9. In the Undiscounted cash flow field, enter a number.
    * In this example, enter field '3900000.'  
10. In the Recoverable amount field, enter a number.
    * In this example, enter field '3350226.'  
11. Click Save.

## Update impairment indicator on the impairment management form
1. Go to Fixed assets > .. > .. > Impairment management.
2. Click Query.
3. In the Criteria field for the fixed asset group row, click the drop-down button to open the lookup.
4. Click OK.
5. In the list, find and select the desired record.
    * TOOLM-000007  
6. In the list, find and select the desired record.
    * TOOLM-000008  
7. Click Update impairment indicators.
8. In the list, mark the selected row.
    * Select the record with Fixed asset number 'TOOLM-000007.'  
9. In the Modify date field, enter a date.
    * Define date = 2013-04-01  
10. In the Description field, type a value.
11. In the Undiscounted cash flow field, enter a number.
    * Enter 2500000.00.  
12. In the Recoverable amount field, enter a number.
    * Enter = 2000000.00.  
13. In the list, find and select the desired record.
    * Select the row with Fixed asset number 'TOOLM-000008.'  
14. In the Modify date field, enter a date.
15. In the Description field, type a value.
16. In the Undiscounted cash flow field, enter a number.
    * Enter 2000000.00.  
17. In the Recoverable amount field, enter a number.
    * Enter 1500000.00.  
18. Click Update indicator.

