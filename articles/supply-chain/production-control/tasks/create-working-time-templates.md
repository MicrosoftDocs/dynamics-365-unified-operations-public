--- 
# required metadata 
 
title: Create working time templates
description: Working time templates define the working hours throughout a week and are used to generate working times for a period of time. 
author: sorenva
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: OpResLifeCycleManagementWorkspace, WorkTimeTable, WorkTimeCopyDayDialog   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: sorenand
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create working time templates

[!include [banner](../../includes/banner.md)]

Working time templates define the working hours throughout a week and are used to generate working times for a period of time. This procedure shows you how to define a working time template using working time scheduling properties for categorizing working time intervals. You can walk through this procedure in demo data company USMF, or using your own data.

1. Go to All workspaces > Resource lifecycle management.
2. Click Working time templates.

## Create working time template
1. Click New.
2. In the Working time template field, type a value.
3. In the Name field, type a value.
4. Expand the Monday section.
5. Click Add.
6. In the From field, enter a time.
    * Specify the time when work begins in the morning.  
7. In the To field, enter a time.
    * Specify the time when workers break for lunch.  
8. Click Add.
9. In the From field, enter a time.
    * Specify the time when work resumes after lunch.  
10. In the To field, enter a time.
    * Specify the end of the work day.  

## Replicate working times to all week days
1. Click Copy day.
    * Copy the working times definitions from Monday to Tuesday.  
2. Click OK.
3. Click Copy day.
    * Copy the working times definitions from Monday to Wednesday.  
4. In the To weekday field, select an option.
5. Click OK.
6. Click Copy day.
    * Copy the working times definitions from Monday to Thursday.  
7. In the To weekday field, select an option.
8. Click OK.
9. Click Copy day.
    * Copy the working times definitions from Monday to Friday.  
10. In the To weekday field, select an option.
11. Click OK.

## Define time slots for special operations
1. Expand the Friday section.
2. In the list, find and select the desired record.
3. In the Property field, enter or select a value.
4. In the list, find and select the desired record.
5. In the Property field, enter or select a value.

## Mark weekend days as closed for pickup
1. Expand the Saturday section.
2. Select Yes in the Closed for pickup field.
3. Expand the Sunday section.
4. Select Yes in the Closed for pickup field.

