--- 
# required metadata 
 
title: Develop salary/compensation structure and plan
description: This task guide walks though the process of creating a Fixed compensation plan and enabling employees to be enrolled in the plan through eligibility rules. 
author: andreabichsel
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, HcmCompensationWorkspace, HcmCompFixedPlansPart, HRMCompFixedPlanTable, HRMCompCreateGridDialog, HRCCompGridView, HRMCompEligibility,  HRCCompGrid   
audience: Application User 
# ms.devlang:  
ms.reviewer: anbichse
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Develop salary/compensation structure and plan



This task guide walks though the process of creating a Fixed compensation plan and enabling employees to be enrolled in the plan through eligibility rules. The demo data company used to create this task is USMF and the task is intended for Compensation and Benefits Managers.


## Create fixed compensation plan
1. Click Compensation management.
2. Click Fixed compensation plans.
3. Click New.
4. In the Plan field, type a value.
5. In the Description field, type a value.
6. In the Effective date field, enter a date.
7. In the Type field, select whether the Fixed compensation plan is a Band, Grade, or Step plan.
8. The Recommendation allowed checkbox acts as a default value for any actions added to this plan in a Process event.  Allowing recommendations enables you to override the calculated guideline amount when processing compensation.
9. The Out of range tolerance allows you to specify how you want to handle compensation amounts that fall outside of the specified compensation structure range for the given level.  An Out of range tolerance of None will allow any compensation amount to be used.  A Soft tolerance will warn the user if the compensation amount is less than the minimum reference point amount for that level, or greater than the maximum amount for that level. The user can ignore the warning and continue.  A Hard tolerance will generate an error if an employee's compensation is set outside of the minimum and maximum reference points for the level and will automatically adjust the employee's compensation to fall within the range.
10. The Hire rule field is used when a compensation Process event is run to calculate an employee's compensation.  A Hire rule of Percent will calculate an increase that's prorated for the length of the time the worker has been employed in the cycle.
11. In the Currency field, type a value.
12. In the Pay rate conversion field, enter or select a value.
13. Expand the Range utilization matrix section.
    * Optionally, add range utilization records to get employees to their midpoint faster and slow them from reaching the maximum of their range.  
14. At this point, you must save the Fixed compensation plan to enable the Set up compensation button and continue defining your compensation structure for the plan.  Click Save.
15. Click Set up compensation.
    * There are three ways to create a compensation structure. 1: Create a completely new structure by selecting a set of reference points and adding the levels to create your own structure. 2: Copy a compensation structure from an existing plan as a starting point and modify it for the new plan. 3: Select an existing compensation grid. If the compensation grid is already being used by another plan, any changes made to the grid will also be reflected in the other plan.  
16. Select the Create new from existing compensation matrix option.
17. In the Copy from grid field, enter or select a value.
    * Optionally you can change the name of the new compensation grid that will be created as a copy of the selected grid.  
18. Click OK.
19. Click Mass change.
    * Mass change allows you to maintain the compensation matrix amounts by applying a percent or flat amount increase to one or more levels and/or reference points.  
20. In the Adjustment amount field, enter a number.
21. In the list, mark or unmark all rows.
22. Click Apply to grid.
23. Close the page.
    * Once a compensation structure has been created or selected, you can select which of the reference points should be used as the Control point for the Fixed compensation plan.  The Control point is used to calculate an employee's Compa Ratio.  
24. In the Control point field, enter or select a value.
25. Close the page.

## Create an eligibility rule for the new Fixed compensation plan
    * The new Fixed compensation plan cannot be assigned to an employee until Eligibility rules have been defined for the plan.  
1. Click Eligibility rules.
2. Click New.
3. In the Eligibility field, type a value.
4. In the Description field, type a value.
5. In the Effective date field, enter a date.
    * Eligibility rules are used for both Fixed and Variable compensation plans.  In the Type field, select which type of plan this set of eligibility rules is for.  
6. In the Plan field, enter or select a value.
    * Select the criteria an employee must meet in order to be eligible for the compensation plan. Criteria can include a Department, Labor union, Location (Compensation region), Job, Function, Job type, or Compensation level. The employee must meet all specified criteria to be eligible for the compensation plan. If no criteria are specified, all employees are eligible for the compensation plan. If an employee does not meet the criteria specified in the eligibility rule, or an eligibility rule has not been specified for a compensation plan, the compensation plan will not appear in the lookup when creating a Fixed compensation record for an employee.  
7. Close the page.
8. Close the page.

