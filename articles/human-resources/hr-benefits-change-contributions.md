---
# required metadata

title: Change health savings account (HSA) and savings plan contributions during the year
description: Learn how employees and benefits administrators can change contributions for health savings account (HSA) and savings plans, such as 401(k) plans, at any time during a benefit period.
author: ramagadu
ms.reviewer: twheeloc
ms.date: 09/24/2026
ms.topic: how-to
# optional metadata

ms.search.form: BenefitPlanEmployee, BenefitESSViewCheckedOutPlans, BenefitPlanListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ramagadu
ms.search.validFrom: 2026-09-24
ms.dyn365.ops.version: Human Resources

---

# Change HSA and savings plan contributions during the year

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article explains how employees and benefits administrators can change contributions for health savings account (HSA) plans and savings plans, such as 401(k) plans, at any time during a benefit period.

Employees often need to adjust HSA contributions or 401(k) contribution amounts several times a year, not only during open enrollment or after a life event. When you turn on ongoing contribution changes, employees can change their own contributions from **Employee self service**, and benefits administrators can change contributions on behalf of employees. Neither needs to cancel the enrollment and re-enroll.

A contribution change doesn't overwrite the existing enrollment. Instead, the system ends the current enrollment record the day before the effective date and creates a new enrollment record with the new contribution amount. This approach keeps a full history of contribution amounts, and payroll uses the deduction start and end dates on each record to pick up the correct amount for each pay period.

## Supported plans

You can change contributions during the year only for benefit plans whose plan type has one of the following plan type codes:

| Plan type code | Examples |
| --- | --- |
| **Savings** | 401(k) and other retirement savings plans |
| **Flexible spending account** | Flexible spending accounts (FSAs) and HSAs. Set up HSA plans by using a plan type that has the **Flexible spending account** plan type code. |

### Prerequisites

Before employees and benefits administrators can change contributions during the year, follow these steps:

1. In **Feature management**, turn on the **Benefits management** and the **Enable ongoing benefit contribution changes** features. The **Enable ongoing benefit contribution changes** feature depends on the **Benefits management** feature. For more information, see [Feature management overview](../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
1. For each savings or FSA plan that should allow changes, select **Allow ongoing contribution changes** on the plan's **Configuration** tab. For more information, see [Create a benefit plan](hr-benefits-plans-setup.md).
1. Optional: Set a default **Rate change reason code** in **Benefits management parameters**. The system uses it as the default reason code for contribution changes. For more information, see [Set Benefits management and Employee self service parameters for all companies](hr-benefits-setup-parameters.md).
1. Make sure that you have reason codes where **Benefits management** is set to **Yes** under **Applicable scenarios**. Only those reason codes are available when you change a contribution. For more information, see [Set up reason codes](hr-benefits-setup-reason-codes.md).

### Turn on ongoing contribution changes for a plan

1. In the **Benefits management** workspace, under **Plans**, select **Benefit plans**.
1. Select a plan that has a plan type code of **Savings** or **Flexible spending account**.
1. On the **Configuration** tab, set **Allow ongoing contribution changes** to **Yes**.
1. Select **Save**.

The **Allow ongoing contribution changes** option appears only when the **Enable ongoing benefit contribution changes** feature is turned on and the plan type code is **Savings** or **Flexible spending account**. By default, the option is set to **No**.

### When you can change a contribution

The **Change contribution** button is available when the **Enable ongoing benefit contribution changes** feature is turned on. The button is enabled only when all of the following conditions are met for the selected enrollment:

- The enrollment is confirmed.
- The enrollment isn't canceled.
- The plan type code is **Savings** or **Flexible spending account**.
- **Allow ongoing contribution changes** is set to **Yes** on the benefit plan.

You can change the contribution for only one enrollment at a time.

### Change a contribution as a benefits administrator

To change a contribution, follow these steps:

1. In the **Benefits management** workspace, under **Plans**, select **Worker benefit plans**.
1. Filter the list to find the worker and the benefit period.
1. On the **Plans** FastTab, select the enrollment that's in effect on the date when the change should start.
1. In the action pane above the grid, select **Change contribution**.
1. In the **Change contribution** dialog, enter the new contribution details. For more information, see [Change contribution dialog fields](#change-contribution-dialog-fields).
1. Select **OK**.

### Change a contribution as an employee

To change a contribution as an employee, follow these steps:

1. Go to **Employee self service**.
1. Select the **My benefit plans** tile.
1. Select the benefit period.
1. Select the confirmed plan that you want to change, and then select **Change contribution**.
1. In the **Change contribution** dialog, enter the new contribution details. For more information, see [Change contribution dialog fields](#change-contribution-dialog-fields).
1. Select **OK**.

After an employee confirms enrollment in a savings or FSA plan in the **Benefits** workspace, a message tells them they can update contributions from **My benefit plans**.

When the **Enable ongoing benefit contribution changes** feature is turned on, **My benefit plans** shows every enrollment record for the plan in the selected benefit period, including earlier records that a contribution change ended. The **Valid from** and **Valid to** columns show when each contribution amount applies.

### Change contribution dialog fields

| Field | Description |
| --- | --- |
| **Coverage code** | The coverage code of the enrollment's coverage option. This field is read-only. It determines how the system interprets the new contribution amount. If the coverage code is **Percentage**, the amount is a percentage of the employee's benefits annual salary. Otherwise, the amount is a fixed amount per pay period. |
| **New contribution amount** | The new employee contribution amount per pay period, or the new percentage if the coverage code is **Percentage**. |
| **Effective from date (future)** | The date when the new contribution amount starts. The field is blank each time that you open the dialog, so you must enter a date. |
| **Reason code** | The reason for the change. By default, the value is the **Rate change reason code** from the **Benefits management parameters** page. Only reason codes where **Benefits management** is an applicable scenario are available. The reason code is saved as the enrollment reason on the new enrollment record. |

#### Validation rules

When you select **Ok**, the system checks the following conditions. If a condition isn't met, the system shows an error message and doesn't save the change.

| Rule | Message |
| --- | --- |
| A reason code is selected. | A valid reason code is required. |
| The new contribution amount isn't negative. | Contribution amount must be positive. |
| The effective date is within the benefit period. | Effective date must be within the benefit period (*start date* - *end date*). |
| The effective date is within the valid from and valid to dates of the selected enrollment record. | Effective date must be within the selected plan's validity from *start date* to *end date*. |
| The effective date is today or a later date. Retroactive changes aren't supported. | Effective date must be in the future. |
| The plan type code is **Savings** or **Flexible spending account**. | This plan type isn't eligible for contribution changes. |
| The enrollment is confirmed. | The plan must be confirmed before changing contributions. |
| The projected annual contribution is within the plan's **Minimum annual contribution** and **Maximum annual contribution**. | The annual employee contribution amount of *amount* is invalid because it is less than the minimum of *currency* *amount*.<br><br>The annual employee contribution amount of *amount* is invalid because it is more than the maximum of *currency* *amount*. |

#### How annual contribution limits are validated

The way the system checks the plan's **Minimum annual contribution** and **Maximum annual contribution** depends on whether the plan prorates contributions:

- **Plans that don't prorate contributions**: When you select **OK**, the system calculates the projected annual contribution. The projected amount is the sum of the following amounts:

  - The amount already contributed in the benefit period, based on each earlier confirmed enrollment record for the plan and the number of pay periods that it was in effect before the effective date.
  - The new contribution amount multiplied by the number of pay periods that remain in the benefit period from the effective date.

    The system rounds pay periods to whole pay periods based on the pay period of the enrollment, such as 12 for monthly or 26 for biweekly. If the enrollment has no pay period, the number of days are used.

- **Plans that prorate contributions**: The existing proration rules are used to validate the contribution after it creates the new enrollment record. For more information, see [Prorate employee contribution amounts](prorate-contributions.md).

For example, a monthly plan has a benefit period from January 1 to December 31 and a **Maximum annual contribution** of 3,000. An employee contributes 200 a month and changes the contribution to 350 a month, effective April 16. The system calculates about three pay periods at 200 (600) and nine remaining pay periods at 350 (3,150), so the projected total is 3,750. Because the projected total is more than the maximum, the change isn't saved.

#### What happens when you change a contribution

When the change passes validation, the enrollment records are updated in a single transaction:

1. **Ends the current enrollment record** - The **Valid to** date and time and the deduction end date and time of the selected record is set to one second before the effective date. For example, if the effective date is April 16, the record ends on April 15 at 11:59:59 PM.
1. **Creates a new enrollment record** - A new record is created that copies the details of the selected record and uses the following values:

    - **Valid from** - Deduction start date and time: The effective date.
    - **Valid to** - Deduction end date and time: The end of the benefit period.
    - **Employee contribution amount** - The new contribution amount.
    - **Coverage amount**, **Employer amount**, and **Admin amount** - Recalculated from the new contribution amount. For example, an employer match on a savings plan is recalculated.
    - **Enrollment reason** - The reason code from the dialog.
    - **Confirmation** - The record is confirmed, and **Confirmed by** is set to the user who made the change.

1. **Copies dependents and beneficiaries** - The dependents and beneficiaries are copied from the selected record to the new record if they're still eligible on the effective date.
1. **Runs eligibility rules again** - The system checks the plan's eligibility rules for the new record. If the rules fail, the system shows the reason and the message "Eligibility selection rules failed," and it doesn't save any of the changes.

### Example

An employee is enrolled in an HSA plan for a benefit period from January 1 to December 31 and contributes 200.00 per pay period. The employee changes the contribution to 350.00, effective April 16. After the change, the employee has two enrollment records.

| Record | Valid from | Valid to | Employee contribution |
| --- | --- | --- | --- |
| Original | January 1, 12:00:00 AM | April 15, 11:59:59 PM | 200.00 |
| New | April 16, 12:00:00 AM | December 31 | 350.00 |

Payroll deducts 200.00 for pay periods before April 16 and 350.00 for pay periods from April 16.

### Changes that replace later contribution records

Every contribution change runs through the end of the benefit period. If you make a change with an effective date that's earlier than an existing later enrollment record for the same plan and coverage option, the new change replaces the later records.

For example, an employee has a record at 200.00 from January 1 and a record at 350.00 from July 1. If the employee changes the January record to 300.00, effective May 1, the system shows the following message:

"This change will update your contribution amount effective *date* and replace any future contribution records through the end of the benefit period. You can update the contribution again later by selecting a new effective date. Do you want to continue?"

- If you select **Yes**, the system removes later records that start on or after the effective date. It removes the confirmation, clears the selection, and then deletes each record. It then ends the selected record and creates a new record from May 1 to the end of the benefit period at 300.00.
- If you select **No**, no changes are made.

If you want the later contribution amount to apply again, make another contribution change with a later effective date.

#### Payroll impact

The contribution change feature doesn't change payroll calculations. Payroll and payroll integrations use the deduction start and end dates on each enrollment record to determine which contribution amount applies to each pay period. For more information, see [Payroll worker benefit plan](hr-admin-integration-payroll-api-payroll-worker-benefit-plan.md).

#### Limitations

- Retroactive contribution changes aren't supported. The effective date must be today or a later date.
- You can change the contribution for only one enrollment at a time.
- Contribution changes don't use an approval workflow. Changes are confirmed when they're saved.
- Only confirmed enrollments that aren't canceled can be changed.

#### Related information

- [Create a benefit plan](hr-benefits-plans-setup.md)
- [Create worker benefit plans](hr-benefits-plans-worker.md)
- [Prorate employee contribution amounts](prorate-contributions.md)
- [Employees select plans by using Employee self service](employee-select-benefits-ess.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
