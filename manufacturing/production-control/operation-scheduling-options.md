---
# required metadata

title: Operations scheduling options
description: This topic describes the options for operations scheduling. You can use operations scheduling to provide a general estimate of the production process over time.
author: YuyuScheller
manager: AnnBe
ms.date: 2016-10-04 13 - 34 - 14
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: ProdSchedule
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2094
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 198123
ms.assetid: 1a12b205-4cb5-44b2-bef9-526b868b5058
ms.search.region: global
ms.search.industry: Manufacturing
ms.author: crytt
ms.dyn365.ops.intro: Feb-16
ms.dyn365.ops.version: AX 7.0.0

---

# Operations scheduling options

This topic describes the options for operations scheduling. You can use operations scheduling to provide a general estimate of the production process over time.

Operations scheduling calculates the following information for a production order:

-   Start and end dates are set for the production order and each operation.
-   Resources are assigned to operations.

Several settings determine how production schedules are calculated. You define these settings on the **Operations scheduling** page. The following information describes the scheduling options.

## Operations scheduling
### Scheduling direction

The scheduling direction is fundamental to the scheduling process. A production can be scheduled forward or backward from any date, depending on timing and scheduling requirements.

-   **Forward scheduling** – You can schedule a production to start as early as possible. The production can be started today, tomorrow, or on any specific date in the future. The production is scheduled to start on the earliest possible date and is planned forward in time to the earliest possible end date.
-   **Backward scheduling** – You can schedule a production to start as late as possible. The schedule is based on the date when the production must be completed and counts backward to the latest possible date that the production can be started without missing its target deadline.

The following options are available:

-   **Forward from today** – Schedule forward from the current date. (The current date is the system date.)
-   **Forward from planned start** – Schedule forward from an earlier start date. If there is no previous scheduling, the scheduling direction is forward from the current date.
-   **Forward from scheduling date** – Schedule forward from the date that is specified in the **Scheduling date** field. If you don't specify a scheduling date, the scheduling direction is forward from the current date.
-   **Backward from delivery date** – Schedule backward from the delivery date that is specified for the production order. If you select this option, but no delivery date is specified, the delivery date is the current date.
-   **Backward from planned end** – Schedule backward from a previously calculated end date. If there is no previous scheduling, the end date is the current date.
-   **Backward from scheduling date** – Schedule backward from the date that is specified in the **Scheduling date** field. If you don't specify a scheduling date, the current date is used. Backward from scheduling date is calculated for the production order the last time that a requirement was calculated. If no date is specified for the production order, the current system date is used.
-   **Backward from futures date** – Schedule backward from the futures date that was calculated for the production order the last time that a requirement was calculated. If no futures date is specified for the production order, the current system date is used.
-   **As last scheduling** – For operations scheduling and job scheduling, the selected scheduling direction and date are saved. Therefore, you can select this option for subsequent scheduling. If there is no previous scheduling of the production order, scheduling is backward from the current system date.
-   **Forward from tomorrow** – Schedule forward from the current date plus one day.
-   **Forward from previous job** – This option is relevant only in job scheduling. If you select this scheduling direction for operations scheduling, the production order is scheduled forward from the current date. In job scheduling, scheduling is established for one job, and all other jobs for the production are scheduled based on that job.
-   **Backward from previous job** – This option is relevant only in job scheduling. If you select this scheduling direction for operations scheduling, planned orders are scheduled backward from the current date. In job scheduling, scheduling is established for one job, and all other jobs for the production are scheduled based on that job.

### Scheduling date

This date is used for the **Forward from scheduling date** and **Backward from scheduling date** scheduling directions. Scheduling is backward or forward from this date. For more information, see the previous section, "Scheduling direction."

### Recalculate BOM levels

When you select **Recalculate BOM levels**, the selected bill of materials (BOM) levels will be recalculated to help guarantee the correct scheduling order.

## Limitations
### Finite capacity

Scheduling depends on the availability of the resources that are required in order to complete production. If there isn't enough capacity, production orders can be delayed or even stopped. If finite capacity is applied to operations scheduling, existing capacity reservations that are made on the resources are considered, and that capacity is seen as unavailable. The production order is scheduled based on the availability of capacity on the resources that are required. Operations scheduling uses the specified sequence of operations to determine the order of operations in the production route. Operations scheduling reserves capacity on the resource groups, based on the operation times that are defined on the production route. The capacity of the resource groups is the sum of available capacity on all the resources in the resource groups.

### Finite material

Scheduling also depends on the availability of the materials that are required for production. Insufficient component availability can also cause production delays. Scheduling can also be based on the use of materials. Just specify the materials that must be available for production instead of the materials that aren't critical. This type of scheduling is known as scheduling with finite material. When you specify finite materials, production is scheduled based on whether materials are available. **Note:** When you optimize on both capacity and materials, production is calculated to meet both restrictions. The availability of capacity and materials is considered, and the production order’s operations can't be scheduled to start until capacity and materials are available at the same time and in the required quantities. Select this check box if materials should be considered limited during scheduling. If the materials are limited, the material's coverage for that time will be considered. In other words, scheduling considers the futures dates that are calculated for the items. Scheduling reserves raw materials and explodes the current production. If scheduling occurs several times, only the first scheduling runs an explosion and makes reservations. If you make changes in the production BOM or route, the next scheduling runs an explosion. For the explosion, it's assumed that the materials are required on the same day. Because the production isn't scheduled at the time of the master schedule explosion, the current date is the best estimate of when the items will be available. The explosion then checks whether the items are available. If the items are available, the production requirement can be fulfilled. If the items aren't available by the current date, a planned order is generated, and an offset selection is made for the planned order. If automatic firming is set for the planned order, the planned order is firmed automatically for purchase or production. The production status is automatically changed to the status that is specified in the **Requested production status** field in the **Coverage groups** dialog box. If the check box is cleared, the materials are always considered available. Therefore, scheduling doesn't consider whether the materials are available at the time of requirement.

### Finite property

Select this check box if the job scheduling should include property requirements.

### Keep production unit

Select whether the scheduling engine should schedule only resources that are already specified on the production unit.

### Keep warehouse from resource

Select whether the scheduling engine should schedule only resources that are associated with the input warehouse that is specified on the resource.

## References
### Schedule references

When references depend on production orders, they are also known as subproductions. Subproductions can be scheduled as part of the scheduling of a production order. Select this check box if the scheduling of subproductions should be based on the scheduling of the main production. In relation to the main production, overlying productions are scheduled forward, and underlying productions are scheduled backward. You can view production order references can be viewed in the **Reference level** field on the **Production orders** page.

### Synchronize references

You can synchronize references with the production order. If this option is selected, the dates of the subproductions are moved and aligned when changes are made to the production order’s schedule. If a production order has one or more subproductions, you might want to schedule the subproductions together with the main production. In this case, the main production can't be started until the related subproductions have been completed. Therefore, select this check box if the scheduling of subproductions should be based on the start and end times of the selected production. You can select this check box only if the **Schedule references** check box is also selected.

## Cancellation
### Cancel queue time

Select this check box to exclude queue time from the scheduling.

### Cancel setup

Select this check box to exclude setup time from the scheduling.

### Cancel process

Select this check box to exclude run time from the scheduling.

### Cancel overlap

Select this check box to exclude overlap time from the scheduling.

### Cancel transport

Select this check box to exclude transit time from the scheduling.

## Set default
You can save the current values as default values. There are two options:

-   Set as my default
-   Set as default for everyone


See also
--------

[Operations scheduling](operations-scheduling.md)

