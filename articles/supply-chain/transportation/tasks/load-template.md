--- 
# required metadata 
 
title: Set up Load template
description: This procedure shows how to set up a load template. 
author: kamaybac
manager:  
ms.date: 10/16/2020
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: WHSLoadTemplate   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: 
ms.search.validFrom: 2020-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---

## Load Template

When you create a new load, you can assign a load template that contains information about equipment and measures such as height, width, depth, and volume of the load.

This topic describes how to set up load templates and how to associate a load template with a new load.

To set up load templates, follow these steps:

1.  Click Transportation management**&gt;**Setup**&gt;**Load Building**&gt;**Load template.

2.  In the Load template ID field, enter a unique identifier (ID) for the load template.

3.  In the Equipment field, select the equipment to use for shipping the load.

4.  In the Load height**, **Load width**,** and Load depth fields, enter the dimensions of the load.

5.  In the Max. allowed load volume and Max. allowed load weight fields, enter the maximum allowed volume and weight of the load.

6.  In the Maximum allowed gross weight field, enter the maximum allowed gross weight of the load. The load's gross weight includes both its tare weight and its loading weight.

7.  In the Maximum number of freight pieces allowed field, enter the maximum number of freight pieces that the load can contain.

8.  Select the Stack load on floor check box if you want to use floor loading. In a floor loading scenario, boxes are stacked floor-to-ceiling, wall-to-wall inside the container to maximize the inside capacity.

## Associate a load template with a new load

To associate a load template with a new load, follow these steps:

1.  Click Transportation management**&gt;**Planning**&gt;**Load planning workbench**.**

2.  Click To new load**.**

3.  In the Load template ID field, select a template.


