---
# required metadata

title: Compensation plans
description: Compensation and Benefits Managers can use Compensation management to maintain and process fixed and variable compensation plans for the organization's employees.
author: twheeloc
manager: AnnBe
ms.date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: HcmCompensationLevel, HRCCompGrid, HRMCompFixedAction, HRMCompFixedBudget, HRMCompFixedPlanTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 3b953d5f-6325-4c9e-8b9b-6ab0458a73f8
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Compensation plans

Compensation and Benefits Managers can use Compensation management to maintain and process fixed and variable compensation plans for the organization's employees.

### Introduction

Compensation management is used to control the delivery of base pay and awards. An employee's fixed base pay and merit increases are controlled through fixed compensation plans. The payment of incentive pay, such as bonus payments, performance awards, stock options, and grants, and also one-time awards, are controlled through variable compensation plans. 

Employees can be enrolled in one or more plans of both types. An employee must meet the following requirements in order to be eligible for enrollment in a compensation plan:
-   The employee must have an active position assignment.
-   The employee must meet the criteria that are defined by eligibility rules for a compensation plan.

## Compensation setup
The following table lists components of the compensation process that can be integral in setting up your company's compensation plans.

<table>
<thead>
<tr class="header">
<th>Component</th>
<th>More information…</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Fixed compensation actions</td>
<td>Fixed compensation actions accomplish two purposes:
<ul>
<li>Actions can specify the kind of information that must be recorded when an employee’s compensation changes. For example, you can require that the reason a change, such as a promotion or a demotion be recorded.</li>
<li>Actions can ensure that a calculation is applied when fixed compensation plans are processed.  For example, actions of type Equity will compare the employees pay to the minimum reference point for the level on the employee's and ensure the employee is getting paid at least the minimum.</li>
</ul></td>
</tr>
<tr class="even">
<td>Levels</td>
<td>Levels are associated with jobs and any positions that are related to a job reference. You can create discrete levels for the three types of compensation plans: Grade, Band, and Step.</td>
</tr>
<tr class="odd">
<td>Range utilization matrix</td>
<td>A range utilization matrix helps you transition employees to the control point for their jobs. You can also use range utilization to control pay rate equity in the company without regard to an individual employee's performance or the overall performance of the company. For example, employees who are paid lower in their range get higher percentage increases than employees who are paid higher in the range. In this manner, you can systematically offset equity differences. The range utilization is calculated as follows: (Fixed Pay Rate - Range Minimum) ÷ (Range Maximum - Range Minimum).</td>
</tr>
<tr class="even">
<td>Reference point setups</td>
<td>A reference point setup includes a set of reference points that represent ranges in a matrix. Each range can be associated with a pay rate. For example, grade plans will often have reference points of Minimum, Midpoint, and Maximum.</td>
</tr>
<tr class="odd">
<td>Compensation matrix</td>
<td>A compensation matrix is the set of reference points and levels that you use to create a compensation structure.</td>
</tr>
<tr class="even">
<td>Compensation structure</td>
<td>A compensation structure is a compensation matrix that has pay rates associated with the reference points for each level.</td>
</tr>
<tr class="odd">
<td>Eligibility rules</td>
<td>Eligibility rules are used to identify employees in specific jobs, job functions, job types, departments, labor unions, or compensation regions that are covered by specific compensation plans. You must create eligibility rules for both variable and fixed compensation plans in order to enroll employees in the plan. After eligibility rules are specified for a compensation plan, you can define the levels that should apply to the jobs that are covered by the plan.</td>
</tr>
<tr class="even">
<td>Pay frequencies</td>
<td>Pay frequencies are used to define the time period for which the compensation is specified.  For example, the pay frequency helps you understand if the compensation amount is specified as an annual salary versus an hourly pay rate. Pay frequencies are also used to set up conversion factors to convert compensation amounts from monthly, weekly, biweekly and hourly pay frequencies to an annual pay frequency.</td>
</tr>
<tr class="odd">
<td>Compensation regions</td>
<td>Compensation regions are used to specify employee compensation based on the location of the workplace.</td>
</tr>
<tr class="even">
<td>Control point</td>
<td>The control point defines what you consider to be the ideal pay rate for all employees at a compensation level. For grade plan structures, control points are typically the midpoint of the ranges. Band structures rarely use control points. You can specify the control point for a fixed compensation plan in the Fixed compensation plans form.</td>
</tr>
<tr class="odd">
<td>Job functions</td>
<td>Job functions are used to classify and filter compensation plans to specific jobs.</td>
</tr>
<tr class="even">
<td>Job types</td>
<td>Job types are used to classify and filter compensation plans to specific jobs.</td>
</tr>
<tr class="odd">
<td>Variable compensation types</td>
<td>Variable compensation types, such as stock awards or cash award bonuses, are set up in variable compensation plans.</td>
</tr>
<tr class="even">
<td>Compensation grids</td>
<td>Compensation grids contain the compensation structure.  Compensation grids can be used by one or more compensation plans.</td>
</tr>
<tr class="odd">
<td>Performance plans</td>
<td>Performance plans are used to associate performance with an allocation matrix, so that you can use the plan in a pay-for-performance strategy.</td>
</tr>
<tr class="even">
<td>Performance ratings</td>
<td>Performance ratings are used in performance plans to determine the amount of a merit award or performance award.</td>
</tr>
</tbody>
</table>

## Process events
A process event calculates compensation information for a specific period for all employees who are enrolled in one or more fixed or variable compensation plans. You can run a process event repeatedly to test or update calculated compensation results.

Compensation events
-------------------

Each time a process event is run, a compensation event is created.  Compensation events contain the results of the compensation process for each employee included in that process event.  When the calculations are correct, you can load the compensation event to update the compensation records for the employees who are affected by the process event.

## Recommendations
After you run a process event, you can recommend adjustments to an employee’s merit increase or award amount, based on the calculated guidelines of the process event. To make recommendations for employees, you must enable recommendations when you set up compensation plans or when you set up the process event.

