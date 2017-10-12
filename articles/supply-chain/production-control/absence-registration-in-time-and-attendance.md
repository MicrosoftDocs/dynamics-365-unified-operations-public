---
# required metadata

title: Absence registration in Time and attendance
description: This topic describes how to handle absence registrations in Time and attendance.
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

 

This topic describes the concepts of absence and how to handle absence in Time and
attendance.

 

**Absence based on normal work hours**

A worker who is not working according to normal work hours is considered absent for the periods that deviate from the normal work hours. The normal work hours are defined in the worker's standard time profile.

For example, if a worker is working on a day profile with clock-in at 7:00am and
clock-out at 3:00pm and he clocks in at 9:00am, then he is considered to be absent
from 7:00am to 9:00am on that day. 

The worker will in that case be prompted for a reason for the absence and he can provide the reason by selecting an absence code.

## Absence codes
Absence codes are defined by the company and they define types of absence.
Different rules can be applied to absence codes. A code can, for
example, be configured to deduct or grant pay. A company can, for example, define an absence code called ***Late*** for coming in late without any good reason and an absence code called ***Internal course*** for time spent on internal courses. ***Late*** could be set up to deduct pay and ***Internal course*** would not deduct from the workers’ pay in the time he was absence attending an internal course.

Automatic absence codes can be set up to be used for calculating workers' time when no absence is registered. The workers time profile determines if the absence code for standard time or flex time is used. You can configure the standrd and flex-time parameters by using the **Auto insert absence** or **Auto insert Flex-** options on the **Time and attendance parameters** page.

## Absence groups

Absence codes are grouped in Absence groups. You use absence groups to group codes with common characteristics such as codes for legal
absence, doctor's appointments, jury duty, and children's sickness.


## Planned absence
If you know that a worker is going to be absent for a coming period, such as an upcoming vacation, you can use planned absence. You set up planned absence by configuring the absence code to consider the planned absence. With a planned absence setup you can avoid getting prompted for an absence code in the planned absence period when calculating users' time registrations. Planned absence can be defined for a single worker or as a batch job where you can bulk update the workers' planned absence.

### Set up planned absence
1.	Click **Human resources** -> **Workers** -> **Employees**, and select an employee.
2.	Click **Time** -> **Time assignments** -> **Time Absence registration**, and set up the planned absence . 

## Planned absence interrupted
If you apply the option **Interrupt** on a planned absence setup, the planned absence will
be interrupted if the worker logs in during the planned absence period. Subsequently, the planned absence will be marked as **Interrupted** and it will not have any effect on future calculations. 

### Set up planned absence with interruption
1.	Navigate to the **Time Absence registration** page as described in the guidelines to set up planned absence
2.	Select **Interrupt**.

The use of the **Interrupt** option is applicable when time is registered through the Shop floor terminal
or the Shop floor device, but it is not applicable if the registrations are entered on the
calculate and approval pages or on the **Electronic timecard** page.

## Example of the use of absence in a flex profile

The following three examples illustrate how absence is calculated in a profile
with flex periods.

The examples uses this profile.

| Clock-in | Standard time | Break        | Standard time | Flex-     | Clock-out | Flex+     |
|----------|---------------|--------------|---------------|-----------|-----------|-----------|
| 8pm      | 9am - 11:30am | 11:30am 12pm | 12pm - 3pm    | 3pm - 4pm | 4pm       | 4pm - 6pm |


### Example 1 - Logging out in the Flex- period

The worker clocks in at 8:00am and clocks out at 3:30pm.

As the worker clocks out in a Flex- period, no absence is calculated and half an
hour is deducted from the worker's flex balance.

### Example 2 - Logging out in the Standard time period

The worker clocks in at 8:00am and clocks out at 2:30pm. 

As the worker clocks out during the standard time period, absence is calculated from 2:30pm to 4pm and an absence period of 1.5 hours is registered. An an absence code for that period is required.

### Example 3 - Logging out in the Flex+ period

The worker clocks in at 8:00am and clocks out at 4:30pm. As the worker clocks out
in a Flex+ period, no absence is calculated and half an hour is added to the
worker's flex balance.

 
## Absence in the calculation and approve process

Workers time registrations must be calculated and approved before they can
be transferred as pay items to a payroll system. 

An approver can make changes to a worker's time registrations, including any absence that the worker has registered. If the approver manually enters a time period with an absence code, the absence code for this period will not be
overridden by the default absence code from the time and attendance parameters.

For example, a worker might clock in at 10am and select an absence code that signifies that he is late,
and then later he might inform the supervisor that from 8am to 10am he had a doctor's appointment. A doctor's appointment should not result in deduction in the payroll so in this case the supervisor can adjust the two hours absence from 8am to 10am with a manually entered absence code of two hours that signifies illness.

### Calculate and approve absence 
""In the calculate and approve pages"" (path)

1.	Click Time attendance -> Review and approve -> Approve or Calculate 


 
