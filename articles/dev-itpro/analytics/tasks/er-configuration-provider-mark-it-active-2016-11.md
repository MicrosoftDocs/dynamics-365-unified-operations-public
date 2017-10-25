--- 
# required metadata 
 
title: Create a configuration providand mark it as active for electronic reporting (ER)
description: The following steps explain how a user assigned to the System Administrator or Electronic Reporting Developer role can create a configuration provider for Electronic reporting (ER). 
author: NickSelin
manager: AnnBe 
ms.date: 10/18/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a configuration provider and mark it as active for electronic reporting (ER)

[!include[task guide banner](../../includes/task-guide-banner.md)]

The following steps explain how a user assigned to the System Administrator or Electronic Reporting Developer role can create a configuration provider for Electronic reporting (ER). Each ER configuration will refer to the provider as the author of the configuration. In this example, you will create a configuration provider for sample company, Litware, Inc. These steps can be performed in any company as ER configuration providers are shared among all companies.


## Create a provider
1. Go to Organization administration > Workspaces > Electronic reporting.
2. Click Configuration providers.
3. Click New.
    * A provider record has a unique name and URL. Review the content of this page and skip this procedure if a record for Litware, Inc. (http://www.litware.com) already exists.  
4. In the Name field, type 'Litware, Inc.'.
    * Litware, Inc.  
5. In the Internet address field, type 'http://www.litware.com'.
    * http://www.litware.com  
6. Click Save.
7. Close the page.

## Select as an active provider
1. Select the Litware, Inc. provider.
2. Click Set active.

