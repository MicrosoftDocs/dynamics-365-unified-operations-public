--- 
# required metadata 
 
title: Create and assign advanced rule structures
description: This task guide steps through creating and assigning an advanced rule structure to an account structure. 
author: aprilolson
manager: AnnBe 
ms.date: 11/10/2016
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
# Create and assign advanced rule structures

[!include[task guide banner](../../includes/task-guide-banner.md)]

This task guide steps through creating and assigning an advanced rule structure to an account structure. This guide uses the USMF demo company.


## Create an advanced rule structure
1. Go to General ledger > Chart of accounts > Structures > Advanced rule structures.
2. Click New to open the drop dialog.
3. In the Advanced rule structure field, type a name to descritbe the rule structure.
4. In the Description field, type a value to describe the structure.
5. Click OK.
6. Click Add segment.
7. In the list of segments, select a financial dimension.
    * For example, Store.  
8. Click Add segment.
9. In the list, click the link of the advanced rule structure to view it.
10. Click Activate.
11. Click Activate.

## Apply an advanced rule structure to an account structure
1. Close the form.
2. Close the page.
3. Go to General ledger > Chart of accounts > Structures > Configure account structures.
4. In the list, find and select the account structure you want to apply the advanced rule to.
5. Click the name of the account structure to open it.
6. Click Edit.
    * You can also click Advanced rules and you will be prompted to put the account structure in Draft mode.  
7. Click Advanced rules.
8. Click New to open the drop dialog.
9. In the Advanced rule field, type a value.
10. In the Name field, type a value.
11. Click Create.
12. Click Add new criteria.
13. In the Where field, select main account or a financial dimension.
14. In the Operator field, select an option, such as is between and includes.
15. In the Value field, type a value.
16. In the through field, type a value.
17. Click Add to open the drop dialog.
18. In the list, find the advanced rule structure you want to use when the criteria you entered is met.
19. Click Add.
20. Close the page.
21. Click Activate.
22. Click Activate.

