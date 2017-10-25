--- 
# required metadata 
 
title: Change the depreciation method during the asset life for one asset (Japan)
description: In Japan, the depreciation method is permitted to change during the service life of a fixed asset. 
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
# Change the depreciation method during the asset life for one asset (Japan)

[!include[task guide banner](../../includes/task-guide-banner.md)]

In Japan, the depreciation method is permitted to change during the service life of a fixed asset.



This procedure walks you through changing the depreciation profile for a fixed asset.



In order to complete this task, the Fixed Assets configuration key must be selected. Also, the Undepreciated balance schedule or Years passed schedule has to be configured before you can complete this procedure.



This procedure was created using the demo data company JPMF.


## Change the depreciation profile for a fixed asset
1. Go to Fixed assets > Fixed assets > Fixed assets.
2. Use the Quick Filter to find records. For example, filter on the Fixed asset number field with a value of 'STRUM-000001'.
3. Click Books.
4. Click Functions.
5. Click Change depreciation profile.
6. Click New.
7. In the Start date field, enter a date.
    * The date has to be the start date of a fiscal year, in the current fiscal calendar.  
8. In the Depreciation profile field, type a value.
9. Click Update service life.
    * Confirm that Service life and Depreciation periods remaining are updated.  

## View the undepreciated balance schedule for fixed assets
1. Go to Fixed assets > Setup > Depreciation rate schedules > Undepreciated balance schedules.
    * Refer to the procedure for Depreciation rate schedules to learn how to edit a depreciation rate schedule.  
    * The corresponding data has to exist for the depreciation profile update.  
    * From method, To method, Service life and Years passed determine the record to apply to the asset change.  

