---
title: "Fix the 'Not enough capacity could be found' scheduling engine error and finite capacity"
description: "This topic provides information about the reasons and resolutions for the 'Production order %1 could not be scheduled. Not enough capacity could be found' scheduling engine error."
author: t-benebo
ms.date: 7/29/2021
ms.topic: article
ms.search.form: ProdTable
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2021-07-19
ms.dyn365.ops.version: 10.0.20
---

# Fix the "Not enough capacity could be found" scheduling engine error

[!include [banner](../includes/banner.md)]

When you run scheduling, you might receive the following error message:

> Production order %1 could not be scheduled. Not enough capacity could be found.

There are several reasons why the scheduling engine might fail and issue this error message. This topic provides guidelines that will help you find the root cause of the error and then mitigate it.

## Review the applicable resources

The error can occur if no applicable resources satisfy the operation requirements at the production order site.

To review the applicable resources, follow these steps.

1. Go to **Production control \> Production orders \> All production orders**, and open or select the production order that can't be scheduled.
1. On the Action Pane, on the **Production order** tab, in the **Production details** group, select **Route**.
1. On the **Production route** page, select the operation, and then, on the Action Pane, select **Applicable resources**.
1. In the **Applicable resources** dialog box, set the **Use requirements for** field to *Operations scheduling* or *Job scheduling*, depending on the type of scheduling that you're using.
1. Make sure that there are applicable resources at the production order site.

## Review the calendars that are associated with resources

The error can occur if no calendar is associated with the resource or resource group, or if the associated calendar isn't correctly set up (for example, it has no working times, or its efficiency as a percentage is 0 \[zero\]).

To verify that a calendar is associated with the resource or resource group, follow these steps.

1. Go to **Production control \> Production orders \> All production orders**, and open or select the production order that can't be scheduled.
1. On the Action Pane, on the **Production order** tab, in the **Production details** group, select **Route**.
1. On the **Production route** page, select the operation, and then, on the Action Pane, select **Applicable resources**.
1. In the **Applicable resources** dialog box, select the resource, and then select **View resource**. Alternatively, select and hold (or right-click) in the **Resource group** field, and then select **View details**.
1. On the **Resources** page or the **Resource groups** page, on the **Calendars** FastTab, make sure that a calendar is associated with the resource or resource group.

> [!NOTE]
> If the error occurs during operation scheduling, you must make sure that a calendar is associated with all applicable resource groups.

To review the setup of the calendar, follow these steps.

1. Go to **Organization administration \> Setup \> Calendars \> Calendars**, and select the calendar that is associated with the resource or resource group.
1. On the Action Pane, select **Working times**.
1. On the **Working times** page, make sure that the page isn't blank. Additionally, for the days that you're interested in, make sure that the **Control** field isn't set to *Closed*, working times exist, and the **Efficiency is percentage** field isn't set to *0* (zero).

If the calendar is associated with the base calendar, you must also review the setup of the base calendar.

> [!NOTE]
> In operation scheduling, the resource group's calendar is used to determine the start and end times and dates for each operation. It also limits the amount of time that the system can schedule for one specific operation for one specific day in one specific resource group. For example, if the working times for a resource group on one specific day are from 8:00 AM to 4:00 PM, the load that one operation puts on the resource group can't exceed the load that can be fit into eight hours, regardless of the amount of available capacity that the resource group has on that day. However, the available capacity can further limit the load.

## Review the scheduling parameters

To ensure good performance, the scheduling engine will search for a resource only for a specific amount of time and a specific number of scheduling conflicts.

To review the scheduling parameters, follow these steps.

1. Go to **Organization administration \> Setup \> Scheduling parameters**.
1. Follow one of these steps:

    - If the **Scheduling timeout enabled** option is set to *No*, move on to step 3.
    - If the **Scheduling timeout enabled** option is set to *Yes*, increase the value of the **Maximum scheduling time per sequence** field to give the processing more time to be completed.

1. Follow one of these steps:

    - If the **Scheduling optimization timeout enabled** option is set to *No*, move on to step 4.
    - If the **Scheduling optimization timeout enabled** option is set to *Yes*, increase the value of the **Optimization attempts timeout** field to give the processing more time to be completed.

1. If you changed any of the settings on the page, reschedule the order to try again.

## Review capacity

The error can occur when you perform finite scheduling, but there is no free capacity.

To perform infinite capacity scheduling, follow these steps.

1. Go to **Production control \> Production orders \> All production orders**, and select or open the production order that can't be scheduled.
1. On the Action Pane, on the **Schedule** tab, in the **Production order** group, select **Schedule operations** or **Schedule jobs**.
1. In the **Operations scheduling** or **Jobs scheduling** dialog box, set the **Finite capacity** option to *No*.
1. Select **OK** to schedule the order.

To review the available capacity on the resource, follow these steps.

1. Go to **Organization administration \> Resources \> Resources**, and select a resource that is applicable to the order that can't be scheduled.
1. On the Action Pane, on the **Resource** tab, in the **View** group, select **Capacity load** or **Capacity load, graphically**, and make sure that there is available capacity.

To review the available capacity on the resource group, follow these steps.

1. Go to **Organization administration \> Resources \> Resource groups**, and select a resource group that is applicable to the order that can't be scheduled.
1. On the Action Pane, on the **Resource group** tab, in the **View** group, select **Capacity load** or **Capacity load, graphically**, and make sure there is available capacity.

## Master planning books a resource when the resource calendar is closed

When using operations scheduling, master planning will plan capacity according to the calendar of the primary resource group. It books the secondary operation at the same time as the primary operation and doesn't take into account the calendars or capacity of the secondary operation. This can result in the production order being scheduled on a closed calendar or at a time when the secondary operation isn't available (calendar closed, no capacity).

When using job scheduling, master planning will take into account the capacity and calendar of both the primary and secondary operation when scheduling the order. For the order to be scheduled, calendars for the resources of both operations must be open and have available capacity.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
