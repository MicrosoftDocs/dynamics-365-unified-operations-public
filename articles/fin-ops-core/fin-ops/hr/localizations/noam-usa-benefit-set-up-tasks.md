---
# required metadata

title: Set up benefits
description: This article describes how to set up benefits that workers and their dependents and beneficiaries can receive, and how to maintain payroll information for benefits.
author: twheeloc
ms.date: 02/28/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: HcmBenefit, HcmBenefitElementSetup, PayrollBenefitCalculationRateSetup
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 221174
ms.assetid: eb7d562e-075f-448a-b9c2-0a06e938805b
ms.search.region: USA
# ms.search.industry: 
ms.author: panolte
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Set up benefits

[!include [banner](../../includes/banner.md)]

This article describes how to set up current and future benefits that workers and their dependents and beneficiaries can receive, and how to maintain payroll information for benefits. Examples of benefits include medical insurance, retirement investments, workers' compensation plans, and parking benefits.

Garnishments and tax levies are also set up as benefits, but the steps for setting them up differ. For more information, see [Set up garnishments and tax levies](noam-usa-garnishment-tax-levy-set-up-tasks.md). After you set up benefit elements by using the **Benefit elements** page, you must create the benefits so that they can be assigned to workers. When you create a benefit, you link an option to a benefit plan, designate a benefit period, and assign eligibility rules to the benefit.

## Setting up benefit elements

A benefit is a combination of the benefit type, plan, and option:

- **Type** – A collection or category that includes plans for a specific benefit, such as health insurance or parking.
- **Plan** – A specific benefit that is contracted from a provider.
- **Option** – The coverage level, such as employee only, or employee and spouse.

### Setting up benefit types

To set up benefits, you must first set up benefit types. On the **Benefit elements** page, in the **Types** area, click **New** to create a benefit type. Then enter the following information.

<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Type Description</td>
<td>Enter a name and a brief description for the benefit type.</td>
</tr>
<tr>
<td>Concurrent enrollment</td>
<td>Select one of the following concurrent enrollment options:
<ul>
<li><strong>Multiple enrollments per type</strong> – You can enroll a worker in multiple plans that have the same benefit type, even if the enrollment is effective for the same period. For example, a worker can be enrolled in two term life insurance plans.</li>
<li><strong>One enrollment per type</strong> – You can't enroll a worker in more than one plan that has the same benefit type for the same period. For example, if the worker already has health insurance for a specified period, you can't enroll the worker in another health insurance plan that covers the same period.</li>
</ul>
</td>
</tr>
<tr>
<td>Payroll category</td>
<td>Select a payroll category to use for benefits that have the new benefit type. The payroll category determines the settings that are available for a selected plan in the <strong>Plans</strong> area of this page. Settings that don't apply to the payroll category aren't available.</td>
</tr>
</tbody>
</table>

### Setting up benefit plans

You must also set up benefit plans. On the **Benefit elements** page, in the **Plans** area, click **New** to create a new benefit plan. Then enter the following information.

<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Plan description</td>
<td>Enter a name and a brief description for the benefit plan.</td>
</tr>
<tr>
<td>Type</td>
<td>Select the benefit type. The payroll category that is associated with the selected benefit type controls the options that are available for the benefit plan. For example, options that are related to retirement plans are available only when the payroll category for the benefit type is <strong>Retirement</strong>.</td>
</tr>
<tr>
<td>Payroll impact</td>
<td>Select one of these options:
<ul>
<li><strong>None</strong> – No amounts are contributed by the employer or deducted from the worker's pay. When you select this option, the FastTabs on this page aren't available. Note that when the payroll category for the benefit type is <strong>None</strong>, the payroll impact is also <strong>None</strong>.</li>
<li><strong>Deduction only</strong> – An amount is deducted from the worker's pay for this benefit, but no employer contribution is made. When you select this option, controls that are related to payroll deductions are available on the other FastTabs, but controls that are related to employer contributions aren't available.</li>
<li><strong>Contribution only</strong> – An employer contribution is made for this benefit, but no amount is deducted from the worker's pay. When you select this option, controls that are related to employer contributions are available on the other FastTabs, but controls that are related to payroll deductions aren't available.</li>
<li><strong>Deduction and contribution</strong> – An employer contribution is made for this benefit, and an additional amount is deducted from the worker's pay. When you select this option, controls that are related to both employer contributions and payroll deductions are available on the other FastTabs.</li>
</ul>
</td>
</tr>
</tbody>
</table>

Next, you must select the pretax basis for the plan on the **Tax rule** FastTab. The pretax basis determines the pattern of before-tax and after-tax treatment for payroll deductions and employer contributions. In the rare event that no preset options are available for your plan, select **Custom**, and then select a custom pretax method to specify the taxes that should not be deducted from the paychecks of employees who enroll in the plan.

> [!IMPORTANT]
> Select **Custom** only when no preset patterns are appropriate. If you must use **Custom**, work with your legal advisors to verify that the settings for the benefit plan are correct. For **Retirement** plans, you must enter the following information on the **Retirement plans** FastTab.

<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Retirement type</td>
<td>Select the type of retirement plan.</td>
</tr>
<tr>
<td>Contribution limit</td>
<td>Select the value that the maximum contribution for this benefit plan is based on:
<ul>
<li><strong>None</strong> – There is no contribution limit.</li>
<li><strong>Employee limit</strong> – The employer contribution stops when the employee's payroll deduction limit is reached. For the payment that the deduction limit is reached in, the employer contribution is proportionally limited. For example, if only half the expected employee deduction can be made before the limit is reached, only half the employer contribution is made.</li>
<li><strong>Fixed</strong> – The employer contribution limit is a fixed amount per calendar year. The amount is set in the contribution limit field for the benefit plan.</li>
<li><strong>Combination</strong> – Both the Employee limit method and the Fixed method are evaluated, and the employer contribution is limited by whichever method reaches the limit first.</li>
</ul>
You enter the actual amount of the contribution limit on the <strong>Payroll details</strong> FastTab.</td>
</tr>
</tbody>
</table>

Enter the following information on the **Payroll details** FastTab.

<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Lock pay statement</td>
<td>Select this option to prevent pay statement lines that include the benefit plan from being changed. When you select this option, lines that include the benefit plan can be added to or deleted from the pay statement, but lines that include this benefit plan can't be changed.</td>
</tr>
<tr>
<td>Recover arrear</td>
<td>Select this option to recover arrearages that are based on this plan. This option is available only if the payroll category on the benefit type that is used for this plan is <strong>Standard</strong>.</td>
</tr>
<tr>
<td>Deduction method</td>
<td>Select the method that is used to determine the deduction amount if the employee's pay isn't enough to cover the whole amount of the deduction for the selected benefit plan:
<ul>
<li><strong>All or nothing</strong> – If the whole amount of the deduction can't be made, no amount is deducted. The whole amount is placed in arrears.</li>
<li><strong>Partial</strong> – As much of the deduction amount as possible is deducted. Any remaining amount is placed in arrears.</li>
</ul>
</td>
</tr>
<tr>
<td>Payment type</td>
<td>Select at least one of the following payment run types:
<ul>
<li>Primary</li>
<li>Additional</li>
<li>Gross up</li>
</ul>
Deductions and contributions for the selected benefit plan are included in payroll calculations for payroll runs that produce the payment run types that you select here. For more information about payment run types, see <a href="noam-usa-earning-code-group-tasks.md">Earning code and earning code group tasks</a>.</td>
</tr>
<tr>
<td>Deduction priority</td>
<td>Enter a number to specify where this deduction should be made in the sequence of applicable deductions. The lower the deduction priority number that you enter, the higher the deduction priority. The lowest deduction priority number that you can enter is 0 (zero). When amounts are deducted from pay statements, the deductions start with the benefit that has the lowest deduction priority number. When multiple benefits have the same number, the deductions for those benefits are made in alphabetical order. 
<blockquote>[!IMPORTANT] Some benefits are considered mandatory deductions in some states. Those benefit plans should have the highest deduction priority (that is, the lowest deduction priority number). In many states, deductions for garnishments and tax levies must be made before deductions for any other benefits are made. For more information, see <a href="noam-usa-garnishment-tax-levy-set-up-tasks.md">Garnishment and tax levy setup tasks</a>. </blockquote>
<p>By default, the value in this field is entered on the <strong>Maintain benefits</strong> page when a worker is enrolled in a benefit. You can change the value for a worker at the time of enrollment or at any other time. If you change the default value, existing benefit assignments don't change. You must change those values individually.</p></td>
</tr>
<tr>
<td>Default deduction limits Default contribution limits</td>
<td>Enter the limit amount for the limit period. The limit amount is the maximum amount that can be deducted or contributed for the selected benefit during the specified limit period. If there is no maximum amount, leave these fields blank. When the payroll category that is assigned to the benefit type is <strong>Retirement</strong>, the limit period is automatically set to <strong>Year</strong>. When payroll is calculated, the limit amount is calculated across the limit period. For example, the limit amounts for deductions is 1,200.00, and the limit period is <strong>Year</strong>. In this case, when the cumulative amount that has been deducted for the benefit reaches 1,200.00, no additional deductions are made for the benefit for the rest of the year.</td>
</tr>
</tbody>
</table>

On the **Accounting** FastTab, after you've selected the legal entity to set the accounting information for, you must enter the following information.

| Field                | Description |
|----------------------|-------------|
| Category             | Select the project category to use for the employer contribution. Typically, the **Payroll** category is used. However, your organization might use a different category. |
| Vendor               | Select the vendor that payments for this plan are paid to. |
| Financial dimensions | Enter the default financial dimensions. |
| Main account         | Select the main accounts to use to post deductions and contributions. |

If the benefit plan is offered by more than one legal entity in your organization, complete this page for each legal entity. On the **Reporting** FastTab, if the benefit must be reported on Form W-2, select the number of the box on Form W-2 where the amount of the payroll deductions or employer contributions for the selected benefit are reported. Then enter the label to use for the boxes.

### Setting up benefit options

> [!NOTE]
> To create retirement benefits, you must first set up the contribution calculation rate tables. If you haven't yet set up the rate tables, continue with the "Setting up contribution calculation rates for retirement benefits" section and then the "Creating a new benefit" section, later in this article.

## Setting up contribution calculation rates for retirement benefits

For retirement benefits, the method that is used to determine the employee contribution rate and the employer contribution rate is determined by the rate table that you define on the **Contribution calculation rates** page and then assign to the benefit on the **Benefits** page. Before you start this task, we recommend that you create a list of your retirement plans. For each plan, include the contribution method, employee deductions, and employer contributions.

### Example that involves two retirement plans

Your organization offers two retirement plans:

- **Plan 1** – Your organization matches the worker's contributions to the plan at a rate of 50 percent up to the first 3 percent, and then at a rate of 100 percent up to 6 percent.
- **Plan 2** – Your organization contributes 1 percent of the worker's pay to the 401(k) plan when the worker's contributions are between 1 percent and 3 percent of their pay. It contributes 2 percent when the worker's contributions are between 3 percent and 6 percent. Finally, it contributes 3 percent when the worker's contributions are 6 percent or more.

For this example, the rate table looks like this.

| Plan | Employee deduction rate | Employee contribution rate | Contribution method |
|---|---|---|---|
| Plan 1 | 0.0000 | 0.5000 | Percent of employee |
| Plan 1 | 0.0300 | 1.000 | Percent of employee |
| Plan 1 | 0.0600 | 0 | Fixed percent |
| Plan 2 | 0.0100 | 0.0100 | Fixed percent |
| Plan 2 | 0.0300 | 0.0200 | Fixed percent |
| Plan 2 | 0.0600 | 0.0300 | Fixed percent |

Two tier types are available on the **Contribution calculation rates** page.

- **Single line** – If you select this tier type, only one line from the rate table is used to calculate the amount of the employer's contribution. For example, if the worker's deduction rate is 10 percent of their $1,000.00 earnings, the employer's contribution for plan 1 is 0.00. For plan 2, the employer's contribution is 30.00 for the same worker.
- **Cascading tier** – If you select this tier type, multiple lines from the rate table are used to calculate the amount of the employer's contribution. Only lines that have a deduction rate that is less than or equal to the actual worker deduction rate are used to calculate the employer contribution amount. For example, if the worker's deduction rate is 10 percent of their $1,000.00 earnings, the employer's contribution for plan 1 is 45.00. For plan 2, the employer's contribution is 60.00 for the same worker.

The following table shows the formula that is used to calculate the amount of the employer's contribution amount for plans 1 and 2 for each tier type.

| Plan | Tier type | Employee earnings | Employee deduction amount | Employer contribution amount | Formula for calculating the employer contribution amount |
|---|---|---|---|---|---|
| Plan 1 | Single line | 1,000.00 | 100.00 | 0.00 | |
| Plan 1 | Cascading tier | 1,000.00 | 100.00 | 45.00 | (1,000 × 0) + (\[1,000 × (0.06 – 0.03)\] × 0.5) + (\[1,000 × (0.03 – 0.00\]) × 1) = 45 |
| Plan 2 | Single line | 1,000.00 | 100.00 | 30.00 | |
| Plan 2 | Cascading tier | 1,000.00 | 100.00 | 60.00 | (1,000 × 0.03) + (1,000 × 0.02) + (1,000 × 0.01) = 60 |

Use the data in your own table to set up the contribution calculation rate tables that you require.

### Setting up a rate table for a retirement benefit plan

> [!IMPORTANT]
> The tier type that you select can significantly affect the amount of the employer's contribution for the retirement benefit plan. See the example earlier in this section to understand how tier types affect employer contribution amounts. When you create your rate table, you must enter the following information on the **Maintain rate structure versions** page.

<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Worker deduction</td>
<td>The lowest percentage of a worker's pay that is matched by an employer contribution at the specified rate.</td>
</tr>
<tr>
<td>Employer contribution</td>
<td>The matching contribution to an employee's retirement plan. The value is expressed either as a percentage of the employee's pay or as a percentage of the employee's own contribution to the plan. The <strong>Contribution method</strong> field determines how this rate is used to calculate the amount of the employer's contribution.</td>
</tr>
<tr>
<td>Contribution method</td>
<td><ul>
<li><strong>Fixed percent</strong> – The employer's contribution is calculated by multiplying the employer contribution rate by the employee's earnings. For example, the rate for the worker's deduction is 0.03, and the rate for the employer's contribution is 0.02. In this case, the amount of the employer's contribution is 0.02, or 2 percent of the employee's earnings. For this option, the worker deduction amount and the employer contribution amount are calculated separately.</li>
<li><strong>Percent of employee</strong> – The employer's contribution is calculated by multiplying the employer contribution rate by the worker deduction rate. For example, the worker deduction rate is 0.03, and the employer contribution rate is 0.5. In this case, the amount of the employer's contribution is 0.03 × 0.5 = 0.015, or 1.5 percent of the employee's earnings.</li>
</ul>
<blockquote>[!NOTE] The worker deduction rate and employer contribution rate are determined by the rate table that you define on the <strong>Contribution calculation rates</strong> page and then assign to the benefit on the <strong>Benefits</strong> page.</blockquote>
</td>
</tr>
</tbody>
</table>

## Creating new benefits

After you've set up benefit elements on the **Benefit elements** page, you must create the benefits so that they can be assigned to workers. When you create a benefit, you link an option to a benefit plan, designate a benefit period, and assign eligibility rules to the benefit. When you create a new benefit, you must enter the following information.

| Field                | Description                                                         |
|----------------------|---------------------------------------------------------------------|
| Plan                 | The name of the benefit.                                            |
| Option               | An option to add to the benefit.                                    |
| Effective Expiration | The first and last dates when the benefit is available to a worker. |

After you've created the benefit, you must add some details. Click **Edit**, and enter information on the following FastTabs. On the **Eligibility rules** FastTab, you must select the method that is used to determine eligibility. Select one of the following options.

| Method                     | Description |
|----------------------------|-------------|
| All workers are eligible   | The benefit is included in eligibility processing, but eligibility rules aren't enforced for the benefit. All workers are always eligible. When you select this method, any worker who is included in an eligibility event can enroll in the benefit after the event is processed. However, workers can't enroll at any other time. Therefore, you can limit enrollment in the benefit to the appropriate enrollment periods, but without otherwise limiting eligibility for the benefit. |
| Rule based                 | User-defined eligibility rules are enforced for the benefit. In the **Rule type** list, select the type of rule type to use. This method is used for most benefits. |
| Bypass eligibility process | The benefit isn't included in eligibility processing. Any worker can be enrolled in the benefit at any time. You don't have to process an eligibility event before you enroll a worker in the benefit. This method is usually used for garnishments and tax levies. |

If any eligibility overrides are required, enter the following information on the **Eligibility overrides** FastTab.

| Field                       | Description |
|-----------------------------|-------------|
| Name                        | Select the worker to add an override for. |
| Override start Override end | Enter the first and last dates when the override applies. When you determine eligibility for a benefit by using a coverage start date that is in the specified date range, the employee is eligible for the benefit, regardless of the benefit eligibility rules. |

On the **Payroll** FastTab, you must enter the following information for the benefit. Note that this FastTab might include settings only for deductions, only for contributions, or for both deductions and contributions. The settings that are included depend on the value of the **Payroll impact** field for the benefit plan on the **Benefit elements** page. If the **Payroll impact** field is set to **None**, this FastTab isn't available. The values on this FastTab are used as default values on the **Maintain benefits** page for each worker who is enrolled in the selected benefit.

<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Frequency</td>
<td>The payroll calculation frequency that is used to determine the pay periods that the selected benefit is calculated in. You define payroll frequencies and pay periods on the <strong>Payroll calculation frequencies</strong> page.</td>
</tr>
<tr>
<td>Basis</td>
<td>The option to use together with the value of the <strong>Amount or rate</strong> field to determine the amount that should be deducted or contributed for the benefit. The amount is calculated only in the pay periods that are determined by the payroll calculation frequency. Earnings are included in the calculation only when the earning code for the earnings is listed on the <strong>Earnings basis</strong> FastTab, and when the required parameters are set on the <strong>Earning codes</strong> page.</td>
</tr>
<tr>
<td>Amount or rate</td>
<td>The amount or rate to use together with the value of the <strong>Basis</strong> field to determine the amount that should be deducted or contributed for the benefit.
<ul>
<li>If the basis for deduction is <strong>Fixed amount</strong>, enter the amount to use as the payroll deduction or employer contribution for the selected benefit.</li>
<li>If the basis for the deduction is <strong>Percentage of earnings</strong>, <strong>Regular portion of all pay</strong>, or <strong>Regular earnings</strong>, enter the percentage of the worker's included earnings or pay to use as the payroll deduction or employer contribution for the selected benefit.</li>
<li>If the basis for the deduction is <strong>Productive hours</strong>, <strong>Earning hours</strong>, or <strong>Total hours</strong>, enter the hourly rate for the payroll deduction or employer contribution.</li>
</ul>
This field isn't available if the <strong>Retirement</strong> payroll category is assigned to the benefit type on the <strong>Benefit elements</strong> page.</td>
</tr>
<tr>
<td>Calculation rate</td>
<td>The variable rate structure that is used to calculate employer contributions to a retirement plan. This field is available only when the <strong>Retirement</strong> payroll category is assigned to the benefit type on the <strong>Benefit elements</strong> page.</td>
</tr>
</tbody>
</table>

## Setting up worker's compensation plans

Worker's compensation plans are handled like other employee benefits. To set up a worker's compensation plan, follow the steps in the preceding section, "Creating new benefits," and use the values in the following table.

| Field                 | Enter this value                                                          |
|-----------------------|---------------------------------------------------------------------------|
| Type                  | The benefit type that you created to use with worker's compensation plans |
| Concurrent enrollment | **Multiple enrollments per type**                                         |
| Payroll category      | **Worker's compensation**                                                 |
| Payroll impact        | **Contribution only**                                                     |
| Pretax basis          | **None**                                                                  |
| Limit period          | Leave this field blank.                                                   |
| Limit amount          | Leave this field blank.                                                   |

On the **Worker's compensation** FastTab, specify the state that each benefit applies to.

## Next step

The next step is to set up payroll information for positions and workers. For more information, see [Set up payroll for workers](noam-usa-worker-position-payroll-tasks.md).

## Additional resources

[Set up payroll for workers](noam-usa-worker-position-payroll-tasks.md)

[Set up payroll calculation frequencies](noam-usa-payroll-calculation-frequencies-tasks.md)

[Set up garnishments and tax levies](noam-usa-garnishment-tax-levy-set-up-tasks.md)


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
