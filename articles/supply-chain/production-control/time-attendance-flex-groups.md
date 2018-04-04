---
# required metadata

title: Flex groups
description: This topic describes the use of flex groups in time and attendance.
author: johanhoffmann
manager: AnnBe
ms.date: 03/15/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: JmgFlexGroup 
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
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 8.0.0
---

# Flex groups

[!include[banner](../includes/banner.md)]

Flexible hours can be used by companies to minimize payment for overtime by
offering workers extra time off in periods where the workload is low. This is,
for example, relevant in segments with seasonal changes in workload.

You can use flex groups to set the following rules and principles for a worker’s
flexible hours.

-   Rules for flex regulations

-   Principle for calculating the worker’s flex balance

### Set up flexible working hours in flex groups

-   Select **Time and attendance** \> **Setup** \> **Groups**\> **Flex groups**
    to set up flex groups for flexible working hours.

### Associate workers with flex groups

-   Select **Time and attendance \> Setup \> Time registration workers**

### Rules for flex regulations

You can use rules for flex regulations to define an allowed minimum and maximum
for the worker’s flex account. The allowed minimum and maximum flex limits are
set up on the flex group. When the tolerance is exceeded, a worker’s flex
balance and pay can be adjusted.

If a worker’s allowed minimum is exceeded, you can adjust as follows by making a
flex regulation:

-   The worker’s flex account can be adjusted to the specified allowed minimum
    without deducting the worker’s pay for the hours that the account is below
    the minimum.

-   The number of hours that the worker has exceeded the allowed minimum can be
    set up to deduct the worker’s pay with a generation of pay items for a
    specific pay type and with a negative or a positive pay unit.

If the worker’s allowed maximum is exceeded, you can adjust as follows by making
a flex regulation:

-   The worker’s flex account will be adjusted back to the specified allowed
    maximum without compensating the worker’s pay for the hours worked above the
    maximum.

-   The number of hours that the worker has exceeded the allowed maximum can be
    set up to be converted to pay with generation of a pay items for a specific
    pay type.

Flex regulations can be completed by the following actions.

-   When a payment file, based on the payroll data, is exported with the
    **Transfer pay** job. The payroll data are generated when you transfer the
    worker’s registration from the **Approve** page.

-   When the **Flex adjustment** job is processed.

**Note**

The Flex regulation does not take place during the daily approval and
transferring of the worker’s registrations in the **Approve** page.

### Principle for calculating the worker’s flex balance

The principle for calculating the hours to adjust the worker’s flex balance is
set up on the flex group.

Select **Time and attendance** \> **Setup** \> **Groups**\> **Flex groups.** The
following two principles can be used.

-   Time

-   Pay types

**Time**

When using the **Time principle,** the worker’s flexible hours are calculated
purely from the worker’s registered time for the day. When calculating the
worker’s daily registrations, the number of Flex+ and Flex- hours for the day is
calculated from the Flex+ and Flex- zones that are defined in the worker’s time
profile.

**Pay types**

When using the Pay types principle, the worker’s flexible hours are calculated
based on earnings of the pay types for Flex+ and Flex- that are defined in the
worker’s pay agreement. The pay agreement is associated with the time
registration worker. Using the pay types to manage the flex account can be an
advantage if, for example, you want to increase the worker’s flex account with a
factor in one or more flex zones.

**Scenario 1 – The worker’s pay, and flex account is adjusted because the limit
for flex minimum is exceeded**

A worker who can work flexible hours has a negative flex account:

| **Flex account** |
|------------------|
| \-4              |

The worker is associated with a flex group with the following configuration.

| **Flex minimum**     | \-0.5  |
|----------------------|--------|
| **Minimum pay type** | 1302   |
| **Pay type factor**  | \-1.00 |

From the difference between the worker’s flex account and his allowed flex
minimum you can see that the worker has exceeded his allowed minimum flex with
3.5 hours.

When the pay roll administrator transfers the worker’s pay data by using the
**Transfer to pay** job or by running the **Flex adjustment** job, the following
adjustments are made:

-   The worker’s flex account will be adjusted with 3.5 hours so the flex
    balance of -4.0 hours will be adjusted to the allowed minimum of -0.5 hours.

-   A pay item for pay type 1302 is created. This pay item has a pay unit of -
    3.5 hours, which will be deducted from the worker’s pay. The pay unit, in
    this case, has a negative number because the positive adjustment of 3.5
    hours is multiplied with the negative **Pay type factor** of -1.0 that is
    defined on the flex group. This pay item will be part of the pay file that
    is generated by the **Transfer to pay** job.

**Scenario 2 – The worker’s pay and flex account is adjusted because the limit
for flex maximum is exceeded**

A worker, who can work flexible hours, has a positive flex account.

| **Flex account** |
|------------------|
| 6                |

The worker is associated with a flex group with the following configuration:

| **Flex maximum**     | 2.0    |
|----------------------|--------|
| **Minimum pay type** | 1302   |
| **Pay type factor**  | \-1.00 |

From the difference between the worker’s flex account and his allowed flex
maximum you can see that the worker has exceeded his allowed maximum flex with
4.0 hours.

When the pay roll administrator transfers the worker’s pay data by using the
**Transfer to pay** job or by running the **Flex adjustment** job, the following
adjustments are made:

-   The worker’s flex account will be adjusted with -4.0 hours so the flex
    balance of 6.0 hours will be adjusted to his allowed maximum of 2.0 hours.

-   A pay item for pay type 1302 is created. This pay item has a pay unit of 4.0
    hours that will be added to the worker’s pay. The pay unit, in this case,
    has a positive number because the negative adjustment of 4.0 hours is
    multiplied with the negative **Pay type factor** of -1.0 defined on the flex
    group. This pay item will be part of the pay file that is generated by the
    **Transfer to pay** job.

**Scenario 3 - Manage the worker’s flex balance based on pay types**

In addition to managing flex accounts based on the time that is registered in
the Flex+ zones of the worker’s time profile, a worker’s flex account can be
managed based on the pay types that are defined in the pay agreements. In this
case, the flex account is adjusted by the pay items that are generated when you
transfer the workers registration from the **Approve** page. Using the pay types
to manage the flex account can be an advantage if, for example, you want to
increase the worker’s flex account with a factor in one or more flex zones.

Consider the following flex profile that represents a work day:

| **Profile type** | **Start** | **End**  |
|------------------|-----------|----------|
| Flex+            | 12:00 AM  | 08:00 AM |
| Clock in         | 08:00 AM  | 08:00 AM |
| Flex-            | 08:00 AM  | 09:00 AM |
| Standard time    | 09:00 AM  | 11:30 AM |
| Paid break       | 11:30 AM  | 12:00 PM |
| Flex-            | 12:00 PM  | 04:00 PM |
| Clock out        | 04:00 PM  | 04:00 PM |
| Flex+            | 04:00 PM  | 12:00 AM |

We want to enable the worker’s flex balance to be managed by the pay types. This
is done by setting the field **Based on pay types = Yes** on the worker’s flex
group.

To account for the flexible hours, we define a new pay type, in this case called
**FlexCnt**.

| **Pay type** | **Description** |
|--------------|-----------------|
| FlexCnt      | Flex counter    |

1.  Click **Time and attendance** \> **Setup** \> **Groups** \> **Flex groups**
    and select New.

2.  In the **Flex+** and **Flex-** fields, add the new pay type, FlexCnt.

3.  Click **Time and attendance** \> **Setup** \> **Pay agreements**, and select
    **Agreement lines.**

Add the following three lines for Monday for the Flex+ profile type:

| **Monday** | **Flex+**    |                 |               |             |             |             |            |
|------------|--------------|-----------------|---------------|-------------|-------------|-------------|------------|
|            |              |                 |               |             |             |             |            |
|            | **Pay type** | **Description** | **From time** | **To time** | **Minimum** | **Maximum** | **Factor** |
|            | FlexCnt      | Flex counter    | 12:00 AM      | 06:00 PM    | 00.00       | 00.00       | 1.00       |
|            | FlexCnt      | Flex counter    | 06:00 PM      | 12:00 AM    | 00.00       | 02.00       | 1.50       |
|            | FlexCnt      | Flex counter    | 06:00 PM      | 12:00 AM    | 02.00       | 06.00       | 2.00       |

Note

Each line has a different factor to multiply the flexible hours that the worker
has worked in each time interval. Hours worked from 06:00 PM to 08:00 PM are,
for example, multiplied by 1.50. The factor is specified in the field **Factor**
field under the **General** tab on the **Pay agreement lines** page.

The worker has entered the following registrations for the day:

| **Journal registration type** | **Start** | **End**  |
|-------------------------------|-----------|----------|
| Clock in                      | 07:00 AM  | 07:00 AM |
| Production job                | 07:00 AM  | 09:00 PM |
| Clock out                     | 09:00 PM  | 09:00 PM |

The amount to be paid is calculated in the **Approve** page based on the
worker’s registration. When the registration has been calculated, you can see
the result of the calculation under the **Times** tab. For this scenario, the
following fields are of interest:

| **Flex +**  | **Flex -** | **Time** | **Pay time** |
|-------------|------------|----------|--------------|
| 6.00        | 0.00       | 13.50    | 08.00        |

The Flex+ time is 6 hours and the calculation is based on the flex zones in the
time profile. This adds up to one hour of Flex+ from 07:00 AM to 08:00 AM and
five hours of Flex+ from 04:00 PM to 09:00 PM.

When you transfer the registrations, you will notice that Flex+ changes from 6.0
hours to 8.0 hours.

| **Flex +**  | **Flex -** | **Time** | **Pay time** |
|-------------|------------|----------|--------------|
| 8.00        | 0.00       | 13.50    | 08.00        |

The change in Flex+ after the transfer happens because the flexible hours have
been calculated based on the pay types instead of time. In the table below, you
can see how the eight hours are calculated.

| **From** | **To**   | **Time** | **Factor** | **Flex account** |
|----------|----------|----------|------------|------------------|
| 07:00 AM | 08:00 AM | 1        | 1          | 1                |
| 04:00 PM | 06:00 PM | 2        | 1          | 2                |
| 06:00 PM | 08:00 PM | 2        | 1.5        | 3                |
| 08:00 PM | 09:00 PM | 1        | 2          | 2                |
|          |          |          | Total      | 8                |
