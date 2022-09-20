---
title: Finite capacity planning and scheduling
description: Finite capacity planning and scheduling let you understand how much work can be produced in a certain time period, taking limitations on different resources into consideration
author: t-benebo
ms.date: 09/19/2022
ms.topic: article
ms.search.form: ReqParameters, ReqPlanSched, WrkCtrTable
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2022-09-19
ms.dyn365.ops.version: 10.0.29
---

# Finite capacity planning and scheduling

[!include [banner](../includes/banner.md)]

Finite capacity is an approach to understanding how much work can be produced in a certain time period, taking limitations on different resources into consideration. The goal of finite capacity scheduling is to ensure that work proceeds at an even and efficient pace throughout the plant.

Finite capacity planning and scheduling creates a more realistic schedule for the production processes than the infinite loading approach. If there is not enough capacity on the resources, the delivery date will be pushed out and the job will be scheduled when there is enough capacity.

## Planning Optimization support for finite capacity planning

Finite capacity planning and scheduling works nearly the same way regardless of whether you using Planning Optimization or the built-in planning engine. However, the **Bottleneck time** fence parameter isn't used by Planning Optimization. When you use Planning Optimization, bottleneck resources are always scheduled using the same time fence as non-bottleneck resources (as indicated by the finite capacity time fence).

## Set up finite capacity functionality

To use finite capacity functionality, you must enable capacity planning globally, and enable finite capacity planning both for the master plan where you want to use it and for each resource where it applies. For plans and resources where finite capacity is enabled, scheduling of planned production orders will consider capacity that has already been reserved. Planned production orders are backward-scheduled from the requirement date. If capacity isn't available to meet the optimal schedule, the system will try to require component items on an earlier date. If your capacity can change as requirements change (such as when working with shifts), you shouldn't use finite capacity functionality because the calculated processing times won't be correct. Scheduling only considers capacity that is already reserved for resources where finite capacity is enabled. Enabling finite capacity for a resource makes it possible to modify the finite capacity time fence.

### Activate Master planning parameters

To use finite capacity functionality, you must enable capacity planning on the **Master planning parameters** page, as described in the following procedure.

1. Go to **Master planning > Setup > Master planning parameters**.
1. Open the **Planned orders** tab.
1. In the **Capacity planning** field group, set **Production** to *Yes*.

### Activate a Master plan

You must enable finite capacity planning and scheduling for each master plan where you want to use it, as described in the following procedure.

1. Go to **Master planning > Setup > Plans > Master plans**.
1. On the list pane, select a master plan you want to set up to use finite capacity planning and scheduling.
1. Expand the **General** FastTab.
1. In the **Planned production orders** field group, set **Finite capacity** to *Yes*.
1. Repeat this procedure as needed to set up each relevant master plan.

### Activate resources

You must enable finite capacity planning and scheduling for each resource where you want to use it, as described in the following procedure.

1. Go to **Production control > Setup > Resources > Resources**.
1. On the list pane, select a resource you want to set up to use finite capacity planning and scheduling.
1. Expand the **Operation** FastTab.
1. In the **Capacity button** field group, set **Finite capacity** to *Yes*.
1. Repeat this procedure as needed to set up each relevant resource.

## Examples

This section provides the following examples of how to work with both infinite and finite capacity planning and scheduling:

- Example 1 – Infinite capacity planning
- Example 2 – Finite capacity planning with a time fence of one day
- Example 3 – Finite capacity planning with a time fence of two days

### Preconditions

Each of the examples assumes the preconditions described in this section.

There is a product *Product1* with route that contains the operations listed in the following table.

| Operation no. | Operation name | Resource        | Run time | Process qty. | Next |
|---------------|----------------|-----------------|----------|--------------|------|
| 10            | Welding        | Welding line    | 1        | 2            | 20   |
| 20            | Assembling     | Assembling line | 1        | 4            |      |

Workers at your company work in one shift for 8 hours (8:00 – 16:00).

There is a scheduled production order for *24 pcs* of *Product1* with delivery date of *Today + 3 days*.

As a result of planning, the system loads the resources as follows:

- **Welding line** – Loaded from *Today at 8:00* until *Today + 1 at 12:00*
- **Assembling line** – Loaded from *Today + 1 at 12:00* until *Today + 2 at 10:00*.

The following image shows the resulting Gantt chart (select to enlarge).

[![Gantt chart showing preconditions.](media/finite-examples-conditions-small.png "Gantt chart showing preconditions")](media/finite-examples-conditions.png)

### Example 1 – Infinite capacity planning

This example shows planning results when you use infinite capacity planning instead of finite capacity planning.

The master plan as the following relevant setting, which disables finite capacity planning for this plan:

- **Finite capacity:** *No*

Both relevant resources are likewise disabled for finite capacity planning due to the following settings:

- Welding line  – **Finite capacity:** *No*
- Assembling line  – **Finite capacity:** *No*

Now you add a new sales order for *8 pcs* of *Product1* and run the plan. Therefore, the system will load the welding line from *today at 8:00* until *today at 12:00*. After finishing operations on the welding line, the assembling line will be loaded from *today at 12:00* until *today at 14:00*.

The following image shows the resulting Gantt chart (select to enlarge).

[![Gantt chart showing an infinite capacity planning example.](media/finite-examples-example1-small.png "Gantt chart showing an infinite capacity planning example")](media/finite-examples-example1.png)

### Example 2 – Finite capacity planning with a time fence of one day

This example shows planning results when you use finite capacity planning with a time fence of one day.

The master plan as the following relevant settings, which enable finite capacity planning and set a time fence for this plan:

- **Finite capacity:** *Yes*
- **Finite capacity time fence:** *1*

Both relevant resources are likewise enabled for finite capacity planning due to the following settings::

- Welding line  – **Finite capacity:** *Yes*
- Assembling line  – **Finite capacity:** *Yes*

Now you add a new sales order for *8 pcs* of *Product1* and run the plan. Therefore, the system will load the welding line from *today + 1 at 8:00* until *today + 1 at 12:00*. After finishing operations on the welding line, the assembling line will be loaded from *today + 1 at 12:00* until *today + 1 at 14:00*. The system considers the finite capacity only for one day.

The following image shows the resulting Gantt chart (select to enlarge).

[![Gantt chart showing finite capacity planning with a time fence of one day.](media/finite-examples-example2-small.png "Gantt chart showing finite capacity planning with a time fence of one day")](media/finite-examples-example2.png)

### Example 3 – Finite capacity planning with a time fence of two days

This example shows planning results when you use finite capacity planning with a time fence of two days.

The master plan as the following relevant settings, which enable finite capacity planning and set a time fence for this plan:

- **Finite capacity:** *Yes*
- **Finite capacity time fence:** *2*


Both relevant resources are likewise enabled for finite capacity planning due to the following settings::

- Welding line  – **Finite capacity:** *Yes*
- Assembling line  – **Finite capacity:** *Yes*

Now you add a new sales order for *8 pcs* of *Product1* and run the plan. Therefore, the system will load the welding line from *today + 1 at 12:00* until *today + 1 at 16:00*. After finishing operations on the welding line, the assembling line will be loaded from *today + 2 at 8:00* until *today + 2 at 10:00*. The system considers the finite capacity only for two days.

The following image shows the resulting Gantt chart (select to enlarge).

[![Gantt chart showing finite capacity planning with a time fence of two days.](media/finite-examples-example3-small.png "Gantt chart showing finite capacity planning with a time fence of two days")](media/finite-examples-example3.png)

> [!NOTE]
> You should always set the finite-capacity time fence as required to fit your business needs. The examples provided in this article simply illustrate the functionality. In reality, a single-day time fence would probably be too low for most manufacturers using finite capacity planning.
