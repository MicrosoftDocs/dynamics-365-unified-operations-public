--- 
# required metadata 
 
title: Create an accelerated depreciation profile and assign it to book (Japan)
description: For Japan, accelerated depreciation requires configuration of a depreciation profile, just like other depreciation methods. 
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
# Create an accelerated depreciation profile and assign it to book (Japan)

[!include[task guide banner](../../includes/task-guide-banner.md)]

For Japan, accelerated depreciation requires configuration of a depreciation profile, just like other depreciation methods. 



Use this procedure to learn how to create a depreciation profile for accelerated depreciation and assign it to a book. 



In order to complete this procedure, the Fixed Asset configuration key must be selected.



This procedure was created using the demo data company JPMF.


## Create a depreciation profile
1. Go to Fixed assets > Setup > Depreciation profiles.
2. Click New.
3. In the Depreciation profile field, type a value.
4. Note the value in the Depreciation profile field to reference later
5. In the Name field, type a value.
6. In the Method field, select 'Accelerated'.
7. Click Save.

## Assign the depreciation profile to a book
1. Go to Fixed assets > Setup > Books.
2. Select the book to assign the accelerated depreciation profile to.
3. Click Edit.
4. Use the value noted previously in the Accelerated depreciation profile field
5. Click Save.

