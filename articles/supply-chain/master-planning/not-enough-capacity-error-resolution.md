---
title: Resolve 'Not enough capacity could be found' scheduling engine error
description: This topic provides information about the possible reasons for the 'Production order %1 could not be scheduled. Not enough capacity could be found.' scheduling engine error and options on how to resolve the error.
author: crytt
ms.date: 7/29/2021
ms.topic: article
ms.search.form: ProdTable
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: crytt
ms.search.validFrom: 2021-07-19
ms.dyn365.ops.version: 10.0.20
---

# Resolve 'Not enough capacity could be found' scheduling engine error

[!include [banner](../includes/banner.md)]

When you run scheduling, you may face the *'Production order %1 could not be scheduled. Not enough capacity could be found.'* error. There might be different reasons for why the scheduling engine fails with this error.

A list of things below illustrates what you can do to find a root cause of the error and mitigate it.

## Review applicable resources

The error occurs if there are no applicable resources that satisfy the operation requirements at the production order site.

To check the applicable resources, follow these steps.

1. Go to **Production control > Production orders > All production orders** and select the production order that can't be scheduled.
1. On the Action Pane, on the **Production order** tab, in the **Production details** group, select the **Route** button.
1. On the **Production routes** page, select the operation and then select the **Applicable resources** button.
1. On the **Applicable resources** page, set **Use requirements for** to *Operations scheduling* or *Job scheduling depending* on the type of scheduling you perform.
1. Make sure there are applicable resources at the production order site.

## Review calendars associated with resources

The error occurs if there is no calendar associated with the resource or resource group or if the associated calendar is not properly set up (for example, the calendar has no working times or zero efficiency in percentage).

To check that the calendar is associated with the resource or resource group, follow these steps.

1. Go to **Production control > Production orders > All production orders** and select the production order that can't be scheduled.
1. On the Action Pane, on the **Production order** tab, in the **Production details** group, select the **Route** button.
1. On the **Production routes** page, select the operation and then select the **Applicable resources** button.
1. On the **Applicable resources** page, select the resource and then select the **View resource** button or right-click in the **Resource group** field and then select **View details** option
1. On the **Resources** page or **Resource groups** page, expand **Calendar** FastTab to make sure there is a calendar associated with the resource or resource group.

> [!NOTE]
> If the error occurs during operation scheduling, you need to make sure that a calendar is associated with all applicable resource groups.

To check the setup of the calendar, follow these steps.

1. Go to **Organization administration > Setup > Calendars > Calendars**.
1. Select the calendar that is associated with the resource or resource group and then select the **Working times** button.
1. On the **Working times** page, make sure the page is not empty and that for the days you are interested in, the **Control** field value is not set to *Closed*, working times exist and the **Efficiency is percentage** field value is not set to *zero*.

If the calendar is associated with the base calendar, you need to check the setup of the base calendar as well.

> [!NOTE]
> In operation scheduling, the resource group's calendar is used to determine the start and end times and dates for each operation. Also it puts a limit on how much time the system can schedule for one specific operation for one specific day in one specific resource group. For example, if the working times for a resource group on one specific day is from 8:00 AM till 4:00 PM, then one operation can't put more load on the resource group than what can be fit into eight hours, no matter how much capacity does the resource group have available on that day. The available capacity can, however, limit the load further.

## Review scheduling parameters

Due to performance reasons, the scheduling engine will only search for a resource for a certain time and number of scheduling conflicts encountered. 

To review scheduling parameters, follow these steps.

1. Go to **Organization administration > Setup > Scheduling parameters**.
1. On the **Scheduling parameters** page, make sure the **Scheduling timeout enabled** toggle and the **Scheduling optimization timeout enabled** toggle are set to *No*.
1. If one of these toggles is set to *Yes*, change **Maximum scheduling time per sequence** or **Optimization attempts timeout** field values and reschedule the order.

## Review capacity

The error occurs when there is no free capacity and you perform finite scheduling. 

To perform infinite capacity scheduling, follow these steps.

1. Go to **Production control > Production orders > All production orders** and select the production order that can't be scheduled.
1. On the Action Pane, on the **Schedule** tab, in the **Production order** group, select the **Schedule operations** or **Schedule jobs** button.
1. On the **Operations scheduling** or **Jobs scheduling** dialog, set **Finite capacity** toggle to *No*.
1. Select **OK** button to schedule the order.

To check available capacity on the resource, follow these steps.

1. Go to **Organization administration > Resources > Resources**. 
1. On the **Resources** page, select a resource that is applicable to the order that can't be scheduled.
1. On the Action Pane, on the **Resource** tab, in the **View** group, select the **Capacity load** or **Capacity load, graphically** button to make sure there is available capacity.

To check available capacity on the resource group, follow these steps.

1. Go to **Organization administration > Resources > Resource groups**.
1. On the **Resource groups** page, select a resource group that is applicable to the order that can't be scheduled.
1. On the Action Pane, on the **Resource** tab, in the **View** group, select the **Capacity load** or **Capacity load, graphically** button to make sure there is available capacity.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]