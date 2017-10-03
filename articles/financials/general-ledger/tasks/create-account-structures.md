--- 
# required metadata 
 
title: Create account structures
description: This task guide steps through creating an account structure. 
author: aprilolson
manager: AnnBe 
ms.date: 11/08/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create account structures

[!include[task guide banner](../../includes/task-guide-banner.md)]

This task guide steps through creating an account structure. The steps use demo data company USMF.

1. Go to General ledger > Chart of accounts > Structures > Configure account structures.
2. Click New to open the drop dialog.
3. In the Account structure field, type a name to describe the purpose of the account structure.
4. In the Description field, type a description to specify the purpose of the account structure.
5. Click Create.
6. Click Add segment.
7. In the Dimensions list, select the dimension to add to the account structure.
8. Click Add segment.
9. Click Add segment.
10. In the Dimensions list, select the dimension to add to the account structure.
11. Click Add segment.
12. Click Add segment.
13. In the Dimensions list, select the dimension to add to the account structure.
14. Click Add segment.
15. In the grid, select the segment to edit the allowed values.
    * For example, click in Main Account.  
16. In the Operator field, select an option, such as is between and includes.
17. In the Value field, type a value.
    * For example, 600000.  
18. In the through field, type a value.
    * For example, 699999.  
19. Click Apply.
20. In the grid, select the segment to edit the allowed values.
    * For example, Department.  
21. In the Operator field, select an option, such as is between and includes.
22. In the Value field, type a value.
    * For example, 022.  
23. In the through field, type a value.
    * For example, 031.  
24. Click Add new criteria.
25. In the Operator field, select an option, such as is between and includes.
26. In the Value field, type a value.
    * For example, 033.  
27. In the through field, type a value.
    * For example, 034.  
28. Click Apply.
29. In the grid, select the segment to edit the allowed values.
    * For example, Cost Center.  
30. In the CostCenter field, type a value.
    * For example, 007..021.  
31. Click Add.
32. In the MainAccount field, type a value.
    * For example, 600000..699999  
33. In the grid, select the segment to edit the allowed values.
    * For example, Department.  
34. In the Department field, type a value.
    * For example, 032.  
35. In the CostCenter field, type a value.
    * For example, 086.  
36. Click Validate.
37. Click Activate.
38. Click Activate.

