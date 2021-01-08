---
# required metadata

title: Leave and absence concepts
description: This topic describes leave and absence concepts, and how time-off balances are determined. 
author: andreabichsel
manager: AnnBe
ms.date: 01/03/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

# ms.search.form: LeaveAbsenceWorkspace
audience: Application user
# ms.devlang: 
ms.reviewer: anbichse
# ms.search.scope: Core, Operations, Talent
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: 
---

# Leave and absence concepts

The concepts and terms that are described in this topic can help you determine how an employee is awarded time off, and how that employee's time balances are calculated. For more information about leave and absence management, see 
[Leave and absence management](https://docs.microsoft.com/dynamics365/unified-operations/talent/leave-absence-overview).

## Leave plan details

### Start date

The start date is the date when accrual processing begins. The start date also serves as the anniversary date that is used to calculate carry-forward amounts.

## Accruals

Accruals determine when and how often an employee is awarded time off. Policies about when accruals should be awarded and policies about proration are defined in the **Accruals** section when setting up the leave and absence plan.

### Accrual frequency

The accrual frequency defines how often leave is accrued or awarded. The following options are available:

- Daily
- Weekly
- Biweekly
- Semimonthly
- Monthly
- Quarterly
- Semiannually
- Annually
- None

### Accrual period basis

The accrual period basis determines the date that is used to calculate accrual periods. The following options are available:

- **Plan start date**
- **Employee specific date** – When this option is selected, the value determines the source of the initial date value that is used to calculate accrual periods. The following options are available:

    - Custom
    - Anniversary date
    - Original hire date
    - Seniority date
    - Worker's adjusted start date
    - Worker's start date

### Accrual award date

The accrual award date determines when an employee is awarded time off. The following options are available:

- **Accrual period end date** – The employee will be awarded time off on the last day of the award period.

    To accrue the correct amount, the accrual process must include the whole period. For example, the accrual period is January 1, 2018, through January 31, 2018. In this case, for January to be included, the accrual must be run for February 1, 2018.

- **Accrual period start date** – The employee will be awarded time off on the first day of the award period.

### Accrual policy on enrollment

The accrual policy on enrollment defines how accrual is calculated when an employee is enrolled in the middle of an accrual period. The following options are available:

- **Prorated** – The date range between the enrollment date and the start date is used to determine the difference in days. That difference is applied when accruals are processed.
- **Full accrual** – The full accrual amount, based on the tier, is awarded during the first accrual processing.
- **No accrual** – No accrual is awarded until the next accrual period.

### Accrual policy on unenrollment

The accrual policy on unenrollment defines how accrual is calculated when an employee is unenrolled in the middle of an accrual period. The following options are available:

- **Prorated** – The date range between the enrollment date and the start date is used to determine the difference in days. That difference is applied when accruals are processed.
- **Full accrual** – The full accrual amount, based on the tier, is awarded during the first accrual processing.
- **No accrual** – No accrual is awarded until the next accrual period.

## Accrual schedule

The accrual schedule determines how an employee will accrue time off, and what amounts that employee will accrue and carry forward. Tiers can be created so that time off is awarded based on different levels.

### Months of service

The **Months of service** value defines the minimum number of months that employees must work to be entitled to accruals. If no minimum is required for employees, set the value to **0**.

### Hours worked

The **Hours worked** value defines the minimum number of hours that employees must work per accrual period to be entitled to accruals. If no minimum is required for employees, set the value to **0**.

### Accrual amount

The accrual amount is the number of hours or days that employees will accrue per period. The period is based on the accrual frequency.

### Minimum balance

A negative value can be used for the minimum balance if employees can request more leave than they have available.

### Maximum carry-forward

The accrual process will adjust leave balances that exceed the maximum carry-forward balance on the anniversary of the start date.

### Grant amount

The grant amount is the initial number of hours or days that employees are granted when they first enroll in the leave plan. The amount doesn't accrue for each accrual period.

## Enrollments and balances

### Enrollment date

The enrollment date determines when an employee can start to accrue time off. For example, if an employee is enrolled in a vacation plan on June 15, 2018, she can't accrue any time off before June 15, 2018.

### Current balance

The current balance is the amount of leave that is available for time off requests. This amount includes accruals, approved requests, and adjustments through the current date.

### Current balance examples

#### Annual plan

**Plan setup**

| Plan start date | Enrollment date | Accrual frequency | Accrual period basis | Accrual award date    |
|-----------------|-----------------|-------------------|----------------------|-----------------------|
| 1/1/2018        | 1/1/2018        | Annual            | Plan start date      | End of accrual period |

Accruals are processed on January 1, 2019 (1/1/2019), so that that whole period is included.

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

Accruals are processed on May 1, 2018 (5/1/2018), so that that whole period is included.

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

Accruals are processed on May 1, 2018 (5/1/2018), so that that whole period is included.

**Results**

| Accrual amount | Minimum balance | Maximum carry-forward | Request amount | Current balance (as of 1/1/2019) |
|----------------|-----------------|-----------------------|----------------|----------------------------------|
| 5              | 0               | 120                   | 8              | 7                                |

Current balance (7) = Accrual amount (5 × 3) – Request amount (8)

### Forecasted balance

The *forecasted balance* is the amount of leave that is available on a future date. Accruals and carry-forward adjustments are forecasted up to that date.

The following formula is used:

Monday forecasted balance = Current balance – Requests + Accruals – Carry-forward adjustment

### Forecasted balance examples

#### Annual plan

**Plan setup**

| Plan start date | Enrollment date | Accrual frequency | Accrual period basis | Accrual award date    |
|-----------------|-----------------|-------------------|----------------------|-----------------------|
| 1/1/2018        | 1/1/2018        | Annual            | Plan start date      | End of accrual period |

Accruals are processed on February 15, 2019 (2/15/2019), so that that whole period is included.

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

Accruals are processed on February 15, 2019 (2/15/2019), so that that whole period is included.

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

Accruals are processed on February 15, 2019 (2/15/2019), so that that whole period is included.

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
