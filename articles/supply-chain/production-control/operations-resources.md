---
# required metadata

title: Operations resources
description: Operations resources perform the activities of a project or a production process. They can be of different types, and can have different capabilities. 
author: johanhoffmann
ms.date: 11/03/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: OpResLifecycleManagementWorkspace, WrkCtrCapability, WrkCtrResourceGroup, WrkCtrResourceAbilityMap, OpResCapacityPlanningWorkspace, WrkCtrCapResGraph, WrkCtrResourceRequirementPart, WrkCtrCapResGraphDialog, WrkCtrResourceCopy, WrkCtrCapResStatistic
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: a3847f07-fca4-4140-a26f-d83c6ac68dde
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: johanho
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Operations resources

[!include [banner](../includes/banner.md)]

Operations resources perform the activities of a project or a production process. They can be of different types, and can have different capabilities. 

## Operations resources

Operations resources are the machines, tools, workers, facilities, physical areas or vendors that perform the activities of a project or a production process. They can be of different types and can have different capabilities.

-   **Vendor** – An external resource that performs project activities or production operations. An example is a subcontractor. By linking vendor resources to a vendor account, you can generate purchases for subcontractors, based on the bill of materials (BOM) lines or production lines.
-   **Human resources** – A project or production worker that perform an activity, either alone or as an operator of a tool or a machine. If you're using the Human resources functionality, you can link human resources to a worker. The scheduling engine can then allocate the resources, based on the competencies that are defined for the corresponding worker.
-   **Machine** – A machine or other production equipment that is required in production.
-   **Tool** – An instrument or device that is typically used together with another resource to perform an activity in a project or in production.
-   **Location** – A physical location of a specific size that is required in order to perform an activity. An example is an assembly area.
-   **Facility** – A building or fixed structure that is required in order to perform an activity.

## Calendars
A calendar can be assigned to an operations resource and describes the capacity (in hours) of that resource. The working times of the operations resource are determined by the calendar that is assigned to the resource group that the operations resource is part of. You can set an effective date and an expiration date for the assigned calendar. You can then assign more than one calendar to an operations resource. However, the dates of the assigned calendars can't overlap, and the operations resource can be assigned only one calendar at a time. **Note:** If there are no effective working calendars for a resource group (for example, if the last assigned calendar or the only assigned calendar has expired), you can no longer access the operations resources that are assigned to the resource group for production planning and operations scheduling. You can also assign a calendar to a resource group to specify the working times for both the resource group and all the operations resources that are assigned to the resource group. The capacity of the resource group is calculated as the sum of the capacities of each operations resource that is assigned to that resource group. The calendar that is assigned to a resource group can change over time.

## Resource capabilities
A capability is the ability of an operations resource to perform a particular activity. You can assign one or more capabilities to an operations resource. The scheduling engine will then allocate resources by matching the resource requirements of each activity to the capabilities of the available operations resources. Capabilities can be assigned to all types of operations resources (**Tool**, **Vendor**, **Machine**, **Human resources**, **Location**, or **Facility**). To assign capabilities to operations resources for a limited time, define a start date and an expiration date on the capability assignment. For more information, see [Resource capabilities](resource-capabilities.md).

## Resource groups
A resource group is a set of operations resources that represents the granularity at which you want to schedule resources when you use the operations scheduling method. Therefore, resource groups typically correspond to the physical organization of work cells that is demarcated by yellow lines on the production shop floor. The resource group defines the site, production unit, and warehouse context for operations resources that are assigned to the group. When you assign an operations resource to a resource group, the resource can be scheduled at the site where the resource group is located. You don't have to assign the operations resources that you create to a resource group. However, an operations resource must be assigned to a resource group before it can be scheduled to perform work. An operations resource can be assigned to a resource group for a limited time. You can also assign an operations resource to multiple resource groups, so that you can then share the resource across sites. However, the effective dates and expiration dates can't overlap. In other words, you can't assign an operations resource to two resource groups at the same time. Changes in resource group assignments are effective only for new resource allocations. Capacity reservations for jobs, operations, and project hour forecasts that are already scheduled won't be affected. **Note:** When you assign operations resources of the **Vendor** type to a resource group, all operations resources that are assigned to that resource group must be of the **Vendor** type and must be linked to the same vendor account.

## Production units
A production unit is an administrative unit that is a collection of resource groups. A production unit can contain multiple resource groups, but a resource group can be assigned to only one production unit. A production unit reflects the physical layout of production resources, and has no effect on transactions or how they are processed. You must associate a production unit with a site. You can also assign a picking warehouse and a storage warehouse to a production unit. You can use a production unit to consolidate and filter production-related data. For example, a shop floor manager can see an overview of the outstanding workload and the available capacity for a particular production unit. You can change the production unit that is assigned to a resource group. You can also delete a production unit. However, these changes to the production unit are effective only for new orders that are created after master scheduling is run. If you want to apply the production unit change to existing orders, you must make this change manually.

## Resource scheduling
Operations resources are assigned to activities when a project or a production is scheduled. Two scheduling methods are available: operations scheduling and job scheduling. When you use operations scheduling, each operation or project activity is scheduled on the resource group that contains operations resources that match the resource requirements that are specified for the operation. If a specific operations resource is required for the operation, scheduling reserves capacity only on a specific operations resource in the group. Job scheduling is a more detailed form of scheduling than operations scheduling. It breaks down each operation into its individual tasks or jobs. These jobs are then assigned to the operations resources that will perform them. Scheduling reserves capacity on the resource groups, based on the operation times that are defined on the production route or project activities. If you're working with finite capacity, the schedule depends on the availability of the operations resources that are required in order to complete the activity. For operations scheduling, the capacity of the resource group is the sum of the available capacity of the operations resources that are part of that group. Capacity reservations that already exist for the operations resources are considered unavailable capacity. If there isn't enough available capacity for production, the production orders can be delayed or even stopped. On the **Resources** page, you can define several properties that control how capacity reservations are made:

-   **Capacity** – Specify the operations resource's capacity per hour in terms of the capacity unit of measure.
-   **Batch capacity** – Specify the maximum number of pieces that the operations resource can process per run.
-   **Efficiency percentage** – Specify the efficiency that you expect from the operations resource. The efficiency percentage adjusts the throughput of the operations resource and affects the time that is reserved for the resource. The lead times for the operations that use the operations resource are also adjusted accordingly. Here is the formula that is used for the calculation: Scheduling time = Time × 100 ÷ Efficiency percentage. *Time* includes both the run time and setup time.
-   **Operations scheduling percentage** – Specify the maximum percentage of capacity of the operations resource that you want to use in operations scheduling. To allow for flexibility in capacity during job scheduling, you should set this percentage to less than 100 percent.
-   **Finite capacity** – Set this option to **Yes** if the operations resource should be scheduled based on the actual capacity that is available, and if existing capacity reservations should be considered. If this option is set to **No**, the operations resource is assumed to have infinite capacity, and the resource might therefore be overbooked.
-   **Finite property** – Set this option to **Yes** if you want the operations resource to be scheduled based on the actual capacity that is available with respect to the required working time scheduling properties.
-   **Exclusive** – Set this option to **Yes** if you don't want the operations resource to be available for another job or operation until the current production is completed. In this case, the operations resource can't be used even if there are gaps in the resource's run time.
-   **Bottleneck resource** – Define the operations resource as a bottleneck resource. A bottleneck resource is scheduled by using finite capacity when the **Finite capacity** and **Bottleneck scheduling** options on the **Master plans** page are selected.

To schedule multiple operations resources at the same time to perform, for example, an operation in production, you must specify the requirements for the various resources by using primary and secondary operations. You can then also reserve multiple operations resources that have different capacity. The operations resource that are scheduled for the primary operation determine the duration of the activity.

## Lean work cells
You can specify that a resource group is a lean work cell. The resource group can then be part of a production flow. By specifying a resource group as a lean work cell, you also prevent the resource group and the assigned operations resources from being allocated to the operations of a production order or a project hour forecast. For each resource group that acts as a lean work cell, you must specify the following information:

-   **Calendar** – The working calendar of the work cell, which must have the property of a standard workday.
-   **Input warehouse and location** – The default location that is used to pick material for an activity.
-   **Output warehouse and location** – The default location where all output of the work cell is put.
-   **Runtime cost category** – This category must be defined for the work cell if direct labor is tracked in costing.

When a resource group is used as a lean work cell, the capacity of the work cell is specified directly on the resource group. Therefore, you don't have to assign operations resources to the resource group. Only when the work cell is managed by a subcontractor, an operations resource of the **Vendor** type must be assigned to the work cell. If you assign an operations resource to a resource group that is marked as a work cell, the capacity of the work cell isn't affected.

## Costing resources
When you define an activity such as a route operation or a project hour forecast, you can specify the requirement for a specific operations resource or resource group. However, you can also specify the requirement for an operations resource of a specific type, or an operations resource that has a specific capability or competency. For this reason, the actual resource assignment isn't made until the activity is scheduled and capacity is reserved. Therefore, on a route operation, you can specify that estimation and BOM calculation must be based on a specific operations resource. This operations resource is referred to as the costing resource. You can also transfer cost categories and operation times from the costing resource to the activity. When the operation is scheduled, estimation and BOM calculation are done by using the operations resource that is actually scheduled.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]