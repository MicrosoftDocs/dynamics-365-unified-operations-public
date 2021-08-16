---
title: "Resolve the 'Not enough capacity could be found' scheduling engine error"
description: "This topic provides information about the possible reasons for the 'Production order %1 could not be scheduled. Not enough capacity could be found' scheduling engine error and options on how to resolve it."
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

# Resolve the "Not enough capacity could be found" scheduling engine error

[!include [banner](../includes/banner.md)]

When you run scheduling, you may receive the following error:

> Production order %1 could not be scheduled. Not enough capacity could be found.

There are several reasons why the scheduling engine might fail with this error. This topic provides guidelines that will help you find the root cause of the error and then mitigate it.

## Review applicable resources

The error can occur when there are no applicable resources that satisfy the operation requirements at the production order site.

To check the applicable resources, follow these steps.

1. Go to **Production control > Production orders > All production orders** and open or select the production order that can't be scheduled.
1. On the Action Pane, on the **Production order** tab, in the **Production details** group, select **Route**.
1. On the **Production route** page, select the operation and then select **Applicable resources** on the Action Pane.
1. The **Applicable resources** dialog opens. Set **Use requirements for** to *Operations scheduling* or *Job scheduling*, depending on the type of scheduling you are using.
1. Make sure there are applicable resources at the production order site.

## Review calendars associated with resources

The error can occur when there is no calendar associated with the resource or resource group, or if the associated calendar is not properly set up (for example, the calendar has no working times or zero efficiency in percentage).

To check that the calendar is associated with the resource or resource group, follow these steps.

1. Go to **Production control > Production orders > All production orders** and open or select the production order that can't be scheduled.
1. On the Action Pane, on the **Production order** tab, in the **Production details** group, select **Route**.
1. On the **Production route** page, select the operation and then select **Applicable resources** on the Action Pane.
1. The **Applicable resources** dialog opens. Select the resource and then select **View resource** on the toolbar (or right-click in the **Resource group** field and then select **View details** option).
1. On the **Resources** page or **Resource groups** page, expand the **Calendars** FastTab to make sure there is a calendar associated with the resource or resource group.

> [!NOTE]
> If the error occurs during operation scheduling, you need to make sure that a calendar is associated with all applicable resource groups.

To check the setup of the calendar, follow these steps.

1. Go to **Organization administration > Setup > Calendars > Calendars**.
1. Select the calendar that is associated with the resource or resource group and then select **Working times** on the Action Pane.
1. On the **Working times** page, make sure the page is not empty and that, for the days you are interested in, the **Control** field value is not set to *Closed*, working times exist, and the **Efficiency is percentage** field value is not set to *0*.

If the calendar is associated with the base calendar, you must check the setup of the base calendar as well.

> [!NOTE]
> In operation scheduling, the resource group's calendar is used to determine the start and end times and dates for each operation. It also puts a limit on how much time the system can schedule for one specific operation for one specific day in one specific resource group. For example, if the working times for a resource group on one specific day is from 8:00 AM till 4:00 PM, then one operation can't put more load on the resource group than what can be fit into eight hours, no matter how much capacity the resource group has available on that day. The available capacity can, however, limit the load further.

## Review scheduling parameters

To ensure good performance, the scheduling engine will only search for a resource for a certain amount of time and for a certain number of scheduling conflicts.

To review the scheduling parameters, follow these steps.

1. Go to **Organization administration > Setup > Scheduling parameters**.
1. Do one of the following:
    - If **Scheduling timeout enabled** is set to *No*, then skip this step.
    - If **Scheduling timeout enabled** is set to *Yes*, then increase the **Maximum scheduling time per sequence** setting to allow more time for the processing to complete.
1. Do one of the following:
    - If **Scheduling optimization timeout enabled** is set to *No*, then skip this step.
    - If **Scheduling optimization timeout enabled** is set to *Yes*, then increase the **Optimization attempts timeout** setting setting to allow more time for the processing to complete.
1. If you changed any of the settings on this page, then reschedule the order to try again.

## Review capacity

The error can occur when there is no free capacity and you perform finite scheduling.

To perform infinite capacity scheduling, follow these steps.

1. Go to **Production control > Production orders > All production orders** and select or open the production order that can't be scheduled.
1. On the Action Pane, on the **Schedule** tab, in the **Production order** group, select **Schedule operations** or **Schedule jobs**.
1. On the **Operations scheduling** or **Jobs scheduling** dialog, set **Finite capacity** to *No*.
1. Select **OK** to schedule the order.

To check available capacity on the resource, follow these steps.

1. Go to **Organization administration > Resources > Resources**.
1. On the **Resources** page, select a resource that is applicable to the order that can't be scheduled.
1. On the Action Pane, on the **Resource** tab, in the **View** group, select **Capacity load** or **Capacity load, graphically** to make sure there is available capacity.

To check available capacity on the resource group, follow these steps.

1. Go to **Organization administration > Resources > Resource groups**.
1. On the **Resource groups** page, select a resource group that is applicable to the order that can't be scheduled.
1. On the Action Pane, on the **Resource group** tab, in the **View** group, select **Capacity load** or **Capacity load, graphically** to make sure there is available capacity.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]