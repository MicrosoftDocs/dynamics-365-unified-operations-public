---
title: Scheduling with infinite capacity
description: This topic provides information about infinite capacity scheduling for Planning Optimization. It also describes current feature limitations.
author: crytt
ms.date: 6/9/2021
ms.topic: article
ms.search.form: RouteInventProd
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: crytt
ms.search.validFrom: 2021-06-09
ms.dyn365.ops.version: AX 7.0.0
---

# Infinite capacity scheduling for Planning Optimization

[!include [banner](../../includes/banner.md)]

Infinite capacity scheduling for Planning Optimization introduces scheduling based on route information. The feature allows users to do job scheduling based on wide range of the route setup. Scheduling for Planning Optimization covers frequently used route settings like route operations sequence or route operation resource requirements. More details about implemented functionality provided later in this topic.

## Enable infinite capacity scheduling feature

To make scheduling functionality available in your system, [Feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md), and turn on the *Infinite capacity scheduling for Planning Optimization* feature.
 
## Introduced functionality

Infinite capacity scheduling for Planning Optimization enables job scheduling based on route information. Making it possible to schedule production process using route setup. Even though the implemented feature has some limitations compared to what is supported by the built-in master planning, it supports the most common functionality required for manufacturing scenarios.
 
Infinite capacity scheduling for Planning Optimization considers both *simple routes* and *route networks*. The user can set up complex routes with multiple starting points and operations that run in parallel using **Next** field on the route operation. The system would consider such complex route structures during the scheduling.
 
Also, scheduling feature supports *parallel operations* in route. If the user defines the route structure in which one operation is chosen as primary operation and another operation is secondary (using *Primary/Secondary* options in the **Priority** field on the route operation), the system will take such route structure into account during scheduling.
 
During the scheduling process, the system also considers the *resource requirements* specified for an operation. The system uses resource requirements to determine which resources are applicable to perform the operation. For now, scheduling for Planning Optimization feature supports following types of resource requirements:

- Resource type
- Resource
- Resource group
- Capability
 
> [!NOTE]
> HR related resource requirements like skill or certificate requirements are not yet supported.

Other operational properties that are supported by scheduling in Planning Optimization are *setup time* and *run time* values. When user defines times in the **Setup time** and **Run time** fields on the route operation, the scheduling process will create respective setup and process jobs. 
 
To sum up, scheduling for Planning Optimization supports the most frequently used scenarios. The user can create the route, add primary and secondary operations, define next operations, add resource requirements, add setup time and run time and the system would consider this information during the scheduling.
 
## Limitations

There are following limitations that you need to consider while using scheduling for Planning Optimization:

- The feature supports job scheduling only. Operation scheduling related setup is not taken into account during scheduling, regardless of the scheduling method on master plans.
- The feature support infinite capacity only.
- The feature does not support resource load functionality.
- The feature does not consider route scrap.
- The feature support *Duration* only as primary resource selection.
 
It is important to note that scheduling for Planning Optimization feature is being constantly improved and the consideration for more of the scheduling settings will be introduced with future releases.
