---
# required metadata

title: Absence registration in Time and attendance
description: This topic describes how to handle ***.
author: johanhoffmann
manager: AnnBe
ms.date: 05/26/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: bis
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 269384
ms.search.region: Global
# ms.search.industry: 
ms.author: johanhoffmann
ms.search.validFrom: 2017-09-20
ms.dyn365.ops.version: AX 7.0.0

---

# Absence registration in Time and attendance

[!include[banner](../includes/banner.md)]

**Introduction:**

 

This wiki topic describes the concepts of absence and how to use it in time and
attendance.

 

**Absence**

 

A worker is regarded as absence if he is not working according to his normal
work hours. The normal work hours are defined in the workers standard time
profile.

If a worker is for example working on a day profile with clock-in at 7:00am and
clock-out at 3:00pm and is clocking in at 9:00am, then he is regarded as absence
from 7:00am to 9:00am on that day. The worker will in that case be prompted for
a reason for being absence by selecting from a list of absence codes defined by
the company. Different rules can be applied to absence codes; a code can for
example be configured to deduct or grant pay. A company could for example define
an absence code **Late** for coming in late without any good reason, that
deducts pay, and an absence code **Internal course** that when selected will not
deduct the workers’ pay in the time he was absence attending an internal course.

**Absence groups and codes**

Absence codes are grouped in Absence groups. In that way it is possible to group
codes with common characteristics for example group of absence codes for legal
absence doctor's appointment, jury duty and a sick child.

 

In the setup we have capabilities to setup auto absence codes that will be used
when the workers time is calculated. If no absence if given for a worker, the
auto absence code from setup is used. The workers time profile determine if the
absence code for Auto insert absence or Auto insert Flex- is used.

 

**Planned absence**

You can set up **planned absence**, with the use of an absence code. You use
**Planned absence** if you know that a worker is going to be absence for a
coming period, for example a coming vacation period. This way you avoid getting
prompted for an absence code in the planned absence period when calculating the
users time registrations. Planned absence can be defined on a single worker or
as a batch job where you can bulk update the workers planned absence. With the
use of the option **Interrupt** on **Planned absence**, the planned absence will
be interrupted if the worker is logging in in the planned absence period. After
that the planned absence will be marked as **Interrupted** and will not have any
effect for future calculations. The use of the **Interrupt** option is
applicable when the time registrations are done through the shop floor terminal
or the shop floor device, but not when the registrations are done through the
calculate and approval pages or the Electronic time card page.

 

**Example of the use of absence in a flex profile**

In the following are three examples of how absence is calculated in a profile
with flex periods.

 

In all three examples uses the below profile.

| Clock-in | Standard time | Break        | Standard time | Flex-     | Clock-out | Flex+     |
|----------|---------------|--------------|---------------|-----------|-----------|-----------|
| 8pm      | 9am - 11:30am | 11:30am 12pm | 12pm - 3pm    | 3pm - 4pm | 4pm       | 4pm - 6pm |

 

**Example 1 - Logging out in the Flex- period**

The worker clocks-in at 8:00am and clock-out at 3:30pm.

 

As the worker is clocking out in a Flex- period no absence is calculated a half
hour is deducted from the workers flex balance.

 

**Example 2 - Logging out in the Standard time period**

Worker clock-in at 8:00am and clock-out at 2:30pm. As the worker is clocking out
in the standard time period absence is calculated from 2:30pm to 4pm = 1.5 hours
and an absence code for that period is required.

 

**Example 3 - Logging out in the Flex+ period**

Worker clock-in at 8:00am and clock-out at 4:30pm. As the worker is clocking out
in a Flex+ period no absence is calculated and a half hour is added to the
workers flex balance.

 

 

**Register absence in the calculation and approve process**

 

The workers time registrations must be calculated and approved before they can
be transferred as pay items to a payroll system. In the calculate and approve
pages is it possible to make changes to the workers time registrations including
the workers absence registration. If a time period is manually provided with an
absence code by the approver, the absence code for this period will not be
overridden by the default absence code from the time and attendance parameters.
If for example a worker is clock-in at 10am and select Late as absence code,
then he later informs the supervisor that from 9am to 10am he had a doctor's
appointment, which should not result in deduction in the payroll. The supervisor
will adjust the two hours Late absence from 8am to 10am with a manual entered
Illness absence for one hour.

 
