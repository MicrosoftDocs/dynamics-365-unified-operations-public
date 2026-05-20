--- 
# required metadata 
 
title: Define compensation process and calculate results
description: Compensation processes are used to determine new compensation amounts and awards for employees enrolled in fixed and variable compensation plans. 
author: twheeloc
ms.date: 05/14/2026
ms.topic: how-to 
 
# optional metadata 
 
ms.search.form: HRMCompProcess, HRMCompProcessLine, HRMCompEvent, HRMCompEventEmpl, HcmCompensationWorkspace 
audience: Application User 
# ms.devlang:  

# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---

# Define compensation process and calculate results

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

Compensation processes are used to determine new compensation amounts and awards for employees enrolled in fixed and variable compensation plans. Compensation processes can be run multiple times to perform "what-if" analysis, to verify all changes and settings are correct. This procedure creates a compensation process, runs the process, and view the results. The demo data company used to create this procedure is USMF.

## Create a compensation process

1. Go to **Human resources** > **Compensation** > **Process** > **Compensation processes**.
1. Select **New**.
1. In the **Process** field, enter a value.
1. In the **Description** field, enter a value.
1. In the **Process type** field, select an option.
    * A cycle specifies the time period evaluated to determine compensation. The evaluation considers which positions employees held, which performance ratings to include, calculation of the percentage of time the employee was employed during the cycle, and more. An example of a cycle start date might be the first day of the past fiscal year.  
1. In the **Cycle start** field, enter a date.
    * The cycle end date is important because it's the date used to determine which employees were actively employed and enrolled in one or more compensation plans.  
1. In the **Cycle end** field, enter a date.
1. In the **Transaction active date** field, enter a date. The transaction active date is the date the new compensation rates should take effect. Many companies include a few months between their end of a cycle and the time the new compensation rates go into effect. Use the additional time for processing and reviewing the new compensation.
1. The **Point-in-time date** field is used for variable compensation plans that determine an employee's award amount based on their compensation rate at this point in time.
1. The **Fixed pay pro rated hire date** is used with fixed compensation plans with a hire rule of **Percent**. Employees who are hired between the cycle start and the fixed pay pro rated hire date receive 100% of their calculated compensation increase, instead of pro-rated percentage.  
1. In the **Fixed pay pro rated hire date** field, enter a date.
    * The review deadline is the date by which all process results should be reviewed so that you can load them into an employee's compensation record before the transaction active date. This field is informational only.  
1. In the **Review deadline** field, enter a date.
1. Select **Save**.

## Set up the compensation plans and actions for a compensation process

1. Select **Setup**.
    * Use the **Setup** page to select which plans to process as part of this compensation process, and choose which actions to take against each plan.  
1. In the **Plan** field, enter or select a value.
1. Select **Save**.
1. Select **Add**.
1. In the **Action** field, select an **Equity** type of action.
1. Select **Add**.
1. In the **Action** field, select a **Merit** type of action.
    * You can chain compensation actions together by using the **Use previous result** field to indicate whether the selected action should use the employee's base pay or the result of the previous action as the starting point for this action's calculation.  
1. Select **Yes** in the **Use previous result** field.
1. Select **Add**.
1. In the **Action** field, select a **General** type of action.
    * Different compensation action types enable different fields. For a General compensation action type, you can specify an increase percent or increase amount.  
1. Select the **Select increase amount** option.
1. In the **Increase amount** field, enter a number.
1. Select **Add**.
1. In the **Action** field, select a **Promotion** type of action.
    * Promotion and Other level change action types enable users to make manual adjustments to employee compensation. You can enable recommendations for these action types, as well as other action types, to enable you to enter a new recommended compensation value for an employee.  
1. Select **Add**.
1. In the **Type** field, select an option.
    * You can run fixed and variable compensation plans in the same compensation process.  
1. In the **Plan** field, enter or select a value.
    * Use the **Enable pay for performance** check box to determine whether fixed and variable compensation amounts should be adjusted based on the employee's performance rating.  
    * You can override leverage on variable compensation plans.  
1. Select **Save**.
1. Select **Add**.
1. Close the page.

## Run the compensation process

1. Select **Run process**.
    * The **Show processing results** control displays processing messages for the complete compensation process when processing finishes.  
1. Select **Yes** in the **Show processing results** field.
1. Select **OK**.

## View the results

1. Select **Process results**.
1. Select **Employee results**.
1. In the list, find and select the desired record.
1. Expand the **Fixed compensation** section.
    * Expand the FastTabs to view the results of the process. If you select **Enable recommendations** for a compensation action, the **Recommendation** fields are enabled for that action.  
1. In the list, find and select the desired record.
    * To view the results for a single employee, select the **View results** button.  
    * To overwrite the calculated compensation amount, adjust the percent or the increase amount in the **Recommendation** fields.  
1. In the **Percent recommended** field, enter a number.
1. In the list, find and select the desired record.
1. In the **Percent recommended** field, enter a number.
    * Select **Recalculate** to ignore any changes you made to the existing record and generate a new compensation result for the selected employee.  
    * When all changes are complete for an employee, change the status to **Approved**.  
1. Select **Change status**.
1. Select **Approved**.
    * After you approve the record, you can load it to the employee's official compensation record. The new compensation is effective as of the transaction date set on the compensation process.  

[!INCLUDE[footer-include](../includes/footer-banner.md)]
