---
title: Scheduling with infinite capacity
description: This topic provides information about infinite capacity scheduling for Planning Optimization. It also describes current feature limitations.
author: t-benebo
ms.date: 09/21/2021
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

The *Infinite capacity scheduling for Planning Optimization* feature introduces scheduling that is based on route information. It lets you schedule jobs based on a wide range of route setups. Scheduling for Planning Optimization covers frequently used route settings, including the route operation sequence or requirements for route operation resources.

## Turn on the infinite capacity scheduling feature

Before you can use this feature, it must be turned on in your system. Admins can use the [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Master planning*
- **Feature name:** *Infinite capacity scheduling for Planning Optimization*

For more information about this feature, see [Scheduling with resource selection based on capability](capability-based-scheduling.md).

## Added functionality

The *Infinite capacity scheduling for Planning Optimization* feature enables job scheduling that is based on route information. Therefore, a route setup can be used to schedule production processes. Although this feature has some limitations that the built-in master planning doesn't have, it supports the most common functionality that is required for manufacturing scenarios.

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

In summary, scheduling for Planning Optimization supports the most frequently used scenarios. You can create the route, add primary and secondary operations, define next operations, add resource requirements, and add setup time and run time. The system will then consider this information during scheduling.

## Limitations

The following limitations apply when you use scheduling for Planning Optimization:

- The feature supports only infinite capacity.
- The feature doesn't support resource load functionality.
- The feature doesn't consider route scrap.
- The feature supports *Duration* only as the primary resource selection.

Note that the *Infinite capacity scheduling for Planning Optimization* feature is constantly being improved. Microsoft expects to introduce support for additional scheduling settings in future releases.
