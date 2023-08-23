---
# required metadata

title: Set up payroll for workers
description: Before you can pay a worker, you must set up payroll information about the worker's position, taxes, and benefits.
author: twheeloc
ms.date: 11/01/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: HcmBenefit, HcmBenefitElementSetup, PayrollWorkerTaxCode, PayrollWorkerTaxRegion
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 248404
ms.assetid: d6530f02-bbee-4d8e-94e7-173aecb4452e
ms.search.region: USA
# ms.search.industry: 
ms.author: panolte
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Set up payroll for workers

[!include [banner](../../includes/banner.md)]

Before you can pay a worker, you must set up payroll information about the worker's position, taxes, and benefits. This information is used when you generate pay statements for the worker. In addition, if contribution and deduction amounts are changed on a benefit, that change must be made for each worker who is enrolled in that benefit. This article provides information about these tasks and the fields that are used to complete them.

For more information, see [Payroll data updates FAQ](noam-usa-payroll-data-updates.md).

[![Flow of worker and position tasks.](./media/worker-tasks.gif)](./media/worker-tasks.gif)

## Adding payroll periods to positions

You must specify payroll details and add them to a position before you can generate payroll for the position. The following table show the information that you must enter on the **Payroll** FastTab.

<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Pay cycle</td>
<td>Select the pay cycle that specifies the payroll calculation frequency and pay date for the position.</td>
</tr>
<tr>
<td>Work cycle</td>
<td>For non-exempt positions only, select the work cycle that specifies the work periods for the position. Some earnings, such as the regular-rate-of-pay premiums that are required by the Fair Labor Standards Act (FLSA), are based on work periods instead of pay periods. For exempt positions, leave this field blank.
[!IMPORTANT] For workers who have more than one position, make sure that all positions that are assigned to the worker have the same work cycle.
</td>
</tr>
<tr>
<td>Paid by</td>
<td>Select the legal entity that is responsible for making the payroll payments for this position. The legal entity that is responsible for paying for the position must be assigned to the position before you can assign worker tax codes to workers.
[!NOTE] You can use the <strong>Worker</strong> page to assign default tax codes for each position.
</td>
</tr>
<tr>
<td>Annual regular hours</td>
<td>Enter the number of regularly paid hours that the position is expected to have each year. This value is used to determine salary adjustments. For example, you might enter <strong>2080</strong> for a regular salaried worker. This value represents 40 hours per week. If a worker has eight hours of sick time, the difference of 32 hours can be calculated automatically.</td>
</tr>
<tr>
<td>Workers' compensation</td>
<td>Click <strong>Add</strong>, and select a compensation state and a compensation code. Repeat these steps for any additional workers' compensation benefits.</td>
</tr>
<tr>
<td>Earnings</td>
<td>The fields in this group interact in the following ways to determine how earnings are generated and shown on earnings statements:
<ul>
<li>If neither <strong>Generate salary</strong> nor <strong>Generate earnings from schedule</strong> is selected, base earnings statement lines for the position aren't generated. Only the recurring earnings that are specified on the <strong>Worker</strong> page are generated.</li>
<li>If <strong>Generate earnings from schedule</strong> is selected, but <strong>Generate salary</strong> isn't selected, the following information applies:
<ul>
<li>A schedule is required. You can select among the calendars that have been created for the legal entity that is selected in the <strong>Paid by</strong> field.</li>
<li>A default earning code is required.</li>
<li>A day-by-day breakout of earnings for the position appears on the worker's earnings statement.</li>
</ul>
This set of selections is typically used for hourly workers.</li>
<li>If <strong>Generate salary</strong> is selected, but <strong>Generate earnings from schedule</strong> Isn't selected, the following information applies:
<ul>
<li>A default earning code is required.</li>
<li>The worker is paid the standard position salary amount for each pay period, and a single line is included on the earnings statement. This line has the date of the last day in the pay period.
[!NOTE] If earnings statement lines were entered manually before the earnings were generated, the salary might be split across multiple lines. The total of the manually entered lines and the single generated line is always the standard salary amount.
</li>
</ul>
This set of selections is typically used for salaried workers.</li>
<li>If both <strong>Generate salary</strong> and <strong>Generate earnings from schedule</strong> are selected, the following information applies:
<ul>
<li>A schedule is required. You can select among the calendars that have been created for the legal entity that is selected in the <strong>Paid by</strong> field.</li>
<li>A default earning code is required.</li>
<li>The worker is paid the standard position salary amount for each pay period.</li>
<li>A day-by-day breakout of earnings for the position appears on the worker's earnings statement.</li>
</ul>
This set of selections is typically used for salaried workers when you want a day-by-day breakout of their time. This functionality might be useful if, for example, a worker's time is associated with a project on two out of five days.</li>
</ul>
</td>
</tr>
</tbody>
</table>

## Adding earning codes to worker position agreements

If a worker receives recurring earnings or an earning rate that differs from the default earning code, you must assign an earning code to the worker to make sure that earnings are generated correctly. For more information, see [Generate earnings for workers](noam-usa-generate-earnings.md).

> [!NOTE]
> If you're setting up an earning code that is based on hours or pieces, the **Frequency** field isn't available. Earnings that are based on hours are generated based on the **Generate salary** and **Generate earnings from schedule** selections on the **Position** page. Earnings that are based on pieces are entered manually.

## Setting up worker tax regions

When you assign a tax region to a worker, all worker tax codes that apply to the worker are set up automatically. All parameters for the worker tax codes are set to their default values. We recommend that you review the worker tax codes for each worker to verify their accuracy. For more information, see [Set up taxes, tax regions, tax codes, and tax groups](noam-usa-tax-information-tasks.md).

To set up tax regions for workers, you must first create a list or spreadsheet that contains the following information for each worker that you're setting up tax regions for:

- The city and state where the worker claims residency
- The city and state of each location where the worker works

Additionally, for some states, you must specify the school district and municipality that are associated with the residence or work locations. To determine whether this information is required, consult the state tax office.

- On the **Worker tax regions** page, create a new tax region. Select the first task region by selecting the tax region where the worker claims residency, or the tax region where the worker can work. The first region that is assigned to a worker is designated as the worker's resident tax region. You can change the worker's residency at any time. For more information, see the "Changing worker residency (if a change is required)" section in this article.
- Most workers have only one worker tax region. However, a worker who resides in one tax region and works in another tax region has two worker tax regions. A worker who works in multiple locations has multiple tax regions.
- In most cases, the worker tax codes that are required for the tax region are automatically assigned to the worker when you close this page. However, if the worker isn't assigned to a position, or if the worker's position isn't assigned to a legal entity for payroll, the tax codes are assigned later, when the position and legal entity are assigned.
- You must then select a school district and municipality, if this information is required. If you use both fields, you must select a school district before you can select a municipality. To determine whether this information is required, consult the state tax office. If it isn't required, leave the fields blank.

## Changing worker residency (if a change is required)

The first tax region that is assigned to a worker is designated as the worker's resident tax region. A worker can have only one resident tax region at a time. If you know that a worker's resident tax region will change later, you can set up a new resident tax region that takes effect on a specified date. The current resident tax region automatically expires when the new resident tax region takes effect.

> [!TIP]
> If the resident tax region that you want to change has never been used in a payroll run, you can delete it.

## Assigning default tax regions

Tax regions are geographic areas where a specific set of payroll taxes applies. Tax regions generally correspond to the cities or towns where your workers reside or work. A worker tax region is a tax region that has been assigned to a specific worker. A default tax region is required for each position that a worker holds. A default tax region is a worker tax region that is used to generate earnings for a specific position that a worker holds. Therefore, if you don't assign a default tax region to the worker's tax position, earnings can't be generated for the position. In this case, to pay the worker, you must manually enter the earnings and then manually enter the tax region on each earning statement line.

If a worker's position requires different tax regions at different times, you must still select a single default tax region for the position. You can then change the tax region on individual earning statement lines after you generate earnings for the position.

> [!NOTE]
> Although the default tax region is used to generate earnings for a position, it's assigned to the worker who holds the position, not to the position itself. If the position is later reassigned to a different worker, a default tax region must be assigned to the new worker who holds the position. The default tax region isn't reassigned to the new worker when the position is reassigned.
>
> If the worker tax region that should be specified for the position isn't included in the list, close this page, and use the **Worker tax region** page to assign the tax region to the worker. Then return to this page to assign the default tax region.

## Setting up worker tax codes

You can manage a worker's tax options, such as filing status and total allowances, on the **Worker tax codes** page. You don't have to create or assign the worker tax codes, because the codes are automatically created and assigned to the worker when you create worker tax regions. At first, all parameters for worker tax codes are set to their default values. We recommend that you review the worker tax codes for each worker to make sure that they're accurate. For more information, see [Set up taxes, tax regions, tax codes, and tax groups](noam-usa-tax-information-tasks.md). You must first create a list or spreadsheet that contains the values of the tax options for all the tax codes that are assigned to each worker whose tax codes you're setting up. These values differ for each tax code. The information is typically collected on IRS Form W-4 or a similar form for the state.

### Tips for setting up worker tax codes

- When the **Worker tax codes** page is opened, it shows the tax codes that are effective on the current date. To view the tax codes and tax code parameters that were effective or will be effective on another date, click **Maintain versions**.
- You can also change the value of the parameter directly in the grid. In this case, the new version of the tax code parameter is stamped with the date but not the time. Therefore, the first change that is made during a given day creates a new version of the parameter. If you change the value later during the same day, the new change overwrites the previous change but doesn't create a new version of the parameter. Only the last change is saved in the date-effective version.

## Enrolling workers in benefits

Payroll information for a benefit isn't available if the **Payroll impact** field on the **Benefit elements** page is set to **None** for the benefit plan.

> [!NOTE]
> To set up payroll information for a garnishment or tax levy, see [Enroll workers in garnishments or tax levies](noam-usa-garnishment-tax-levy-enrollment-tasks.md). Benefit accrual plans, such as paid time off, aren't set up or calculated like other benefits.

For information about how to enroll a worker in a benefit accrual plan, see [Set up benefit accrual plans](noam-usa-benefit-accrual-plan-tasks.md). For more information about how to set up a benefit, see [Set up benefits](noam-usa-benefit-set-up-tasks.md).

The following table show the information that you must enter on the **Payroll** FastTab. The fields on this FastTab can vary, depending on the setting of the **Payroll impact** field on the **Benefit elements** page.

<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Paid by</td>
<td>The legal entity that pays for the selected benefit for this worker. This legal entity is usually the same legal entity that the worker is employed by and that pays for the worker position.</td>
</tr>
<tr>
<td>Position</td>
<td>Leave this field blank, except when the total costs for the benefit must follow a specific position. Union dues are an example of a benefit that is assigned to a position. If you select a position, the benefit calculations are based only on the earnings from the position. If you don't select a position, the deductions and contributions for the benefit are calculated based on all the worker's earnings. The amounts are split among all the positions that the employee is currently assigned to. The distribution for the deductions and calculations uses the same distribution as the earnings for those positions.</td>
</tr>
<tr>
<td>Calculation priority</td>
<td>The order that deductions and contributions for the selected benefit are calculated in, relative to other benefits. The deductions and contributions for the benefit that has the lowest calculation priority are calculated first. The lowest calculation priority is 0 (zero). When multiple benefits have the same number, the calculations for those benefits are done in alphabetical order. The calculation order is important when the result of the calculation for one benefit is used in the calculation for another benefit. This behavior is especially likely for garnishments and tax levies. Your legal advisors should help you determine the correct calculation priority for all benefits.</td>
</tr>
<tr>
<td>Deduction priority</td>
<td>The order that deductions for the selected benefit are made in, relative to other deductions. The deduction for the benefit that has the lowest deduction priority is made first. The lowest deduction priority is 1. When multiple benefits have the same number, the deductions for those benefits are made in alphabetical order. Your legal advisors should help you determine the correct deduction priority for all benefits. The default value for this field is set up on the <strong>Benefit elements</strong> page.</td>
</tr>
<tr>
<td>Rate source, Basis, Deduction</td>
<td>Together, the basis option and the deduction amount are used to calculate the amount of the payroll deduction for the benefit. The default values for these fields are set in the <strong>Basis</strong> and <strong>Amount or rate</strong> fields on the <strong>Benefits</strong> page. The <strong>Rate source</strong> field determines whether these fields are changed to match the default values when the benefit rates are updated from the benefit.
<ul>
<li>If you select <strong>Benefit</strong>, the deduction amount and basis for the worker are updated automatically when you click <strong>Update benefit rates</strong> on the <strong>Benefits</strong> page.</li>
<li>If you select <strong>Custom</strong>, the deduction amount and basis for the worker aren't changed when you click <strong>Update benefit rates</strong> on the <strong>Benefits</strong> page. Select this option when the contribution for a worker is specific to that worker. For example, after a rate change, contribution amounts might be grandfathered in for some workers.</li>
</ul>
[!NOTE] For contributions, the default value of the <strong>Rate source</strong> field is <strong>Benefit</strong>.
</td>
</tr>
<tr>
<td>Notes</td>
<td>As a best practice, if you change the default values for any payroll fields on this page, you should enter an explanation in this field.</td>
</tr>
</tbody>
</table>

The following tables show the information that you must enter on the **Payroll limits** FastTab. This FastTab might contain a set of payroll limits for contributions, deductions, or both contributions and deductions, depending on the value of the **Payroll impact** field on the **Benefit elements** page.

**Deductions**

| Field        | Description |
|--------------|-------------|
| Limit amount | The maximum amount that can be deducted from a worker's pay for the selected benefit. If there is no maximum amount, leave this field blank.[!IMPORTANT] The **Remaining** field shows the amount that can be deducted for the benefit in future pay periods before the end of the limit period is reached. The amount is automatically updated during each pay run. You can also manually change the amount. Because no change history is kept, we recommend that you not enter or change the value of this field. |
| Limit period | The period that the deduction limits apply to. For example, the limit amount is 1,200.00, and the **Limit period** field is set to **Year**. In this case, when the cumulative deductions for the benefit reach 1,200.00, no additional deductions are allowed for that benefit for the rest of the year. The **Limit end** field shows the last day of the current limit period. When the current limit period ends, the value of this field is automatically reset to the end of the new limit period.[!NOTE] The limit period is based on the calendar. |

**Contributions**

| Field        | Description |
|--------------|-------------|
| Limit amount | The maximum amount that the employer can contribute for the selected benefit. If there is no maximum amount, leave this field blank.[!IMPORTANT] The **Remaining** field shows the amount that can be contributed for the benefit in future pay periods before the end of the limit period is reached. The amount is automatically updated during each pay run. You can also manually change the amount. Because no change history is kept, we recommend that you not enter or change the value of this field. |
| Limit period | The period that the contribution limits apply to. For example, the limit amount is 1,200.00, and the **Limit period** field is set to **Year**. In this case, when the cumulative contributions for the benefit reach 1,200.00, no additional contributions are allowed for that benefit for the rest of the year. The **Limit end** field shows the last day of the current limit period. When the current limit period ends, the value of this field is automatically reset to the end of the new limit period.[!NOTE] The limit period is based on the calendar. |

## Additional resources

[Set up taxes, tax regions, tax codes, and tax groups](noam-usa-tax-information-tasks.md)

[Set up benefits](noam-usa-benefit-set-up-tasks.md)

[Set up garnishments and tax levies](noam-usa-garnishment-tax-levy-set-up-tasks.md)

[Enroll workers in garnishments or tax levies](noam-usa-garnishment-tax-levy-enrollment-tasks.md)


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
