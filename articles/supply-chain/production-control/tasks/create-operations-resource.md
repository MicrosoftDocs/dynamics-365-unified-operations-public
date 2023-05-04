--- 
# required metadata 
 
title: Create an operations resource
description: An operations resource performs the activities of a project or a production process. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: WrkCtrTable   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: johanho
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create an operations resource

[!include [banner](../../includes/banner.md)]

An operations resource performs the activities of a project or a production process. This procedures shows you how to define an operations resource. You can walk through this procedure in demo data company USMF, or using your own data.

1. Go to Resources.
2. Click New.
3. In the Resource field, type a value.
4. In the Description field, type a value.

## Define capacity and consumption parameters
1. Expand the Operation section.
2. In the Scrap percentage field, enter a number.
3. In the Setup category field, enter or select a value.
    * Specify the cost category that defines how to account for the cost of setup.  
4. In the Run time category field, enter or select a value.
    * Specify the cost category that defines how to account for the cost of run time.  
5. In the Quantity category field, enter or select a value.
    * Specify the cost category that defines how to account for the resource cost based on the output quantity.  
6. In the Capacity unit field, select an option.
    * Specify the unit in which to express the capacity of the operations resource.  
7. In the Capacity field, enter a number.
8. In the Efficiency percentage field, enter a number.
    * Specify the efficiency that you expect from the operations resource. The efficiency percentage adjusts the throughput of the operations resource and affects the time that is reserved for the resource.  
9. In the Operations scheduling percentage field, enter a number.
    * Specify the maximum percentage of capacity of the operations resource that you want to use in operations scheduling.  
10. Select Yes in the Finite capacity field.
    * Set this option to Yes if the operations resource should be scheduled based on the actual capacity that is available, and if existing capacity reservations should be considered. If this option is set to No, the operations resource is assumed to have infinite capacity, and the resource might be overbooked.  
11. Select Yes in the Bottleneck resource field.

## Define working times
1. Expand the Calendars section.
2. Click Add.
3. In the Calendar field, enter or select a value.
    * Specify the working time calendar that defines the capacity (in hours) of the resource.  
4. In the list, find and select the desired record.
5. In the list, click the link in the selected row.

## Define resource capabilities
1. Expand the Capabilities section.
2. Click Add.
    * A capability is the ability of an operations resource to perform a particular activity. The scheduling engine allocates resources by matching the resource requirements of each activity to the capabilities of the available operations resources.  
3. In the Capability field, enter or select a value.
4. In the Level field, enter a number.
    * Specify the level of proficiency by which the resource processes the capability.  
5. In the Priority field, enter a number.
    * Specify the priority of the operations resource with respect to the capability. When scheduling by priority, the operations resource with the highest priority (lowest numeric value) is selected first.  

## Assign resource to resource group
1. Expand the Resource groups section.
2. Click Add.
    * The resource group defines the site, production unit, and warehouse context for operations resources. The operations resource can only be scheduled when assigned to a resource group, and only on the site where the resource group is located.  
3. In the Resource group field, enter or select a value.
4. In the Input location field, enter or select a value.
    * Specify the warehouse location from where the operations resource is consuming materials.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]