---
# required metadata

title: Pay based on registrations
description: This topic describes how how pay is calculated based on workers’ registrations.
author: johanhoffmann
manager: AnnBe
ms.date: 03/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: JmgCalcApproveWeekView
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: bis
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 1705903
ms.assetid: 427e01b3-4968-4cff-9b85-1717530f72e4
ms.search.region: Global
# ms.search.industry: 
ms.author: johanho
ms.search.validFrom: 2018-03-20
ms.dyn365.ops.version: AX 8.0.0
---

# Pay based on registrations

[!include[banner](../includes/banner.md)]

This topic provides a detailed description of how pay is calculated based on
workers’ registrations and you’ll see examples of how the various combinations
of setup options that are available for the calculation will affect the result.
Here are some of the areas that will be covered:

-   Flex time

-   Overtime

-   Break

-   Switch codes

-   Pay items

-   Pay agreements

-   Time and attendance calculation parameters

-   Absence

## The use of Flex time

Periods of flex time are set up in the time profiles that are used in Time and
attendance. There are two flex profile types: **Flex+** and **Flex-**.
When a worker registers time in a Flex+ period, the worker’s flex balance is
increased with the hours worked. The worker will not receive any compensation
for the hours worked in the Flex+ period but he can take time off in the
Flex- periods and be compensated with the hours from his flex balance. So time
off in the flex periods is not considered as absence by the system.

## Scenarios based on flex periods

The two scenarios below are based on a flex profile that represents a work day.
For both of the scenarios, pay is calculated according to the flex period where
the worker clocks in and out.

### Flex profile for one work day

| **Profile type** | **Start** | **End**  | **Day** |
|------------------|-----------|----------|---------|
| Over time        | 00:00 AM  | 06:00 AM | Monday  |
| Flex+            | 06:00 AM  | 07:00 AM | Monday  |
| Clock in         | 07:00 AM  | 07:00 AM | Monday  |
| Standard time    | 07:00 AM  | 02:30 PM | Monday  |
| Flex-            | 02:30 PM  | 03:30 PM | Monday  |
| Clock out        | 03:30 PM  | 03:30 PM | Monday  |
| Over time        | 03:30 PM  | 06:00 AM | Tuesday |

### Scenario 1 – A worker registers clock-in in a Flex+ period and clock-out in a
Flex- period  
  
The worker’s registration for the day:

| **Journal registration type** | **Start** | **End**  |
|-------------------------------|-----------|----------|
| Clock in                      | 06:30 AM  | 06:30 AM |
| Production job                | 06:30 AM  | 02:45 PM |
| Clock out                     | 02:45 PM  | 02:45 PM |

The worker's registration for the day is calculated and transferred to pay on the
**Approve** page. When the registration has been calculated, the result of the
calculation is visible under the **Times** tab. 

For an understanding of this scenario, see the following fields:

| **Flex +**  | **Flex -** | **Time** | **Pay time** |
|-------------|------------|----------|--------------|
| 0.50        | 0.75       | 8.25     | 8.50         |
-   To access the **Approve** page, click **Time and attendance**, and then click
    **Approve** under **Review and approve**.

### Calculation of Flex+

If the worker clocks-in at 06:30 AM, he earns 0.5 hours because, according to
the profile, the time between 06:00 AM and 07:00 AM is a Flex+ period. The 0.5
hours are added to the workers flex account.

### Calculation of Flex-

If the worker clocks-out at 02:45 PM, the 45 minutes from 02:45 to 03:30 will be
registered as pay time and the same amount of time will be deducted from his
flex account. This is because the Flex- period starts at 02:30 PM and ends
at 03:30 PM, so he has 45 minutes (0.75 hours) left of the Flex- period. The
worker will be granted pay for the remaining 45 minutes in the Flex- period,
which is why the 45 minutes are included as pay time. if he is absent in the Flex- period The 45 minutes will be
deducted from the worker’s flex account.

### Calculation of Time

Time is calculated as the time between clock-in and clock-out, that is, 06:30 AM
to 14:45 PM with equals 8.25 hours.

### Calculation of Pay time

Pay time is the time in which a worker is granted pay. In this scenario, the
worker is at work for 8.25 hours (Time), but the pay time is calculated to 8.50
hours. This is because the worker is granted pay in the Flex- period after he
clocked out. The pay time equals the planned work hours since Flex+ is added to
the worker’s flex account and not to the pay time. The absence time in the Flex-
period is compensated with pay time and deducted on the worker’s flex account.

| **Time**          | **Registration type** | **Pay time (hours)**  |
|-------------------|-----------------------|-----------------------|
| 6:30 AM - 7:00 AM | Flex+                 | 0                     |
| 7:00 AM – 2:45 PM | Standard time         | 7.75                  |
| 2:45 PM – 3:30 PM | Flex-                 | 0.75 (Absence period) |
|                   | Total                 | 8.50                  |

### Scenario 2 – A worker works in the complete Flex- period and works overtime

The worker’s registrations for the day

| **Journal registration type** | **Start** | **End**  |
|-------------------------------|-----------|----------|
| Clock in                      | 06:30 AM  | 06:30 AM |
| Production job                | 06:30 AM  | 05:00 PM |
| Clock out                     | 05:00 PM  | 05:00 PM |

When you have calculated the journal registrations on the **Approve** page, you
can see the calculation result under the **Times** tab. For an understanding of
this scenario, see the following fields:

| **Flex +**  | **Flex -** | **Time** | **Pay time** | **Pay overtime** |
|-------------|------------|----------|--------------|------------------|
| 0.50        | 0.00       | 10.50    | 10.00        | 1.50             |

### Calculation of Flex+

The worker clocks-in at 06:30 AM, so he earns 0.5 hours Flex+ on his flex
balance, because the time between 06:00 AM and 07:00 AM is a Flex+ period
according to the profile.

### Calculation of Flex-

The worker is working in the Flex- period, so no Flex- time will be calculated.
Flex- is only calculated if the worker is absent in the Flex- period. From a
payment perspective, the worker is granted the pay rate defined for the Standard
time if he is working the Flex- period. If the worker if is absent in the Flex- period, the 45 minutes will be
deducted from the his flex account.

### Calculation of Time

Time is calculated as the time between clock-in and clock-out at 06:30 AM to
05:00 PM which equals 10.50 hours.

### Calculation of Pay time

In this scenario, the worker works 10.50 hours (Time), but the **Pay time** is
calculated to 10.00 hours. This is because the worker is not granted pay in the
Flex+ period.

### Calculation of Pay overtime

| **Time**           | **Registration type** | **Pay time (hours)** |
|--------------------|-----------------------|----------------------|
| 6:30 AM - 7:00 AM  | Flex+                 | 0                    |
| 7:00 AM – 2:30 PM  | Standard time         | 7.50                 |
| 2:30 PM – 3:30 PM  | Flex-                 | 1.00                 |
| 3:30 PM – 05:00 PM | Overtime              | 1.50                 |
|                    | Total                 | 10.00                |

### Generation of Pay items

Workers’ registrations for the day can be transferred from the **Approve** page.
In the transfer process, pay items and transferred registrations are generated.
Pay items represent a breakdown of Pay time into Standard time, Overtime, Paid
break time etc.

-   To open the list of pay items, click **Time and attendance** \> **Approve**,
    and then click **Transferred registrations** on the **Inquiry** menu.

The pay items are the basis for a workers’ pay and a file can be generated and transferred to a payroll system with the information from the pay items.

As part of the transfer process, time and cost from production and project
activities are transferred to production and project journals to account for the
time and cost spend. The transferred registrations are the basis for time and
cost price per hour for production orders and projects. The transferred
registrations can be opened from the **Inquiry** menu on the **Approve** page.

Pay items generated with the use of the above example:

| **Wage type** | **Pay type** | **Pay units** | **Rate** | **Total cost** |
|---------------|--------------|---------------|----------|----------------|
| Standard time | 1201         | 10.0          | 10       | 100            |
| Overtime      | 1301         | 1.50          | 5        | 7.50           |
|               |              |               | Total    | 107.50         |

The pay item for standard time has a pay unit of 10 hours that covers standard
time, flex- time and overtime. Standard time, flex- time, and overtime are
consolidated into one pay item because all the types are calculated as standard
time based on the default parameter setting on the Calculation parameters page.
The overtime is calculated on top of the standard time with an additional rate
of 5.

-   To open the **Calculation parameters** page, click **Time and attendance** \> **Setup** \> **Calculation parameters**.

If you want to distinguish clearly between the standard time and overtime so
that the pay units for the pay types only cover the actual time spend on
standard time and overtime, the pay units for standard time must be calculated
to 8.50 and the pay units for overtime must be calculated to 1.50.

To configure the system to clearly distinguish between standard time and
overtime, you must exclude overtime from the standard time and change the setup
of the pay type for overtime so that the pay rate for overtime covers all
payments for the hours spent on overtime.

### Exclude overtime from the standard time

-   On the **Calculation** parameters page, select the **Overtime** profile
    specification type and set the **Pay time** field to **No** as shown below

| **Reg. specification** | **Profile specification type** | **Calculation** | **Paid** |               |        |
|------------------------|--------------------------------|-----------------|----------|---------------|--------|
| Working time           |                                | Standard time:  | Yes      | Pay time:     | **No** |
|                        | Overtime                       | Pay time:       | Yes      | Pay overtime: | Yes    |

Pay items generated after the calculation parameters are adjusted:

| **Wage type** | **Pay type** | **Pay units** | **Rate** | **Total cost** |
|---------------|--------------|---------------|----------|----------------|
| Standard time | 1201         | 8.50          | 10       | 85.0           |
| Overtime      | 1301         | 1.50          | 15       | 22.50          |
|               |              |               | Total    | 107.50         |

> [!NOTE]
The calculation parameters have a recommended standard setting, so you
should in general be careful changing the parameters. On the **Calculation
parameters** page, you can click **Restore values** to restore the recommend
standard setting.

### Allow a deviation from the standard pay profiles

Click **Time and attendance** \> **Setup** \> **Time profiles** \> **Profiles**
to open the **Profiles** page where you can set the following profile types:

### Switch codes

You can use witch codes to allow that workers deviate from their profile type by
changing from one profile type to another. You can, for example, allow a worker
to convert from Flex+ time to overtime. A worker can add a switch code during
registration, or you can make it a task of the approver of the registrations to
add the switch code.

To enable the use of the switch code, you must define it as a type of an
indirect activity. The switch code must be added to the time profile for the
time-period where you want to allow a change of the profile type. In the
following example a switch code is created that allows converting the Flex+
period from 06:00 AM to 07:00 AM to overtime. The task includes the following
steps.

-   Create a switch code called OTBCI (Convert flex to overtime before
    clock-in). Click **Time and attendance** \> **Manage indirect activities**
    \> **Indirect activities**

-   In the Switch code column, add OTBCI to the Flex+ line in the time profile.

-   In the Secondary column, add the Overtime profile type.

Consider the following Flex profile that represents a work day:

| **Profile type** | **Start** | **End**  | **Day** |
|------------------|-----------|----------|---------|
| Over time        | 00:00 AM  | 06:00 AM | Monday  |
| Flex+            | 06:00 AM  | 07:00 AM | Monday  |
| Clock in         | 07:00 AM  | 07:00 AM | Monday  |
| Standard time    | 07:00 AM  | 02:30 PM | Monday  |
| Flex-            | 02:30 PM  | 03:30 PM | Monday  |
| Clock out        | 03:30 PM  | 03:30 PM | Monday  |
| Over time        | 03:30 PM  | 06:00 AM | Tuesday |

The worker's registrations for the day:

| **Journal registration type** | **Start** | **End**  |
|-------------------------------|-----------|----------|
| Clock in                      | 06:30 AM  | 06:30 AM |
| Production job                | 06:30 AM  | 02:45 PM |
| Clock out                     | 05:00 PM  | 05:00 PM |

Pay items generated after transfer:

| **Wage type** | **Pay type** | **Pay units** | **Rate** | **Total cost** |
|---------------|--------------|---------------|----------|----------------|
| Standard time | 1201         | 8.50          | 10       | 85.0           |
| Overtime      | 1305         | 1.50          | 15       | 22.50          |
|               |              |               | Total    | 107.50         |

On the **Approve** page, undo the transfer and from the **Switch code** menu
apply the switch code OTBCI. When you transfer the registrations a second time,
you will get the following pay items:

| **Wage type** | **Pay type** | **Pay units** | **Rate** | **Total cost** |
|---------------|--------------|---------------|----------|----------------|
| Standard time | 1201         | 8.50          | 10       | 80.0           |
| Overtime      | 1305         | 2.00          | 15       | 30.0           |
|               |              |               | Total    | 107.50         |

> [!NOTE] 
When you apply the switch code, overtime is increased with 0.5 hour
from 1.50 to 2.00. The 0.5 hour is the conversion of the Flex+ time registered
from 6:30 AM to 07:00 to overtime.

### Breaks

Break from work has an impact on the calculation of the workers’ pay. A break is
defined as a type of indirect activity. The break can be defined as either
Unpaid or Paid to either allow or not allow the break to add to the workers’
pay. A break can also be defined as either Planned or Registered.

### Planned break

If a company has a fixed break time such as a fixed break for lunch, the break
can be pre-defined in the time profile. In that case, the worker does not need
to register the break in the job card pages, but the break is automatically
accounted for when calculating the worker's registrations on the **Approve**
page.

### Registered break

If a company does not use planned breaks, a worker can register breaks during
the work day. The use of registered break can, for example, be relevant if the
worker is working against a flexible time profile with no defined clock-in and
clock-out time. The registered break is a type of an indirect activity. The
break is registered by the worker on the Job card terminal page or on the Job
card device page. In these pages the user can select from a list of defined
break activities.

### Paid and unpaid breaks

The Break activity can be set up as Paid or Unpaid. If a break is set up as
Paid, it is included in the calculation of pay time and the system will use the
pay type that is defined in the pay agreement for Break registration type.

### Example of the use of Planned break

Consider the following time profile with an unpaid break for lunch.

| **Profile type** | **Start** | **End**  | **Day** |
|------------------|-----------|----------|---------|
| Over time        | 00:00 AM  | 06:00 AM | Monday  |
| Flex+            | 06:00 AM  | 07:00 AM | Monday  |
| Clock in         | 07:00 AM  | 07:00 AM | Monday  |
| Standard time    | 07:00 AM  | 12:00 PM | Monday  |
| Break            | 12:00 PM  | 12:30 PM | Monday  |
| Standard time    | 12:30 PM  | 02:30 PM | Monday  |
| Flex-            | 02:30 PM  | 03:30 PM | Monday  |
| Clock out        | 03:30 PM  | 03:30 PM | Monday  |
| Over time        | 03:30 PM  | 06:00 AM | Tuesday |

The worker's registrations for the day:

| **Journal registration type** | **Start** | **End**  |
|-------------------------------|-----------|----------|
| Clock in                      | 06:30 AM  | 06:30 AM |
| Production job                | 06:30 AM  | 02:45 PM |
| Clock out                     | 05:00 PM  | 05:00 PM |

After calculating the journal registrations, go to the calculation result under
the **Times** tab. For an understanding of this scenario, see the following
fields:

| **Flex +**  | **Flex -** | **Time** | **Pay time** | **Non-paid break time** | **Pay overtime** |
|-------------|------------|----------|--------------|-------------------------|------------------|
| 0.50        | 0.00       | 10.50    | 9.50         | 0.5                     | 1.50             |

> [!NOTE]> 
The system calculated 0.5 hours of non-paid break time and that this
time is not part of the pay time.

### Example of the use of Registered breaks

Consider the following time profile without planned breaks:

| **Profile type** | **Start** | **End**  | **Day** |
|------------------|-----------|----------|---------|
| Over time        | 00:00 AM  | 06:00 AM | Monday  |
| Flex+            | 06:00 AM  | 07:00 AM | Monday  |
| Clock in         | 07:00 AM  | 07:00 AM | Monday  |
| Standard time    | 07:00 AM  | 02:30 PM | Monday  |
| Flex-            | 02:30 PM  | 03:30 PM | Monday  |
| Clock out        | 03:30 PM  | 03:30 PM | Monday  |
| Over time        | 03:30 PM  | 06:00 AM | Tuesday |

The workers registrations for the day:

| **Journal registration type** | **Start** | **End**  |
|-------------------------------|-----------|----------|
| Clock in                      | 06:30 AM  | 06:30 AM |
| Production job                | 06:30 AM  | 05:00 PM |
| Break                         | 12:03 PM  | 12:32 PM |
| Clock out                     | 05:00 PM  | 05:00 PM |

When the registrations are calculated, the time for the activities are
calculated:

| **Journal registration type** | **Start** | **End**  | **Time** |
|-------------------------------|-----------|----------|----------|
| Clock in                      | 06:30 AM  | 06:30 AM |          |
| Production job                | 06:30 AM  | 05:00 PM | 10.00    |
| Break                         | 12:03 PM  | 12:32 PM | 0.50     |
| Clock out                     | 05:00 PM  | 05:00 PM |          |

[!NOTE]
The break time runs in parallel time with an activity, in this case a
production job. This is always the case for break activities. When the
registrations are calculated, the break time will be subtracted from the
activity time. In this case the production job has a duration of 10.50 hours,
but the time is calculated to 10 because 0.5 hours or break is subtracted from
the activity time.

After calculating the journal registrations, go to the calculation result under
the **Times** tab. For an understanding of this scenario, see the following
fields:

| **Flex +**  | **Flex -** | **Time** | **Pay time** | **Non-paid break time** | **Pay overtime** |
|-------------|------------|----------|--------------|-------------------------|------------------|
| 0.50        | 0.00       | 10.50    | 9.50         | 0.5                     | 1.50             |

If the planned break had been paid rather than non-paid, the resulting
calculation would look like this:

| **Flex +**  | **Flex -** | **Time** | **Pay time** | **Paid break time** | **Pay overtime** |
|-------------|------------|----------|--------------|---------------------|------------------|
| 0.50        | 0.00       | 10.50    | 10.00        | 0.5                 | 1.50             |

### Pay items and paid breaks

When you transfer registrations in the **Approve** form, pay items are
generated. For paid breaks, a separate pay item will be generated.

The pay rate for a paid break is determined by the pay type that is set up in
the pay agreements for the break. Instead of using a pay type, you can set up
the cost price per hour on the break for a defined date interval.

Consider following time profile

| **Profile type** | **Start** | **End**  | **Day** |
|------------------|-----------|----------|---------|
| Over time        | 00:00 AM  | 06:00 AM | Monday  |
| Flex+            | 06:00 AM  | 07:00 AM | Monday  |
| Clock in         | 07:00 AM  | 07:00 AM | Monday  |
| Standard time    | 07:00 AM  | 02:30 PM | Monday  |
| Flex-            | 02:30 PM  | 03:30 PM | Monday  |
| Clock out        | 03:30 PM  | 03:30 PM | Monday  |
| Over time        | 03:30 PM  | 06:00 AM | Tuesday |

The worker's registrations for the day:

| **Journal registration type** | **Start** | **End**  | **Time** |
|-------------------------------|-----------|----------|----------|
| Clock in                      | 07:00 AM  | 07:00 AM |          |
| Production job                | 07:00 AM  | 03:00 PM | 7.5      |
| Break (Paid)                  | 12:00 PM  | 12:30 PM | 0.5      |
| Clock out                     | 03:00 PM  | 03:00 PM |          |

For this example, the pay type for Standard time is set to 1201 with a pay rate
of 10 in the pay agreement. The paid break has a pay type of 1301 with a pay
rate of 8. When the registrations are transferred the following pay items will
be generated.

| **Wage type** | **Pay type** | **Pay units** | **Rate** |
|---------------|--------------|---------------|----------|
| Standard time | 1201         | 7.50          | 10       |
| Flex-         | 1201         | 0.50          | 10       |
| Break (Paid)  | 1301         | 0.50          | 8        |

## How the cost of paid breaks is allocated to projects and production orders**

The hourly cost on project activities and production jobs can be set up to be
determined by the pay rates calculated in Time and attendance or by the cost
categories defined for the activities.

-   To set up the cost category, click **Production control** \> **Setup** \>
    **Manufacturing execution** \> **Production order defaults** and set the **Cost
    category** field to either **Yes** or **No**.

-  - If set to **No**, cost is calculated based on pay rates defined for Time and
    attendance registration types.

-  - If set to **Yes**, cost is calculated based on cost categories for production
    and project activities.

Cost calculation based on pay rates calculated in Time and attendance

The following example illustrates how the hourly cost is calculated when the
cost is set up to be calculated based on pay rates.

The hourly cost rate that is used for production orders and projects is
calculated in the transfer process. To view hourly rate per activity, open the
**Approve** page in **Time and attendance**, and then click **Inquiry** \> **Transferred
registrations**. The hourly cost rate per registration is found under the **Cost
prices** tab.

Consider the following registrations using the same time profile as in the previous
example:

| **Journal registration type** | **Start** | **End**  | **Time** |
|-------------------------------|-----------|----------|----------|
| Clock in                      | 07:00 AM  | 07:00 AM |          |
| Process (Order: 4711)         | 07:00 AM  | 11:00 AM | 4        |
| Process (Order: 4712)         | 11:00 AM  | 03:00 PM | 3.50     |
| Break (Paid)                  | 12:00 PM  | 12:30 PM | 0.50     |
| Clock out                     | 03:00 PM  | 03:00 PM |          |

After transferring the registrations, the following transferred registrations
are generated:

| **Registration type** | **Time** | **Cost price per hour** |
|-----------------------|----------|-------------------------|
| Clock-in              | 0.00     | 0.00                    |
| Process (Order: 4711) | 4.00     | 10.00                   |
| Process (Order: 4712) | 3.50     | 11.14                   |
| Break (Paid)          | 0.50     | 0.00                    |
| Clock out             | 0.00     | 0.00                    |

The calculation of cost price per hour for the paid break depends on a setting
of the direct payroll costs.

-   To set up the direct payroll costs, click **Time and attendance** \>
    **Setup** \> **Time and attendance parameters** and open the **Cost price**
    tab. In the **Standard time** field under **Direct payroll costs** you can
    select Yes, No, and Allocation. See the following sections for at
    description of each of these options.

**Yes**

In the above example, the cost is calculated with the direct payroll costs
parameter set to **Yes**. The cost is allocated to the production or project
activity that runs in parallel with the paid break activity which is the
production job for order 4712. As it can be seen, the cost price per hour for
the paid break is zero and it is allocated to the job that runs in parallel with
the break.

The paid break has a duration of 0.5 hour and the pay rate is 8 so the total
cost is 4 for the paid break. The total cost is then allocated to the 3.5 hour
process job which means that the paid break contributes to the cost with 4/3.5 =
1.14 per hour.

**Allocation**

Select the **Allocation** method to have the paid break be equally distributed
to the jobs registered for the day. This method will generate the following
transferred registrations.

| **Registration type** | **Time** | **Cost price per hour** |
|-----------------------|----------|-------------------------|
| Clock-in              | 0.00     | 0.00                    |
| Process (Order: 4711) | 4.00     | 10.53                   |
| Process (Order: 4712) | 3.50     | 10.53                   |
| Break (Paid)          | 0.50     | 0.00                    |
| Clock out             | 0.00     | 0.00                    |

The total process time for the two production jobs is 7.5 hours. The total cost
of the paid break is 4, so the cost of the break is calculated to 4 / 7.5 = 0.53

**No**

The cost of the paid break will not add to the hourly cost of the process
activities

| **Registration type** | **Time** | **Cost price per hour** |
|-----------------------|----------|-------------------------|
| Clock-in              | 0.00     | 0.00                    |
| Process (Order: 4711) | 4.00     | 10.00                   |
| Process (Order: 4712) | 3.50     | 10.00                   |
| Break (Paid)          | 0.50     | 0.00                    |
| Clock out             | 0.00     | 0.00                    |

**Absence**

An absence code is used for the registration of a period for workers’ absence.
An absence code is, like breaks and switch codes, a type of an indirect
activity. Absence time can be either planned or registered, and absence can be
legal or illegal. Legal absence can, for example, be a doctor’s appointment, a
seminar or jury duty. Illegal absence is absence with no good reason such as
being late for work. Legal absence normally does not affect a deduction in
workers’ pay whereas illegal does.

**Planned absence**

Workers’ planned absence can be created on the **Create planned absence** page
where the planned absence is registered as an absence job for a specified date
and time interval.

-   Click **Time and attendance** \> **Create planned absence** to open the
    **Create planned absence** page.

The job is based on a query, so you can create planned absence for multiple
workers such as workers that belong to the same calculation group. If the
planned absence is only for a single worker, the registration can be entered
from the **Attendance** page or from the **Time registration workers** page.

-   Click **Time and attendance** \> **Inquiries and reports** \> **Attendance**
    \> **Attendance**, and then click **Absence registration**.

-   Click **Time and attendance** \> **Setup** \> **Time registration workers**,
    and then click **Absence registrations** under **Time assignment** on the
    **Time tab** page.

Use the report **Planned absences** for an overview of planned absences for
workers.

Click **Time and attendance** \> **Inquiries and reports** \> **Absence
reports** \> **Planned absences** to open the **Planned absences** report.

**Registered absence**

In general, a worker is regarded as absent for the time where he is not at work
during his planned clock-in and clock-out. If a worker clocks in later than
planned or clocks out earlier, he will be prompted to select an absence code for
the reason for being absent. An absence code can be set up to be applicable
registration and only applicable codes will be shown in the list.

Scenarios based on various combinations of work hour registrations

The following scenarios illustrate what pay items and entries for approval are
generated for workers based on their registrations.

| **Profile type** | **Start** | **End**  | **Day** |
|------------------|-----------|----------|---------|
| Over time        | 00:00 AM  | 06:00 AM | Monday  |
| Flex+            | 06:00 AM  | 07:00 AM | Monday  |
| Clock in         | 07:00 AM  | 07:00 AM | Monday  |
| Standard time    | 07:00 AM  | 02:30 PM | Monday  |
| Flex-            | 02:30 PM  | 03:30 PM | Monday  |
| Clock out        | 03:30 PM  | 03:30 PM | Monday  |
| Over time        | 03:30 PM  | 06:00 AM | Tuesday |

**Scenario 1 – The worker clocks in later than planned**

The worker clocks in at 08:30 AM, and since his planned clock-in time is 07:00
AM, he is 1.50 hour late for work. The 1.50 hour is regarded as absence time, so
the worker is prompted to provide an absence code. The worker leaves work at
03:30 PM. When the worker’s registrations are calculated and approved, the
absence registration with the absence code that the worker selected at clock-in
will appear for the time between 07:00 AM and 08:30 AM.

You can set up a tolerance for being late at work on the Clock-in registration
type in the time profile. For example, if a tolerance of 5 is set up, then the
worker will only be prompted for absence if he is clocking in later than 07:05
AM. In this case, the worker is late for work with no good reason, so he selects
an absence code defined for illegal absence. An absence code is considered
applicable for illegal absence if the **Deduct overtime** check box is selected
on the absence group for the absence code.

-   Click **Time and attendance** \> **Setup** \> **Groups** \> **Absence
    groups** and then select the **Deduct overtime** check box to set the
    setting for overtime deduction.

This is how the worker’s registrations for the day will appear on the
**Approve** page after calculation:

| **Journal registration type**     | **Start** | **End**  | **Time** |
|-----------------------------------|-----------|----------|----------|
| Absence (illegal - late for work) | 07:00 AM  | 08:30 AM | 1.5      |
| Clock in                          | 08:30 AM  | 08:30 AM |          |
| Production job                    | 07:30 AM  | 03:30 PM | 7.0      |
| Clock out                         | 03:30 PM  | 03:30 PM |          |

The resulting pay item after transfer:

| **Wage type** | **Pay type** | **Pay units** | **Rate** |
|---------------|--------------|---------------|----------|
| Standard time | 1201         | 7.00          | 10       |

**Scenario 2 – The worker clocks out before planned clock-out in a Standard-time
period**

The worker clocks in at 07:00 AM and clocks out early at 01:00 PM. As 01:00 PM
is before planned clock-out at 03:30 PM and 01:00 AM is in a standard-time
period, the worker is prompted to provide an absence code. The worker selects an
absence code for a doctor’s appointment, which is defined as legal absence. The
pay rate for legal absence is defined in the **Pay agreements** for the
registration type **Absence**.

-   Click **Time and attendance** \> **Setup** \> **Payroll** \> **Pay
    agreements**

| **Journal registration type**          | **Start** | **End**  | **Time** |
|----------------------------------------|-----------|----------|----------|
| Clock in                               | 07:00 AM  | 07:00 AM |          |
| Production job                         | 07:00 AM  | 01:00 PM | 4.0      |
| Clock out                              | 01:00 PM  | 01:00 PM |          |
| Absence (legal – doctor’s appointment) | 01:00 PM  | 03:30 PM | 3.5      |

The resulting pay item after transfer

| **Wage type** | **Pay type** | **Pay units** | **Rate** |
|---------------|--------------|---------------|----------|
| Standard time | 1201         | 7.50          | 10       |

**Scenario 3 – The worker clocks out in a Flex- period before planned
clock-out**

The worker clocks in at 07:00 AM and clocks out at 02:15 PM which is in the
planned Flex- period. The time between the clock-out and the planned clock-out
is not regarded as absence and the worker is not prompted to provide an absence
code. The amount will be deducted from the worker’s flex account, and he will be
granted pay in the remaining part of the Flex- period from 02:15 to 03:30 PM.

| **Journal registration type** | **Start** | **End**  | **Time** |
|-------------------------------|-----------|----------|----------|
| Clock in                      | 07:00 AM  | 07:00 AM |          |
| Production job                | 07:00 AM  | 02:15 PM | 7.25     |
| Clock out                     | 02:15 PM  | 02:15 PM |          |

The resulting pay item after transfer:

| **Wage type** | **Pay type** | **Pay units** | **Rate** |
|---------------|--------------|---------------|----------|
| Standard time | 1201         | 8.50          | 10       |

**Scenario 4 – The worker clocks-in late and clocks-out in an overtime period
after planned clock-out**

The worker clocks in late at 09:30 AM and to compensate for his late attendance,
he works overtime and clocks out at 05:00 PM. In this case, the company does not
want to grant the worker overtime pay for the hours he worked between planned
clock out at 03:30 PM and his actual clock-out at 05:00 PM, even though this
period is defined as overtime in the time profile. This is because the worker
came in late and compensated by working longer. The absence code can be set up
to reduce overtime hours with any hours of illegal absence that the worker has
on the same day.

-   Click **Time and attendance** \> **Setup** \> **Groups** \> **Absence
    groups** and select the **Deduct overtime** check box to deduct overtime
    from hours of illegal absence.

This is how the worker’s registrations for the day will appear on the
**Approve** page after calculation:

| **Journal registration type**     | **Start** | **End**  | **Time** |
|-----------------------------------|-----------|----------|----------|
| Absence (illegal - late for work) | 07:00 AM  | 09:30 AM | 1.5      |
| Clock in                          | 09:30 AM  | 09:30 AM |          |
| Production job                    | 09:30 AM  | 05:00 PM | 7.5      |
| Clock out                         | 05:30 PM  | 05:30 PM |          |

If the selected Absence code is set to **Deduct overtime = No**, the overtime
payment is granted to the worker even though he was late with illegal absence.
This can be seen from the Pay items generated after transfer in the Approve form

| **Wage type** | **Pay type** | **Pay units** | **Rate** |
|---------------|--------------|---------------|----------|
| Standard time | 1201         | 7.50          | 10       |
| Overtime      | 1301         | 2.0           | 15       |

If the selected absence code is set to deduct overtime, the overtime payment is
deducted with the hours the worker was illegally absent. This appears from the
pay items that are generated after the registrations have been transferred:

| **Wage type** | **Pay type** | **Pay units** | **Rate** |
|---------------|--------------|---------------|----------|
| Standard time | 1201         | 9.00          | 10       |
| Overtime      | 1301         | 0.5           | 15       |

In this case, the 1.5 hours of illegal absence from 07:00 AM to 09:30 AM will
deduct the 2.0 hours of overtime from 03:30 PM to 05:30 PM and the result of the
registration will be 1.5 hours of standard time and 0.5 hours of overtime.

**Scenario 5 – The worker clocks out before planned clock-out and can convert
the absence period to a Flex- period**

The following example illustrates how a worker’s flex account can be reduced by
converting the absence period to a Flex- period:

The worker clocks in at 07:00 AM and clocks out at 01:00 PM. He agrees with his
supervisor that he can go home for weekend if he deducts these hours from his
flex account. When the worker clocks out at 01:00 PM, he is prompted to provide
an absence code for absence. This is because the period of absence for the
remaining part of the day that this will effect is not in a planned Flex-
period. To convert the remaining part of the work day to a Flex- period, the
worker can select an absence code that is set up to reduce his flex account.

-   Click **Time and attendance** \> **Setup** \> **Groups** \> **Absence
    groups** and select the **Reduce flex** check box to reduce the balance of
    flexible hours for workers who register absence on a work day.

This is how the workers registrations for the day will appear on the **Approve**
page before calculation

| **Journal registration type** | **Start** | **End**  | **Time** |
|-------------------------------|-----------|----------|----------|
| Clock in                      | 07:00 AM  | 07:00 AM |          |
| Production job                | 07:00 AM  | 01:00 PM | 6.0      |
| Clock out                     | 01:00 PM  | 01:00 PM |          |

If the user selects an absence code for illegal absence this is how the
resulting pay item will look after the registration has been transferred:

| **Wage type** | **Pay type** | **Pay units** | **Rate** |
|---------------|--------------|---------------|----------|
| Standard time | 1201         | 6.00          | 10       |

If the worker selects and absence code for legal absence that is set up to
reduce his flex account, the resulting pay items after transfer will look like
this:

| **Wage type** | **Pay type** | **Pay units** | **Rate** |
|---------------|--------------|---------------|----------|
| Standard time | 1201         | 8.50          | 10       |

In this case, the workers flex balance will be reduced with the hours from where
he clocks-out to the time of planned clock-out, that is 2.5 hours from 01:00 PM
to 03:30 PM.

**Note**: It is not recommended to use absence codes where both the **Deduct
flex** and the **Deduct overtime** check box is selected because that will
convert the worker’s overtime hours with the illegal hours and reduce his flex
account at the same time.

**Scenario 6 – No planned absence for the day and no workers attendance for the
day**

If the worker does not show up at work on a work day and there is no planned
absence for the worker for this day, a default absence code will be used for the
calculation of the worker’s registrations.

-   To define a default absence code, click **Time and attendance** \> **Time
    and attendance parameters**.

>   The following two absence codes can be defined in the parameters:

-   Auto insert Flex-

-   Auto insert absence

When the daily registrations are calculated for a worker that is enabled for
flexible hours, then the absence code specified in **Auto insert flex-** is
defaulted. If the worker is not enabled for flexible hours, then the absence
code specified in **Auto insert absence** is defaulted. If a company has a
combination of workers that are enabled for flexible hours and workers that are
not enabled for flexible hours, then both parameters need to be set up.
