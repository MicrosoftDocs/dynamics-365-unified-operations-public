--- 
# required metadata 
 
title: Modify reporting relationships for a position
description: This procedure shows how to change the reporting relationship for an employee. 
author: twheeloc
ms.date: 06/25/2026
ms.topic: how-to 
 
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

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This procedure shows how to change the reporting relationship for an employee. Use the reporting relationship to route documents through workflow. This procedure also shows how to assign the employee to additional hierarchies. For example, an employee might be part of a project team with an informal reporting relationship to a project supervisor. You can define additional reporting relationships on the position to accommodate various project or matrix scenarios. The demo data company used to create this procedure is USMF.

1. Go to **Human resources** > **Positions** > **All positions**.
1. Use the Quick Filter to find records. For example, filter on a value of **000091** for the **Position** field.
1. In the list, select the link in the selected row.
1. Expand the **Reports to position** section.
1. Select **New** to open the drop-down dialog box.
1. In the **Reports to** field, enter or select a value.
1. Select **Create**.
1. Expand the **Relationships** section.
1. Select **Add**.
1. Select the check box on the left of the grid.
1. In the **Hierarchy name** field, enter or select a value (for example, **Project**).
1. In the **Reports to position** field, enter or select a value (for example, **000437**).
1. Select **Save**.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
