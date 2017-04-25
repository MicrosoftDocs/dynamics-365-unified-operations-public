---
# required metadata

title: Earnings and generating earnings FAQ
description: This topic answers some frequently asked questions about earnings and generating earnings. It includes questions about distributions and earning lines, recurring earnings, calculating salaries for workers who are on leave, and earnings generation. 
author: rschloma
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: HcmPosition, HcmWorker, PayrollEarningStatement
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 31
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 220904
ms.assetid: 8eef7aff-5d9a-47aa-b6a2-86958c3694cf
ms.search.region: USA
# ms.search.industry: 
ms.author: brpotter
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Earnings and generating earnings FAQ

[!include[banner](../includes/banner.md)]


This topic answers some frequently asked questions about earnings and generating earnings. It includes questions about distributions and earning lines, recurring earnings, calculating salaries for workers who are on leave, and earnings generation. 

This topic describes functionality that is available only if the **Payroll - USA** configuration key is selected.

## Can I change the distributions for an earning line?
Yes. Select the line, and then click **Distribute earnings** to view and change the distributions. The default main account and dimensions for earning lines are based on the accounting rule for the earning, and on the default dimensions and dimension templates that are defined for the earning code or the position. Distributions for earnings must be changed from the earnings statement line. After the earnings are processed, the distributions can't be changed on the pay statement.

## What are recurring earnings?
Recurring earnings are earnings that are assigned to workers, and that occur regularly. Some examples include a monthly car allowance or a clothing allowance for uniforms, where the allowance is based on the pay period amount and is earned each pay period. Recurring earnings are generated automatically when earnings are generated. Here are some important notes about recurring earnings:

-   Worker payroll earning codes that have a frequency specified are generated if the frequency is in the pay period that you’re generating earnings for. Only earning codes that have **Each** assigned as the unit of measure require a frequency.
-   The fixed compensation plan is determined by the combination of worker, position, and legal entity. The plan provides the fixed compensation rate, which is used in the formula that determines the earning amount. If the earning is a flat amount, fixed compensation plans aren’t used.
-   If a recurring earning is generated, the source of the earning line is set to **Recurring** on the **Earnings statement** page.
-   If a recurring earnings statement line is generated that is identical to a line that you entered manually, both lines will exist, but the source will differ. The source for the line that is entered manually line will be **User entry**, and the source for line that the system calculated will be **Recurring** in the earnings statement line details.

## How are earnings calculated for salaries?
Salary earnings are generated automatically during the generation process that is described earlier in this topic. Here are some important notes about salary earnings:

-   Positions that are identified as salaried positions should receive a base earning amount, even if they have earnings that have been entered manually. For example, if you enter eight hours of sick time, the earnings statement lines are adjusted so that a worker receives no more and no less than the salary amount that is authorized for that worker's position.
-   Recurring earnings and the earnings from schedules are created first, because salary amounts might be affected by other earnings that are automatically generated if those other earnings are considered base salary components. **Note:** If you enter earning lines manually after you generate earnings, the earning lines that were previously generated are recalculated so that the worker pay is accurate. If you don’t want the earning lines to be recalculated so that the salary amounts are correct, you can click **Calculate Salary** on the earnings statement to keep the line values unchanged. Typically, you use this approach only if you’re terminating a worker’s employment.

## How do I generate earnings for a salaried worker who is on leave?
To generate earnings for leave, you must assign a schedule to the position that the worker is taking leave from, even if that position is a salaried position. For more information, see [Work schedule and leave tasks](noam-usa-work-schedule-leave-tasks.md). If an earning code is assigned to the leave type, the scheduled lines will use the earning code from the leave type instead of the earning code from the schedule. The earning code that is on the leave type can be configured as either paid or unpaid, based on the amount or multiplier, which will be 0 (zero) for unpaid leave. If no earning code is assigned to the leave type, no lines will be created from the schedule or the leave type for the days when the worker is on leave.

## Can a salaried worker receive retroactive earnings?
Yes. However, when you use the process for generating retroactive earnings to change the compensation for a salaried position, you must make all compensation rate changes effective at the start of the pay period. If you must change the compensation during a pay period, you must manually calculate the retroactive adjustment for the pay period when the change took effect.

## Why didn't the selection criteria return any results?
When you generate earnings, you might receive the following message: “The selection criteria did not return any results.” If you expected earnings to be generated, the following factors might be causing the lack of results:

-   Earnings were already generated for the selection.
-   The pay cycle that you selected doesn't match the pay cycle that is specified on the **Payroll** FastTab of the **Position** page for the worker.
-   The worker wasn't assigned to a position during the pay period that you selected.
-   The legal entity that you're signed in to doesn't match the **Paid by** value that was in effect for the position at the end of the pay period.
-   You haven’t selected the **Generate salary** or **Generate earnings from schedule** option on the **Position** page, and there aren’t any recurring earning codes to generate for any workers.
-   The pay period that you selected has the wrong year. For example, you selected January 1, 2013, through January 15, 2013, but you intended to select January 1, 2014, through January 15, 2014.

**Important:** The fields on the **Payroll** FastTab of the **Position** page have their own date-effective settings. To view these settings, click **Changes timeline** &gt; **Manage changes** &gt; **Payroll Tab**.

## Don't see your question here?
We're working to include as many questions as we can, so that Help will be more useful to people just like you. Tell us what question you would like to add to this topic. Send email to <adocs@microsoft.com>. Announcements: To see known issues and recent fixes, use [Issue search](http://go.microsoft.com/fwlink/?LinkID=389258) in [Microsoft Dynamics Lifecycle Services](http://go.microsoft.com/fwlink/?LinkID=306505) (LCS).


