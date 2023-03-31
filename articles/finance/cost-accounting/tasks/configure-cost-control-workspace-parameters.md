--- 
# required metadata 
 
title: Configure cost control workspace parameters
description: Use this procedure to configure the Cost control workspace so that managers at various levels in an organization can gain insight into their cost objects, such as cost centers and product groups. 
author: twheeloc
ms.date: 03/27/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: CAMCostControlWorkspaceConfigurationPerUser
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Configure cost control workspace parameters

[!include [banner](../../includes/banner.md)]

Use this procedure to configure the Cost control workspace so that managers at various levels in an organization can gain insight into their cost objects, such as cost centers and product groups. The USP2 demo company was used to create this recording.

1. Go to **Cost accounting > Setup > Cost control workspace configuration**.
2. Click **New**.
3. In the **Name** field, type a value.
4. In the **Description** field, type a value.
5. Select **Yes** in the **Published** field.
    * If you set this option to **Yes**, users who are assigned one of these roles can see the report in the **Cost control workspace**: cost accounting manager, cost accountant, cost accountant clerk, or cost object controller. If you set this option to **No**, only users who are assigned one of these roles can see the report in the **Cost control workspace**: cost accounting manager, cost accountant, or cost accountant clerk.  
6. Expand the **Data filtering** section.
7. In the **Cost control unit** field, enter or select a value.
8. In the **Budget original version** field, enter or select a value.
9. In the **Cost element dimension hierarchy** field, enter or select a value.
10. In the **Cost object dimension hierarchy** field, enter or select a value.
11. Expand the **Assign calculation records** section.
12. Click **New**.
13. In the list, mark the selected row.
14. In the **Fiscal calendar period** field, enter or select a value.
15. In the **Actual version** field, enter or select a value.
16. Expand the **Fiscal periods per column** section.
17. Select **Yes** in the **Current period** field.
18. Expand the **Columns** to display for costs section.
19. Select **Yes** in the **Fixed cost** field.
20. Select **Yes** in the **Variable cost** field.
21. Select **Yes** in the **Total cost** field.
22. Click **Save**.
23. Close the page.
24. Go to **Cost accounting > Workspaces > Cost control**.
25. Select a statement to see fixed, variable, total, and unclassified costs for the selected fiscal periods.
26. In the **Fiscal calendar period** field, enter or select a value.
27. In the **Cost object dimension hierarchy node** field, enter or select a value.
    * After you've selected a **Cost object dimension hierarchy**, expand the **Cost element dimension hierarchy** to see the desired cost values. For example, you can expand the hierarchy to Manufacturing overhead to see the value.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
