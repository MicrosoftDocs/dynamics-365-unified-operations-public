---
# required metadata

title: Deployment FAQ
description: This topic provides answers to some frequently asked questions about self-service deployment.
author: sarvanisathish
manager: AnnBe
ms.date: 12/14/2018
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

# Self-service deployment FAQ

[!include[banner](../includes/banner.md)]
[!include [banner](../includes/limited-availability.md)]

This topic provides answers to some frequently asked questions about [self-service deployment](infrastructure-stack.md). Refer to the [known issues](known-issues-new-deployment-experience.md) list if your scenario is not listed here.  

## Why do I see only application version 8.1.1 and Platform update 21 and above when I try to deploy my sandbox environment using self-service deployment? 

Currently, self-service deployment supports only application version 8.1.1 with Platform update 21 and above.  

## My development environment is on application version 8.1. Am I still able to move my customization to the sandbox environment? 

Yes. Application version 8.1.1 is fully backward compatible with application 8.1. 

## What is the minimum supported application and platform version when trying to use the self-service deployment? 

Application version 8.1 with Platform update 20 is the minimum supported version. 

## What do I do if deployment fails? 

1. Delete the deployment.  
2. If you want to reuse the same environment name, wait 5 minutes and try again. Otherwise, retry deploying with a new name. 
3. If deployment fails again, log a Support ticket.  

> [!Note]
> Microsoft will add automatic retry logic in an upcoming release and make logs available. 

## What if my deployment fails with an “environment already exists” error? 

You may be trying to reuse the environment name of a deployment that you just deleted. Wait 5–10 minutes before retrying the deployment. 

## I do not have Remote desktop access to my Sandbox environment. How do I perform the critical actions that need Remote desktop access today?

While you will no longer have remote desktop access, you will be able to continue operating your Tier 2+ sandbox environments, as we are providing self-service capabilities and tools to perform the common actions as listed below.

### Access Azure SQL database
You may access the SQL Azure database by following the below steps.
1. Whitelist the IP address of the machine that you will use to connect to the Azure SQL database, using SQL management studio, from LCS.  
2. Request access to **see** the database credentials through LCS JIT. You will need to provide a reason for requesting access. 
3. As soon as you submit the request, it gets **auto-approved**. Within a minute or two, you will be able to **see the database access credentials** in the LCS environment details page. 

You may use the credentials to connect to the Azure SQL database. **Note:** The credentials are valid for 8 hours and will expire after that duration. On expiration, you will need to request access again. 

### Access F&O Logs
You are able to view and download all F&O logs on the activity tab in the LCS environment monitoring page.

### Use perfmon tools
While you will no longer be able to remote desktop in and use perfmon.exe to diagnose performance issues, you will be able to monitor critical health metrics on CPU and memory consumption through LCS. In addition, you will have the option to run pre-defined queries on demand and execute pre-defined actions to mitigate performance issues on your Tier 2+ environments. 

### Access Self-service Logs
All logs related to any self-service operations on the environment through LCS, such as deployment, servicing, database movement, are available for download from LCS. You may download the log folders from the LCS environment history page.

### Set Maintenance mode on/off
You will be able to turn-on and off maintenance mode on your environment through a self-service action on LCS that will be available with the January 2019 release. 

### Restart services
You will able to restart services through a self-service action on LCS that will be available with the January 2019 release.

### Configure Regression Suite automation tool
We are working on tooling by which you will no longer need Remote desktop access to update the certificate thumbprints in the wif.config file. This is scheduled for release in February 2019. If you need to use the Regression suite automation tool before then, please log a support request.

## I need to perform a critical action listed above and the self-service feature is not yet available. How do I get help?

Please log a support ticket and we will help you perform the necessary action on your environment.

## I do not have Remote desktop access to my Sandbox environment. And I do not see my critical action listed above. How do I get help?

If you do not see your critical action in the list above, do comment below or log a documentation bug and we will address your requirement.



 
