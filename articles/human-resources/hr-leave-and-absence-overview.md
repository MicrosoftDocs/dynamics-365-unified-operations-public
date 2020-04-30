---
# required metadata

title: Overview
description: In Dynamics 365 Human Resources, the Leave and absence workspace provides a flexible framework for creating new leave plans, workflows for managing requests, and an intuitive self service page for employees to request time off. 
author: andreabichsel
manager: AnnBe
ms.date: 04/03/2020
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

Dynamics 365 Human Resources helps you provide great leave benefits to your workers. The **Leave and absence** workspace provides a flexible framework for creating new leave plans, workflows for managing requests, and an intuitive self service page for employees to request time off. Analytics helps your organization measure and monitor leave balances and usage for your leave plans.

## Set up Leave and absence

Before creating leave plans for your employees, you need to do a few setup steps:

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

## Leave and absence known issues

### Rounding precision

You can't set **Rounding precision** when you set **Rounding type**. You can only set **Rounding precision** by using the **Leave and absence type** entity. 

1. From **Leave and absence types**, select **Open in Excel** to open the **Leave and absence type** entity.

2. After the file opens and is enabled, select **Design**.

3. On the **Leave and absence type** table, select the pencil option to edit.

4. Select **RoundingPrecision** and **RoundingType**, and then select **Add** to add to the list of fields.

5. Select **Update**, and then select **Done**.

6. Enter or select the **Rounding type** for each leave type if they haven't been set already. 

7. Enter the **Rounding precision** for the appropriate types.

8. Select **Publish** to push the changes into Human Resources.

## Leave and absence preview features

You can try out new Leave and absence preview features in a **Sandbox** environment. For information about turning on preview features, see [Manage features](hr-admin-manage-features.md). The preview features include:

- **Leave suspension** - You can suspend leave and absence in Human Resources for an employee. Suspending leave stops the leave accruals for selected leave types. If the suspension occurs after an accrual processes, suspending leave creates a prorated adjustment to the employee's leave balance. Reason codes can also be included when suspending an employee's leave. Also, when leave is supsended, the user experience has been updated to indicate suspension. 

- **Carry forward rules** - You can specify a carry forward leave type for carry forward balances where carry forward adjustments are transferred. For example, if an employee carries forward 10 days, you can pick a different leave type for those 10 days. 

- **Include reason code and comments for adjustments** - You can include a reason code and a comment when making an adjustment to an employee's leave balance. 

- **Transition to Leave and absence parameters** - You can now use only Leave and absence parameters instead of using Human resources parameters. 
