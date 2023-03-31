--- 
# required metadata 
 
title: Modify reporting relationships for a position
description: This procedure shows how to change the reporting relationship for an employee. 
author: twheeloc
ms.date: 10/28/2021
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: HcmPosition, HcmPositionReportsToDialog, HcmPositionLookup, HcmPersonnelManagementWorkspace
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
# Modify reporting relationships for a position


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]



This procedure shows how to change the reporting relationship for an employee. The reporting relationship can be used for routing documents through workflow. The procedure also shows how to assign the employee to additional hierarchies. For example, an employee might be a part of a project team with an informal reporting relationship to a project supervisor. Additional reporting relationships can be defined on the position to accommodate various project or matrix scenarios. The demo data company used to create this procedure is USMF.

1. Go to **Human resources** \> **Positions** \> **Positions**.
2. Use the Quick Filter to find records. For example, filter on a value of **000091** for the **Position** field.
3. In the list, select the link in the selected row.
4. Expand the **Reports to position** section.
5. Select **New** to open the drop-down dialog box.
6. In the **Reports to** field, enter or select a value.
7. Select **Create**.
8. Expand the **Relationships** section.
9. Select **Add**.
10. Select the checkbox on the left of the grid.
11. In the **Hierarchy name** field, enter or select a value (for example, **Project**).
12. In the **Reports to position** field, enter or select a value (for example, **000437**).
13. Select **Save**.



[!INCLUDE[footer-include](../includes/footer-banner.md)]
