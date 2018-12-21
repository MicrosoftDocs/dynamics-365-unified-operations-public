---
# required metadata

title: Leave and absence concepts
description: This topic describes leave and absence concepts and how time off balances are determined. 
author: jcart
manager: AnnBe
ms.date: 12/21/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

# ms.search.form: LeaveAbsenceWorkspace
audience: Application user
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Talent
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: 
# ms.search.industry: 
ms.author: jcart
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: 
---

# Leave and absence concepts

[!include[banner](../includes/banner.md)]

The concepts and terms below can help to determine how an employee is awarded time off and how his or her time balances are calculated. For more information on leave and absence management, see 
[Leave and absence management](https://docs.microsoft.com/en-us/dynamics365/unified-operations/talent/leave-absence-overview).


## Leave plan details

### Start date
The start of accrual processing. Start date also serves as the anniversary date to calculate carry-forward amounts.

## Accruals

Accruals determine when and how often an employee is awareded time off. Policies around when the accruals should be awarded as well as proration are also defined in the accruals section. 

### Accrual frequency
Accrual frequency defines how often leave is accrued or awarded. Options include:
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
Accrual period basis determines the date used for calculating accrual periods. Options include:
- Plan start date
- Employee specific date
    - When selected, this determines the source for the initial date value used for calculating accrual periods. Options include:
     - Custom
     - Anniversary date
     - Original hire date
     - Seniority date
     - Worker's adjusted start date
     - Worker's start date

### Accrual award date
This date determines when an employee is awarded time off. Options include:
  - Accrual period end date
    - The employee will be awarded time off on the last day of the award period.
    - The accrual process needs to include the entire period in order to accrue the correct amount. For example, if the accrual period is 1/1/2018 - 1/31/2018, in order to include January, the accrual has to be run for 2/1/2018.
  - Accrual period start date: the employee will be awarded time off on the first day of the award period.

### Accrual policy on enrollment
The policy for calculating accrual when the employee is enrolled in the middle of an accrual period. Options include:
  - Prorated: when processing accruals, the range between enrollment date and start date is used to determine the difference in days. That difference is applied when processing accruals. 
  - Full accrual: full accrual amount based on the tier is awarded during the first accrual processing.
  - No accrual: no accrual is awarded until the next accrual period.

### Accrual policy on unenrollment
The policy for calculating accrual when the employee is unenrolled in the middle of an accrual period. Options include:
  - Prorated: when processing accruals, the range between enrollment date and start date is used to determine the difference in days. That difference is applied when processing accruals. 
  - Full accrual: full accrual amount based on the tier is awarded during the first accrual processing.
  - No accrual: no accrual is awarded until the next accrual period.
    
## Accrual schedule
 
 The accrual schedule determines how an employee will accrue time off and what amounts he or she will accrue and carry-forward. Tiers
 can be created to awared time off based on different levels. 
 
### Months of service
This value defines the minimum number of months to be entitled for accruals. If no mininmum is required for employees, set to 0.
 
### Hours worked
Hours worked is the minimum number of hours worker per accrual period to be entitled for accruals. If there is no minimum required for employees, set to 0.
   
### Accrual amount
The accrual amount is the number of hours or days employees will accrue per period. The period is based on the accrual frequency.
 
### Minimum balance
A negative value that can be used for minimum balance if employees can request more leave than what they have available.
 
### Maximum carry-forward
The accrual process will adjust leave balances which exceed the maximum carry-forward balance on the anniversary of the start date.
 
### Grant amount
This amount is the initial number of hours or days employees will be granted upon enrollment in the leave plan. The amount doesn't accrue for each accrual period.
 
 
## Enrollments and balances
 
### Enrollment date
The enrollment date determines when an employee can start accruing time off. For example, if the employee is enrolled in a vacation plan on 6/15/2018, she can't accrue any time off before 6/15/2018. 
 
### Current balance
The current balance is the amount of leave available for time off requests that includes accruals, approved requests, and adjustments through today.
 
### Current balance examples
 
#### Annual plan
 
Plan setup:
 
| Plan start date | Enrollment date  | Accrual frequency | Accrual period basis | Accrual award date    |
|-----------------|------------------|-------------------|----------------------|-----------------------|
|     1/1/2018    |     1/1/2018     |       Annual      |    Plan start date   | End of accrual period |
 
Accruals are processed on **1/1/2019** (to include the entire period ). 

Results: 

| Accrual amount | Minimum balance | Maximum carry-forward | Request amount  | Current balance  (as of 1/1/2019) |
|----------------|-----------------|-----------------------|-----------------|-----------------------------------|
|       200      |        0        |          120          |        40       |                160                |

Current balance (160) = Accrual amount (200) - Request amount (40)

#### Semimonthly plan

Plan setup:
 
| Plan start date | Enrollment date  | Accrual frequency | Accrual period basis | Accrual award date    |
|-----------------|------------------|-------------------|----------------------|-----------------------|
|     1/1/2018    |     2/1/2018     |    Semimonthly    |    Plan start date   | End of accrual period |
 
Accruals are processed on **5/1/2018** (to include the entire period ). 

Results: 

| Accrual amount | Minimum balance | Maximum carry-forward | Request amount  | Current balance  (as of 1/1/2019) |
|----------------|-----------------|-----------------------|-----------------|-----------------------------------|
|       5        |        0        |          120          |        8        |                22                 |

Current balance (22) = Accrual amount (5*6) - Request amount (8)

#### Monthly plan

Plan setup:
 
| Plan start date | Enrollment date  | Accrual frequency | Accrual period basis | Accrual award date    |
|-----------------|------------------|-------------------|----------------------|-----------------------|
|     1/1/2018    |     2/1/2018     |    Semimonthly    |    Plan start date   | End of accrual period |
 
Accruals are processed on **5/1/2018** (to include the entire period ). 

Results: 

| Accrual amount | Minimum balance | Maximum carry-forward | Request amount  | Current balance  (as of 1/1/2019) |
|----------------|-----------------|-----------------------|-----------------|-----------------------------------|
|       5        |        0        |          120          |        8        |                7                  |

Current balance (7) = Accrual amount (5*3) - Request amount (8)

### Forecasted balance
 - Amount of leave available on future date that forecasts accruals and carry-forward adjustments up to that date
 - Formula:
  - Monday forecasted balance = Current balance - Request(s) + Accrual(s) - Carry-forward adjustment
 

### Forecasted balance examples
 
 #### Annual plan
 
 Plan setup:
 
| Plan start date | Enrollment date  | Accrual frequency | Accrual period basis | Accrual award date    |
|-----------------|------------------|-------------------|----------------------|-----------------------|
|     1/1/2018    |     1/1/2018     |       Annual      |    Plan start date   | End of accrual period |
 
Accruals are processed on **2/15/2019** (to include the entire period ). 

Results: 

| Accrual amount | Minimum balance | Maximum carry-forward | Current balance  | Forecasted balance (as of 2/15/2019) |
|----------------|-----------------|-----------------------|------------------|--------------------------------------|
|       20       |        0        |          20           |        40        |                40                    |

Forecasted balance (40) = Accrual amount (20) + Current balance (40) - Carry-forward adjustment (20)

 #### Semimonthly plan

 Plan setup:
 
| Plan start date | Enrollment date  | Accrual frequency | Accrual period basis | Accrual award date    |
|-----------------|------------------|-------------------|----------------------|-----------------------|
|     1/1/2018    |     2/1/2018     |    Semimonthly    |    Plan start date   | End of accrual period |
 
Accruals are processed on **2/15/2019** (to include the entire period ). 

Results: 

| Accrual amount | Minimum balance | Maximum carry-forward | Current balance  | Forecasted balance (as of 2/15/2019) |
|----------------|-----------------|-----------------------|------------------|--------------------------------------|
|       5        |        0        |          20           |        40        |                35                    |

Forecasted balance (35) = Accrual amount (5*3) + Current balance (40) - Carry-forward adjustment (20)

#### Monthly plan

Plan setup:
 
| Plan start date | Enrollment date  | Accrual frequency | Accrual period basis | Accrual award date    |
|-----------------|------------------|-------------------|----------------------|-----------------------|
|     1/1/2018    |     2/1/2018     |    Semimonthly    |    Plan start date   | End of accrual period |
 
Accruals are processed on **2/15/2019** (to include the entire period ). 

Results: 

| Accrual amount | Minimum balance | Maximum carry-forward | Current balance  | Forecasted balance (as of 2/15/2019) |
|----------------|-----------------|-----------------------|------------------|--------------------------------------|
|       10       |        0        |          20           |        40        |                30                    |

Forecasted balance (30) = Accrual amount (10*1) + Current balance (40) - Carry-forward adjustment (20)
 
### Proration balance examples
 
#### Prorated monthly plan
 
Plan setup:
 
| Plan start date | Accrual frequency | Accrual period basis | 
|-----------------|-------------------|----------------------|
|     1/1/2018    |      Monthly       |    Plan start date  | 
 
Results: 

| Employee            | Months of service | Enrollment date | Start date | Accrual amount | Process accrual | Balance |
|---------------------|-------------------|-----------------|------------|----------------|-----------------|---------|
| Jeannette Nicholson | 0.00              | 6/1/2018        | 6/1/2018   | 1.00           | 9/1/2018        | 3.00    |
| Jay Norman          | 0.00              | 6/15/2018       | 6/15/2018  | 1.00           | 9/1/2018        | 2.53    |
 
 
#### Full accrual monthly plan
 
Plan setup:
 
| Plan start date | Accrual frequency | Accrual period basis | 
|-----------------|-------------------|----------------------|
|     1/1/2018    |      Monthly       |    Plan start date  | 
 
Results: 

| Employee            | Months of service | Enrollment date | Start date | Accrual amount | Process accrual | Balance |
|---------------------|-------------------|-----------------|------------|----------------|-----------------|---------|
| Jeannette Nicholson | 0.00              | 6/1/2018        | 6/1/2018   | 1.00           | 9/1/2018        | 3.00    |
| Jay Norman          | 0.00              | 6/15/2018       | 6/15/2018  | 1.00           | 9/1/2018        | 3.00    |
 
#### No accrual monthly plan
 
Plan setup:
 
| Plan start date | Accrual frequency | Accrual period basis | 
|-----------------|-------------------|----------------------|
|     1/1/2018    |      Monthly       |    Plan start date  | 
 
Results: 

| Employee            | Months of service | Enrollment date | Start date | Accrual amount | Process accrual | Balance |
|---------------------|-------------------|-----------------|------------|----------------|-----------------|---------|
| Jeannette Nicholson | 0.00              | 6/1/2018        | 6/1/2018   | 1.00           | 9/1/2018        | 3.00    |
| Jay Norman          | 0.00              | 6/15/2018       | 6/15/2018  | 1.00           | 9/1/2018        | 2.00    |
 
 
 
 
 
 
