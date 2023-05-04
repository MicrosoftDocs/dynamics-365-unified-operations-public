--- 
# required metadata 
 
title: Define compensation process and calculate results
description: Compensation processes are used to determine new compensation amounts and awards for employees enrolled in fixed and variable compensation plans. 
author: twheeloc
ms.date: 08/25/2021
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
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


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

Compensation processes are used to determine new compensation amounts and awards for employees enrolled in fixed and variable compensation plans. Compensation processes can be run multiple times to perform "what-if" analysis, to verify all changes and settings are correct. This procedure will create a compensation process, run the process, and view the results. The demo data company used to create this procedure is USMF.


## Create a compensation process
1. Go to **Compensation management** > **Process** > **Compensation processes**.
2. Click **New compensation process**.
3. In the **Process field**, type a value.
4. In the **Description** field, type a value.
5. In the **Process type** field, select an option.
    * A cycle specifies the time period evaluated to determine compensation. The evaluation considers which positions were held by employees, which performance ratings to include, calculation of the percentage of time the employee was employed during the cycle, and more. An example of a cycle start date might be the first day of the past fiscal year.  
6. In the **Cycle start** field, enter a date.
    * The cycle end date is important because it is the date used to determine which employees were actively employed and enrolled in one or more compensation plans.  
7. In the **Cycle end** field, enter a date.
    * The transaction active date is the date the new compensation rates should take effect. Many companies include a few months between their end of a cycle and the time the new compensation rates go into effect. The additional time is used for processing and reviewing the new compensation.  
8. In the **Transaction active date** field, enter a date.
    * The point-in-time date is used for variable compensation plans that determine an employee's award amount based on their compensation rate at this point in time.  
    * The fixed pay pro rated hire date is used with fixed compensation plans with a hire rule of **Percent**. Employees who are hired between the cycle start and the fixed pay pro rated hire date will receive 100% of their calculated compensation increase, instead of pro-rated percentage.  
9. In the **Fixed pay pro rated hire date** field, enter a date.
    * The review deadline is the date by which all process results should be reviewed so that they can be loaded into an employee's compensation record before the transaction active date. This field is informational only.  
10. In the **Review deadline** field, enter a date.
11. Click **Save**.

## Set up the compensation plans and actions for a compensation process
1. Click **Setup**.
    * The **Setup** page is used to select which plans to process as part of this compensation process, as well as which actions should be taken against each plan.  
2. In the **Plan** field, enter or select a value.
3. Click **Save**.
4. Click **Add**.
5. In the **Action** field, select an **Equity** type of action.
6. Click **Add**.
7. In the **Action** field, select a **Merit** type of action.
    * Compensation actions can be "chained" together using the **Use previous result** field to indicate whether the selected action should use the employees base pay or the result of the previous action as the starting point for this action's calculation.  
8. Select **Yes** in the **Use previous result** field.
9. Click **Add**.
10. In the **Action** field, select a **General** type of Action.
    * Different compensation action types enable different fields. For a General compensation action type, an increase percent or increase amount can be specified.  
11. Select the **Select increase amount** option.
12. In the **Increase amount** field, enter a number.
13. Click **Add**.
14. In the **Action** field, select a **Promotion** type of Action.
    * Promotion and Other level change action types enable users to make manual adjustments to employee compensation. Recommendations can be enabled for these action types, as well as other action types to enable you to enter a new recommended compensation value for an employee.  
15. Click **Add**.
16. In the **Type** field, select an option.
    * Fixed and variable compensation plans can be run in the same compensation process.  
17. In the **Plan** field, enter or select a value.
    * Use the **Enable pay for performance** check box to determine whether fixed and variable compensation amounts should be adjusted based on the employee's performance rating.  
    * Leverage can be overridden on variable compensation plans.  
18. Click **Save**.
19. Click **Add**.
20. Close the page.

## Run the compensation process
1. Click **Run process**.
    * The **Show processing results** control lets you view processing messages for the complete compensation process when processing has finished.  
2. Select **Yes** in the **Show processing results** field.
3. Click **OK**.

## View the results
1. Click **Process results**.
2. Click **Employee results**.
3. In the list, find and select the desired record.
4. Expand the **Fixed compensation** section.
    * Expand the FastTabs to view the results of the process. If **Enable recommendations** was marked for a compensation action, the **Recommendation** fields will be enabled for that action.  
5. In the list, find and select the desired record.
    * The results for a single employee can be viewed by clicking the **View results** button.  
    * You can overwrite the calculated compensation amount by adjusting the percent or the increase amount in the **Recommendation** fields.  
6. In the **Percent recommended** field, enter a number.
7. In the list, find and select the desired record.
8. In the **Percent recommended** field, enter a number.
    * Recalculate can be used to ignore any changes made to the existing record and generate a new compensation result for the selected employee.  
    * When all changes are complete for an employee, change the status to **Approved**.  
9. Click **Change status**.
10. Click **Approved**.
    * After the record has been approved it can be loaded to the employee's official compensation record. The new compensation will be effective as of the transaction date set on the compensation process.  



[!INCLUDE[footer-include](../includes/footer-banner.md)]
