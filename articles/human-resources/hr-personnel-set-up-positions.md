--- 
# required metadata 
 
title: Set up positions
description: This article describes how positions are an important element of the lower level of an organization hierarchy. 
author: twheeloc
ms.date: 10/28/2021
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
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


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]



Positions are an important element of the lower level of an organization hierarchy. A position is an individual instance of a job. For example, the position, "Sales manager (East)," is one of the positions that is associated with the job, "Sales manager." A position exists in a department and may have only one worker associated with it. In this task we will walk through the steps required to create a position. This procedure is intended for Human Resources Specialists.

1. Select **Workforce management**.
2. Select **Open positions**.
3. Select **New** to open the drop-down dialog box.
4. In the **Job** field, enter or select a value.

    The **Job description**, **Title**, and **Full-time equivalent employment factor** fields are automatically copied from the selected job into the position.

5. Select **Create position**.
6. In the **Department** field, enter or select a value.
7. In the **Position type** field, enter or select a value.
8. In the **Compensation region** field, enter or select a value.

    The **Compensation region** field determines the compensation eligibility rules and fixed increase budgets that apply to an employee in that position.

9. In the **Available for assignment** field, enter a date and time.
10. Expand the **Position duration** section.

    The position duration is entered by default, based on activation and retirement dates that were entered earlier.

11. Expand the **Reports to position** section.

    When you assign a worker to a position that reports to another position, you create a direct reporting relationship between the workers who are assigned to the two positions.

12. Select **New to** open the drop-down dialog box.
13. In the **Reports to** field, enter or select a value.
14. Select **Create**.
15. Expand the **Worker assignment** section.
16. Expand the **Relationships** section.

    If your organization uses a matrix hierarchy or another custom hierarchy, you can set up position hierarchy types and then add reporting relationships to positions for each hierarchy type that you set up.

17. Select **Add**.
18. In the list, mark the selected row.
19. In the **Hierarchy name** field, enter or select a value.
20. In the **Reports to position** field, enter or select a value.
21. Expand the **Payroll** section.
22. In the **Pay cycle** field, enter or select a value.
23. In the **Paid by field**, enter or select a value.
24. In the **Annual regular hours** field, enter a number.

    The value that you enter is the number of regularly paid hours that the worker in this position is expected to work each year.

25. Expand the **Labor union** section.
26. Collapse the **Labor union** section.
27. Expand the **Financial dimensions** section.
28. In the **Distribution template** field, enter or select a value.
29. In the **Department** field, enter or select a value.
30. Select **Save**.



[!INCLUDE[footer-include](../includes/footer-banner.md)]
