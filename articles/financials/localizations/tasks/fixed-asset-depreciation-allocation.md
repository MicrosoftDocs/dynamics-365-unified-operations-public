--- 
# required metadata 
 
title: Set up fixed asset depreciation allocation (China)
description: In Japan, the depreciation expenses of a particular fixed asset can be shared among multiple departments. 
author: ShylaThompson
manager: AnnBe 
ms.date: 11/11/2016
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
ms.search.region: China (PRC), Japan
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up fixed asset depreciation allocation (China)

[!include[task guide banner](../../includes/task-guide-banner.md)]

In Japan, the depreciation expenses of a particular fixed asset can be shared among multiple departments. 



This task walks you through setting up fixed asset depreciation allocation. 



This task was created using the demo data company JPMF.


## Create a Fixed asset allocation rule
1. Go to Fixed assets > Setup > Depreciation allocation rules.
2. Click New.
3. In the Rule ID field, type a value.
4. In the Description field, type a value.
5. In the Dimension name field, type a value.
6. Click Add.
7. In the BusinessUnit field, type a value.
    * Enter the information for the first allocation target.  
8. In the Percentage field, enter a number.
    * The total of all the allocation target must be 100.  
9. In the Offset account field, specify the desired values.
10. Click Add.
11. In the BusinessUnit field, type a value.
12. In the Percentage field, enter a number.
    * The total of all the allocation target must be 100.  
13. In the Offset account field, specify the desired values.
14. Click Save.

## Assign a fixed asset allocation rule to a posting profile
1. Go to Fixed assets > Setup > Fixed asset posting profiles.
2. Click Edit.
3. In the Transaction type field, select 'Depreciation'.
4. In the list, find and select the desired record.
    * Select the record that you want to link the allocation rule to.  
5. Expand the Depreciation allocation rules section.
6. In the Asset allocation rule for depreciation field, type a value.
7. Click Save.

