--- 
# required metadata 
 
title: Import users from Azure Active Directory
description: This procedure can be used by system administrators to manually import selected users or to import a large number of users from Azure Active Directory. 
author: peakerbl
manager: AnnBe 
ms.date: 07/07/2017
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: sericks
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: peakerbl
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Import users from Azure Active Directory

[!include [banner](../../includes/banner.md)]

This procedure can be used by system administrators to imported selected users from Azure Active Directory.

1. User will be imported with the current sesssion Compnay as thier default compnay. Change current company is applicable before importing users.
2. Go to System administration > Users > Users.
3. Click Import users.
4. Select the user that shouls be imported and Select Import users

After import is completed it will be required to assing roles to users.

# Import users in bulk

[!include [banner](../../includes/banner.md)]

This procedure can be used by system administrators to import a large number of users from Azure Active Directory.
Note that it is not possible to select users when using the Batch import option.


## Run the import as a batch job
1  User will be imported with the current sesssion Compnay as thier default compnay. Change current company is applicable before importing users.
2. Go to System administration > Users > Users.
3. Click Batch import.
4. Expand the Run in the background section.
4. Select Yes in the Batch processing field.
6. In the Batch group field, enter or select a value.
    * This is an optional step.  
7. Select Yes in the Private field.
    * This is an optional step.  
8. Select Yes in the Critical Job field.
    * This is an optional step.  
9. In the Monitoring category field, select an option.
10. Click OK.

After import is completed, it will be required to assing roles to users.

## Run in a sandbox environment
1. Click Batch import.
2. Click OK.

