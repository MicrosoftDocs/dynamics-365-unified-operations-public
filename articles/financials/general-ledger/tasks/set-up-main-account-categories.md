--- 
# required metadata 
 
title: Set up main account categories
description: Main account categories are used for the default reports in financial reporting and in Power BI. 
author: aprilolson
manager: AnnBe 
ms.date: 11/14/2016
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
# Set up main account categories

[!include[task guide banner](../../includes/task-guide-banner.md)]

Main account categories are used for the default reports in financial reporting and in Power BI. Main account categories that are created by default can be renamed but not deleted. Additional account categories can be created and used for reporting and analysis purposes. This task uses the USMF demo company.


## Create a main account category
1. Go to General ledger > Chart of accounts > Accounts > Main account categories.
2. Click New.
3. In the Main account category field, enter a unique name.
4. In the Description field, enter a description for the main account category.
5. In the Main account type field, select the main account type that will be linked to the category.

## Link main accounts to account category
1. Click Link main accounts.
2. In the list, select the main accounts to assign to the main account category.
    * Assigning main accounts to a main account category will aggregate the balances of the accounts when that category is used for financial reporting and analysis.  
3. Select or clear the Linked option to choose the main accounts.
4. Click OK.
5. Click Yes.

