---
title: Scheduling with infinite capacity
description: This article provides information about infinite capacity scheduling. It also describes current feature limitations.
author: t-benebo
ms.date: 08/09/2022
ms.topic: article
ms.search.form: RouteInventProd
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2021-06-09
ms.dyn365.ops.version: 10.0.22
---

# Scheduling with infinite capacity

[!include [banner](../../includes/banner.md)]

The *Infinite capacity scheduling for Planning Optimization* feature introduces scheduling that is based on route information. It lets you schedule jobs based on a wide range of route setups. Scheduling covers frequently used route settings, including the route operation sequence or requirements for route operation resources.

## Turn the infinite capacity scheduling feature on or off

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.29, it's turned on by default. As of Supply Chain Management version 10.0.36, the feature is mandatory and can't be turned off. If you're running a version older than 10.0.36, then admins can turn this functionality on or off by searching for the *Infinite capacity scheduling for Planning Optimization* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

For more information about this feature, see [Scheduling with resource selection based on capability](capability-based-scheduling.md).

## Added functionality

The *Infinite capacity scheduling for Planning Optimization* feature enables job scheduling that is based on route information. Therefore, a route setup can be used to schedule production processes. Although this feature has some limitations that the deprecated master planning engine doesn't have, it supports the most common functionality that is required for manufacturing scenarios.

The feature considers both *simple routes* and *route networks*. By using the **Next** field on a route operation, you can set up complex routes that have multiple starting points and multiple operations that run in parallel. The system will consider complex route structures of this type during scheduling.

Additionally, the feature supports *parallel operations* in routes. By using the *Primary* and *Secondary* options in the **Priority** field on route operations, you can define a route structure where one route operation is the primary operation and another operation is secondary. In this case, the system will consider the route structure during scheduling.

During the scheduling process, the system also considers the *resource requirements* that are specified for an operation. The system uses resource requirements to determine which resources are required to perform the operation. Currently, the *Infinite capacity scheduling for Planning Optimization* feature supports following types of resource requirements:

- Resource type
- Resource
- Resource group
- Capability (For more information, see [Scheduling with resource selection based on capability](capability-based-scheduling.md).)

> [!NOTE]
>
> - If the resource and/or the resource group are set to infinite capacity, master planning will consider them as infinite capacity.
> - Requirements that are related to human resources, such as skills or certificate requirements, aren't yet supported.

The feature also supports the **Setup time** and **Run time** operational properties. When you set these properties on a route operation, the scheduling process will create the appropriate setup and process jobs.

In summary, scheduling supports the most frequently used scenarios. You can create the route, add primary and secondary operations, define next operations, add resource requirements, and add setup time and run time. The system will then consider this information during scheduling.

## Limitations

The following limitations apply when you use the *Infinite capacity scheduling for Planning Optimization* feature:

- The feature supports only infinite capacity.
- The feature doesn't support resource load functionality.
- The feature doesn't consider route scrap.
- The feature supports *Duration* only as the primary resource selection.
