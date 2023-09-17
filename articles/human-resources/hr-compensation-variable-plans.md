---
# required metadata

title: Create variable compensation plans
description: This article describes the components that must be set up before you can use variable compensation and enroll an employee in a variable compensation plan.
author: twheeloc
ms.date: 08/24/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: HCMCompEligibility, HcmJobFunction, HcmWorker, HRMCompPerfPlan, HcmCompensationWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: fc3a394e-9ac6-4f8c-9162-dc16ec22720f
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Human Resources

---

# Create variable compensation plans


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

Variable compensation makes up an employee's irregular pay, such as bonuses or stock awards. This article explains how to set up the components that are needed for variable compensation and enroll an employee in a variable compensation plan.

The calculation of variable compensation amounts for your employees can be based on several factors, such as the employee's performance, the employee's compensation level, and the department's performance.

## Variable compensation components
### Create compensation types

**Variable compensation types** are a required component. **Variable compensation types** describe the kinds of variable compensation that your organization awards. They also let you specify whether the compensation will be in cash or in a non-monetary form, such as stock.

### Describe vesting rules

Optionally, companies can set up **Vesting rules**. **Vesting rules** describe how the variable award should be allocated over time. For example, a vesting rule might state that the employee will receive 25 percent of the total award every year for the next four years. Vesting rules are informational only.

## Variable compensation plans
The **variable compensation plan** contains the rules, calculation methods, and default values for the calculation of variable compensation for enrolled employees. When you create a variable compensation plan, you must set the variable compensation type. The variable compensation type determines whether the system calculates a currency amount or a number of units as the award. 

The **Restrict access to selected roles** parameter restricts access to the compensation plan to selected security roles that have been assigned to that plan in Human Resources. For example, when you create compensation plans that are for executives and should not be visible to all HR-specific roles, you can use this parameter to restrict access to those compensation plans. 

You must also set the calculation method:

-   **Point in time** – The calculation of the variable award is based on the fixed compensation that the employee had on a specific date. That date is specified on the process event when new compensation amounts are processed.
-   **Composite** – An award amount is calculated for each unique fixed compensation pay rate that the employee had between the cycle start date and the cycle end date on the process event. The rates are then added together to determine the final award. For example, during the cycle, an employee transferred to a different position that had a different pay rate. In this case, the variable award is adjusted for the length of time that the employee had each pay rate.

The amount of the variable award can be based on either a percentage of the employee's regular base earnings or a set number of units.

-   Select the **Percent of basis** option to enter a default percentage, and specify whether the basis should be the employee's fixed pay rate or the control point for the employee's compensation level. The compensation level is set on the employee's job. One of the reference points from the compensation structure can be set as the control point on the fixed compensation plan. The compensation level from the employee's job will be used and cross-referenced with the control point that is listed on the employee's fixed compensation plan to find the control point amount for the employee's compensation level. The control point amount will then be used instead of the employee's fixed pay rate as the basis for the award.
-   Select the **Number of units** option to enter a default number of units, the value of each unit and the currency of the unit value if the compensation plan is for a non-cash award (for example, 200 units of stock that are valued at 40 USD), or just the number of units if the compensation plan is for a cash award. For a cash award, the employee will receive the specified number of units of the currency that is used for the fixed compensation plan (for example, 500 units of 1 USD). The one-to-one relationship control can be used to indicate whether there is a direct one-to-one mapping between the number of units and the unit value. When you create a variable compensation plan for a cash-based plan by using the number of units, this option is automatically locked to **Yes**, and the unit value is **1.0000**.

The **Hire rule** specifies whether all employees should receive the same increase, regardless of the date they were hired (**Hire rule** = **None**), or whether employees should receive a percentage of the award that is based on the length of their employment during the cycle (**Hire rule** = **Percent**). 

**Leverage** adjusts an employee's award, based on the performance of the employee's department. Performance metrics can be set for each department on the **Departments** page, under **Related forms** &gt; **Compensation** &gt; **Performance**. The award that employees in that department receive depends on the value of the **Percent of target achieved** field, which indicates the department's performance:

-   If the department's performance is 100 percent, the award for the employees in that department is factored by the percentage that is set in the **Payout at 100%** field.
-   If the department's performance is more than 100 percent, the system adds the percentage that is set in the **Per 1% over objective** field to the percentage that is set in the **Payout at 100%** field until the value that is set in the **Highest allowable payout** field is reached.
-   If the department's performance is less than 100 percent, the system subtracts the percentage that is set in the **Per 1% under objective** field from the percentage that is set in the **Payout at 100%** field until the value that is set in the **Lowest allowable payout** field is reached.

**Tolerance levels** can be set on the threshold percentages, so that a warning message appears if the leverage causes the percentage to be outside the threshold percentage. 

By default, the department that is set on the employee's position is used for employee awards. However, the award for some employees might depend on the performance of multiple departments. In this case, the various departments and the percentage of the award that is allocated to the performance of each department can be set on the employee's variable compensation enrollment. For more information, see the "Variable compensation enrollment" section that follows. 

Leverage is used only if **Pay for performance** is selected when the compensation process is run. 

The **Levels overrides** tab lets you override the award's default percentage or number of units, based on the compensation level of the employee. If **Enable overrides for levels** is set to **Yes** for employees who are enrolled in the variable compensation plan, the level from an employee's job will be compared to the levels overrides table to determine the percentage or number of units for that level. If the level is not found in the level overrides table, the default percentage or number of units from the **General** tab is used. The percentage and number of units can also be overridden on the employee's enrollment in the variable compensation plan.

## Variable compensation enrollment
### Determine who is eligible for the plan

When you're ready to enroll employees in a variable compensation plan, the first step is to determine who is eligible for the compensation that is specified in the plan. You can't assign the plan to any employees unless you determine eligibility. To set up eligibility, open the **Eligibility rules** page to create a new eligibility rule for your plan, and then define the criteria that an employee must meet to be eligible for the compensation plan. You can limit eligibility by department, labor union, compensation region (location), job, job function, job type, and/or compensation level. Employees can be enrolled in a compensation plan only if they meet **all** the criteria that are set on the eligibility rule. 

**Note:** Eligibility rules determine eligibility for both fixed compensation plans and variable compensation plans. The eligibility rules use the following fields on the job, position, and employee records to determine whether an employee is eligible for a compensation plan:

- On the **Job** page:
  -   The **Job** field
  -   The **Function** and **Job type** fields on the **Job classification** tab
  -   The **Level** field on the **Compensation** tab
- On the **Positions** page: The **Department** and **Compensation region** fields
- On the <strong>Employees</strong> page: The information about labor unions that is associated with the employee under <strong>Personal information</strong> &gt; <strong>Labor unions</strong> on the *<strong><em>Worker</em></strong>* tab

### Enable enrollment for the variable compensation plan

On the **Variable compensation plans** page, set the **Enable enrollment** option to **Yes** to allow eligible employees to be enrolled in the plan.

### Enroll the employee

You can now enroll employees in the variable compensation plan. To enroll an employee, go to the **Employees** page, and select the employee. Then, on the Action Pane, click **Compensation** &gt; **Variable plan enrollment**. 

**Note:** **Enrollment** must be set to **Yes** on the variable compensation plan. The **Plan** field shows only the plans that the employee is eligible for, based on the eligibility rules that are set up for those plans. If an eligibility rule isn't set for a plan, no employees will be eligible for that plan. 

Make sure that the **Effective date** field is set correctly. If the variable compensation plan uses the **Composite** calculation method, the effective date of the enrollment might be considered during the calculation of the employee's award. 

You can use the **Overrides** tab to override specific values for the employee. For example, if **Hire rule** is set to **Percent** on the plan, and a different hire date should be used during the calculation of the employee's hire percentage, you can set the hire date in the **Hire rule date** field. You can also override the **Award percent** value or the **Number of units** value for a specific employee, depending on the plan's settings. These values will still be factored by the hire rule, performance factors, and other settings on the plan. 

**Organizational overrides** are used to base an employee's award on the performance of one or more departments. The percentage that is allocated across departments should total 100 percent. The employee's individual performance is also considered. These settings are used only if **Pay for performance** is selected when the compensation process is run.





[!INCLUDE[footer-include](../includes/footer-banner.md)]
