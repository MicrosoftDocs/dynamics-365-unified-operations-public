--- 
# required metadata 
 
title: Create account structures
description: This procedure walks through creating an account structure. 
author: aprilolson
ms.date: 03/28/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: DimensionConfigureAccountStructure, DimensionCreateAccountStructure, DimensionHierarchyAddLevel, DimensionHierarchyConstraintActivate   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create account structures

[!include [banner](../../includes/banner.md)]

This procedure walks through creating an account structure. The steps use demo data company USMF.

1. Go to **General ledger > Chart of accounts > Structures > Configure account structures**.
2. On the **Action pane**, click **New** to open the drop dialog.
3. In the **Account structure** field, type a name to describe the purpose of the account structure.
4. In the **Description** field, type a description to specify the purpose of the account structure.
5. Click **Create**.
6. In the **Segments and allowed values**, click **Add segment**.
7. In the dimensions list, select the dimension to add to the account structure.
8. At the end of the list, click **Add segment**.
9. Repeat step 6 to 9 as needed.
10. In the **Allowed value details** section, select the segment to edit the allowed values.
    For example, click the **Main Account** field.  
11. In the **Operator** field, select an option, such as is between and includes.
12. In the **Value** field, type a value. For example, 600000.  
13. In the **through** field, type a value. For example, 699999.  
14. In the **Allowed value details** section, click **Apply**.
15. Repeat step 10 to 15 as needed.  
16. In the **Allowed value details** section, click **Add new criteria**.
17. In the **Operator** field, select an option, such as is between and includes.
18. In the **Value** field, type a value. For example, 033.  
19. In the **through** field, type a value. For example, 034.  
20. Click **Apply**.
21. In the grid, select the segment to edit the allowed values. For example, Cost Center.  
22. In the **CostCenter** field, type a value. For example, 007..021.  
23. In the **Segments and allowed values**, click **Add**.
24. In the **MainAccount** field, type a value. For example, 600000..699999  
25. In the grid, select the segment to edit the allowed values. For example, Department.  
26. In the **Department** field, type a value. For example, 032.  
27. In the **CostCenter** field, type a value. For example, 086.  
28. On the **Action pane**, click **Validate**.
29. On the **Action pane**, click **Activate**.
30. Click **Activate**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
