--- 
# required metadata 
 
title: Set up positions
description: This article describes how positions are an important element of the lower level of an organization hierarchy. 
author: twheeloc
ms.date: 06/25/2026
ms.topic: how-to 
 
# optional metadata 
 
ms.search.form: DefaultDashboard, HcmWorkforceWorkspace, HcmWorkerActivityChart, HcmAllWorkersListPart, HcmPosition, HcmPositionNewPosition, HcmJobLookup, HcmPositionReportsToDialog, HcmPositionLookup, FinancialDimensionDefaultTemplatesLookup, DimensionLookup, HcmPersonnelManagementWorkspace
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
# Set up positions

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

Positions are an important element of the lower level of an organization hierarchy. A position is an individual instance of a job. For example, the position, "Sales manager (East)," is one of the positions that is associated with the job, "Sales manager." A position exists in a department and can have only one worker associated with it. In this task, you create a position. Human Resources Specialists use this procedure.

1. Select **Workforce management**.
1. Select **Open positions**.
1. Select **New** to open the drop-down dialog box.
1. In the **Job** field, enter or select a value.

    The system automatically copies the **Job description**, **Title**, and **Full-time equivalent employment factor** fields from the selected job into the position.

1. Select **Create position**.
1. In the **Department** field, enter or select a value.
1. In the **Position type** field, enter or select a value.
1. In the **Compensation region** field, enter or select a value.

    The **Compensation region** field determines the compensation eligibility rules and fixed increase budgets that apply to an employee in that position.

1. In the **Available for assignment** field, enter a date and time.
1. Expand the **Position duration** section.

    The system enters the position duration by default, based on activation and retirement dates that you entered earlier.

1. Expand the **Reports to position** section.

    When you assign a worker to a position that reports to another position, you create a direct reporting relationship between the workers who are assigned to the two positions.

1. Select **New** to open the drop-down dialog box.
1. In the **Reports to** field, enter or select a value.
1. Select **Create**.
1. Expand the **Worker assignment** section.
1. Expand the **Relationships** section.

    If your organization uses a matrix hierarchy or another custom hierarchy, you can set up position hierarchy types and then add reporting relationships to positions for each hierarchy type that you set up.

1. Select **Add**.
1. In the list, mark the selected row.
1. In the **Hierarchy name** field, enter or select a value.
1. In the **Reports to position** field, enter or select a value.
1. Expand the **Payroll** section.
1. In the **Pay cycle** field, enter or select a value.
1. In the **Paid by** field, enter or select a value.
1. In the **Annual regular hours** field, enter a number.

    The value that you enter is the number of regularly paid hours that the worker in this position is expected to work each year.

1. Expand the **Labor union** section.
1. Collapse the **Labor union** section.
1. Expand the **Financial dimensions** section.
1. In the **Distribution template** field, enter or select a value.
1. In the **Department** field, enter or select a value.
1. Select **Save**.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
