---
# required metadata

title: Create a leave and absence plan
description: This article describe how to create leave plans in Dynamics 365 Human Resources for different types of leave.
author: twheeloc
ms.date: 01/28/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LeavePlanFormPart, LeaveAbsenceWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Create a leave and absence plan

> [!Important]
> The functionality noted in this article is currently available for customers on the stand-alone Dynamics 365 Human Resources. Some or all of the functionality will be available as part of a future release on the Finance infrastructure after Finance release 10.0.26.


[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

Define leave and absence plans in Dynamics 365 Human Resources for each type of leave you offer. Leave and absence plans can accrue at different frequencies, such as annually, monthly, or semimonthly. You can also define a plan as a grant, where a single accrual occurs on a specific date. For example, you might create a plan that grants floating holidays annually.

Tiered leave plans allow employees to receive benefits based on the amount of time they've spent with an organization. Tiered plans enable automatic enrollment in additional benefit hours.

You can specify maximum carry-over amounts or minimum balances to ensure employees use only the benefit hours they've accrued.

For example, with a tiered plan, you can grant a benefit of 80 hours of paid time-off (PTO) to new employees. Then you can grant 120 hours of 60 months of service.

You can also create position-based leave benefits, such as executive-only benefit hours.

## Create a leave plan

1. On the **Leave and absence** page, select **Create new plan**.

2. Under **Details**, enter the **Name**, **Start date**, **Description**, and **Leave type** for your plan.

If the feature **Configure multiple leave types for a single leave and absence plan** is enabled, leave types are configured in the **Accrual schedule** instead of under **Details**. For each record in the accrual schedule table, you can define a leave type. Also, when this feature is enabled, you'll need to use new data entities for integrations or other scenarios where you need to use entities. 

The new entities are:

- Leave and absence bank transaction V2
- Leave and absence enrollment V2
- Leave and absence plan tier V2
- Leave and absence plan V2
- Leave time off request V2

 > [!IMPORTANT]
   > After you enable this feature, you can't turn it off.

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
      | **Plan start date** | The accrual period start date is the date the plan is available. |
      | **Employee-specific date** | The accrual period start date depends on an employee event:</br><ul><li>Custom (you must specify an accrual date basis for each individual enrollment)</li><li>Anniversary date</li><li>Original hire date</li><li>Seniority date</li><li>Worker's adjusted start date</li><li>Worker's start date</li></ul> |

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
   - What amounts will carry forward

   You can create tiers to award time off based on different levels.

   If you have hourly employees, you can award time off based on hours worked instead of tenure with your organization. The data for hours worked is typically stored in a time and attendance system. You can import regular and overtime hours worked from the time and attendance system and use them as a basis for an employee's award.
   
    1. Select an option from the **Accrual type** dropdown box:

      - **Months of service** - Base the accrual schedule on months of service.

      - **Hours worked** - Base the accrual schedule on hours worked. For more information about accruals for hours worked, see [Accrue time off based on hours worked](hr-leave-and-absence-plans.md?accrue-time-off-based-on-hours-worked).

      For more information about accrual balances, see [Accrue time off based on hours worked](hr-leave-and-absence-plans.md?enrollments-and-balances).

    2. Enter values in the accrual schedule table:

      - **Months of service** - The minimum number of months that employees must work to be entitled to accruals. If you don't require a minimum, set the value to 0.

      - **Hours worked** - The minimum number of hours that employees must work per accrual period to be entitled to accruals. If you don't require a minimum, set the value to 0.

      - **Accrual amount** - The number of hours or days that employees accrue per period. The period is based on the accrual frequency.

      - **Minimum balance** - You can use a negative value for the minimum balance if employees can request more leave than is available.

      - **Maximum carry-forward** - The accrual process adjusts leave balances that exceed the maximum carry-forward balance on the anniversary of the start date.

      - **Grant amount** - The initial number of hours or days that employees are granted when they first enroll in the leave plan. The amount doesn't accrue for each accrual period.
      
If the feature **Configure multiple leave types for a single leave and absence plan** is enabled, select an option from the **Leave type**. 

   > [!IMPORTANT]
   > After you enable this feature, you can't turn it off.

If the feature **Use full time equivalency** is enabled, Human Resources uses the full time equivalency (FTE) defined for the position to prorate an employee's accrual. 

The FTE calculation would take place based on the value at the time of the accrual and if the FTE value is updated between the current accrual and the next accrual, there will be no change in the leave accrual value. The change in the FTE value will be considered for the next leave accrual.

>[!NOTE]
>This feature is available when the **Configure multiple leave types for a single leave and absence plan** feature is enabled.  

For example, if the FTE is .5 and the accrual amount is 10, the employee will accrue 5.  

If the FTE is set to .5 before the actual accrual date, then the employee will accrue 5. 
If the FTE is set to .5 after the accrual date, then the employee will accrue 10 leaves as the FTE value isn't considered at that time and only for the next accrual, .5 will be considered for leave accrual calculation. 


5. Select **Save**.

## Accrue time off based on hours worked

If you have hourly employees, you can award time off based on hours worked instead of tenure with your organization. Data for hours worked data is typically stored in a time and attendance system. You can import regular and overtime hours worked from your time and attendance system and use it as a basis for an employee's award.

When you select hours worked as the accrual type, you can use two types of hours for the accrual: regular and overtime. Accrual processing for hours worked plans uses the accrual frequency, along with the accrual period basis, to determine the hours to be accrued.

### Annual accrual frequency

| Accrual award date    | Hours worked tier    | Accrual amount        | Hours worked dates   | Hours worked actuals| Award               |
| --------------------- | -------------------- | --------------------- | -------------------- |-------------------- |-------------------- |
| 12/31/2018            | 2080                 | 144                   | 1/1/2018-12/31/2018  | 2085                | 144                 |        
| 12/31/2018            | 2080                 | 144                   | 1/1/2018-12/31/2018  | 2000                | 0                 |


### Monthly accrual frequency

| Accrual award date    | Hours worked tier    | Accrual amount        | Hours worked dates   | Hours worked actuals| Award               |
| --------------------- | -------------------- | --------------------- | -------------------- |-------------------- |-------------------- |
| 8/31/2018             | 160                  | 12                    | 8/1/2018-8/31/2018   | 184                 | 12                  |        
| 8/31/2018             | 160                  | 3                     | 8/1/2018-8/31/2018   | 184                 | 3                   |

### Semi-monthly accrual frequency

| Accrual award date    | Hours worked tier    | Accrual amount        | Hours worked dates   | Hours worked actuals| Award               |
| --------------------- | -------------------- | --------------------- | -------------------- |-------------------- |-------------------- |
| 8/31/2018             | 80                   | 6                     | 8/16/2018-8/31/2018  | 81                  | 6                  |        
| 8/31/2018             | 80                   | 6                     | 8/16/2018-8/31/2018  | 75                  | 0                   |

### Weekly accrual frequency

| Accrual award date    | Hours worked tier    | Accrual amount        | Hours worked dates   | Hours worked actuals| Award               |
| --------------------- | -------------------- | --------------------- | -------------------- |-------------------- |-------------------- |
| 8/31/2018             | 40                   | 3                     | 8/27/2018-8/31/2018  | 42                  | 3                  |        
| 8/31/2018             | 40                   | 3                     | 8/27/2018-8/31/2018  | 35                  | 0                   |

### Employee assigned leave plans

In the employee's assigned leave plans, the tier basis and type of hours displays for hours worked plans. The actual hours worked for the accrual periods as of the current date also displays for active plans.

### Loading data

You can import actual hours by using the **Leave and absence hours worked** entity in data management. If you use working time calendars, the import validates that regular hours worked doesn't exceed the scheduled hours in a day defined by the calendar. The import also validates that the hours worked for a given day doesn't exceed 24. 

You need the following information to import the actual hours to be used in the leave accrual process:

- Personnel number 
- Date worked
- Type
- Hours

A single date can only have one of each type associated with it.

| Personnel number       | Date worked           | Type                  | Hours                |
| --------------------- | -------------------- | --------------------- | -------------------- |
| 000337                | 8/6/2018             | Regular               | 8                    |       
| 000337                | 8/7/2018             | Regular               | 8                    |
| 000337                | 8/7/2018             | Overtime              | 3                    |
| 000337                | 8/8/2018             | Regular               | 8                    |
| 000337                | 8/7/2018             | Regular               | 8                    |
| 000337                | 8/9/2018             | Regular               | 8                    |

## Enrollments and balances

### Enrollment date

The enrollment date determines when an employee can start to accrue time off. For example, an employee enrolled in a vacation plan on June 15, 2018 can't accrue any time off before June 15, 2018.

### Current balance

The current balance is the amount of leave that is available for time-off requests. This amount includes accruals, approved requests, and adjustments through the current date.

### Current balance examples

#### Annual plan

**Plan setup**

| Plan start date | Enrollment date | Accrual frequency | Accrual period basis | Accrual award date    |
|-----------------|-----------------|-------------------|----------------------|-----------------------|
| 1/1/2018        | 1/1/2018        | Annual            | Plan start date      | End of accrual period |

Accruals are processed on January 1, 2019 (1/1/2019) to include the whole period.

**Results**

| Accrual amount | Minimum balance | Maximum carry-forward | Request amount | Current balance (as of 1/1/2019) |
|----------------|-----------------|-----------------------|----------------|----------------------------------|
| 200            | 0               | 120                   | 40             | 160                              |

Current balance (160) = Accrual amount (200) – Request amount (40)

#### Semimonthly plan

**Plan setup**

| Plan start date | Enrollment date | Accrual frequency | Accrual period basis | Accrual award date    |
|-----------------|-----------------|-------------------|----------------------|-----------------------|
| 1/1/2018        | 2/1/2018        | Semimonthly       | Plan start date      | End of accrual period |

Accruals are processed on May 1, 2018 (5/1/2018) to include the whole period.

**Results**

| Accrual amount | Minimum balance | Maximum carry-forward | Request amount | Current balance (as of 1/1/2019) |
|----------------|-----------------|-----------------------|----------------|----------------------------------|
| 5              | 0               | 120                   | 8              | 22                               |

Current balance (22) = Accrual amount (5 × 6) – Request amount (8)

#### Monthly plan

**Plan setup**

| Plan start date | Enrollment date | Accrual frequency | Accrual period basis | Accrual award date    |
|-----------------|-----------------|-------------------|----------------------|-----------------------|
| 1/1/2018        | 2/1/2018        | Semimonthly       | Plan start date      | End of accrual period |

Accruals are processed on May 1, 2018 (5/1/2018) to include the whole period.

**Results**

| Accrual amount | Minimum balance | Maximum carry-forward | Request amount | Current balance (as of 1/1/2019) |
|----------------|-----------------|-----------------------|----------------|----------------------------------|
| 5              | 0               | 120                   | 8              | 7                                |

Current balance (7) = Accrual amount (5 × 3) – Request amount (8)

### Forecasted balance

The *forecasted balance* is the amount of leave available on a future date. Accruals and carry-forward adjustments are forecasted up to that date.

Human Resources uses the following formula:

Monday forecasted balance = Current balance – Requests + Accruals – Carry-forward adjustment

### Forecasted balance examples

#### Annual plan

**Plan setup**

| Plan start date | Enrollment date | Accrual frequency | Accrual period basis | Accrual award date    |
|-----------------|-----------------|-------------------|----------------------|-----------------------|
| 1/1/2018        | 1/1/2018        | Annual            | Plan start date      | End of accrual period |

Accruals are processed on February 15, 2019 (2/15/2019) to include the whole period.

**Results**

| Accrual amount | Minimum balance | Maximum carry-forward | Current balance | Forecasted balance (as of 2/15/2019) |
|----------------|-----------------|-----------------------|-----------------|--------------------------------------|
| 20             | 0               | 20                    | 40              | 40                                   |

Forecasted balance (40) = Accrual amount (20) + Current balance (40) – Carry-forward adjustment (20)

#### Semimonthly plan

**Plan setup**

| Plan start date | Enrollment date | Accrual frequency | Accrual period basis | Accrual award date    |
|-----------------|-----------------|-------------------|----------------------|-----------------------|
| 1/1/2018        | 2/1/2018        | Semimonthly       | Plan start date      | End of accrual period |

Accruals are processed on February 15, 2019 (2/15/2019) to include the whole period.

**Results**

| Accrual amount | Minimum balance | Maximum carry-forward | Current balance | Forecasted balance (as of 2/15/2019) |
|----------------|-----------------|-----------------------|-----------------|--------------------------------------|
| 5              | 0               | 20                    | 40              | 35                                   |

Forecasted balance (35) = Accrual amount (5 × 3) + Current balance (40) – Carry-forward adjustment (20)

#### Monthly plan

**Plan setup**

| Plan start date | Enrollment date | Accrual frequency | Accrual period basis | Accrual award date    |
|-----------------|-----------------|-------------------|----------------------|-----------------------|
| 1/1/2018        | 2/1/2018        | Semimonthly       | Plan start date      | End of accrual period |

Accruals are processed on February 15, 2019 (2/15/2019) to include the whole period.

**Results**

| Accrual amount | Minimum balance | Maximum carry-forward | Current balance | Forecasted balance (as of 2/15/2019) |
|----------------|-----------------|-----------------------|-----------------|--------------------------------------|
| 10             | 0               | 20                    | 40              | 30                                   |

Forecasted balance (30) = Accrual amount (10 × 1) + Current balance (40) – Carry-forward adjustment (20)

### Proration balance examples

#### Prorated monthly plan

**Plan setup**

| Plan start date | Accrual frequency | Accrual period basis |
|-----------------|-------------------|----------------------|
| 1/1/2018        | Monthly           | Plan start date      |

**Results**

| Employee            | Months of service | Enrollment date | Start date | Accrual amount | Process accrual | Balance |
|---------------------|-------------------|-----------------|------------|----------------|-----------------|---------|
| Jeannette Nicholson | 0.00              | 6/1/2018        | 6/1/2018   | 1.00           | 9/1/2018        | 3.00    |
| Jay Norman          | 0.00              | 6/15/2018       | 6/15/2018  | 1.00           | 9/1/2018        | 2.53    |

#### Full accrual monthly plan

**Plan setup**

| Plan start date | Accrual frequency | Accrual period basis |
|-----------------|-------------------|----------------------|
| 1/1/2018        | Monthly           | Plan start date      |

**Results**

| Employee            | Months of service | Enrollment date | Start date | Accrual amount | Process accrual | Balance |
|---------------------|-------------------|-----------------|------------|----------------|-----------------|---------|
| Jeannette Nicholson | 0.00              | 6/1/2018        | 6/1/2018   | 1.00           | 9/1/2018        | 3.00    |
| Jay Norman          | 0.00              | 6/15/2018       | 6/15/2018  | 1.00           | 9/1/2018        | 3.00    |

#### No accrual monthly plan

**Plan setup**

| Plan start date | Accrual frequency | Accrual period basis |
|-----------------|-------------------|----------------------|
| 1/1/2018        | Monthly           | Plan start date      |

**Results**

| Employee            | Months of service | Enrollment date | Start date | Accrual amount | Process accrual | Balance |
|---------------------|-------------------|-----------------|------------|----------------|-----------------|---------|
| Jeannette Nicholson | 0.00              | 6/1/2018        | 6/1/2018   | 1.00           | 9/1/2018        | 3.00    |
| Jay Norman          | 0.00              | 6/15/2018       | 6/15/2018  | 1.00           | 9/1/2018        | 2.00    |

## See also

- [Leave and absence overview](hr-leave-and-absence-overview.md)
- [Configure leave and absence types](hr-leave-and-absence-types.md)
- [Accrue leave and absence plans](hr-leave-and-absence-accrue.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
