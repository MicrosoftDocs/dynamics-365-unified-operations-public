---
# required metadata

title: Configure and enroll in benefits
description: 
author: andreabichsel
manager: AnnBe
ms.date: 02/01/2020
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

# Configure and enroll in benefits

This demonstration illustrates how to configure and use benefit plans in Microsoft Dynamics 365 Human Resources. For the demonstration’s scenario, your company offers three plans: a medical plan, an accidental death and dismemberment insurance plan, and a 401k plan.

The medical plan has two offerings: one for the employee only, and one for the employee’s entire family. The family plan is more expensive than the employee-only plan, and both plans are more expensive for employees who smoke.

The AD&D plan also has two offerings: one that provides insurance at the rate of the amount an employee makes in a year, and one that provides twice that amount. The cost of the insurance is based on an employee’s salary.

The 401k plan is only available to full-time employees. They are able to contribute to the 401k plan as a percentage of their income or a flat amount.

The dependents and beneficiaries for all plans must be either a spouse or child of the employee. All employees are paid monthly. 

## Prerequisites

| Prerequisite | Description |
| --- | --- |
| Wizards | To hire employees who will enroll in benefits, you will need configured employee management wizards. Alternatively, you can use employees who are already in the system, but you may need to modify the demonstration to make sure they are eligible for the benefits you create.</br></br>You can use the recruitment guide to configure wizards if they aren’t configured already. |
| Employment types | You must have an employment type configured to use for the employment type eligibility rule. This demonstration uses **Full-time**. If you have different employment types already configured, you can modify the demonstration. |
| Base benefits configuration | This demonstration requires various incidental benefits elements to be configured. If you encounter something that isn’t configured, you can provide values you choose in the setup form at Human resources advanced > Benefits > Setup. |

## Configure benefits administration 

Many of the following configuration tasks may have already been performed in your environment. If so, you can use the already-configured elements. Be aware that you may need to modify other elements of the demonstration if the already-configured elements aren’t exactly the same as described in the demonstration instructions.

### Create personal contact eligibility options 

1. Click Human resources advanced > Benefits > Setup > Personal contact eligibility options. 

2. Click New. Specify values from the following table to create personal contact eligibility options: 

   | Eligibility option | Description | Contact eligibility code | Status | Relationship | Age |
   | --- | --- | --- | --- | --- | --- |
   | Spouse | Spouse | Relationship | Active | Spouse |  |
   | Child_19 | Child (Ages 0-19) | Relationship | Active | Child | 19 |

### Create coverage options for the plans 

1. Click Human resources advanced > Benefits > Setup > Coverage option. 

2. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
   | Coverage option | EE Only |
   | Description | Employee Only |
   | Coverage code | Employee only |
   | Status | Active |

3. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
   | Coverage option | EE + Family |
   | Description | EE + Family |
   | Coverage code | Family |
   | Maximum number | 0 |
   | Status | Active |
   | Personal contact eligibility options | Spouse</br>Child_19 |

4. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
   | Coverage option | 1 x Salary |
   | Description | 1 x Salary |
   | Coverage code | 1 x salary |
   | Status | Active |
   | Personal contact eligibility options | Spouse</br>Child_19 |

5. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
   | Coverage option | 2 x Salary |
   | Description | 2 x Salary |
   | Coverage code | 2 x salary |
   | Status | Active |
   | Personal contact eligibility options | Spouse</br>Child_19 |

6. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
   | Coverage option | Percent |
   | Description | Percentage |
   | Coverage code | Percentage |
   | Status | Active |
   | Percent maximum | 100 |
   | Personal contact eligibility options | Spouse</br>Child_19 |

7. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
   | Coverage option | Flat Amount |
   | Description | Flat Amount |
   | Coverage code | Flat amount |
   | Status | Active |
   | Personal contact eligibility options | Spouse</br>Child_19 |

### Create plan types for the plans

1. Click Human resources advanced > Benefits > Setup > Plan types.

2. Specify the following values to create three plan types: 

   | Plan type | Description | Plan type code | Concurrent enrollment | Contact  type | Coverage option |
   | --- | --- | --- | --- | --- | --- |
   | Demo med | Demo medical | Medical | One enrollment per type | Dependent | EE Only</br>EE + Family |
   | Demo ad&d | Demo ad&d | Accidental Death & Dismemberment | Multiple enrollments per type | Beneficiary | 1 x Salary</br>2 x Salary |
   | Demo 401K | Demo 401K | Savings | Multiple enrollments per type | Beneficiary | Flat amount</br>Percent</br>EE Only |

### Create eligibility rules for the plans

1. Click Human resources advanced > Benefits > Rules/options > Eligibility rules.

2. Click New. Specify the following values for an eligibility rule to use for all three plans: 

   | Field | Value |
   | --- | --- |
   | Eligibility rule | Hire |
   | Description | Default eligibility rule for hired employees |
   | Valid from date and time | 1/1/2000 |
   | Valid to date and time (expiration) | Never |
   | Use employee type | Yes |
   | Worker type | Employee |
   | Use employee category | No |
   | Use employee status | Yes |
   | Status | Employed |
   | Use new hire rule | No |
   | Use former employment status | No |

3. Click New. Specify the following values for an eligibility rule to use for the 401k plan:

   | Field | Value |
   | --- | --- |
   | Eligibility rule | FTE |
   | Description | Eligibility rule for full-time employees |
   | Valid from date and time | 1/1/2000 |
   | Valid to date and time (expiration) | Never |
   | Use employee type | Yes |
   | Worker type | Employee |
   | Use employee category | No |
   | Use employee status | Yes |
   | Status | Employed |
   | Use new hire rule | No |
   | Use former employment status | No |

4. Click Additional criteria > Eligible employment type. 

5. In Employment type, select Full-time. 

### Configure a payment frequency for the plans 

1. Click Human resources advanced > Benefits > Setup > Payment frequency 

2. Click New. Specify the following values:

   | Field | Value |
   | --- | --- |
Payment frequency Monthly Description Monthly Period Monthly 
Number of pay periods Monthly Annual conversion factor 12 Semiannual conversion factor 6 Quarterly conversion factor 3 Monthly conversion factor 1 Semimonthly conversion factor .5 Bi-weekly conversion factor 12/26 Weekly conversion factor 12/52 Daily conversion factor 12/365 

### Create tier codes for the AD&D plan 

1. Click Human resources advanced > Benefits > Setup > Tier codes. 2. Click New. Specify values for the following tier codes: Tier code Description 1 Tier 1 2 Tier 2 3 Tier 3 

### Configure the rate setups for the medical plan 

1. Click Human resources advanced > Benefits > Setup > Rate setup. 

2. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
Field Value Rate Medical EE Description Medical employee-only Valid from 1/1/2016 Valid to (expiration) Never Use tiers  Payment frequency Monthly Pay frequency rate calculation Standard Pay frequency rate rounding Standard Non-smoker EE amount 15 Non-smoker ER amount 0 Smoker EE amount 20 Smoker ER amount 0 Administrative amount 0 

3. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
Field Value Rate Med EE+FM Description Family medical Valid from 1/1/2016 Valid to (expiration) Never Use tiers  Payment frequency Monthly 
Pay frequency rate calculation Standard Pay frequency rate rounding Standard Non-smoker EE amount 90 Non-smoker ER amount 0 Smoker EE amount 100 Smoker ER amount 0 Administrative amount 0 

### Configure the rate setup for the AD&D plan 

1. Click Human resources advanced > Benefits > Setup > Rate setup. 

2. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
Field Value Rate AD&D Description Accidental death and dismemberment Valid from 1/1/2016 Valid to (expiration) Never Use tiers Single tier Payment frequency Monthly Pay frequency rate calculation Standard Pay frequency rate rounding Standard 

3. Click ACTIONS > Tier rates. 

4. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
Field Value Tier code Tier 1 Tier type Salary Level 50000 Calculation type Flat amount Non-smoker EE amount 1.25 Smoker EE amount 2.50 

5. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
Field Value Tier code Tier 2 Tier type Salary Level 100000 Calculation type Flat amount Non-smoker EE amount 2.5 Smoker EE amount 5 

6. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
Field Value Tier code Tier 3 Tier type Salary Level 150000 
Calculation type Flat amount Non-smoker EE amount 5 Smoker EE amount 10 

### Configure the rate setups for the 401k plan 

1. Click Human resources advanced > Benefits > Setup > Rate setup. 

2. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
Field Value Rate 401kFlat Description Flat amount for 401K Valid from 1/1/2000 Valid to (expiration) Never Use tiers  Payment frequency Monthly Pay frequency rate calculation Standard Pay frequency rate rounding Standard Non-smoker EE amount 0 Non-smoker ER amount 0 Smoker EE amount 0 Smoker ER amount 0 

3. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
Field Value Rate 401kPercen Description Percentage amount for 401K Valid from 1/1/2016 Valid to (expiration) Never Use tiers  Payment frequency Monthly Pay frequency rate calculation Standard Pay frequency rate rounding Standard Non-smoker EE amount 0 Non-smoker ER amount 0 Smoker EE amount 0 Smoker ER amount 0 

### Configure deductions for the plans 

1. Click Human resources advanced > Benefits > Setup > Deduction setup. 

2. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
Field Value Deduction Medical Description Medical plan Heading (Employee deduction) Deduction code EE payroll deduction reference (Employee deduction) MEDEE 
Amount heading (Employee deduction) Deduction amount Heading (Employer deduction) Deduction code ER payroll deduction reference (Employer deduction) MEDER Amount heading (Employer deduction) Deduction amount 

3. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
Field Value Deduction AD&D Description AD&D plan Heading (Employee deduction)  EE payroll deduction reference (Employee deduction)  Amount heading (Employee deduction)  Heading (Employer deduction) Deduction code ER payroll deduction reference (Employer deduction) AD&D Amount heading (Employer deduction) Deduction amount 

4. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
Field Value Deduction 401k Description 401k plan Heading (Employee deduction) Deduction code EE payroll deduction reference (Employee deduction) 401K Amount heading (Employee deduction) Deduction amount Heading (Employer deduction)  ER payroll deduction reference (Employer deduction)  Amount heading (Employer deduction)  

### Create a period for your plans 

1. Click Human resources advanced > Benefits > Rules/options > Periods. 

2. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
Field Value Period Demo period Valid from date and time Enter the date for the first of the year Valid to date and time Enter the date for the end of the year Enroll start Enter the date for the first of the year Enroll end Enter the date for the end of the year 

### Create a medical plan 

1. Click Human resources advanced > Benefits > Plans. 

2. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
Field Value Plan type Demo med Plan Medical plan demo Description Medical plan for demonstration 

3. Click Create new plan. 

4. Specify valid dates that will ensure that the plan is valid for the entire span of time you specified for the period. You can use a start date (Valid from date and time) from several years ago and an expiration date (Valid to date and time) of never. 

5. Click the SETUP tab. Select the Allow/continue enrollment option. 

6. Click the ELIGIBILITY RULES tab. Specify the following eligibility rules:

Eligibility rule Value Hire Enroll 

7. Click Attach coverage options. 8. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
Field Value Coverage option EE Only Rate Medical EE Deduction Medical 

8. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
Field Value Coverage option EE + Family Rate Med EE + FM Deduction Medical 

9. Click Save and close the form to return to the new benefit plan (Human resources advanced > Benefits > Plans > Your new plan). 

10. Click Periods. 

11. Click New. 

12. Select Demo period. If the valid dates that you specified in step 4 do not encompass the entire period, you will get an error. 

### Create an AD&D plan 

1. Click Human resources advanced > Benefits > Plans. 

2. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
Field Value Plan type Demo ad&d Plan AD&D plan demo Description AD&D plan for demonstration 

3. Click Create new plan. 

4. Specify valid dates that will ensure that the plan is valid for the entire span of time you specified for the period. You can use a start date (Valid from date and time) from several years ago and an expiration date (Valid to date and time) of never. 

5. Click the SETUP tab. Select the Allow/continue enrollment option. 

6. Click the ELIGIBILITY RULES tab. Specify the following eligibility rules: 
Eligibility rule Value Hire Enroll 

7. Click Attach coverage options. 

8. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
Field Value Coverage option 1 x Salary 
Rate AD&D Deduction AD&D 

9. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
Field Value Coverage option 2 x Salary Rate AD&D Deduction AD&D 

10. Click Save and close the form to return to the new benefit plan (Human resources advanced > Benefits > Plans > Your new plan). 

11. Click Periods. 

12. Click New. 

13. Select Demo period. If the valid dates that you specified in step 4 do not encompass the entire period, you will get an error. 

### Create a 401K plan 

1. Click Human resources advanced > Benefits > Plans. 

2. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
Field Value Plan type Demo 401k Plan 401k plan demo  Description 401k plan for demonstration 

3. Click Create new plan. 

4. Specify valid dates that will ensure that the plan is valid for the entire span of time you specified for the period. You can use a start date (Valid from date and time) from several years ago and an expiration date (Valid to date and time) of never. 

5. Click the SETUP tab. Select the Allow/continue enrollment option. 

6. Click the ELIGIBILITY RULES tab. Specify the following eligibility rules: Eligibility rule Value FTE Enroll 

7. Click Attach coverage options. 

8. Click New. Specify the following values: Field Value Coverage option Percent Rate 401kPercen Deduction 401k 

9. Click New. Specify the following values: Field Value Coverage option Flat amount Rate 401kFlat Deduction 401k 

10. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
Field Value Coverage option EE Only Rate 401kFlat Deduction 401k 

11. Click Save and close the form to return to the new benefit plan (Human resources advanced > Benefits > Plans > Your new plan). 

12. Click Periods. 13. Click New. 14. Select Demo period. If the valid dates that you specified in step 4 do not encompass the entire period, you will get an error. 

### Hire employees 

Use a hire wizard to create test employees. You can launch the wizard from the Employees list page or from Manager self-service. For more information, see the Wizards or Recruitment documentation. The employees should have the following data, but you can add more data as well. For example, provide fictitious address information for each worker to avoid warning messages later in the demonstration. 

1. Click Human resources advanced > Workers > Employees.  

2. Click Create and hire new worker. 

   | Field | Value |
   | --- | --- |
Field Value First name (Employee ID/lookup) Aaron Last name (Employee ID/lookup) Ackman Marital status (Personal details) Single Number of dependents (Personal details) 1 Birth date (Personal details) 05/24/1980 Employment type (Employment details)  New position (Position) Yes Job (Position) Accountant Eligibility date (Benefits) Today’s date Payment frequency (Benefits) Monthly Annual benefit salary (Benefits) 100000 

Add a personal contact for the employee. You can do this by using the hire wizard or after the employee is hired by doing the following: 

3. Click human resources advanced > Workers > Employees. Select Aaron Ackman. 

4. Click WORKER > Personal contacts. 

5. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
Field Value First name John Last name Ackman 

6. Click Create. 

7. Click Edit. Specify the following values: 

   | Field | Value |
   | --- | --- |
Field Value Relationship Child Beneficiary Yes Dependent Yes 
Birth date 05/24/2009 

8. Click Human resources advanced > Workers > Employees.  

9. Click Create and hire new worker. 

Create a second test employee with the following values: 

   | Field | Value |
   | --- | --- |
Field Value First name (Employee ID/lookup) Alexa Last name (Employee ID/lookup) Familglia Marital status (Personal details) Married Number of dependents (Personal details) 2 Birth date (Personal details) 06/20/1984 Employment type (Employment details) Full-time New position (Position) Yes Job (Position) Accountant Eligibility date (Benefits) Today’s date Payment frequency (Benefits) Monthly Annual benefit salary (Benefits) 150000 

Add personal contacts for the employee. You can do this by using the hire wizard or after the employee is hired by doing the following: 

10. Click human resources advanced > Workers > Employees. Select Alexa Familglia.

11. Click Personal contacts. 

12. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
Field Value First name Andrew Last name Familglia 

13. Click Create. 

14. Click Edit. Specify the following values: 

   | Field | Value |
   | --- | --- |
Field Value Relationship Spouse Beneficiary Yes Dependent Yes 

15. Click New. Specify the following values: 

   | Field | Value |
   | --- | --- |
Field Value First name Gina Last name Familglia 

16. Click Create. 

17. Specify the following values: 

   | Field | Value |
   | --- | --- |
Field Value Relationship Child Beneficiary Yes Dependent Yes Birth date 12/11/2013 

18. Click Human resources advanced > Workers > Employees.  

19. Click Create and hire new worker. 

Create a third employee with the following values: 

   | Field | Value |
   | --- | --- |
Field Value First name (Employee ID/lookup) Andrew Last name (Employee ID/lookup) Loner Marital status (Personal details) Single Number of dependents (Personal details) 0 Birth date (Personal details) 02/24/1978 Employment type (Employment details) Full-time New position (Position) Yes Job (Position) Accountant Eligibility date (Benefits) Today’s date Payment frequency (Benefits) Monthly Annual benefit salary (Benefits) 100000 

### Process eligibility 

1. Click Human resources advanced > Benefits > Processing > Enrollment eligibility processing. 

   | Field | Value |
   | --- | --- |
Field Value Enrollment period Demo period Legal entity USMF Benefit plan Medical plan demo 

2. Click OK. 

3.  Click Human resources advanced > Benefits > Processing > Enrollment eligibility processing. 

   | Field | Value |
   | --- | --- |
Field Value Enrollment period Demo period Legal entity USMF Benefit plan 401k plan demo 

4. Click OK. 

5.  Click Human resources advanced > Benefits > Processing > Enrollment eligibility processing. 

   | Field | Value |
   | --- | --- |
Field Value Enrollment period Demo period Legal entity USMF Benefit plan AD&D plan demo 

6. Click OK. 

### Enroll in benefits 

Typically, employees would visit Employee self-service to select their own benefit plans. You can reproduce that effect by creating a user relation between your account and one of the employees in System administration > Users > Users. Then when you click Employee self service, you will see the selfservice workspace of that employee.  

Benefits administrators can also make benefits selections for employees through the Worker benefits plans. For this demonstration, you will act as the benefits administrator to enroll employees in benefits. 
 
When you visit the Worker benefit plans form, you will see the workers you hired along with the plans they are eligible for. Plans that require beneficiaries or dependents are only valid after you specify beneficiary and dependent information.

### Enroll Aaron Ackman in benefit plans 

1. Click Human resources advanced > Benefits > Worker benefit plans.  

2. Click OPTIONS > Change view > Line view, if necessary. Click List view. 

3. In the list, select Aaron Ackman. Notice that 4 plans appear for Aaron, and he is only eligible for one of them. The 401k plans aren’t visible because he isn’t a full-time employee. He isn’t currently eligible for three of the plans because they require dependents and beneficiaries to be specified. 
 
4. Select the AD&D demo plan with 1 x Salary coverage option. 

5. In the Benefit plan details section, click the BENEFICIARY tab. 

6. Click Edit. 

7. In Percent, enter 100. In Rank, enter 1. Click Save. 

8. Notice that the AD&D plan with 1 x Salary coverage option now has a checkmark in the Qualified column. 

Repeat to specify beneficiary and dependent information for the remaining plans. Aaron Ackman should now be eligible for all plans except the medical plan that has the EE + Family coverage option. That’s because the coverage code that was used to create the EE + Family coverage option requires that two or more personal contacts must be selected for the plan. To serve employees with family situations like Aaron’s, you can configure additional plans with different coverage options. 
 
9. Select the benefit plan and an AD&D plan to enroll Aaron in. 

10. Click Select. The status of those plans will change to Selected. The plans will be validated again, and the other AD&D plan that Aaron was previously qualified for is no longer valid. That is because Aaron is only allowed to select one plan of each type (only one coverage option allowed per plan). This step represents the employee’s selection of the benefit plans. Typically, employees would do this themselves on Employee self-service.  

11. Select the same plans again. 

12. Click Confirm. The status for both plans will remain Selected and the Confirmed checkbox will be selected. This step represents the benefit administrator confirming the plans that the employees selected. 
 
### Enroll Alexa Familglia in benefit plans 

1. Click Human resources advanced > Benefits > Worker benefit plans.  

2. Click OPTIONS > Change view > Line view, if necessary. Click List view. 

3. In the list, select Alexa Familglia. Notice that Alexa is only eligible for one plan. This is because the other plans require dependents and beneficiaries to be specified. 

4. Select the Medical plan demo plan with EE + Family coverage option. 

5. In the Benefit plan details section, click the DEPENDENT tab. 

6. Click Edit. 

7. Select both dependents (Andrew Familglia and Gina Familglia). Click Save. 
Notice that the medical plan with EE + Family coverage option now has a checkmark in the Qualified column. Because Alexa’s two dependents meet the criteria for the EE + Family coverage option, she is eligible for the family medical plan where Aaron wasn’t because he had only one dependent. 

8. Select the AD&D with 1 X Salary coverage option. 

9. In the Benefit plan details section, click the BENFICIARY tab. You should still be in edit mode; but if not, click Edit. 

10. Specify percent and rank values for the two beneficiaries. For example, rank Andrew 1 with 60% and Gina 2 with 40%. 
Repeat to specify beneficiary and dependent information for the remaining plans. Alexa should now be eligible for all plans. 

11. Select a benefit plan, an AD&D plan, and a 401K plan to enroll Alexa in. 

12. Click Select. The status of those plans will change to Selected. The plans will be validated again, and some of the plans that Alexa was previously qualified for are no longer valid. That is because Alexa is only allowed to select one plan of each type (only one coverage option allowed per plan). This step represents the employee’s selection of the benefit plans. Typically, employees would do this themselves on Employee self-service.  

13. Select the same plans again. 14. Click Confirm. This step represents the benefit administrator confirming the plans that the employees selected. 

### Enroll Andrew Loner in benefit plans 

1. Click Human resources advanced > Benefits > Worker benefit plans.  

2. Click OPTIONS > Change view > Line view, if necessary. Click List view. 

3. In the list, select Andrew Loner. Notice that Andrew is eligible for two plans: employee-only medical and employee-only 401k. He isn’t eligible for any of the AD&D plans because he doesn’t have any beneficiaries.

4. Select the benefit plan to enroll Andrew in. 

5. Click Select.  

6. Select the same plan again. 

7. Click Confirm. This step represents the benefit administrator confirming the plans that the employees selected. 

## See also