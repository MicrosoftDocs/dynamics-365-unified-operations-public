---
# required metadata

title: Overview
description: 
author: andreabichsel
manager: AnnBe
ms.date: 02/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-human-resources
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Overview

Dynamics 365 Human Resources helps you provide great leave benefits to your workers. The **Leave and absence** workspace provides a flexible framework for creating new leave plans, workflows for managing requests, and an intuitive self service page for employees to request time off. Analytics help your organization measure and monitor leave balances and usage for your leave plans.

## Set up Leave and absence

Before you can create leave plans for your employees, you need to do a few setup steps:

- [Configure leave and absence parameters](hr-leave-and-absence-parameters.md)
- [Create a working time calendar](hr-leave-and-absence-working-time-calendar.md)
- [Create a leave request workflow](hr-leave-and-absence-workflow.md)

## Create and manage leave plans

Before creating leave plans for your workers, you need to create leave and absence types. After you create a leave plan, you can then enroll workers into the plan. You can also run the accrue process, create alerts, and view analytics for your plans.

- [Configure leave and absence types](hr-leave-and-absence-types.md)
- [Create a leave and absence plan](hr-leave-and-absence-plans.md)
- [Assign workers to a leave plan](hr-leave-and-absence-enroll.md)
- [Accrue leave and absence plans](hr-leave-and-absence-accrue.md)
- [View analytics for leave and absence](hr-leave-and-absence-analytics.md)

## Request time off and manage requests

Your employees can submit time off requests, and you can manage them, in the **Employee self service** workspace.

- [Request time off](hr-employee-self-service-request-time-off.md)
- [Manage leave and absence requests](hr-employee-self-service-manage-requests.md)

## Leave and absence preview features

You can try out new Leave and absence preview features in a **Sandbox** environment. For informationa bout turning on preview features, see [Manage features](hr-admin-manage-features.md). The preview features include:

- **Leave and absence calendar** - Leave and absence parameters will move from **Human resources parameters** to a new screen called **Leave and absence parameters**. The new screen includes a new **Calendar** tab. This preview only enables a subset of the parameters. You can access the new screen from the **Links** tab of the **Leave and absence** workspace. The calendars include:
  - **Company calendar** - shows all employee time-off requests. People with the **Human resources** role can access this calendar from the **Links** tab of the **Leave and absence** workspace.
  - **Manager team calendar** - shows all direct reports' time-off requests. Managers can access the calendar from the **My team** tab in Employee self service under **Leave and absence**. 

- **Leave and absence holiday calendars** - Leave types include a new **Holiday** option, used in conjunction with the working time calendar. Days defined by holidays and closures are now designated as **Holiday** when working days are generated. When accruals are processed, adjustments are made to employees assigned to the calendar to account for holidays falling on a working day.

- **Leave accrual auditing** - A new screen lets you review when accruals have been processed and deleted, both by all employees and individual employees. You can access this new screen from the **Links** tab of the **Leave and absence** workspace.

- **Leave accrual deletion** - You can now delete accrual records for specific leave plans. You can access this new option from the **Links** tab of the **Leave and absence** workspace. For individual employees, this option appears in the **Leave and absence** grouping in the employee profile. 

- **Leave accrual rounding** - New options for **Leave type** define what type of rounding accrual should use, plus the decimal precision of the rounding during the accrual process. When accruals are processed, the rounding and precision are applied to the accrual records. 

- **Configure multiple leave types on a single leave plan** - A new column in the leave accrual schedule for leave types lets you define multiple leave types on a leave and absence plan with different accrual schedules. The previous **Leave type** field is removed. On the employee enrollment, the balances for the leave types now display in a table instead of at the top of the screen.

  > [!IMPORTANT]
  > You can't turn this feature off after you enable it.

- **Use an employee's full-time equivalency (FTE) for accrual** - a new column on the leave accrual schedule allows using FTE for accrual. When accruals are processed, the application uses the employee’s primary position and the FTE defined to determine the prorated accrual amount.

  > [!NOTE]
  > This feature is only available if you enable **Configure multiple leave types per leave plan**. 
