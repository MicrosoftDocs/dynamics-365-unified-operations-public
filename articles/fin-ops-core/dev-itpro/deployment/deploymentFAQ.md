---
# required metadata

title: Self-service deployment FAQ
description: This topic provides answers to some frequently asked questions about self-service deployment.
author: rashmansur
manager: AnnBe
ms.date: 09/20/2019
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
ms.author: rashmim
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

## I don't have Remote Desktop access to my sandbox environment. How do I perform critical actions that require Remote Desktop access today?

Although you will no longer have Microsoft Remote Desktop access, you can continue to operate your Tier 2+ sandbox environments, because Microsoft is providing self-service capabilities and tools that you can use to perform the common critical actions that are described here.

### Access the Azure SQL database
You can access the Microsoft Azure SQL database by following these steps.

1. From LCS, whitelist the IP address of the machine that you will use to connect to the Azure SQL database using SQL Management Studio.
2. Use LCS to request access to see the database credentials. You must provide a reason for requesting access. 

As soon as you submit the request, it's automatically approved. Within a minute or two, you will be able to see the database access credentials on the LCS environment details page. You can use the credentials to connect to the SQL database.

> [!NOTE]
> The credentials are valid for eight hours, and then they will expire. After the credentials expire, you will have to request access again. 

### Access log files
You can view and download all log files from the **Activity** tab on the LCS environment monitoring page.

### Use perfmon tools
Although you can no longer use Remote Desktop and then use perfmon.exe to diagnose performance issues, you can monitor critical health metrics for CPU and memory consumption through LCS. In addition, you can run predefined queries on demand, and you can run predefined actions to mitigate performance issues on your Tier 2+ environments. 

### Access self-service logs
All logs that are related to self-service operations that are performed on the environment through LCS are available for download from LCS. These self-service operations include deployment, servicing, and database movement. You can download the log folders from the LCS environment history page.

### Turn Maintenance mode on/off
Starting in the January 2019 release, you will be able to turn Maintenance mode in your environment on and off through a self-service action in LCS.

### Restart services
Starting in the January 2019 release, you will able to restart services through a self-service action in LCS.

### Configure the Regression suite automation tool
Microsoft is working on tooling that will let you update certificate thumbprints in the wif.config file without having to use Remote Desktop. This tooling is scheduled for release in February 2019. If you must use the Regression suite automation tool before then, log a support request.

## I must perform one of the critical actions that are listed earlier in this topic, but the self-service feature isn't yet available. How do I get help?

Log a support ticket, and Microsoft will help you perform the action on your environment.

## I don't have Remote Desktop access to my sandbox environment, and the critical action that I must perform isn't listed in this topic. How do I get help?

If your critical action isn't listed earlier in this topic, add a comment to this topic or log a documentation bug, and Microsoft will address your requirement.
