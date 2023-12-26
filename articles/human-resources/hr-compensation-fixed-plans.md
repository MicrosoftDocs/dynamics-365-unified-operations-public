---
# required metadata

title: Create fixed compensation plans
description: This article describes the components that must be set up before you can create a fixed compensation plan and enroll employees.
author: twheeloc
ms.date: 08/25/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: HRCCompGrid, HRCCompRefPointSetup, HRMCompEligibility, HRMCompEvent, HRMFixedCompPlanTable, HcmCompensationWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: ef8cf992-176c-4c98-9dff-6510e1eb9f1c
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Human Resources

---

# Create a fixed compensation plans


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

Fixed compensation refers to an employee's regular gross salary or wages. This article describes the components that must be set up before you can create a fixed compensation plan and enroll employees.

Fixed compensation amounts can be calculated for your employees, based on factors such as performance, region, and budget increases. Dynamics 365 Human Resources supports step, grade, and band compensation types.

## Fixed compensation components
### Compensation levels

You can use **Compensation levels** to set compensation for various jobs, to help guarantee that the employees who hold those jobs are paid fairly. On the **Compensation levels** page, you can set up the compensation levels that are required for each step, grade, and band plan. Use the **Up** and **Down** buttons to put the levels in the correct order, according to their type. By setting compensation levels on a job, you help guarantee that all employees who hold a position for that job are paid at the same level.

### Reference points

**Reference points** are the columns in the grid that define the compensation ranges for each level. The compensation level is the row in the grid. Typical reference points for a plan of the grade type are a minimum, a midpoint, and a maximum. You create reference points on the **Reference point setups** page.

### Compensation grids

After you set up the levels and reference points, they can be combined to create a **Compensation grid**. On the **Compensation grids** page, define information about the grid. For example, specify what the grid designed to be used for, what type of plan it will be used with, and which reference points or columns are required in the grid. After you've finished entering that information, click **Compensation structure** to add levels and amounts to your grid. 

**Tip:** Use the **Mass changes** function on the compensation structure to set initial amounts, and then increment by percentages or amounts across your levels or reference points.

### Pay frequencies

**Pay frequencies** are used to define how an employee's wage or salary is being specified (for example $10 per hour versus $50,000 per year), and the conversion between the hourly, weekly, monthly (12 months), and annual rates. For example, a company that uses a 38-hour work week for its hourly employees sets up a pay frequency that has an hourly rate of 1, a weekly rate of 38, a monthly rate of 164.6666666667, and an annual rate of 1,976. These conversions are used to calculate the various pay rates that appear on an employee's fixed compensation record.

## Fixed compensation plans
You can design the fixed compensation plan to combine all the components that you've configured. To create a fixed compensation plan, open the **Fixed compensation plans** page. Here, you can give your plan a name and description, select what type of plan it is (step, grade, or band), select the pay frequency that you'll use for the employee's pay rate (amount per hour, amount per year, and so on), and set some options that control how compensation is processed. 

The **Out of range tolerance** setting lets you specify how strict you want to be about making sure that compensation amounts are between the minimum and maximum amounts. A **Hard** tolerance requires that compensation be within the range that is defined for a given level. A **Soft** tolerance alerts you when the compensation amount is outside the range but allows you to continue. If you set the tolerance to **None**, you can enter any compensation amount for an employee without receiving warning or error messages. 

The **Hire rule** setting lets you specify whether all employees should receive the same increase, regardless of the date that they were hired (**Hire rule** = **None**), or whether employees should receive a percentage of the award, based on how long they were employed during the cycle (**Hire rule** = **Percent**). 

A **Range utilization matrix** is useful if you want either to reduce the time that is required for employees to reach the midpoint of their range, or to increase the time that is required for employees to reach to the maximum reference point in the range. For example, you want to give employees who are in the bottom 25 percent of their range 110 percent of their target award, but you want to give employees who are in the top 25 percent of their range only 80 percent of their target award, to prevent them from reaching the maximum as quickly. 

After you define the basics of the fixed compensation plan, you can set up the compensation structure for the plan. Click **Set up compensation**. A dialog slider opens that gives you three options:

-   **Create a new compensation matrix** by selecting a reference point setup and giving the grid a name.
-   **Create a new compensation matrix** by making a copy of an existing grid that you can use as a starting point.
-   **Use an existing compensation matrix** that has already been defined. All compensation plans that use the same grid receive updates if that grid is changed.

After you select an option, the **Compensation structure** page opens, and you can make changes to the new compensation grid or the existing compensation grid.

## Fixed compensation enrollment
### Determine who is eligible for the plan

The first step in enrolling employees in a fixed compensation plan is to determine who is eligible for the compensation that is defined in the plan. Until you determine eligibility, you won't be able to assign the plan to any employees. To set up eligibility, open the **Eligibility rules** page. Here, you create a new eligibility rule for your compensation plan and define the criteria that an employee must meet to be eligible for a plan. You can limit eligibility based on department, labor union, compensation region (location), job, job function, job type, or compensation level. Employees can be enrolled in a compensation plan only if they meet all conditions that are set on the eligibility rule. 

**Note:** Eligibility rules are used to determine eligibility for both fixed and variable compensation plans. 

The eligibility rule considers the value of specific fields in the **Job**, **Position**, and **Employee** records to determine whether an employee is eligible for a compensation plan.

-   On the **Job** page, the eligibility rule considers the following fields:
    -   The **Job** field
    -   On the **Job classification** tab, the **Function** and **Job type** fields
    -   On the **Compensation** tab, the **Level** field
-   On the **Positions** page, the eligibility rule considers the **Department** and **Compensation region** fields.

The eligibility rule also considers labor unions that are associated with the employee (on the **Employees** page, on the **Worker** tab, click **Personal information** &gt; **Labor unions**).

### Define fixed compensation actions

**Fixed compensation actions** are used when you set or apply changes to an employee's fixed compensation. Fixed compensation actions let you provide descriptive names for the types of actions that a compensation and benefits manager can perform. Different action types have special logic behind them, so that they can be used at specific times. 

For example, when the fixed compensation is set up for an employee, only actions that have a type of **Hire/Rehire** can be used. In this case, you might want to create three different actions of the **Hire/Rehire** type, and name them **Hire**, **Rehire**, and **Transfer**. You then have a more descriptive explanation of why the fixed compensation was given to an employee or changed.

### Enroll the employee

You can now assign an employee to a fixed compensation plan. Open the **Employees** page, and select the employee to enroll in the compensation plan. On the Action Pane, click **Compensation** &gt; **Fixed plan**. You can now create a new fixed compensation action for that employee. 

**Note:** The **Compensation plan** field shows only the plans that an employee is eligible for under the eligibility rules that were set up for each plan. If no eligibility rule is set up for a plan, no employees will be eligible for that plan. 

The compensation amount that is specified for a compensation plan of the grade or band type is verified that it is within the minimum and maximum reference points for the given compensation level on the employee's job. If the compensation amount is outside the allowed range, a warning or error message is displayed, depending on the tolerance level that is set on the fixed compensation plan.



[!INCLUDE[footer-include](../includes/footer-banner.md)]
