---
# required metadata

title: Process compensation
description: Compensation processing allows you to calculate new base compensation amounts for your employees based on equity adjustments, merit increase targets, and performance.
author: twheeloc
ms.date: 05/14/2026
ms.topic: article
# optional metadata

# ms.search.form: HcmCompensationWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 3b953d5f-6325-4c9e-8b9b-6ab0458a73f8
ms.search.region: Global
# ms.search.industry: 
ms.author: anisagrawal
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: AX 7.0.0, Human Resources

---

# Process compensation

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

Compensation processing calculates new base compensation amounts for your employees based on equity adjustments, merit increase targets, and performance. This article covers the basic flow of compensation processing for fixed compensation plans without factoring an employee's performance.

## Plan the new compensation amounts and budgets

To give your employees a merit increase, set up a fixed increase budget for each of your departments:  **Compensation management** > **Links** > **Merit increase targets**. (Alternatively, open this page through the department: **Organization** > **Departments**.) You can specify whether employees in a certain labor union or location should get a different increase percentage. Use the **Budget** and **Currency** fields to note a currency amount for the budget.

## Set up the compensation process

On the **Compensation processes** page, you can specify the parameters for the compensation processing. This includes the date period to evaluate for determining the compensation amounts, and the date that the new compensation amounts should go into effect.

Optionally, include a **Fixed pay pro rated hire date** if any of your fixed compensation plans use a hire rule of Percent. For those plans, anyone who was hired after the **Cycle start** date and before the **Fixed pay pro rated hire date** receives 100% of their calculated merit or general increase. Anyone who was hired after the **Fixed pay pro rated hire date** and before the **Cycle end date** receives a portion of their calculated increase based on how many days out of the total cycle days they were employed. For example, if your cycle runs from January 1 through December 31 and there's a fixed pay prorated hire date of April 1, an employee who is hired in March receives the full calculated increase while an employee hired on July 1 receives approximately half of the calculated increase.

The process event **Point-in-time** date is used for processing only certain variable compensation plans and isn't covered here. The **Review deadline** is the deadline to make all the recommendations so that the new compensation amounts can be loaded into the employee’s record. The review date is informational only.

After the parameters of the process event have been saved, you can select the **Setup** button to select the plans to include when the process is run, and which fixed compensation actions to take for each plan.

Select the **Add** button on the **Plans** tab to add a compensation plan to the process event. The **Use other leverage**, **Leverage factor**, and **Leverage description** columns are used for variable compensation plans only and aren't be covered in this article.

Save the record, then select the **Add** button on the **Actions** tab to add fixed compensation actions for the selected plan. Use the **Enable recommendation** option to enter an amount that's different than the calculated guideline increase for the action. To calculate an action that's based on the result of the previous action to link multiple compensation actions, mark the **Use previous result** option. Fixed compensation actions are types of compensation logic that you can give descriptive names to. For **Grade** and **Band** plans, you can only add fixed compensation actions that are of the following Types:

| Fixed compensation action type | Functionality                  |
|-------------------------------|-------------------------------------------------------------------------|
| Equity                        | Equity actions compare the employee’s rate of pay as of the cycle end date with the lowest reference point for the level indicated on the employee’s job. If the employee’s pay rate is less than the minimum reference point, the action calculates the increase needed to bring the employee to the minimum point in the range.                  |
| Merit                         | Merit actions calculate an increase based on the employee’s pay rate as of the cycle end date and the increase percent found in the fixed increase budget for the employee’s department, labor union, and location.       |
| General                       | General actions calculate an increase based on either a Percent or give the employees a flat amount. This calculation is determined based on the **Fixed compensation** settings on the **General** tab.                         |
| Promotion                     | Promotion actions provide you with a named place where you can award increases. Mark the **Enable recommendation** option to enter a recommendation for employees who receive promotions.  Employees without a recommended increase don't have the **Promotion** action added to their fixed compensation records.                                                                       |
| Other level change            | In the preceding example, **Demotion** is the name of the **Fixed compensation** action with a type of **Other level change**. This action generates a 0 (zero-change) guideline increase so you can enter a recommendation amount to adjust the employee’s pay rate. (Select the **Enable recommendation** option.) Employees without a recommendation don't have this action added to their fixed compensation records. |

You can only add **Fixed compensation** actions with a type of Step to a Step plan.

| Fixed compensation action type | Functionality                |
|--------------------------------|------------------------------|
| Step                           | On the **General** tab, indicate whether this Step action should move the employees forward 0 steps, 1 step, or 2 steps.                                                                                  |
|                                | **0 steps** - The employee receives the pay rate for the current step they are on.         |
|                                | **1 step** - The system checks whether the employee is already at the last reference point for their level.                                                                                       |
|                                | **2 steps** - The employee moves forward two steps on their current level. The employee might only move one or zero steps if they reach the last reference point for their level. |

## Run the compensation process

After setting up the process event with the necessary date fields, plans, and actions, select **Run process** on the **Process event** page. This action opens the **Run compensation process events** dialog. Select the **Show processing results** option to see how the compensation amounts were calculated for each employee. Select **OK** to run the compensation process for all employees who are in the selected compensation plans as of the cycle end date.

## View the process results

To view the process results, open the **Process results** page. Each time you run the process event, you create a new compensation event. This process allows you to make trial runs, make adjustments, and run the compensation event multiple times to see how various changes impact employee compensation.

The **Process results** page contains information about the process run, including when the run occurred, the user who ran the process, and whether any errors occurred when the process ran. Select the **Locked** option to disable the **Load compensation** button and prevent anyone from loading the compensation events to the employee records. Selecting the **Employees results** button displays the list of employees included in the run.

The **Employee results** option shows information about the process itself, as well as any compensation actions performed in the process. The **Fixed compensation** section contains a record for each action included in the process event for the compensation plan. The **Current Guideline** and **Recommendation** columns display more information for the action selected in the **Fixed compensation** section. If you marked **Enable recommendations** for the action, you can edit the **Recommendation** fields. This option lets you manually adjust the amounts for the employee. If you marked **Use previous result** for the action on the process event, you must manually update the amounts for any dependent actions.

When you review the compensation amounts for an employee and make any adjustments to the recommended values, you can change the **Status** on the **Employee event** line to indicate whether the event is approved or should be ignored. Optionally, you can erase any changes made to the employee’s recommendation by selecting the **Recalculate** button. This action marks the existing employee event with a status of **Ignore** and creates a new employee event with recalculated values.

## Load approved compensation changes

When you update the status of one or more employee events to **Approved**, you can load them to the employees’ fixed compensation records. You can either select each employee event one at a time and select the **Load employee compensation** button on the **Employee results** page, or select **Load compensation** on the **Process results** page to load all approved employee events at once.

Selecting **OK** in the **Load compensation** dialog adds the nonzero compensation action lines to the **Employee fixed compensation** page.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
