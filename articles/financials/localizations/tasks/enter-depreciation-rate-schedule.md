--- 
# required metadata 
 
title: Enter a depreciation rate schedule and associate to a depreciation profile (Japan)
description: In Japan, the fixed asset depreciation rate is released by a government agency. 
author: ShylaThompson
manager: AnnBe 
ms.date: 09/16/2016
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
# Enter a depreciation rate schedule and associate to a depreciation profile (Japan)

[!include[task guide banner](../../includes/task-guide-banner.md)]

In Japan, the fixed asset depreciation rate is released by a government agency. You can enter the depreciation rate schedule into the system. The depreciation rate schedule is implemented as a data entity so that it can be imported from a file. 



Use this task to learn how to modify the depreciation rate schedule and associate it to a depreciation profile. The import is not covered in this task. 



In order to complete this task, the Fixed Assets configuration key must be selected.



This task uses the JPMF demo company data.


## Modify a depreciation rate schedule
1. Go to Fixed assets > Setup > Depreciation rate schedules > Depreciation rate schedules.
2. Click Edit.
3. In the Service life field, enter a number.
4. In the Depreciation rate field, enter a number.
5. In the Revised depreciation rate field, enter a number.
6. In the Guaranteed depreciation rate field, enter a number.

## Associate a depreciation rate schedule to a depreciation profile 
1. Go to Fixed assets > Setup > Depreciation profiles.
2. Click Edit.
3. In the Depreciation rate schedule field, click the drop-down button to open the lookup.
4. In the list, click the link in the selected row.
    * Select the depreciation schedule that you modified in the earlier task.  
5. Click Save.

