--- 
# required metadata 
 
title: Create and assign an equipment group (Japan)
description: Use this procedure to learn how to create an equipment group and configure an equipment group it to a fixed asset. 
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
# Create and assign an equipment group (Japan)

[!include[task guide banner](../../includes/task-guide-banner.md)]

Use this procedure to learn how to create an equipment group and configure an equipment group it to a fixed asset.



The equipment groups provide default values when creating an accelerated depreciation document.



In order to complete this procedure, the Asset configuration key must be selected.



This procedure was created using the demo data company JPMF.


## Create equipment group
1. Go to Fixed assets > Setup > Equipment group.
2. Click New.
3. In the Fixed asset equipment group field, type a value.
4. In the Description field, type a value.
5. In the Equipment type field, type a value.
6. In the Location field, type a value.
    * This will be the default value when you create an accelerated depreciation document.  
7. In the Equipment type division field, type a value.
8. In the Industry average hours per day field, enter a number.
    * This will be the default value when you create an accelerated depreciation document.  
9. In the Industry annual working days field, enter a number.
    * This will be the default value when you create an accelerated depreciation document.  
10. Click Save.

## Configure default equipment group on fixed assets
1. Go to Fixed assets > Fixed assets > Fixed assets.
2. Select the fixed asset that you would like to assign the equipment group to
3. Click Edit.
4. In the Fixed asset equipment group field, type a value.
5. Click Save.

