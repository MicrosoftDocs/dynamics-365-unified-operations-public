--- 
# required metadata 
 
title: Develop a compensation structure
description: This article explains how to create a fixed compensation plan and enroll employees in the plan through eligibility rules. 
author: twheeloc
ms.date: 08/25/2021
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, HcmCompensationWorkspace, HcmCompFixedPlansPart, HRMCompFixedPlanTable, HRMCompCreateGridDialog, HRCCompGridView, HRMCompEligibility,  HRCCompGrid   
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

# Develop a compensation structure


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes creating a fixed compensation plan and enrolling employees in the plan through eligibility rules. This article uses the USMF demo data and applies to compensation and benefits Managers.

## Create a fixed compensation plan

1. Select **Compensation management**.

2. Select **Fixed compensation plans**.

3. Select **New**.

4. In the **Plan** field, enter a value.

5. In the **Description** field, enter a value.

6. In the **Effective date** field, enter a date.

7. In the **Type** field, select whether the fixed compensation plan is a **Band**, **Grade**, or **Step** plan.

8. The **Recommendation allowed** check box will be the default value for any actions added to this plan in a Process event. Allowing recommendations enables you to override the calculated guideline amount when processing compensation.

9. The **Out of range tolerance** field allows you to specify how you want to handle compensation amounts that fall outside of the specified compensation structure range for the given level. Setting the **Out of range tolerance** field to **None** allows you to use any compensation amount. **Soft tolerance** warns users if the compensation amount is less than the minimum or greater than the maximum reference point amounts for that level. Users can ignore the warning and continue. **Hard tolerance** generates an error if an employee's compensation is outside the minimum and maximum reference points for the level and will automatically adjust the employee's compensation to fall within the range.

10. The **Hire rule** field calculates an employee's compensation during a process event. A **Hire rule** of **Percent** calculates an increase that's prorated for the length of the time the worker has been employed in the cycle.

11. In the **Currency** field, type a value.

12. In the **Pay rate conversion** field, enter or select a value.

13. Expand the **Range utilization matrix** section. Optionally, add range utilization records to get employees to their midpoint faster and slow them from reaching the maximum of their range.

14. Select **Save**. This enables the **Set up compensation** button and continue defining your compensation structure for the plan.

15. Select **Set up compensation**. You can create a compensation structure by using one of these three methods:

    - Create a completely new structure by selecting a set of reference points and adding the levels to create your own structure.
    - Copy a compensation structure from an existing plan as a starting point and modify it for the new plan.
    - Select an existing compensation grid. If another plan already uses the compensation grid, the other plan also reflects any changes you make to the grid.

16. Select **Create new from existing compensation matrix**.

17. In the **Copy from grid** field, enter or select a value. Optionally, you can change the name of the new compensation grid that you create by copying the selected grid.

18. Select **OK**.

19. Select **Mass change**. **Mass change** allows you to maintain the compensation matrix amounts by applying a percent or flat amount increase to one or more levels or reference points.

20. In the **Adjustment amount** field, enter a number.

21. In the list, mark or unmark all rows.

22. Click **Apply to grid**.

23. Close the page. After you create the compensation structure, you can select which of the reference points to use as the control point for the fixed compensation plan. The control point is used to calculate an employee's Compa Ratio.

24. In the **Control point** field, enter or select a value.

25. Close the page.

## Create an eligibility rule for the fixed compensation plan

You can't assign a fixed compensation plan to an employee until you define eligibility rules for the plan.  

1. Select **Eligibility rules**.

2. Select **New**.

3. In the **Eligibility** field, enter a value.

4. In the **Description** field, enter a value.

5. In the **Effective date** field, enter a date. Both fixed and variable compensation plans use eligibility rules. In the **Type** field, select the type of plan.

6. In the **Plan** field, enter or select a value. Select the criteria an employee must meet in order to be eligible for the compensation plan. Criteria can include:

    - **Department**
    - **Labor union**
    - **Location** (**Compensation region**)
    - **Job**
    - **Function**
    - **Job type**
    - **Compensation level**
    
    The employee must meet all specified criteria to be eligible for the compensation plan. If you don't specify any criteria, all employees are eligible for the compensation plan. If an employee doesn't meet the criteria specified in the eligibility rule, or an eligibility rule has not been specified for a compensation plan, the compensation plan won't appear in the lookup when you create a fixed compensation record for an employee.

7. Close the page.

8. Close the page.



[!INCLUDE[footer-include](../includes/footer-banner.md)]
