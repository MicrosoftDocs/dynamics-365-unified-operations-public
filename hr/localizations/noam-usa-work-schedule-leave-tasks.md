---
# required metadata

title: Set up work schedules and leave
description: This topic describes the processes for creating working time templates, working time calendars, and leave types, and the process for putting workers on leave.
author: rschloma
manager: AnnBe
ms date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: HcmLeaveType, WorkTimeTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: rschloma
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 221494
ms.assetid: 60ce2f9f-73a7-4903-89da-6af7d681cc7a
ms.search.region: USA
# ms.search.industry: 
ms.author: brpotter
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Set up work schedules and leave

This topic describes the processes for creating working time templates, working time calendars, and leave types, and the process for putting workers on leave.

Although you use the same page to maintain the calendars that both Payroll and Production control use, we recommend that you maintain separate calendars for each of those feature areas. 

A seven-day pattern of hours that are typically worked is known as a working time template. After you create a working time template for each schedule that hourly workers in your organization typically work, you can use the template to generate a working time calendar of one year or more. When you specify the working time calendar as the schedule for a position, all workers who are assigned to the position use that schedule. The scheduled hours are used to generate the default earnings statement lines for the combination of workers and a position. 

Schedules that are based on working time calendars are also used together with leave types for paid leave, for both hourly workers and salaried workers. 

## Create working time templates
Create a working time template for each schedule that hourly workers in your organization typically work. 

To create a working time template, on the **Working time templates** page, click **New**, and then enter a brief identifier and a descriptive name for the template. 

Then, on the **Monday** tab, follow these steps:

1.  Enter the regular hours of operation for Mondays. Use the **From** field to specify the time when the work period starts. Use the **To** field to specify the time when the work period ends.
2.  In the **Efficiency** field, enter a value other than 0 (zero). Typically, you will enter **100** to indicate that the worker is on duty during that time.
3.  Leave the **Property** field blank, and make sure that the **Closed for pickup** check box is cleared.

Repeat this procedure for the other days of the week. Or, to copy the same schedule to a different day, click **Copy day**, and select the weekdays to copy from and to. Leave the **Copy property** check box cleared. 

Repeat these steps to create additional working time templates. When you've finished, close the page.

## Create working time calendars
A working time calendar defines the typical schedule for a position. You can use the calendar to generate default earnings statement lines for workers who are assigned to the position. After you create working time calendars, you can assign them to positions. For more information, see [Worker and position payroll tasks](noam-usa-worker-position-payroll-tasks.md). 

**Note:** Time off that is part of a benefit accrual plan, such as vacation time or sick time, isn't considered leave. For more information about benefit accrual plans, see [Benefit accrual plan tasks](noam-usa-benefit-accrual-plan-tasks.md). 

**Tips:**
-   To set up a 24-hour calendar, enter **12:00 am** in the **From** field and **24** in the **To** field.
-   To enter a period that users won't be paid for, such as their lunch hour, enter **0** (zero) in the **Efficiency** field for the line. No earnings will be generated for that line.

## Create leave types
You use leave types to set up the types of leave that workers can take, such as medical, educational, or parental leave. Time off that is part of a benefit accrual plan, such as vacation time or sick time, isn't considered leave. For more information about benefit accrual plans, see [Benefit accrual plan tasks](noam-usa-benefit-accrual-plan-tasks.md). Before you create leave types that can be used to generate earnings statement lines for paid leave, you must create an earning code for each type of paid leave. 

When a worker goes on leave, the leave type, together with the start date and end date for the leave, is recorded on the **Leave** page. 

To create a leave type, on the **Leave types** page, click **New**, and then enter a name and description for the leave type. 

Enter the earning code that is used when earnings lines for the leave are generated, if earning codes are required.

-   For paid leave, earning codes are required. The earnings lines that are generated for the position during the leave will show a daily breakout.
-   For unpaid leave, if you don’t enter any earning codes, no earnings lines will be generated during the leave period, and the salary amount will be adjusted. However, you can manually modify the earnings statement to add earnings statement lines. If you want unpaid leave to generate earning lines, you can create a zero-rate earning code and assign it to the leave type. Hours for time on leave will then be tracked in Payroll, so that you can generate pay statements. These statements will have no pay, but you can force deduction arrears and track time on leave in Payroll. In addition, Payroll can update Family and Medical Leave Act (FMLA) hours that are taken.

Repeat these steps to create additional leave types.

## Put a worker on leave
Schedules are used together with leave types when a worker is on paid leave. To incorporate the leave settings when you generate earnings statements for a worker who is on paid leave, you must assign a schedule to the worker’s position. This step is required even if you generate earnings for that position by salary, not from a schedule. A schedule is optional for a salaried worker who is on unpaid leave. Time off that is part of a benefit accrual plan, such as vacation time or sick time, isn't considered leave. For more information about benefit accrual plans, see [Benefit accrual plan tasks](noam-usa-benefit-accrual-plan-tasks.md). 

To put a worker on leave, enter the following information on the **Workers** page.

| Field      | Description                        |
|------------|------------------------------------|
| Leave type | Select the type of leave.          |
| Start date | Enter the first date of the leave. |
| End date   | Enter the last date of the leave.  |

Repeat this step for any additional salaried positions that the worker holds.

## Next step
The next step is to set up benefit accrual plans. For more information, see [Benefit accrual plan tasks](noam-usa-benefit-accrual-plan-tasks.md).

