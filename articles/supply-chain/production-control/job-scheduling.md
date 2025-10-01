---
title: Job scheduling
description: Learn about job scheduling, which is a more detailed form of scheduling than operations scheduling for individual jobs or shop orders.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: ProdSchedule
ms.topic: article
ms.date: 09/19/2025
ms.custom: 
  - bap-template
---

# Job scheduling

[!include [banner](../includes/banner.md)]

This article provides information about job scheduling, which is a more detailed form of scheduling than operations scheduling. Use job scheduling to schedule individual jobs or shop orders, and to control the manufacturing environment.

You can use job scheduling to schedule individual jobs or shop orders, and to control the manufacturing environment. Job scheduling breaks down each operation into its individual tasks or jobs. Assign these jobs to the operations resources that perform them. Job scheduling also lets you synchronize all jobs that the selected job references. You can specify a start date and time or end date and time for the job, and then run scheduling. The time that you specify can be the start time or the end time, depending on the scheduling direction. This functionality is useful when, for example, a job can run only on one machine at a time, or when you want to optimize the job that runs for each resource.

## Tasks in the job scheduling process

The job scheduling process includes the following tasks:

- Split operations into jobs.
- Schedule jobs, based on the dates and times for the resources that are specified for the related operation.
- Calculate start times and end times for each job. Use finite capacity to make sure that there are no overlapping times.
- Determine which resources in the resource group run the job on. This task requires that a resource group be specified for an operation. Job scheduling selects the resources or resource groups based on the shortest lead time, and also considers any previous reservations on the resources.
- Explode operations into jobs when you run job scheduling. The jobs are scheduled by date and time, according to the order that the production route specifies. The setup of the operation determines the jobs that are exploded during the scheduling process. The route group assigned to the operation controls whether jobs are generated. A job is generated only if it has a specific duration. For example, a transport time job is generated if a transport time was specified for the selected operation.

## Scheduling direction

You can schedule jobs either forward or backward.

- **Forward** – Use the forward scheduling direction to start the production as early as possible. This method is also known as the push method, because the production is being pushed forward through the production process. The production is scheduled to start and end on the earliest possible dates.
- **Backward** – Use the backward scheduling direction to start the production as late as possible. This method is also known as the pull method, because it's based on the date when the production must be completed. Backward scheduling counts backward to the latest possible date that the production can be started without missing its target deadline.

## Finite capacity

You can schedule jobs by using finite capacity. When you use finite capacity, the capacity that is scheduled can't be larger than the capacity that's available for the resource. Available time is defined as the interval when the resource is available and there are no other reservations on capacity. Scheduling that is based on finite capacity makes sure that start times and end times for an operation on a specific date don't overlap. The resource capacity that is already reserved is considered, and overlaps between the start times and end times are also considered. Finite capacity determines the amount of capacity that must be available for a resource in order to achieve optimal use of that resource. This determination is balanced against a calculation of the shortest possible lead time between operations.

## Finite materials

Job scheduling that uses finite materials ensures that the required materials are available when the operation starts. The coverage rules for items define these limits. Scheduling uses requirement explosion to determine when the component items are available. If you schedule without setting finite materials, the system assumes that all items are available when they're required.

## Finite properties

Job scheduling that uses special properties requires that you specify properties for the operations on the production route. The system must fulfill these properties to reserve capacity.

## References

Job scheduling schedules all productions that the current production references. If a production has one or more subproductions, schedule the subproductions at the same time as the main production, because you can't start the main production until the related subproductions are completed.

## Schedule resources

The scheduling engine examines combinations of resources to identify those combinations that can satisfy requirements. You can specify selection criteria by selecting one of the following values in the **Primary resource selection** field on the **Scheduling parameters** page:

- *Duration* – The scheduling engine selects the resource that has the shortest lead time.
- *Priority* – The scheduling engine selects the resource that has the highest priority if two or more resources have identical capabilities and levels. The resource that has the lowest numeric value in this field has the highest priority.

> [!NOTE]
> Scheduling by duration can cause decreased performance when the same resource group contains many resources and secondary operations are used. You can schedule a maximum of 32 resources per operation. If you exceed this quantity, an Action center message is displayed, and job scheduling doesn't find the best alternative resource.

When you run job scheduling, the system plans the resources based on the limitations that you define in the resource parameters. You can control the capacity of the resources by using calendar settings. The system calculates loads for resources during the scheduling process.

> [!NOTE]
> For productions that use the operations scheduling function, you can run job scheduling after operations scheduling. If you aren't using operations scheduling, you can run job scheduling alone.

## Maximum capacities for resources per job order

Job scheduling assigns resources to jobs. You can set maximum capacities for resources per job order. For example, you can set up the system to schedule no more than 50 percent of total capacity for a production order. This setup gives you more control over the scheduling of resources on the job scheduling level. Therefore, it can help prevent issues if not enough capacity is available to perform simultaneous productions.

## Resource efficiency

Job scheduling uses the efficiency percentages that you specify for the resources. Efficiency percentages reduce or increase the time that the system reserves for the resource. Therefore, lead time also increases or decreases. The system uses the following formula for the calculation: `Scheduling time = Time × 100 ÷ Efficiency percentage`. In this formula, *Time* includes both the run time and the setup time.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
