---
# required metadata

title: Resource capabilities
description: This article provides information about resource capabilities. A capability is the ability of an operations resource to perform a particular activity. The article explains how capabilities and related concepts, such as proficiency level and priority, are used to select appropriate resources for an activity.
author: johanhoffmann
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: WrkCtrCapability, WrkCtrTable, WrkCtrCapRes, WrkCtrApplicableResources
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: 30e38233-2a64-4070-911f-8ffd78dd8281
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: johanho
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Resource capabilities

[!include [banner](../includes/banner.md)]

This article provides information about resource capabilities. A capability is the ability of an operations resource to perform a particular activity. The article explains how capabilities and related concepts, such as proficiency level and priority, are used to select appropriate resources for an activity.

A capability is the ability of an operations resource to perform a particular activity. An operations resource can have more than one capability assigned to it, and a capability can be assigned to more than one resource. You can temporarily assign capabilities to resources by defining a start date and expiration date on the capability assignment. When the capability for a resource expires, the resource can't be scheduled for a project or a production that requires that capability. A capability that has expired can be renewed. You can delete capabilities, provided that they aren't on a route relation or on part of a production route of an active production order. In general, be careful when you delete capabilities. Instead, consider adjusting the expiration date on the resources that have the capability. Capabilities can be assigned to all types of resources: tool, vendor, machine, location, facility, or human resource.

## Level
Multiple resources often have the same functional capability but at different levels of proficiency (for example, strength, processing speed, or accuracy). Therefore, when you assign a capability to a resource, you can specify a **Level** value. The level is a simple numeric value. If you specify that a capability is a resource requirement for a production route, you can also specify a **Minimum level needed** value for that capability. The scheduling engine then selects only resources that have the required capability at a level that is equal to or exceeds the minimum level that is specified in the resource requirement.

## Priority
Operations resources that have the same capabilities can be assigned a priority. Then, if multiple resources have capabilities that satisfy the scheduling requirements at the required level, and have free capacity, the scheduling engine can select among those resources. If **Priority** is selected in the **Primary resource selection** field on the **Scheduling parameters** page, the resource that has the highest priority (the lowest numeric value in the **Priority** field) is selected first during scheduling.

## Resource requirements
When you define resource requirements for a production route, you can specify one or more capabilities as requirements. During production scheduling, the capabilities that are defined in the resource requirements on the route operation are matched with the capabilities that are defined for the resources. Resources that have capabilities that satisfy the requirements are selected. If multiple resources have the same functional capability but different proficiencies (such as strength, processing speed, or accuracy), you can either define multiple capabilities or use the capability level to qualify the capability of the resource. Here is an example:

-   On a route, the drilling process time is set to 10 units per hour, but the requirement itself is defined as Drilling.
-   You have two drilling machines, M1 and M2.
-   The Drilling capability is assigned to both resources, the M1 machine and the M2 machine.
-   The M1 machine can drill two units per hour, and the M2 machine can drill 11 units per hour.

In this example, both machines can be selected by the scheduling engine, because both satisfy the basic capability requirement (Drilling). However, the M1 machine can drill only two units per hour. Because this rate is much less than the 10 units per hour that are specified on the route, the M1 machine will cause production problems if it's selected. There are two ways to resolve this issue and make sure that the M2 machine is selected instead:

-   Create two separate capabilities: Low-speed drilling and High speed drilling. Define Low-speed drilling as drilling that has a process time of one to nine units per hour. Define High-speed drilling as drilling that has a drilling process time of 10 to 19 units per hour. Then assign the M1 machine the Low-speed drilling capability, and assign the M2 machine the High-speed drilling capability. Finally, change the resource capability requirement on the route to High-speed drilling. The scheduling engine will then select the correct machine (M2).
-   Use the capability level to qualify the Drilling capability that is assigned to the drilling machines. Specify that the M1 machine has the Drilling capability at a level of 2.0, and that the M2 machine has the Drilling capability at a level of 11.0. Then specify that 10.0 is the minimum level that is required for the Drilling capability requirement on the route. The scheduling engine will then determine that only the M2 machine satisfies the resource requirements.

## Competencies for human resources
When you have operations resources of the **Human resources** type that are linked to workers in Human resources, you can also take advantage of the competencies of workers when you define the resource requirements for a production route. In other words, you can also specify requirements for specific skills, courses, certificates, or titles. The scheduling engine can then select resources that are linked to workers, and the selection will be based on the competencies of those workers. The competencies are set up in Human resources, not on the **Resource capabilities** page. When you define skills, courses, certificates, or titles as resource requirements, you must use the Human resources functionality and link each resource of the **Human resources** type to a corresponding worker. If you aren't using the Human resources functionality, you can define capabilities on the **Resource capabilities** page that resemble or duplicate the competencies from Human resources. However, the **Resource capabilities** page doesn't contain the functionality that is required in order to maintain skills, courses, certifications, or titles.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]