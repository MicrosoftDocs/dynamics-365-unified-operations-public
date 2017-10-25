---
# required metadata

title: Process compensation
description: Compensation processing allows you to calculate new base compensation amounts for your employees based on equity adjustments, merit increase targets, and performance.
author: kherr75
manager: AnnBe
ms.date: 07/01/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: rschloma
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 3b953d5f-6325-4c9e-8b9b-6ab0458a73f8
ms.search.region: Global
# ms.search.industry: 
ms.author: kherr
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: AX 7.0.0, Talent July 2017 update

---

# Process compensation
Compensation processing allows you to calculate new base compensation amounts for your employees based on equity adjustments, merit increase targets, and performance. This topic covers the basic flow of compensation processing for fixed compensation plans without factoring an employee's performance.

## Plan the new compensation amounts and budgets
To give your employees a merit increase, you must set up a fixed increase budget for each of your Departments:  Compensation management > Links > Merit increase targets. (Alternatively, you can open this form through the Department: Organization > Departments.) Here you can further specify whether employees in a certain labor union or location should get a different increase percent. The **Budget** and **Currency** fields are informational and can be used to note a currency amount for the budget.

## Set up the compensation process
A process event lets you specify the parameters for the compensation processing. This includes the date period to evaluate for determining the compensation amounts, and the date that the new compensation amounts should go into effect.

Optionally you can include a fixed pay pro rated hire date if any of you fixed compensation plans use a hire rule of Percent. For those plans, anyone who was hired after the cycle start date and before the fixed pay pro rated hire date will receive 100% of their calculated merit or general increase. Anyone who was hired after the fixed pay pro rated hire date and before the cycle end date will receive a portion of their calculated increase based on how many days out of the total cycle days they were employed. For example, if our cycle runs from January 1 through December 31 and we have a fixed pay prorated hire date of April 1, an employee who is hired in March will receive the full calculated increase while an employee hired on July 1 will receive approximately half of the calculated increase.

The process event **Point-in-time** date is used for processing only certain variable compensation plans and isn't covered here. The **Review deadline** is the deadline to make all the recommendations so that the new compensation amounts can be loaded into the employee’s record. The review date is informational only.

After the parameters of the process event have been saved, you can click the **Setup** button to indicate the plans to include when this process is run, and which fixed compensation actions to take for each plan.

Click the **Add** button in the **Plans** tab to add a compensation plan to the process event. The **Use other leverage**, **Leverage factor**, and **Leverage description** columns are used for variable compensation plans only and are not be covered in this topic.

Save the record, then click the **Add** button in the **Actions** tab to add fixed compensation actions for the selected plan. Use the **Enable recommendation** option to enter an amount that's different than the calculated guideline increase for the action. To calculate  an action that's based on the result of the previous action to link multiple compensation actions, mark the **Use previous result** option, Fixed compensation actions are types of compensation logic that you can give descriptive names to. For Grade and Band plans, you can only add fixed compensation actions that are of the following Types:

| Fixed compensationaction type | Functionality                                                                                                                                                                                                                                                                                                                                                                                                    |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Equity                        | Equity actions will compare the employee’s rate of pay as of the cycle end date with the lowest reference point for the level indicated on the employee’s job. If the employee’s pay rate is less than the minimum reference point, the increase needed to bring the employee to the minimum point in the range will be calculated.                                                                                |
| Merit                         | Merit actions will calculate an increase based on the employee’s pay rate as of the cycle end date and the increase percent found in the fixed increase budget for the employee’s department, labor union, and location.                                                                                                                                                                                         |
| General                       | General actions will calculate an increase based on either a Percent or give the employees a flat amount. This is determined based on the **Fixed compensation** settings on the **General** tab.                                                                                                                                                                                                                        |
| Promotion                     | Promotion actions provide you with a named place where you can award increase so be sure to mark the **Enable recommendation** option so you can enter a recommendation for the employees who will receive promotions.  Employees without a recommended increase will not have the **Promotion** action added to their fixed compensation records.                                                                       |
| Other level change            | In the preceding example, **Demotion** is the name of our **Fixed compensation** action with a type of **Other level change**. This generates a 0 (zero-change) guideline increase so you can enter a recommendation amount to adjust the employee’s pay rate. (Be sure to mark the **Enable recommendation** option.) Employees without a recommendation will not have this action added to their fixed compensation records. |

You can only add **Fixed compensation** actions with a type of Step to a Step plan.

| Fixed compensation action type | Functionality                                                                                                                                                                                           |
|--------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Step                           | On the General tab, indicate whether this Step action should move the employees forward 0 steps, 1 step, or two steps.                                                                                  |
|                                | **0 steps** - The employee will receive the pay rate for the current step they are on.                                                                                                                      |
|                                | **1 step** - The system will check whether the employee is already at the last reference point for their level.                                                                                             |
|                                | **2 steps** - The system will move the employee forward two steps on their current level. The system might only move the employee one or zero steps if they reach the last reference point for their level. |

## Run the compensation process
After the process event has been set up with the necessary date fields, plans and actions you can click **Run process** on the **Process event** page. Doing so opens the **Run compensation process events** dialog. Within this dialog, you can click the **Show processing results** option to seen how the compensation amounts were calculated for each employee. Clicking **OK** will run the compensation process for all employees who in the selected compensation plans as of the cycle end date.

## View the process results
To view the process results, open the **Process results** page. A new compensation event will be created each time the process event is run. In this way, you can do trial runs, make adjustments, and run the compensation event multiple times to see how various changes impact employee compensation.

The **Process results** page contains information about the process run including when the run occurred, the user who ran the process, and whether any errors occurred when the process was run. You can also mark the **Locked** option to disable the **Load compensation** button and prevent anyone from loading the compensation events to the employee records. Clicking the **Employees results** button will display the list of employees included in the run.

The **Employee results** option shows information about the process itself, as well as any compensation actions performed in the process. The **Fixed compensation** section will contain a record for each action included in the process event for the compensation plan. The **Current Guildeline** and **Recommendation** columns will display more information for the action selected in the **Fixed compensation** section. If **Enable recommendations** was marked for the action, the Recommendation fields will be editable. This will let you manually adjust the amounts for the employee. Note that if you marked **Use previous result** for the action on the process event, you must manually update the amounts for any dependent actions.

When the compensation amounts have been reviewed for an employee and any adjustments to the recommended values have been made, you can change the **Status** on the **Employee event** line to indicate whether the event has been approved or should be ignored. Optionally, you can erase any changes made to the employee’s recommendation by clicking the **Recalculate** button. This will mark the existing employee event with a status of Ignore and create a new employee event with recalculated values.

## Loading approved compensation changes
When one or more employee events have had their status updated to Approved, they can be loaded to the employees’ fixed compensation records. This can be done either by selecting each employee event one at a time and clicking the **Load employee compensation** button on the **Employee results** page, or by clicking **Load compensation** on the **Process results** page to load all approved employee events at once.

Clicking **OK** in the **Load compensation** dialog will add the non-zero compensation action lines to the **Employee fixed compensation** page.
