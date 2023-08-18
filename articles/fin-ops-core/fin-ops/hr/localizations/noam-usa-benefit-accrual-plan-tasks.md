---
# required metadata

title: Set up benefit accrual plans
description: This article describes the process for setting up benefit accrual plans. It includes information about how to gather information and enroll workers.
author: twheeloc
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: PayrollAccrual
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 221474
ms.assetid: c6d387ac-91fd-40c0-aaaa-809f2793d28b
ms.search.region: USA
# ms.search.industry: 
ms.author: panolte
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Set up benefit accrual plans

[!include [banner](../../includes/banner.md)]

This article describes the process for setting up benefit accrual plans. It includes information about how to gather information and enroll workers.

For more information about benefit accrual plans, see [Payroll data updates FAQ](noam-usa-payroll-data-updates.md).

## Gather the required information

A benefit accrual plan includes a set of rules that determine how hours in the plan accrue and are used. The plan also includes a list of earning codes that are matched against the earning codes on earnings statement lines. Therefore, the plan balance can be reduced when a specific earning code is used.

The rules for the plan are based on the number of months that a worker has been employed with the organization. The months of employment are based on the employment start date or the seniority date. You define rules to control the rate that benefits accrue at, and to control the maximum accrual limit, minimum balance, and carry-forward limit.

### Example

Your paid time off (PTO) plan has three rates, which are based on years of employment.

| Years of employment          | PTO days per year |
|------------------------------|-------------------|
| Fewer than 5                 | 10                |
| At least 5 but fewer than 10 | 15                |
| At least 10                  | 20                |

The benefit accrual is based on the years of employment. For workers to accrue the correct total, you must convert the years of employment to months of employment. You must also convert the number of PTO days per year to the number of PTO hours that accrue for every hour that is worked. To convert the years of employment to months of employment, multiply the number of years by 12. Here are the calculations for the example plan:

0 × 12 = 0

5 × 12 = 60

10 × 12 = 120

To convert the PTO days per year to the hourly accrual rate, multiply the number of days that accrue per year by the number of hours in a work day to get the number of hours that accrue per year. Then divide that number by the number of hours that are worked in a year to get the hourly accrual rate. The following formula will work for most workers:

Number of days accrued per year × 8 hours worked in a day ÷ 2,080 hours worked in a year = Hourly accrual rate

Here are the calculations for the example plan:

10 × 8 ÷ 2,080 = 0.03846

15 × 8 ÷ 2,080 = 0.05769

20 × 8 ÷ 2,080 = 0.07692

Enter these numbers into a table, as shown here, to make it easier for you to set up the plan rules.

| Months of employment | Hourly accrual rate |
|----------------------|---------------------|
| 0                    | 0.03846             |
| 60                   | 0.05769             |
| 120                  | 0.07692             |

> [!TIP]
> You can use the hourly accrual rate to verify the amount that should accrue in each pay statement. For example, if workers who accrue 15 days per year are paid biweekly, and they work 40 hours per week, multiply the hourly accrual rate of 0.05769 by 80 hours. The result is 4.6152. Therefore, the workers should accrue 4.6152 hours on each pay statement.

## Set up benefit accrual plans

To set up the benefit accrual plans, enter the following information on the **Benefit accrual plans** page.

<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Benefit accrual plan Description</td>
<td>The name and description for the plan.</td>
</tr>
<tr>
<td>Annual plan start date</td>
<td>The start date for the plan. The plan is reset each year on the anniversary of this date. If you leave this field blank, the plan isn't reset. Any fields that show data for the plan year, such as the <strong>Plan year accrued</strong> and <strong>Plan year used</strong> fields on the <strong>Benefit accrual balances</strong> page, will include all transactions from the start of the plan instead of all transactions in the plan year.</td>
</tr>
<tr>
<td>Carry forward balances</td>
<td>If you select this option, balances at the end of the plan year can be carried over to the next plan year. When you create the plan rules, you can limit the number of hours that can be carried forward.</td>
</tr>
<tr>
<td>Accrual rate basis</td>
<td>The method that this plan uses to accrue benefits for workers who are enrolled in the plan. The method is used together with the value in the <strong>Amount or rate</strong> field to determine the number of hours that are added to the worker's plan. Select one of the following options:
<ul>
<li><strong>Hourly rate</strong> – The number of hours that are added to the plan balance are calculated by multiplying the number of eligible hours on the pay statement by the rate in the <strong>Amount or rate</strong> field.</li>
<li><strong>Fixed amount by payroll frequency</strong> – The number of hours in the <strong>Amount or rate</strong> field is added to the plan balance on the last day of each pay period that is included in the selected payroll calculation frequency.</li>
<li><strong>Fixed amount by date</strong> – The number of hours in the <strong>Amount or rate</strong> field is added to the plan balance on the last day of the pay period that includes the date that is determined based on the value in the <strong>Accrual date</strong> field.</li>
<li><strong>Hours of compensatory time</strong> – The number of hours that are added to the plan balance are calculated by multiplying the number of eligible hours on the pay statement by the value in the <strong>Rate for compensatory time</strong> field on the <strong>Earning codes for plan accrual</strong> FastTab.</li>
</ul>
</td>
</tr>
<tr>
<td>Frequency</td>
<td>The payroll calculation frequency that includes the pay periods when the number of hours in the <strong>Amount or rate</strong> field is added to the plan balance.
<blockquote>[!NOTE] This field is available only when the accrual rate basis is <strong>Fixed amount by payroll frequency</strong>.</blockquote>
</td>
</tr>
<tr>
<td>Accrual date</td>
<td>The day each year when the number of hours in the <strong>Amount or rate</strong> field is added to the plan balance. Select one of the following options:
<ul>
<li><strong>Employment start date</strong> – This date is on the <strong>Employment history</strong> page.</li>
<li><strong>Seniority date</strong> – This date is on the <strong>Worker</strong> page. We recommend that you verify that the seniority date field always has a value. If you use the seniority date to determine the months of service, and the <strong>Seniority date</strong> field on the <strong>Worker</strong> page is blank, the worker can use hours from the benefit accrual plan, but no hours can accrue in the plan.</li>
<li><strong>Annual plan start date</strong></li>
<li><strong>Custom date</strong> – A date that is specified for this plan.</li>
</ul>
<blockquote>[!NOTE] This field is available only when the accrual rate basis is <strong>Fixed amount by date</strong>.</blockquote></td>
</tr>
<tr>
<td>Custom accrual date</td>
<td>The month and date each year when the number of hours in the <strong>Amount or rate</strong> field is added to the plan balance.
<blockquote>[!NOTE] This field is available only when the accrual rate basis is <strong>Fixed amount by date</strong> and the accrual date is <strong>Custom date</strong>.</blockquote>
</td>
</tr>
</tbody>
</table>

The following information can be entered on the **Plan rules** FastTab.

Each line that you add to a benefit accrual plan provides the rules for accruing time and using plan benefits for workers who have the specified number of months of service.

| Field                 | Description |
|-----------------------|-------------|
| Months of service     | The minimum number of months of service for the selected rule. The number of months of service is based on the employment start date, the seniority date, or a date that is specified for the worker on the **Benefit accruals** page. **NOTE:**  The employment start date is on the **Employment history** page, and the seniority date is on the **Worker** page. We recommend that you verify that the **Seniority date** field has a value. If you use the seniority date to determine the months of service, and the **Seniority date** field on the **Worker** page is blank, the worker can use hours from the benefit accrual plan, but no hours can accrue to that plan. |
|                       |We recommend that every plan include a row that starts at 0 (zero) months of service. Each row ends when the next row starts. The last row starts at the specified number of months and doesn't end. For example, the rows in your plan have 0, 60, and 120 for months of service. The rate and limits in the first row start when a worker is hired and are applied through the end of the worker's eleventh month. The second row starts at 12 months, and the rates and limits are applied through the end of the fifty-ninth month. The third row starts at 60 months, and the rates and limits are applied as long as the worker continues to be employed by your organization. |
| Amount or rate        | The amount of the accrual if the accrual rate basis is a fixed amount, or the rate that is used to calculate the amount if the accrual rate basis is an hourly rate. For example, in a plan where a worker accrues 80 hours each year, if the benefit accrues at an hourly rate, enter 0.03846. If the benefit accrues as a fixed amount by date, enter 80. The rate for compensatory time plans is entered on the **Earning codes for plan accrual** FastTab. |
| Maximum accrual limit | The maximum number of hours that can accrue in the plan in a single plan year. When this number is reached, no more hours accrue in the plan until the start of the next plan year, unless a manual adjustment reduces the accrued amount for the plan year. If the plan isn't reset each year, this value is the maximum number of hours that can accrue over the life of the plan. |
| Minimum balance       | The number of hours that must be available in the plan before a worker can use hours from the plan. When the available balance is less than this number, the worker can't use any hours from the plan until additional hours have accrued, or until the available balance has been adjusted. **NOTE:**  To let workers take time off before they have accrued the hours, enter a negative number. If an earnings statement includes hours that will reduce the available balance in the plan to less than the minimum balance, the earnings statement lines that include those hours aren't released. |
| Carry-forward limit   | The highest number of hours that can be carried forward from one plan year to the next. If the **Carry forward balances** option isn't selected, this field isn't available, and no hours are carried forward. |

- The earning codes that are entered on the **Earning codes for plan usage** FastTab are used to verify the available balance when an earnings statement that includes the earning code is released. The codes are also used to reduce the plan balance when a pay statement line that includes the earning code is submitted for payment.
- If you use the earning code for a benefit accrual on an earnings statement for a worker who isn't enrolled in the plan, no validation occurs.
- The earning codes that are entered on the **Earning codes for plan accrual** FastTab are used to increase the plan balance when a pay statement line that includes the earning code is submitted for payment. For example, you enter an earning code for regular hours here. If that earning code is used on an earnings statement line that contains eight hours, when the earnings statement is submitted for payment, the worker's balance in the plan is increased by eight hours times the specified rate.

> [!NOTE]
> This FastTab is available only when the accrual rate basis for the plan is **Hourly rate** or **Hours of compensatory time**.

| Fields                     | Description |
|----------------------------|-------------|
| Earning type               | Select whether to enter an earning code or an earning code group. When you include both earning codes and earning code groups in a benefit accrual plan, an earning code might be included in the table multiple times. An earning code is included in the table multiple times if the code appears in the table by itself and as part of an earning code group. Each earning code is processed only one time, regardless of the number of times that the code occurs in the table. **NOTE:**  This control is available only when the accrual rate basis for the plan is **Hourly rate**. |
| Earning code group         | The earning code groups that contain hourly earning codes. The hourly earning codes increase the plan balance when a pay statement line that includes the earning code is submitted for payment. Earning codes other than hourly earning codes are disregarded when the plan balance is calculated. **NOTE:**  This control is available only when the accrual rate basis for the plan is **Hourly rate**. |
| Earning code               | The earning codes that increase the plan balance when a pay statement line that includes the earning code is submitted for payment. |
| Description                | The description of the selected earning code or earning code group. |
| Rate for compensatory time | The rate that is used to calculate the amount of compensatory time. For example, if the worker accrues one hour of compensatory time for each hour that is worked by using the selected earning code, enter **1**. If the worker accrues 1.5 hours of compensatory time, enter **1.5**. **NOTE:**  This control is available only when the accrual rate basis for the plan is **Hours of compensatory time**. |

## Enroll workers in benefit accrual plans

The process for enrolling workers in benefit accrual plans differs from the process for enrolling them in other benefits. Mass enrollment isn't available for benefit accrual plans, and eligibility processing isn't performed.

Make sure the **Service date basis** field is correct.

If the service date basis is set to **Seniority date**, make sure that a seniority date is assigned to the worker.

> [!NOTE]
> You can add and delete enrollments only for benefit accrual plans for the legal entity that you're signed in to.

## Next step
The next step is to set up payroll taxes. For more information, see [Set up taxes, tax regions, tax codes, and tax groups](noam-usa-tax-information-tasks.md).


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
