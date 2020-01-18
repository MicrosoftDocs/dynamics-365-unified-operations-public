---
# required metadata

title: Create a leave and absence plan
description: Create leave plans in Dynamics 365 Human Resources for different types of leave.
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
ms.search.validFrom: 2020-02-01
ms.dyn365.ops.version: Human Resources April 2020 update

---

# Create a leave and absence plan

**Status**

| Description | Status | Notes |
| --- | --- | --- |
| Draft | Complete |  |
| Verify procedures | Complete |  |
| Change links | Complete |  |
| Update screenshots |  |  |
| Add See also links | Complete |  |
| Run Acrolinx | Complete |  |
| Review |  |  |
| Edit |  |  |
| Ready to publish |  |  |

**Notes for Reviewers**

| Description | Comments |
| --- | --- |
| From existing topic? | https://docs.microsoft.com/en-us/dynamics365/talent/leave-absence-concepts and https://docs.microsoft.com/en-us/dynamics365/talent/leave-absence-overview |
| Review document location | (link) |

Define leave and absence plans in Dynamics 365 Human Resources for each type of leave you offer. Leave and absence plans can accrue at different frequencies, such as annually, monthly, or semimonthly. You can also define a plan as a grant, where a single accrual occurs on a specific date. For example, you might create a plan that grants floating holidays annually.

Tiered leave plans allow employees to receive benefits based on the amount of time they've spent with an organization. Tiered plans enable automatic enrollment in additional benefit hours.

You can specify maximum carry-over amounts or minimum balances to ensure employees use only the benefit hours they've accrued.

For example, with a tiered plan, you can grant a benefit of 80 hours of paid time-off (PTO) to new employees. Then you can grant 120 hours of 60 months of service.

You can also create position-based leave benefits, such as executive-only benefit hours.

## Create a leave plan

1. On the **Leave and absence** page, select **Create new plan**.

2. Under **Details**, enter the **Name**, **Start date**, **Description**, and **Leave type** for your plan.

3. Define accruals in the **Accruals** tab. Accruals determine when and how often an employee is awarded time off. In this step, you define policies about when accruals should be awarded and policies about prorating leave benefits.

   1. Select a value from the **Accrual frequency** dropdown box:

      - Daily
      - Weekly
      - Biweekly
      - Semimonthly
      - Monthly
      - Quarterly
      - Semiannually
      - Annually
      - None

   2. Select an option from the **Accrual period basis** dropdown box to determine the start date used for calculating accrual periods:

      | Accrual period basis | Description |
      | --- | --- |
      | Plan start date | The accrual period start date is the date the plan is available. |
      | Employee-specific date | The accrual period start date depends on an employee event:</br><ul><li>Custom (you must specify an accrual date basis for each individual enrollment)</li><li>Anniversary date</li><li>Original hire date</li><li>Seniority date</li><li>Worker's adjusted start date</li><li>Worker's start date</li></ul> |

   3. Select an option from the **Accrual award date** dropdown box:

      - **Accrual period end date** - The employee is awarded time off on the last day of the award period. To accrue the correct amount, the accrual process must include the whole period. For example, if the accrual period is January 1, 2020 through January 31, 2020, you must run the accrual for February 1, 2020 to include January.

      - **Accrual period start date** - The employee is awarded time off on the first day of the award period.

   4. Select an option from the **Accrual policy on enrollment** dropdown box. This value defines how to calculate accrual when an employee enrolls in the middle of an accrual period.

      - **Prorated** - The date range between the enrollment date and the start date is used to determine the difference in days. That difference is applied when accruals are processed.

      - **Full accrual** - The full accrual amount, based on the tier, is awarded during the first accrual processing.

      - **No accrual** - No accrual is awarded until the next accrual period.

   5. Select an option from the **Accrual policy on unenrollment** dropdown box. This value defines how to calculate accrual when an employee unenrolls in the middle of an accrual period.

      - **Prorated** – The date range between the enrollment date and the start date is used to determine the difference in days. That difference is applied when accruals are processed.

      - **Full accrual** – The full accrual amount, based on the tier, is awarded during the first accrual processing.

      - **No accrual** – No accrual is awarded until the next accrual period.

4. Define the accrual schedule in the **Accrual schedule** tab. The accrual schedule determines:

- How an employee accrues time off
- What amounts the employee will accrue
- What amounts will carry forward.

You can create tiers to award time off based on different levels.

   1. Select an option from the **Accrual type** dropdown box:

      - **Months of service** - Base the accrual schedule on months of service.

      - **Hours worked** - Base the accrual schedule on hours worked.

    2. Enter values in the accrual schedule table:

      - **Months of service** - The minimum number of months that employees must work to be entitled to accruals. If you don't require a minimum, set the value to 0.

      - **Hours worked** - The minimum number of hours that employees must work per accrual period to be entitled to accruals. If you don't require a minimum, set the value to 0.

      - **Accrual amount** - The number of hours or days that employees accrue per period. The period is based on the accrual frequency.

      - **Minimum balance** - You can use a negative value for the minimum balance if employees can request more leave than is available.

      - **Maximum carry-forward** - The accrual process adjusts leave balances that exceed the maximum carry-forward balance on the anniversary of the start date.

      - **Grant amount** - The initial number of hours or days that employees are granted when they first enroll in the leave plan. The amount doesn't accrue for each accrual period.

## See also

- [Leave and absence overview](hr-leave-and-absence-overview.md)
- [Configure leave and absence types](hr-leave-and-absence-types.md)