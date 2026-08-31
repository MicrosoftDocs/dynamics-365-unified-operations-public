--- 
# required metadata 
 
title: Develop a compensation structure
description: This article explains how to create a fixed compensation plan and enroll employees in the plan through eligibility rules. 
author: twheeloc
ms.date: 08/06/2026
ms.topic: how-to 
 
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

[!INCLUDE [banner](../includes/banner.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes how to create a fixed compensation plan and enroll employees in the plan through eligibility rules. It uses the USMF demo data and applies to compensation and benefits managers.

## Create a fixed compensation plan

1. Go to **Human resources** > **Compensation** > **Fixed compensation**.
1. Select **Fixed compensation plans**.
1. Select **New**.
1. In the **Plan** field, enter a value.
1. In the **Description** field, enter a value.
1. In the **Effective date** field, enter a date.
1. In the **Type** field, select whether the fixed compensation plan is a **Band**, **Grade**, or **Step** plan.
1. The **Recommendation allowed** checkbox is the default value for any actions added to this plan in a Process event. When you allow recommendations, you can override the calculated guideline amount when processing compensation.

1. Use the **Out of range tolerance** field to specify how you want to handle compensation amounts that fall outside of the specified compensation structure range for the given level.
     - **None** - allows any compensation amount.
     - **Soft tolerance** - warns users if the compensation amount is less than the minimum or greater than the maximum reference point amounts for that level. Users can ignore the warning and continue.
     - **Hard tolerance** - generates an error if an employee's compensation is outside the minimum and maximum reference points for the level and automatically adjusts the employee's compensation to fall within the range.

1. Use the **Hire rule** field to calculate an employee's compensation during a process event. A **Hire rule** of **Percent** calculates an increase that's prorated for the length of the time the worker has been employed in the cycle.
1. In the **Currency** field, type a value.
1. In the **Pay rate conversion** field, enter or select a value.
1. Expand the **Range utilization matrix** section. Optionally, add range utilization records to help employees reach their midpoint faster and slow them from reaching the maximum of their range.
1. Select **Save**. This action enables the **Set up compensation** button and you can continue defining your compensation structure for the plan.
1. Select **Set up compensation**. You can create a compensation structure by using one of these three methods:

    - Create a completely new structure by selecting a set of reference points and adding the levels to create your own structure.
    - Copy a compensation structure from an existing plan as a starting point and modify it for the new plan.
    - Select an existing compensation grid. If another plan already uses the compensation grid, the other plan also reflects any changes you make to the grid.

1. Select **Create new from existing compensation matrix**.
1. In the **Copy from grid** field, enter or select a value. Optionally, you can change the name of the new compensation grid that you create by copying the selected grid.
1. Select **OK**.
1. Select **Mass change**. **Mass change** allows you to maintain the compensation matrix amounts by applying a percent or flat amount increase to one or more levels or reference points.
1. In the **Adjustment amount** field, enter a number.
1. In the list, mark or unmark all rows.
1. Select **Apply to grid**.
1. Close the page. After you create the compensation structure, you can select which of the reference points to use as the control point for the fixed compensation plan. The control point is used to calculate an employee's Compa ratio.
1. In the **Control point** field, enter or select a value.
1. Close the page.

## Create an eligibility rule for the fixed compensation plan

You can't assign a fixed compensation plan to an employee until you define eligibility rules for the plan.  

1. Go to **Human resources** > **Compensation** > **Eligibility**.
1. Select **Eligibility rules**.
1. Select **New**.
1. In the **Eligibility** field, enter a value.
1. In the **Description** field, enter a value.
1. In the **Effective date** field, enter a date. Both fixed and variable compensation plans use eligibility rules. In the **Type** field, select the type of plan.
1. In the **Plan** field, enter or select a value. Select the criteria an employee must meet to be eligible for the compensation plan. Criteria can include:

    - **Department**
    - **Labor union**
    - **Location** (**Compensation region**)
    - **Job**
    - **Function**
    - **Job type**
    - **Compensation level**

    The employee must meet all specified criteria to be eligible for the compensation plan. If you don't specify any criteria, all employees are eligible for the compensation plan. If an employee doesn't meet the criteria specified in the eligibility rule, or if you didn't specify an eligibility rule for a compensation plan, the compensation plan doesn't appear in the lookup when you create a fixed compensation record for an employee.

1. Close the page.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
