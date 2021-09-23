---
# required metadata

title: Absence registration in Time and attendance
description: This topic explains how to handle absence registrations in Time and attendance.
author: johanhoffmann
ms.date: 05/26/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: JMGParameters, JmgAbsenceCalendar
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 269384
ms.search.region: Global
# ms.search.industry: 
ms.author: johanho
ms.search.validFrom: 2017-09-20
ms.dyn365.ops.version: AX 7.0.0

---

# Absence registration in Time and attendance

[!include [banner](../includes/banner.md)]

This topic describes the concepts for absence and explains how to handle absence in Time and attendance.

## Absence that is based on regular work hours

Workers are considered absent for any hours that they don't work during their regular work hours. Regular work hours are defined in a worker's standard time profile.

For example, a worker is working on a day profile that has clock-in at 7:00 AM and clock-out at 3:00 PM. If the worker clocks in at 9:00 AM, they are considered absent from 7:00 AM to 9:00 AM on that day.

In this case, workers are prompted to enter a reason for their absence. They can specify a reason by selecting an absence code.

## Absence codes

Absence codes define the various types of absence. Absence codes are defined by the company.

Various rules can be applied to absence codes. For example, an absence code can be configured to deduct or grant pay.

For example, a company defines a **Late** absence code that workers use if they come in late and don't have a good reason. The company also defines an **Internal course** absence code that workers use for time that they spend attending internal courses. These absence codes can be set up so that **Late** deducts from a worker's pay but **Internal course** doesn't deduct from a worker's pay.

You can set up automatic absence codes. These absence codes can be used to calculate a worker's time when no absence is registered. The worker's time profile determines whether the absence code for standard time or flex time is used.

### Set up standard time and flex time

- Configure the parameters for standard time and flex time by using the **Auto insert absence** and **Auto insert Flex-** options on the **Time and attendance parameters** page.

## Absence groups

Absence codes are grouped into absence groups. You use absence groups to group absence codes that have common characteristics. Examples include absence codes for a legal absence, or absence because of a doctor's appointment, jury duty, or a sick child.

## Planned absence

If you know that a worker will be absent for a period, such as an upcoming vacation, you can use planned absence. You set up planned absence by configuring the absence code so that it considers the planned absence. When you set up a planned absence, you aren't prompted for an absence code during the absence period when user time registrations are calculated. Planned absence can be defined for a single worker, or you can define a batch job to bulk update the planned absence for workers.

### Set up planned absence

1. Select **Human resources** &gt; **Workers** &gt; **Employees**, and select an employee.
2. Select **Time** &gt; **Time assignments** &gt; **Time Absence registration**, and set up the planned absence.

## Interrupted planned absence

If you apply the **Interrupt** option when you set up a planned absence, the planned absence will be interrupted if the worker signs in during the planned absence period. The planned absence will be marked as **Interrupted** and won't have any effect on future calculations.

### Set up a planned absence for interruption

1. Open the **Time Absence registration** page as described in the procedure for setting up planned absence.
2. Select **Interrupt**.

The **Interrupt** option applies when time is registered through the shop floor terminal or the shop floor device. The option doesn't apply if the registrations are entered on the calculation and approval pages, or on the **Electronic timecard** page.

## Examples of the use of absence in a flex profile

The following three examples show how absence is calculated in a profile that has flex periods.

The examples use the following profile.

| Clock-in | Standard time    | Break             | Standard time | Flex-        | Clock-out | Flex+        |
|----------|------------------|-------------------|---------------|--------------|-----------|--------------|
| 8 AM     | 9 AM to 11:30 AM | 11:30 AM to 12 PM | 12 PM to 3 PM | 3 PM to 4 PM | 4 PM      | 4 PM to 6 PM |

### Example 1: Signing out during a Flex- period

The worker clocks in at 8:00 AM and clocks out at 3:30 PM. In this case, because the worker clocks out during a Flex- period, no absence is calculated, and half an hour is deducted from the worker's flex balance.

### Example 2: Signing out in during Standard time period

The worker clocks in at 8:00 AM and clocks out at 2:30 PM. In this case, because the worker clocks out during the Standard time period, absence is calculated from 2:30 PM to 4 PM, and an absence period of 1.5 hours is registered. An absence code for that period is required.

### Example 3: Signing out during a Flex+ period

The worker clocks in at 8:00 AM and clocks out at 4:30 PM. In this case, because the worker clocks out during a Flex+ period, no absence is calculated, and half an hour is added to the worker's flex balance.

## Absence in the calculation and approval process

Worker time registrations must be calculated and approved before they can be transferred to a payroll system as pay items.

An approver can change a worker's time registrations. The approver can even change any absence that the worker has registered. If the approver manually enters a time period that has an absence code, the absence code for that period isn't overridden by the default absence code from the Time and attendance parameters.

For example, a worker clocks in at 10 AM and selects an absence code that indicates that they are late. Later, the worker informs their supervisor that they had a doctor's appointment from 8 AM to 10 AM. A doctor's appointment should not cause a deduction in the worker's pay. Therefore, in this case, the supervisor can adjust the two hours of absence from 8 AM to 10 AM by manually entering an absence code that indicates illness for those two hours.

### Calculate and approve absence

- Select **Time attendance** &gt; **Review and approve** &gt; **Approve or Calculate**.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]