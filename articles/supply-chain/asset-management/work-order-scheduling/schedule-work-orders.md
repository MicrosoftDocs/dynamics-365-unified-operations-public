---
title: Schedule work orders
description: Learn how to schedule work orders in Asset Management. This article includes an outline of scores that are used in work order scheduling, and examples.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form: EntAssetWorkOrderSchdulePreviewPart, EntAssetWorkOrderScheduleExclusively, EntAssetWorkOrderSchduleInfoPart, EntAssetWorkOrderScheduleListPage, EntAssetWorkOrderSchedule, EntAssetWorkOrderScheduleDelete
ms.topic: how-to
ms.date: 01/27/2025
ms.custom: 
  - bap-template
---

# Schedule work orders

[!include [banner](../../includes/banner.md)]

This article explains how to schedule work orders in Asset Management.

The required number of hours for a work order is defined by the sum of forecasted hours minus posted hours. If more time is required, the forecast must be adjusted accordingly. On the **All work orders** page (**Asset management** \> **Work orders** \> **All work orders**) or the **Active work orders** page (**Asset management** \> **Work orders** \> **Active work orders**), you can view or edit forecasts on a work order. Select the work order, and then, on the **Work order** tab, select **Forecast**. After work orders are created and estimated, the next step is to allocate the required maintenance workers and tools.

> [!IMPORTANT]
> Work orders can be scheduled only if their work order lifecycle state allows for scheduling. To set up a lifecycle state so that it allows for scheduling, go to **Asset management** \> **Setup** \> **Work orders** \> **Lifecycle states**, and then, on **General** FastTab, set the **Allow scheduling** option to *Yes*.

1. Go to **Asset management** \> **Work orders** \> **All work orders**.
1. In the list, select the work orders that you want to schedule. To find the correct work orders, you can sort the list by **Current lifecycle state** value, for example.
1. On the **General** tab, select **Schedule**.
1. In the **Schedule work orders** dialog box, you can add selections that are related to the expected start date and service level, as you require. If the scheduling process should observe capacity limitations for resources that are already scheduled for other jobs, make sure that the **Asset**, **Tool**, and **Worker** options are set to *Yes*.

    > [!NOTE]
    > If you set the **Asset**, **Tool**, and **Worker** options to *No*, existing reservations are ignored. The Action center shows a list of overlapping work order schedules. As you require, you can select a message link to open a work order and reschedule it.

1. To view detailed information about the scheduling process, set the **Verbose** option to *Yes*. In this case, the Action center shows detailed information about the calculated scores on the work orders and maintenance workers.
1. Select **OK** to start the work order scheduling process.
1. When scheduling is completed, a message in the Action center shows the number of work orders that were scheduled. If you set the **Verbose** option to *Yes*, the Action center also shows more detailed information.

> [!NOTE]
> Work orders are scheduled in one cycle per work order, not per work order job.
>
> You can also open the **Schedule work orders** dialog box by going to **Asset management** \> **Periodic** \> **Work orders** \> **Schedule work orders**. Make your selections, and then select **OK** to start the work order scheduling process.
>
> On the **Run in the background** FastTab of the **Schedule work orders** dialog box, you can set up work order scheduling as a batch job.

**Example**

In the following illustration, the **Expected start** field in the **Schedule work orders** dialog box is set to the formula `(greaterThanUtcDate(7))`. This formula generates work order scheduling for all work orders where the expected start date is one week from the current date and later. This formula can be useful when you run work order scheduling on an ongoing basis, but you want to ensure that work orders that are scheduled for the next five to six days aren't rescheduled.

![Screenshot of Schedule work orders dialog box where the Expected start field is set to the formula (greaterThanUtcDate(7)).](media/03-work-order-scheduling.png)

On the **Work order types** page (**Asset management** \> **Setup** \> **Work orders** \> **Work order types**), if the **One maintenance worker** option is set to *Yes* for a work order type, that work order type sets up scheduling for a single maintenance worker. If that work order type is used on a work order, the **One maintenance worker** option is automatically set to *Yes* on the **Schedule** FastTab in the **Header** view of the **All work orders** details page. Then, during work order scheduling, all work order jobs that are created on the work order are scheduled to the same maintenance worker. As you require, you can change the setting of the **One maintenance worker** option on the **All work orders** details page to enable either multiple workers or one worker to be scheduled on the work order jobs.

The scheduling process in Asset Management includes several factors in the scheduling calculation:

- Calculating scores for both work orders and maintenance workers. Scores for work orders and maintenance workers are set up in Asset management parameters.
- Checking for matching competencies (that is, skills and certificates) that are required to perform the job. Skills and certificates are set up on maintenance workers in the **Human resources** module. (Go to **Human resources** \> **Workers** \> **Workers**, select a worker in the list, and then, on the **Worker** tab, in the **Competencies** section, select the **Skills** and **Certificates** buttons.) Skills and certificates can also be added to maintenance job types and maintenance job trades. Learn more about competencies and maintenance job types in [Maintenance job type categories and maintenance job types, maintenance job type variants, maintenance job trades, and maintenance checklists](../setup-for-work-orders/job-groups-and-job-types-variants-trades-and-checklists.md).

## Scores used in work order scheduling

Calculating scores for a work order job is based on the expected start date and service level of the work order.

- **Start date calculation** – For every future date that is calculated from the expected start date, the start date score is subtracted and multiplied by the score. (In the examples that follow, the score is *10*.)
- **Criticality calculation** – The criticality score is multiplied by the criticality on the work order.
- **Service level calculation** – The service level score is divided by the service level on the work order.

In the following examples, the criticality score is *2*, and the service level scores are *5* and *100*.

**Example 1**

| Work order ID | Expected start date | Work order criticality | Work order service level | Calculation | Score |
|---|---|---|---|---|---|
| WO-00010816 | Tomorrow | 2 | 20 | (-1 &times; 10) + (2 &times; 2) + (5 &divide; 20) | -5.75 |
| WO-00010817 | Two days from now | 2 | 20 | (-2 &times; 10) + (2 &times; 2) + (5 &divide; 20) | -15.75 |
| WO-00010818 | Two days from now | 3 | 5 | (-2 &times; 10) + (2 &times; 3) + (5 &divide; 5) | -13 |

The work orders will be scheduled in the following order: WO-000108**16**, WO-000108**18**, WO-000108**17**.

**Example 2**

| Work order ID | Expected start date | Work order criticality | Work order service level | Calculation | Score |
|---|---|---|---|---|---|
| WO-00010816 | Tomorrow | 2 | 20 | (-1 &times; 10) + (2 &times; 2) + (100 &divide; 20) | -1 |
| WO-00010817 | Two days from now | 2 | 20 | (-2 &times; 10) + (2 &times; 2) + (100 &divide; 20) | -11 |
| WO-00010818 | Two days from now | 3 | 5 | (-2 &times; 10) + (2 &times; 3) + (100 &divide; 5) | 6 |

If the service level score is increased from *5* to *100*, the scheduling order will be WO-000108**18**, WO-000108**16**, WO-000108**17**.

All the rating scores that are related to calculating which maintenance workers should work on the work orders are set up as numbers. Those numbers are then added to each maintenance worker calculation during work order scheduling. The maintenance worker who has the highest score is selected for the work order. The following table provides a short description of the maintenance worker scores.

| Maintenance worker score | Description |
|---|---|
| Responsible worker | If the maintenance worker is selected as the responsible worker on the work order, the score is added. |
| Responsible maintenance worker group | If the maintenance worker is part of the responsible maintenance worker group on the work order, the score is added. |
| Preferred maintenance worker | If the worker is selected as the preferred maintenance worker on the asset, the score is added. |
| Preferred maintenance worker group | If the worker is part of the preferred maintenance worker group on the asset, the score is added. |
| Location | <p>If your company uses functional locations, maintenance workers get the full score if they are in the functional location that is related to the asset. If the functional location of the asset has a parent location, maintenance workers in that functional location get one-half of the full score. If that location also has a parent, maintenance workers in that location get one-third of the full score. If that location also has a parent, maintenance workers in that location get one-quarter of the full score, and so on.</p><p>If your company uses asset locations, which we don't recommend, the location, area, and zone are used to calculate location scores. Maintenance workers get the full score if they are in the location, area, and zone that are related to the asset. If the maintenance worker location matches only the location and area, the rating score for the maintenance worker is two-thirds of the full score. If the maintenance worker location matches only the location, the rating score for the maintenance worker is one-third of the full score.</p> |
| Worker's start date | For every date that the scheduled start date is later than the expected start date, the score is subtracted. |

> [!NOTE]
> If a score is set to *0*, that score isn't calculated. This behavior is useful if, for example, you don't want to include a responsible worker in your scheduling.

## Competencies used in work order scheduling

Skills and certificate requirements can be set up on maintenance job types (**Asset management** \> **Setup** \> **Jobs** \> **Maintenance job types**) and maintenance job trades (**Asset management** \> **Setup** \> **Jobs** \> **Maintenance job trade**).

Maintenance job types and maintenance job trades are selected on work order jobs. If skills or certificates have been selected on a maintenance job type or maintenance job trade, and that maintenance job type or maintenance job trade is used on a work order job, only maintenance workers with matching skills and certificates are scheduled to work on the work order.

## <a name="gantt"></a>Work with scheduled work orders using a Gantt chart

The **Scheduled work orders gantt chart** provides a graphical interface where you can view and reschedule your work orders.

To view and work with the Gantt chart:

1. Go to **Asset management** \> **Work orders** \> **Scheduled work orders gantt chart**.
1. Use the drop-down lists and fields in the **Settings** section to set up which functional location, time span, and time scale to show in the Gantt chart.
1. Select **Apply**.

    - The Gantt chart updates to show the scheduled work orders that match your settings. Each work order is represented by a blue rectangle.
    - To reschedule a displayed work order, select and then drag it to the appropriate new date and time.

1. If you made any changes, select **Save** on the Action Pane to save them.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
