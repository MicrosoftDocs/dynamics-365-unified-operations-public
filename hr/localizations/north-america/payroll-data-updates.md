---
# required metadata

title: Payroll data updates FAQ
description: A number of changes can and do happen at the end of a year that require changes to your payroll data. Workers can change their benefit election, or your company might change benefit rates, and benefit balances. Workers who move into different positions also result in changes to payroll data. This topic lists questions and answers that address these kinds of changes.
author: rschloma
manager: AnnBe
ms.date: 2016-10-31 16 - 08 - 31
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: HcmBenefit, HcmBenefitElementSetup, HcmWorkerEnrollment
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 31
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 221444
ms.assetid: 27ccec84-8e9a-465e-9b2a-fbe88d974068
ms.search.region: USA
# ms.search.industry: 
ms.author: brpotter
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Payroll data updates FAQ

A number of changes can and do happen at the end of a year that require changes to your payroll data. Workers can change their benefit election, or your company might change benefit rates, and benefit balances. Workers who move into different positions also result in changes to payroll data. This topic lists questions and answers that address these kinds of changes.

This topic describes functionality that is available only if the **Payroll - USA** configuration key is selected.
How do I prepare payroll for a new fiscal year?
-----------------------------------------------

If a pay statement that contains a benefit accrual is generated in one fiscal year and then reversed in the next fiscal year, you might have to adjust the carry-forward balance. You also might have to adjust the carry-forward balance if a pay statement is generated in the new fiscal year before the final pay statement from the previous fiscal year was submitted or posted. For more information about how to adjust benefit accruals, see “Can I adjust the balance in a benefit accrual plan?” later in this topic.

To prepare Payroll for a new fiscal year, you have to set up pay periods and work periods for the year, as described in these steps:
-   Verify that ledger calendars have been set up for the new year.
-   Go to [Pay cycle and pay period tasks](pay-cycle-pay-period-tasks-sample.md) and complete these tasks:
    1.  Generate pay periods.
    2.  Modify payment dates.
-   Go to [Payroll calculation frequencies tasks](payroll-calculation-frequencies-tasks.md) and complete the Associate pay periods with payroll calculation frequencies task.
-   Go to [Work cycle and work period tasks](work-cycle-work-period-tasks.md) and complete the Generate work periods task.

## Can I adjust the balance in a benefit accrual plan?
Yes, you can adjust the balance in a benefit accrual plan. You might have to adjust the balance in these situations:

-   If a worker isn’t enrolled in the plan when they should have been, you can adjust the amounts that were accrued and used so that you can include the correct amounts.
-   If a worker is granted additional time off, you can add that amount to the amount that was accrued.
-   If a worker has reached the maximum accrual limit, you can reduce the amount that was accrued to let the worker accrue additional hours.

>**Important**
>All manual adjustments that you make are accepted, even if they create a plan balance that does not meet the limits that are set by the plan rules. To undo an adjustment, create a new adjustment that offsets the same amount that you added, or that adds the same amount that you subtracted.

To reverse an adjustment, create a second adjustment that has the same type as the adjustment that you want to reverse. Use the same value, but use the opposite sign as the adjustment to reverse. For example, to reverse a carry-forward adjustment of 8.0 hours, create a carry-forward adjustment of -8.0 hours.

## Why can’t I delete a worker enrollment from a benefit accrual plan?
You can delete a worker enrollment from a benefit accrual plan only if these situations apply:

-   You’re logged on to the legal entity where the benefit accrual plan exists.
-   The benefit accrual plan has no balances, or has only manual adjustments or pending usage.

If the plan has a balance that was created when a pay statement was submitted, you can’t delete the worker enrollment from the plan, but you can deactivate the enrollment. To do this, in the **Benefit accruals** page, select both the **Stop accrual** and **Stop balance reduction** options. 

When the **Stop accrual** option is selected, no hours accrue in the plan for this worker. When the **Stop balance reduction** option is selected, validation doesn’t occur for hours used, and hours from the plan that are used aren’t subtracted from the worker’s available balance. When you select both options, this has the same effect as removing the worker from the plan. Neither accrual transactions nor usage transactions are created when you submit a pay statement, and the plan doesn’t appear on the pay statement or the payment.

## Why aren’t hours accruing in a worker’s benefit accrual plan?
If hours aren’t accruing, this usually occurs for one or more of these reasons:

-   The worker isn’t enrolled in the plan.
-   The **Stop accrual** option is selected in the **Benefit accruals** page.
-   The plan balance has reached the maximum accrual limit for the year. Review the plan rules in the **Benefit accrual plans** page.

## How do I update benefit rates before the new plan year?
When the amount or rate that is used to calculate payroll deductions and employer contributions for a benefit changes, you have to change it both on the benefit itself and on the benefit records of the workers who are enrolled in that benefit. A yellow message bar notifies you when the rates for the worker enrollments don’t match the rates for the benefit.

You can use an automated process to update rates for workers who have a rate source of **Benefit**. You must manually update rates for workers who have a rate source of **Custom**.

> **Note**
>If the time zone that is set for the legal entity differs from the time zone where the benefit was created, the automated process might cause some dates to be off by one calendar day. If this occurs, you can adjust the dates by running the process again.

## How do I change payroll settings when a worker changes to a new position assignment?
Before you can make the necessary payroll changes, the worker and position information must already be changed in the Human resources module.

To change the payroll settings after that is done, follow these steps:
1.  Go to [Worker and position payroll tasks](worker-position-payroll-tasks.md) and complete these tasks to update the worker:
    -   Add earning codes to worker position assignments.
    -   Set up worker tax regions: If the new position is in a different tax region, add the new worker tax region.
    -   Assign default tax regions: A default tax region is required for each position that a worker holds.
    -   Configure worker tax codes: If the new position is in a different tax region, or if it is paid by a different legal entity, you can assign additional tax codes to the worker. You must set up these tax codes before the worker can be paid.

2.  When you change a worker position, this also might change which benefits the worker is eligible for. Go to [Define and manage a benefit program](/hr/manage-benefit-program.md) and complete these tasks:
    -   Create an eligibility event.
    -   Process eligibility for benefits.
    -   Enroll workers in benefits.

3.  Go to [Worker and position payroll tasks](worker-position-payroll-tasks.md) and, for each benefit that you enrolled the worker in, perform the task titled Set up payroll information for benefits.

## How do I change benefits for a worker after a qualifying event?
When a worker has a qualifying life event that allows for a change of benefits, other payroll data for that worker might also change because of the event.

To change the benefits, follow these steps:
1.  Go to [Define and manage a benefit program](/hr/manage-benefit-program.md) and complete the following:
    -   Create an eligibility event.
    -   Process eligibility for benefits.
    -   Enroll workers in benefits.

2.  Go to [Worker and position payroll tasks](worker-position-payroll-tasks.md) and, for each benefit that you enrolled the worker in, perform the task titled Set up payroll information for benefits.
3.  If the worker has moved to a new location, go to [Worker and position payroll tasks](worker-position-payroll-tasks.md) and complete these tasks:
    -   Set up worker tax regions.
    -   Change worker residency.



