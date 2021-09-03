---
title: Scheduling with resource selection based on capability
description: This topic describes resource selection during infinite capacity scheduling when you specify capabilities as resource requirements for an operation.
author: crytt
ms.date: 9/3/2021
ms.topic: article
ms.search.form: RouteInventProd, WrkCtrTable, WrkCtrCapability
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: crytt
ms.search.validFrom: 2021-09-03
ms.dyn365.ops.version: 10.0.20
---

# Scheduling with resource selection based on capability

[!include [banner](../../includes/banner.md)]

By specifying resource requirements for an operation of a production route, you define what is required to perform an operation. It can be a specific resource or a resource group, combination of skills or capabilities, etc. This topic describes resource selection during infinite capacity scheduling when you specify capabilities as resource requirements for an operation.

## Capability-based scheduling

A capability is the ability if an operations resource to perform a particular activity. An operations resource can have more than one capability assigned to it, and a capability can be assigned to more than one resource. Capabilities can be assigned to all types of resources, including tools, vendors, machines, locations, facilities, and human resources. 
 
Capabilities as a resource requirements allow you to defer resource allocation until orders are scheduled. Instead of assigning specific resources or resource groups to a route operation, you can define the capabilities required for each route operation. Then during scheduling, the system matches required capabilities with the capabilities that are defined for the resources. The system will select only those resources that satisfy the requirements.
 
To assign capabilities to an operations resource, you can use **Capabilities** FastTab of the **Resources** page. And to assign resources to a capability, you can use **Resources** FastTab of the **Resource capabilities** page. Both pages are located under **Production control > Setup > Resources**.
 
You can use **Effective** and **Expiration** fields in the capability/resource assignment to make it temporary. During scheduling, the system will not use a resource with expired capability even if the capability satisfies the requirements.
 
You can use the **Level** field in the capability/resource assignment to define resource's level of proficiency regarding the capability. The scheduling engine considers the level of proficiency during the resource selection if you specify **Minimum level needed** value for the capability resource requirement. The system will select only those resources that have the required capability at a level that is equal or exceeds the minimum level that is specified in the resource requirement.

## Example

Let's use the illustration below to review how the scheduling engine selects resources based on capability.

![Capability used for scheduling](media/capability-based-scheduling.png "Capability used for scheduling")

There is a production route with several operations: *10*, *20*, *30*, *40*, and *50*. 
 
Each route operation requires resources with some capabilities. For example, route operation *10* requires a resource that has a capability to assemble a speaker (*0050 Spkr Assembly*) and to do wood work (*1010 Wood capabilities*), while route operation 50 requires a resource that has a capability to pack a product (*0070 Packing capability*).
 
During scheduling, the engine will look for resources that satisfy operation requirements. For example, to perform operation *10*, the scheduling engine will select resource 00101 since it is the first found resource with both required capabilities. To perform operation *50*, the scheduling engine will select resource *00301* since it is the only resource with packing capability.
 
Let's consider additional input data:
- Operation *10* requires minimum proficiency level of *7* in *0059 Assembly* capability
- Resource *00101* has proficiency level of *5* in *0059 Assembly* capability.
- Resource *00102* has proficiency level of *10* in *0059 Assembly* capability.
 
In this case, during the infinite capacity scheduling, the scheduling engine will select resource *00102* to perform operation *10* since this resource, unlike the resource *00101*, has the required capability level.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]