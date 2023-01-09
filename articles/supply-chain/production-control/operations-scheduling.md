---
title: Operations scheduling
description: This article provides information about operations scheduling. You can use operations scheduling to provide a general estimate of the production process over time.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: ProdSchedule
ms.topic: conceptual
ms.date: 01/09/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Operations scheduling

[!include [banner](../includes/banner.md)]

This article provides information about operations scheduling. You can use operations scheduling to provide a general estimate of the production process over time.

You can schedule production at the operation level and the job level. Unlike job scheduling, operations scheduling doesn't explode the operations for the production route into jobs. If you want to include more detail in the scheduling, such as information about current capacity, you can run job scheduling after you run operations scheduling. You can also run job scheduling only. Job scheduling is typically used to schedule individual jobs on the shop floor for an immediate or short-term time frame.

## Components of operations scheduling

The main components of operations scheduling are the scheduling direction, the capacity of resources, and materials optimization. By using operations scheduling, you can achieve the following goals:

- Control the planning method by scheduling forward or backward from a given date.
- Optimize the use of resources by scheduling productions based on the capacity of the resources. This approach also helps identify when alternative resources should be used.
- Optimize the use of materials by scheduling productions based on the availability of the required materials.
- Schedule and synchronize reference productions. The dates of the reference productions are adjusted when the production order’s schedule is changed.

You must estimate the cost of a production order before you can run operations scheduling. If you haven't run an estimate, it's automatically run before operations scheduling is started. An operations schedule specifies the following information:

- The product that is planned for production
- The configuration of the product
- The quantities that are involved in the production
- The dates when the production will start and end
- The capacity reservations for the resources that perform the production activities

The setup time, process time, and run time are set for operations in the production. After you run operations scheduling, the status of the production order is *Scheduled*, and all operations are scheduled in the order that is specified by the production route. However, only the duration of the operation is considered. Start times and end times aren't scheduled.

## Scheduling direction and date

The scheduling direction is fundamental to the scheduling process. Production can be scheduled forward or backward from any date, depending on timing and scheduling requirements.

- **Forward from the scheduling date** – You can schedule production to start as early as possible. Production can be started today, tomorrow, or on any date in the future. The production is scheduled forward in time to the earliest possible end date.
- **Backward from the scheduling date** – You can schedule production to start as late as possible. Backward scheduling is based on the date when the production must be completed. The schedule counts backward from that date to the latest possible date that the production can be started and still be completed on time.

## Resource scheduling

When you run an operations schedule, each operation in the production route is scheduled for the resource that is specified for the operation. Additionally, the duration of each operation is specified on the production route. If a resource group is specified for an operation, the scheduling reserves capacity on the group. However, unlike job scheduling, operations scheduling doesn't select the specific resources in the group. If you're working with finite capacity, the schedule depends on the availability of the resources that are required in order to complete production. Operations scheduling follows the sequence of operations that is specified on the production route. The scheduling reserves capacity on the resource groups, based on the operation times that are defined on the production route. The sum of available capacity on the resources that are involved determines the capacity for the resource group. Capacity reservations that already exist for the resources are considered unavailable capacity. If there isn't enough available capacity for the production, the production orders can be delayed or even stopped. You can also specify the efficiency that you expect from the resources that are involved in the production. You specify the efficiency as a percentage on the resource. The efficiency percentage adjusts the throughput of the resource. This adjustment affects the time that is reserved for the resource. The lead times for the operations that use the resource are also adjusted accordingly.

## Operations scheduling and master planning

The operations schedule also drives master planning and determines calculations for material requirements. Operations scheduling considers the following information:

- **Backlogged productions** – Products that are planned, released, or started
- **Material availability** – Inventory, subproductions, suppliers, and vendors
- **Capacity availability** – Resources that are required for production

> [!NOTE]
> If you're using multi-threaded master planning and operations scheduling, finite capacity will not be considered. 

## Cancellations

When you run operations scheduling, you can cancel specific parts of the routing. These parts include the queue time, setup time, process time, overlap time, and transport times.

## Finite materials

If you're working with finite materials, scheduling also depends on the availability of the materials that are required for production. If there aren't enough available components for the production, production can be delayed. You can base scheduling on the use of materials by specifying the materials that must be available for production. When you optimize on both resource capacity and the availability of materials, production is calculated according to these restrictions. A production order can't be scheduled to start until capacity and materials are available at the same time and in the required quantities.

## Additional resources

- [Operations scheduling options](operation-scheduling-options.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
