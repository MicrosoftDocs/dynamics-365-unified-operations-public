--- 
# required metadata 
 
title: Import users in bulk
description: This procedure can be used by system administrators to import a large number of users from Azure Active Directory. 
author: maertenm
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
ms.author: maertenm
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Import users in bulk

[!include [banner](../../includes/banner.md)]

This procedure can be used by system administrators to import a large number of users from Azure Active Directory.


## Run as a batch job
1. Go to System administration > Users > Users.
2. Click Batch import.
3. Expand the Run in the background section.
4. Select Yes in the Batch processing field.
5. In the Task description field, type a value.
6. In the Batch group field, enter or select a value.
    * This is an optional step.  
7. Select Yes in the Private field.
    * This is an optional step.  
8. Select Yes in the Critical Job field.
    * This is an optional step.  
9. In the Monitoring category field, select an option.
10. Click OK.

## Run in a sandbox environment
1. Click Batch import.
2. Click OK.

