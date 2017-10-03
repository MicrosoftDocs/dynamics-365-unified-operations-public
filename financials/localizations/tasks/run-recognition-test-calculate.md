--- 
# required metadata 
 
title: Run the recognition test and calculate the impairment amount on individual assets (Japan)
description: This task walks you through running the recognition test and calculating the impairment amount on individual assets. 
author: ShylaThompson
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
# Run the recognition test and calculate the impairment amount on individual assets (Japan)

[!include[task guide banner](../../includes/task-guide-banner.md)]

This task walks you through running the recognition test and calculating the impairment amount on individual assets.



Before you can complete this task, you must maintain impairment indicators on individual assets.



This task was created using the demo data company JPMF.


## Impairment recognition test
1. Go to Fixed assets > Periodic tasks > Impairment on individual assets > Impairment recognition test.
2. Click Query.
3. In the list, find and select the desired record.
    * For this example, select the Fixed asset group row.  
4. In the Criteria field, type a value.
    * Example: TOOL-M  
5. Click OK.
    * Confirm that three fixed assets with impairment indicators configured will be displayed.  
    * TOOLM-000006 does not have any impairment adjustment, whereas TOOLM-000007 and TOOLM-000008 have -1,750,000.00 and -2,250,000.00 respectively.  
6. Click Save impairment to open the drop dialog.
7. In the Description field, type a value.
8. In the Date field, enter a date.
9. Click OK.
    * The Confirmation form of the impaired fixed assets is displayed.  
    * The Impairment test ID is issued.     Remember the Impairment_test_ID for later use in Propose and post.   

