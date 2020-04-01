---
# required metadata

title: Create a benefits plan
description: Set up benefit plans in Dynamics 365 Human Resources.
author: andreabichsel
manager: AnnBe
ms.date: 04/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-human-resources
ms.technology: 

# optional metadata

ms.search.form: BenefitPlanListPage, BenefitWorkspace
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
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Create a benefits plan

This article shows you how to set up benefit plans in Dynamics 365 Human Resources.

1. In the **Benefits management** workspace, under **Plans**, select **Benefit plans**.

2. Select **New**.

3. On the **General** tab, specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | **Plan** | A unique identifier for the plan. |
   | **Description** | A description of the plan. |
   | **Plan type** | When you create a new plan, you need to specify the plan type. A plan type is a high-level grouping of specific types of benefits. Each plan type specifies whether an employee can enroll in multiple plans of that type, specifies whether contacts are beneficiaries or dependents, and defines coverage options. You can create new custom plan types to meet the needs of your benefits offerings. Main benefit plan types are: <ul><li>401K</li><li>ADD</li><li>Dental</li><li>Fitness</li><li>FSA</li><li>Life</li><li>LTD</li><li>Medical</li><li>PTO</li><li>STD</li><li>Vision</li></ul> |
   | **Plan type code** | The plan type code of the plan type. |
   | **Program** | Specifies a program to optionally assign the plan to. |
   | **Bundle** | Specifies a bundle to optionally assign the plan to. |
   | **Master** | Specifies whether the plan is the master plan within the bundle it is assigned to. |
   | **Status** | Indicates the current status of the benefits plan. The default value is Active. If you change the status to Inactive, the plan won’t be available as a selection during enrollment. |
   | **Valid from date and time** | The date and time the plan starts. The default value is the current system date. |
   | **Valid to date and time** | The date and time the plan ends (the status is set to Inactive). The default value is 12/31/2154, which signifies never. |

4. On the **Configuration** tab, specify values for the following fields, depending on the type of plan you're creating:

   | Plan type | Field | Description |
   | --- | --- | --- |
   | Medical (Medical, Dental, Vision, HMO) | COBRA | Specifies whether the plan is COBRA (Consolidated Omnibus Budget Reconciliation Act) eligible. |
   | Medical (Medical, Dental, Vision, HMO) | HIPAA | Specifies whether the plan is HIPAA (Health Insurance Portability and Accountability Act) eligible. |
   | <ul><li>Medical (Medical, Dental, Vision, HMO)</li><li>Other (PTO, Fitness)</li><li>Other</li><li>Long term disability</li><li>ADD (Basic life, Voluntary life)</li><li>Savings (for example, 401(k))</li><li>FSA</li></ul> | Pretax eligible | Specifies whether contributions can be made to the plan before taxes are applied. |
   | <ul><li>Medical (Medical, Dental, Vision, HMO)</li><li>Other (PTO, Fitness)</li><li>Long term disability</li><li>ADD (Basic life, Voluntary life)</li><li>Savings (for example, 401(k))</li><li>FSA</li></ul> | Post tax eligible | Specifies whether contributions can be made to the plan after taxes are applied. |
   | <ul><li>Medical (Medical, Dental, Vision, HMO)</li><li>Other (PTO, Fitness)</li><li>Long term disability</li><li>ADD (Basic life, Voluntary life)</li><li>Savings (for example, 401(k))</li><li>FSA</li></ul> | Contributor | Specifies who contributes to the plan – the employee, the employer, or both. |
   | <ul><li>Long term disability</li><li>ADD (Basic life, Voluntary life)</li></ul> | Minimum coverage | The minimum amount of insurance coverage required for the plan. |
   | <ul><li>Long term disability</li><li>ADD (Basic life, Voluntary life)</li></ul> | Maximum coverage | The maximum amount of insurance coverage required for the plan. |
   | <ul><li>Long term disability</li><li>ADD (Basic life, Voluntary life)</li></ul> | Use coverage increments | Specifies whether to validate that the coverage amount matches a valid incremental amount. |
   | <ul><li>Long term disability</li><li>ADD (Basic life, Voluntary life)</li></ul> | Incremental amount | The incremental amount of insurance coverage for the plan. For example, if the incremental amount is 1,000, an employee can’t have $200,500 of insurance, they would need to round up to $201,000 or down to $200,000. |
   | <ul><li>Long term disability</li><li>ADD (Basic life, Voluntary life)</li></ul> | Incremental direction | Specifies the direction to round – either up or down – when the coverage amount doesn’t satisfy the incremental amount value. |
   | ADD (Basic life, Voluntary life) | Evidence of insurability | Specifies whether an employee must provide evidence of insurability. |
   | ADD (Basic life, Voluntary life) | Amount | The amount in accounting currency. This field is only active if the Evidence of insurability check box is selected. |
   | <ul><li>Savings (for example, 401(k))</li><li>FSA</li></ul> | Minimum annual contribution | The minimum contribution amount required for the plan. |
   | <ul><li>Savings (for example, 401(k))</li><li>FSA</li></ul> | Maximum annual contribution | The maximum contribution amount required for the plan. |
   | Savings (for example, 401(k)) | Employer maximum annual amount | The maximum amount an employer is allowed to contribute toward an employee savings plan during a benefit period. You must select the Employer match check box to use this field. |
   | Savings (for example, 401(k)) | Employer match | Specifies whether the employer contributes to an employee savings plan. |
   | Savings (for example, 401(k)) | Employer match percent | The percentage of an employee contribution that the employer will match. |
   | Savings (for example, 401(k)) | Employer match cap | The maximum percentage the employer will match. For example, if an employer will match 100% of employee contributions up to 6% of the employee’s pay, the employer match cap is 6%. |

5. On the **Setup** tab, specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | **Allow/continue enrollment** | Specifies whether employees can enroll in the plan if they meet eligibility requirements.</br></br>If this is set to No, the plan won’t be available to employees when you process eligibility. |
   | **Auto enroll from prior year** | Specifies whether to automatically enroll an eligible employee in the plan if they were enrolled during the prior year. |
   | **Auto enroll by default** | Specifies whether to select the plan for enrollment by default. The plan is not mandatory, so the employee can change the default selection. |
   | **Closed for new enrollments** | Specifies whether to restrict the plan to only eligible employees who were enrolled in the plan in the prior year. |
   | **Mandatory plan** | Specifies whether to automatically enroll employees in the plan. Employees can’t change the enrollment selection. |
   | **Inception date** | The date the plan was created in the company. |
   | **Vendor account** (Benefit supplier) | The vendor that the company pays premiums to for the plan. |
   | **Name** (Benefit supplier) | The name of the vendor. |
   | **Vendor reference** (Benefit supplier) | The vendor’s reference for the plan. For example, the company’s group plan number. |
   | **Alternate reference** (Benefit supplier) | The vendor’s alternate reference for the plan. For example, the company’s account number. |
   | **Currency** (Benefit supplier) | The currency that is used to pay premiums to the supplier. |
   | **Expense account** (Benefit supplier) | The general ledger account that is used as the expense account for plan premiums. |
   | **Vendor account** (Benefit administrator) | The vendor the company pays to administrate the plan. If the plan is self-administered, leave this field blank. |
   | **Name** (Benefit administrator) | The name of the benefit administrator vendor. |
   | **Vendor reference** (Benefit administrator) | The administrator vendor’s reference for the plan. |
   | **Alternate reference** (Benefit administrator) | The administrator vendor’s alternate reference for the plan. |
   | **Currency** (Benefit administrator) | The currency that is used to pay the benefits administrator. |
   | **Expense account** (Benefit administrator) | The general ledger account that is used as the expense account for the costs associated with the administration of the plan. |

6. On the **Filters** tab, filter as necessary. You can filter by the following fields:

   - **Business unit**
   - **Department**
   - **Legal entity**
   - **Location**
   - **Position**

7. On the **Eligibility rules** tab, specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | **Line number** | The line number of the eligibility rule. |
   | **Eligibility rule** | An eligibility rule to apply to the benefit plan. This eligibility rule will be applied to the corresponding action type and associated with the specified coverage waiting period and deductions. |
   | **Action type** | The action to apply the eligibility rule to: benefits enrollment or benefits expiration. |
   | **Coverage waiting period** | A value from the Waiting periods form. The coverage waiting period drives the number of days or months an employee waits for benefit coverage or benefit expiration based on the criteria in the eligibility rule and action type. |
   | **Deduction waiting period** | A value from the Waiting periods form. The deduction waiting period drives the number of days or months an employee waits for benefit deductions from their paycheck based on the criteria in the eligibility rule and action type. |

8. Select **Save**.

## View enrolled workers

You can view the workers who are enrolled in a selected benefit plan.

1. In the **Benefits management** workspace, under **Plans**, select **Benefit plans**.

2. Select **Enrolled workers**.

## Attach coverage options

You can add coverage options to the selected benefits plan. Attaching coverage options brings the rate and deduction setup together for a coverage option.  Example:  For a medical plan, the user would select a Family coverage option.  They would then need to select the Family rate for the associated plan (set in Rate setup) and the deduction for the associated plan (set in rate setup). This provides the cost for the employer and employee for a selected coverage. Then you would repeat the process for an Employee+1 coverage or Employee coverage.

1. In the **Benefits management** workspace, under **Plans**, select **Benefit plans**.

2. Select **Attach coverage options**.

## Override eligibility rules

You can add workers to a plan as exceptions to the eligibility rules. Each worker you add will be eligible for the benefits plan.

1. In the **Benefits management** workspace, under **Plans**, select **Benefit plans**.

2. Select **Eligibility rule override**.

## View attached periods

You can see a list of the available benefits periods.

1. In the **Benefits management** workspace, under **Plans**, select **Benefit plans**.

2. Select **Periods**.

## View plan information

You can provide a description of the plan to help employees with their benefits selections. The plan information you enter here displays in Employee self service when hovering on the plan in the coverage options list.

1. In the **Benefits management** workspace, under **Plans**, select **Benefit plans**.

2. Select **Plan information**.

## View flex credit programs

1. In the **Benefits management** workspace, under **Plans**, select **Benefit plans**.

2. Select **Flex credit programs**.
