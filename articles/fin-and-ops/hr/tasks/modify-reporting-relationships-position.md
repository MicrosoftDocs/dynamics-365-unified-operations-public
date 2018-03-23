--- 
# required metadata 
 
title: Modify reporting relationships for a position
description: This procedure shows how to change the reporting relationship for an employee. 
author: ShielaSogge
manager: AnnBe 
ms.date: 03/02/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-365-talent 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: rschloma
ms.search.scope: Operations, Talent 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: shielas
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Modify reporting relationships for a position

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows how to change the reporting relationship for an employee. The reporting relationship can be used for routing documents through workflow. The procedure also shows how to assign the employee to additional hierarchies. For example, an employee might be a part of a project team with an informal reporting relationship to a project supervisor. Additional reporting relationships can be defined on the position to accommodate various project or matrix scenarios. The demo data company used to create this procedure is USMF.

1. Go to Human resources > Positions > Positions.
2. Use the Quick Filter to find records. For example, filter on the Position field with a value of '000091'.
3. In the list, click the link in the selected row.
4. Expand the Reports to position section.
5. Click New to open the drop dialog.
6. In the Reports to field, enter or select a value.
7. Click Create.
8. Expand the Relationships section.
9. Click Add.
10. Select the check box on the left of the grid.
11. In the Hierarchy name field, enter or select a value.
    * Example: Project  
12. In the Reports to position field, enter or select a value.  Example:  000437
13. Click Save.

