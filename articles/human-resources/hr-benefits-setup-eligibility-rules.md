---
# required metadata

title: Configure eligibility rules and options
description: Set eligibility rules and options in Benefits management in Microsoft Dynamics 365 Human Resources.
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
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources April 2020 update

---

# Configure eligibility rules and options

After you've configured the necessary parameters for Benefits management in Microsoft Dynamics 365 Human Resources, you can create eligibility rules, bundles, periods, and programs that you will associate with your benefit plans.

## Create an eligibility rule

Eligibility rules define which employees can enroll in each benefit plan. After you define eligibility rules, you assign them to benefit plans. Then you can process enrollment eligibility to see which employees are eligible for each plan. 

During open enrollment, employees can select benefit plans. If they become ineligible for a benefit plan based on eligibility rules after they are already enrolled, they aren’t automatically unenrolled. Typically, when a life event occurs that affects plan eligibility, an enrollment period is initiated for the employee to select plans that they are eligible for. 

1. In the **Benefits management** workspace, under **Setup**, select **Eligibility rules and options**.

2. In the **Eligibility rules** tab, select **New** to create an eligibility rule. To see plans that are associated with an eligibility rule, select **Attached plans**.

2. Specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | Eligibility rule | A unique identifier for the eligibility rule. |
   | Description | A description of the eligibility rule. |
   | Valid from date and time | The start date of the eligibility rule. | 
   | Valid to date and time | The end date of the eligibility rule. |
   | User worker type | Specifies whether to use the employee’s worker type in the benefit eligibility rule. |
   | Worker type | The worker type, if the Use worker type check box is selected. |
   | Use employee status | Specifies whether to use the employee’s employment status in the benefit eligibility rule. |
   | Status | The employee status, if the Use employee status check box is selected. If the Use employee status check box is not selected, the field isn’t used. |
   | Use employment category | Specifies whether to use the employee’s Employment category value as part of the benefit eligibility rule. | 
   | Employment category | The employee’s employment category if the Use employment category check box is selected. |
   | Use new hire period | Specifies whether to use a new hire’s new hire period value as part of the benefits eligibility rule. |
   | Enrollment period | The time period that new hire enrollment is allowed. |
   | User former employment status | Specifies whether the eligibility rule depends on a change in employee status. For example, you can have an eligibility rule for employees who are currently set to ‘Temporary leave of absence’ but have a former employment status of ‘Employed’ within the last 30 days. This field must be used in conjunction with the fields that follow it (Status, From, and To). | 
   | Status | The former status to use for the eligibility rule. In the preceding example, the value would be ‘Employed’. |
   | From | A value from the Waiting days form that is used to indicate the effective date of the status change time frame. If the ‘From’ date is set to 0 and the ‘To’ date is set to 365, the system will search for a time lapse of 365 days between statuses. | 
   | To | A value from the Waiting days form that is used to indicate the expiration date of the status change time frame. If the ‘From’ date is set to 0 and the ‘To’ date is set to 365, the system will search for a time lapse of 365 days between statuses. |
   | Eligible age | Specifies the age range or ranges that a person must be in to satisfy the eligibility rule. </br>Age is defined by the Birthdate value on the employee’s master record on the Personal information fast tab. |
   | Eligible department | Specifies the department or departments an employee must be in to satisfy the eligibility rule. </br>The department is attached to the position on the General fast tab of the Position details form. |
   | Eligible employment type | Specifies the employment type or types an employee must be categorized as to satisfy the eligibility rule. For example, full time or part time. |
   | Eligible job | Specifies the job or jobs that satisfy the eligibility rule. Jobs are associated with positions, and positions are filled by employees. | 
   | Eligible job function | Specifies the job function or functions that satisfy an eligibility rule. For example, sales workers or technicians. </br>The job function is assigned on the Job classification fast tab of the Job details form. |
   | Eligible job type | Specifies the job type or types that satisfy the eligibility rule. For example, clerical or executive. </br>The job type is assigned to a job record on the Job classification fast tab on the Job details form. The job is assigned to a position, which is associated with an employee. |
   | Eligible legal entity | Specifies the legal entity or legal entities that are valid for the eligibility rule. For example, Contoso Entertainment System USA. </br>Employees are associated to legal entities both on their employment record (on the Employment details fast tab) and on the General fast tab of the Position details form. |
   | Eligible location | Specifies the employee location that satisfies the eligibility rule. For example, central US. </br>The location (compensation region) is attached to the position record on the General fast tab of the Position details form. |
   | Eligible office location | Specifies the employee’s office location that satisfies the eligibility rule. For example, New Jersey office. |
   | Eligible position | Specifies the position or positions that satisfy the eligibility rule. For example, HR Assistant or HR Manager. </br>Positions are associated with employees on the Worker assignment fast tab of the Position details form and on the worker position assignment form. |
   | Eligible position type | Specifies the position type or types that satisfy the eligibility rule. For example, full-time. |
   | Eligible state | Specifies the states or provinces that satisfy the eligibility rule. For example, North Dakota USA or British Columbia, Canada. </br>A state or province is assigned to an employee through the Addresses fast tab of the Employee profile form. If the employee has multiple primary addresses, the eligibility rule will check all of them to assess eligibility. |
   | Eligible terms of employment | Specifies the terms of employment that satisfy the eligibility rule. For example, at will or group contract. |
   | Eligible union |Specifies the labor union memberships that satisfy the eligibility rule. For example, Forklift Drivers of America. Employees are assigned to labor unions by clicking the Labor Unions link on the Employee profile form. </br>When using a union-based eligibility rule, the worker’s union record must have the end date populated. It can’t be left blank. |
   | Eligible ZIP/postal code | Specifies the ZIP/postal codes that satisfy the eligibility rule. For example, 58104. </br>A ZIP/postal code assigned to an employee through the Addresses fast tab of the Employee profile form. If the employee has multiple primary addresses, the eligibility rule will check all of them to assess eligibility. |
   | Eligible user field | Specifies additional eligibility rules based on customerdefined fields. </br>Employees are linked to user fields on the Benefit details fast tab of the Employment form. |
   | Eligibility type | Specifies the criterion category you selected in the Additional criteria fast tab. |
   | Eligibility reference | Specifies the values you selected as criteria in the Additional criteria fast tab. |
   | Description | The description of the criteria you selected in the Additional criteria fast tab. |


3. Select **Save**.

























## Configure bundles

1. In the **Benefits management** workspace, under **Setup**, select **Eligibility rules and options**.

2. In the **Bundles** tab, specify values for the following fields:

   | Field | Description |
   | --- | --- |

3. Select **Save**.



## Configure periods

1. In the **Benefits management** workspace, under **Setup**, select **Eligibility rules and options**.

2. In the **Periods** tab, specify values for the following fields:

   | Field | Description |
   | --- | --- |

3. Select **Save**.


## Configure programs

1. In the **Benefits management** workspace, under **Setup**, select **Eligibility rules and options**.

2. In the **Programs** tab, specify values for the following fields:

   | Field | Description |
   | --- | --- |

3. Select **Save**.


## See also