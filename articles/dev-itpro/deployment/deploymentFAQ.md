---
# required metadata

title: Deployment FAQ
description: [Full description that appears in the search results. Often the first paragraph of your topic.]
author: sarvanisathish
manager: AnnBe
ms.date: 12/07/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global 
# ms.search.industry: 
ms.author: sarvanis
ms.search.validFrom: 2018-12-31
ms.dyn365.ops.version: 8.1.1

---

# Deployment FAQ

[!include[banner](../includes/banner.md)]

Please refer to the known issues list if your scenario is not listed here.  

## Why do I see only application version 8.1.1 and platform update 21 when I try to deploy my sandbox environment? 

The deployment preview launches on application version 8.1.1 with platform update 21.  

## My development environment is on application version 8.1. Am I still able to move my customization to the sandbox environment? 

Yes. Application version 8.1.1 is fully backward compatible with application 8.1. 

## What is the minimum supported application and platform version? 

Application version 8.1 with platform update 20 is the minimum supported version. 

## What do I do if deployment fails? 

1. Delete the deployment.  
2. If you want to reuse the same environment name, wait 5 minutes and try again. Otherwise, retry deploying with a new name. 
3. If deployment fails again, log a Support ticket.  

> [!Note]
> Microsoft will add automatic retry logic in an upcoming release and make logs available. 

## What if my deployment fails with an “environment already exists” error? 

You may be trying to reuse the environment name of a deployment that you just deleted. Wait 5–10 minutes before retrying the deployment. 

 
