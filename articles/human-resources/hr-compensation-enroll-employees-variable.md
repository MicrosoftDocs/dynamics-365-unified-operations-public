--- 
# required metadata 
 
title: Enroll an employee in a variable compensation plan
description: The Compensation and Benefits manager can enroll employees in variable compensation plans to calculate cash and non-cash awards for employees. 
author: ramagadu 
ms.date: 04/25/2025
ms.topic: how-to 
 
# optional metadata 
 
ms.search.form: HRMCompVarEnrollEmpl, HcmCompensationWorkspace 
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

# Enroll an employee in a variable compensation plan

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

The Compensation and Benefits manager can enroll employees in variable compensation plans to calculate cash and non-cash awards for employees. This procedure assumes that a variable compensation plan was created with the **Enable enrollment** field set to **Yes**, and that eligibility rules were created for that variable compensation plan. The demo data company used to create this procedure is USMF. To begin this procedure, go to **Human resources** \> **Workers** \> **Employees** \> **Compensation** \> **Variable plan enrollment**.

1. Select **New**.
2. In the **Plan** field, select the dropdown button to open the lookup.

    The plan lookup is filtered to only show the variable compensation plans that the employee is eligible for based on the eligibility rules.

3. In the list, select the link in the selected row.
4. Toggle the expansion of the **General** section.
5. In the **Effective date** field, enter a date.
6. Select **Save**.
7. Toggle the expansion of the **Overrides** section.

    * Optionally, a hire rule date can be set to override the hire date for an employee when the hire rule specified for the selected variable plan is Percent.
    * If the variable plan is a percent of basis plan, the award percentage can be overridden for the employee. If the variable compensation plan is a number of units plan, the number of units can be overridden for the employee.
    * If the employee should be given a flat amount for their award, the amount can be set here.

8. Toggle the expansion of the **Organizational overrides** section.

    If the employee's performance should consider the performance of different departments, or a department other than the one assigned on the employee's position, the department can be overridden. The **Percent** column should total 100.

## Link variable plan awards and enrollments to positions (preview)

> [!NOTE]
> This feature is currently in preview. The functionality and behavior that are described might change before general availability (GA).
>
> [This is prerelease documentation and is subject to change.]

In Dynamics 365 Human Resources, you can now associate **variable compensation plans**, including awards and enrollments, directly to an employee's **position**. This enhancement gives organization more flexibility to manage variable compensation in alignment with job roles. Therefore, it helps ensure a more accurate and scalable compensation strategy.

Previously, variable compensation plans were linked to the employee level. By associating plans with positions, HR managers can now streamline compensation planning, especially in organizations that have position-based structures.

> [!IMPORTANT]
> To start to use this functionality, enable the **Ability to link variable pay to position** feature in Feature management.

### Link variable plan awards to positions

To link a variable plan award to a position, follow these steps.

1. Go to **Human Resources** \> **Workers**, and select a worker.
1. On the Action Pane, on the **Compensation** tab, select **Variable plan awards**.
1. On the **Employee variable compensation awards** page, in the **Position** field, select the position.
1. Save your changes.

### Link variable plan enrollments to positions

To link a variable plan enrollment to a position, follow these steps.

1. Go to **Human Resources** \> **Workers**, and select a worker.
1. On the Action Pane, on the **Compensation** tab, select **Variable plan enrollment**.

    The **Employee variable compensation enrollment** page includes a new grid that you can use to associate multiple positions with a plan.

1. On the **Positions** tab, select **Add**.
1. In the **Position** field, select the position.
1. Save your changes.

### Data entity updates

To ensure that position details are exported to payroll systems, the following data entities were updated:

- **Employee variable compensation** (HcmVariableCompensationAwardEntity)
- **Payroll integration variable compensation award entity**(PayIntV1HcmVariableCompensationAwardEntity)
- **Payroll integration variable compensation enrollment position** (PayIntV1HcmVariableCompensationEnrollmentPositionEntity)
- **Variable compensation enroll position details** (HcmVariableCompensationEnrollmentPositionEntity)

Learn more about detailed changes that are related to payroll entities in [Payroll integration API introduction](hr-admin-integration-payroll-api-introduction.md).

[!INCLUDE[footer-include](../includes/footer-banner.md)]
