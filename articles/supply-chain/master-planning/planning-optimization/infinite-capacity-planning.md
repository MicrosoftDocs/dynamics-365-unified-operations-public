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

# Scheduling with infinite capacity

[!include [banner](../../includes/banner.md)]

The *Infinite capacity scheduling for Planning Optimization* feature introduces scheduling based on route information. The feature lets you schedule jobs based on a wide range of route setups. Scheduling for Planning Optimization covers frequently used route settings including the route operations sequence or route operation resource requirements.

## Enable infinite capacity scheduling feature

If your system doesn't already include the features described in this topic, go to [Feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) and turn on the *Infinite capacity scheduling for Planning Optimization* feature.

## Added functionality

Infinite capacity scheduling for Planning Optimization enables job scheduling based on route information, which makes it possible to schedule production processes using a route setup. Although this feature has some limitations compared to the built-in master planning, it supports the most common functionality required for manufacturing scenarios.

Infinite capacity scheduling for Planning Optimization considers both *simple routes* and *route networks*. You can set up complex routes with multiple starting points and operations that run in parallel using the **Next** field on the route operation. The system considers such complex route structures during scheduling.

Also, the scheduling feature supports *parallel operations* in route. If you define a route structure in which one operation is chosen as the primary operation and another operation is secondary (using *Primary/Secondary* options in the **Priority** field on the route operation), the system will take that route structure into account during scheduling.

During the scheduling process, the system also considers the *resource requirements* specified for an operation. The system uses resource requirements to determine which resources are required to perform the operation. For now, the *Infinite capacity scheduling for Planning Optimization* feature supports following types of resource requirements:

- Resource type
- Resource
- Resource group
- Capability

> [!NOTE]
> Requirements related to human resources, such as skill or certificate requirements, are not yet supported.

The operational properties **Setup time** and **Run time** are also supported by the the *Infinite capacity scheduling for Planning Optimization* feature. When you make these setting on a route operation, the scheduling process will create respective setup and process jobs.

In summary, scheduling for Planning Optimization supports the most frequently used scenarios. You can create the route, add primary and secondary operations, define next operations, add resource requirements, add setup time and run time, and the system will consider this information during scheduling.

## Limitations

The following limitations apply when you use scheduling for Planning Optimization:

- The feature supports job scheduling only. Settings related to operation scheduling aren't taken into account during scheduling, regardless of the scheduling method on master plans.
- The feature support infinite capacity only.
- The feature doesn't support resource load functionality.
- The feature doesn't consider route scrap.
- The feature supports *Duration* only as primary resource selection.

Note that the *Infinite capacity scheduling for Planning Optimization* feature is constantly being improved and we expect to introduce support for additional scheduling settings in future releases.
