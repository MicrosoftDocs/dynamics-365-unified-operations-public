---
# required metadata

title: Self-service deployment FAQ
description: This topic provides answers to some frequently asked questions about self-service deployment.
author: rashmansur
ms.date: 11/30/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
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

1. From LCS, add a safe list of the IP address of the machine that you will use to connect to the Azure SQL database using SQL Management Studio.
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

## What regions are supported on self-service in North America?
We currently only support the following regions in North America.

- East US
- West US
- Central US
  > [!NOTE]
  > Central US is no longer being provided as an option for self-service migrations beginning April 1, 2021.

For more information about region availability, see [International availability of Dynamics 365](https://www.microsoft.com/trustcenter/privacy/dynamics365-operations-location).

### My environments are currently in the regions that are no longer supported. How will this change affect me?
Projects that have been onboarded on or after August 1, 2020 are no longer supported in the following regions:

-	East US2
-	West US2
-	West Central US
-	North Central US
-	South Central US

> [!NOTE]
> This will not affect any environments that have their data stored in the deprecated regions before August 2020. There is a transition plan to move customers in the deprecated regions into other regions. For a list of the latest supported regions, see [International availability of Dynamics 365](https://www.microsoft.com/trustcenter/privacy/dynamics365-operations-location).

- With all self-service migrations, we are changing the outbound IP addresses in regions where your environments are hosted. New outbound IP addresses are available, so you must add them before your upcoming self-service migrations. For more information about IP addresses, see [For my Microsoft-managed environments, I have external components that have dependencies on an explicit outbound IP safe list. How can I ensure my service is not impacted after the move to self-service deployment?](deploymentFAQ.md#for-my-microsoft-managed-environments-i-have-external-components-that-have-dependencies-on-an-explicit-outbound-ip-safe-list-how-can-i-ensure-my-service-is-not-impacted-after-the-move-to-self-service-deployment).
- If you have any integrations or other dependencies that are latency-driven and have questions regarding how the change in regions will impact that, please contact [Microsoft Support](../lifecycle-services/lcs-support.md).
- Central US is no longer an option for self-service migrations. If a customer plans to leverage dual-write functionality, virtual entities, or any Finance and Operations apps add-ins that have dependencies on Dataverse, keep in mind that Dataverse is not supported in Central US. There are currently no plans to support Dataverse in Central US in the foreseeable future. For continued functionality of features in a supported region, we will plan to move your environment to East US or West US instead of Central US.
- If you have a project which has a few environments using self-service capabilities in Central US and others in North Central, South Central or West Central, the rest of the IaaS environments can still be moved to East or West US as part of migrations. For the environments already on Service Fabric and in Central US, please contact Microsoft Support to get them moved to East/West US based on your preference.
-	Please review all the Azure resources in your current region and assess if they need to be co-located to the new region in preparation for the upcoming changes as part of migrations.
- If you have questions about data movement related to cross-region migrations, see [The source and target are on different infrastructure (Microsoft-managed vs. self-Service)](../database/database-pitr-prod-sandbox.md#the-source-and-target-are-on-different-infrastructure-microsoft-managed-vs-self-service).

## For my Microsoft-managed environments, I have external components that have dependencies on an explicit outbound IP safe list. How can I ensure my service is not impacted after the move to self-service deployment?
With self-service migrations, we are changing the outbound IP addresses in regions where your environments are hosted. New outbound IP addresses are available so you can add them in preparation for the upcoming self-service migrations or post migrations.

* If none of your external components have dependencies on an explicit inclusion list of IPs or special handling of outbound IP addresses for routing or firewall, no action is required.
* If any of your external components have special handling for the outbound IP addresses to communicate to the AOS, add the new outbound IP addresses where the existing ones appear. Don’t replace the existing IP addresses. You can find the new outbound IP addresses in the following list. For example, an outbound IP address may be explicitly included in a firewall outside your AOS, or an external service may have an allowed list that contains the outbound IP address for your AOS.

The inbound IP address to the AOS is dynamic. This can, and will, change over time as infrastructure changes occur.

> [!NOTE]
> The outbound IP address from the AOS will be an IP address from the listed ranges based on the Azure region of your deployment. The specific outbound IP address may vary across outbound requests, even from within the same session.

| Geography | Azure region | IP prefixes<sup>1</sup> |
|---|---|---|
| Asia Pacific | East Asia | 52.229.231.64/26 |
| Asia Pacific | Southeast Asia | 20.44.247.0/26 |
| Australia | Australia East | 20.40.190.0/26 |
| Australia | Australia Southeast | 20.40.165.192/26 |
| Azure Government | US Gov Texas<sup>2</sup> | 52.243.163.224/28 |
| Azure Government | US Gov Virginia | 52.227.253.160/28 |
| Brazil | Brazil South | 191.234.130.0/26 |
| Canada | Canada Central | 20.151.60.0/26 |
| Canada | Canada East | 52.155.27.128/26 |
| China | China East 2 | 52.131.245.128/26 |
| China | China North 2 | 52.130.157.64/26 |
| Europe | North Europe | 52.155.160.192/26 |
| Europe | West Europe | 20.61.88.128/26<br/>51.105.159.192/26 |
| France | France Central | 51.138.205.48/28 |
| France | France South<sup>2</sup> | 52.136.140.96/28 |
| India | India Cental | 20.193.248.192/26 |
| India | India South | 20.40.5.0/26 |
| Japan | Japan East | 20.48.77.192/26 |
| Japan | Japan West | 20.39.179.192/26 |
| South Africa | South Africa North | 102.133.204.16/28 |
| South Africa | South Africa West<sup>2</sup> | 102.133.78.96/28 |
| Switzerland | Switzerland North | 51.103.164.128/28 |
| Switzerland | Switzerland West<sup>2</sup> | 51.107.230.128/28 |
| United Arab Emirates | UAE North | 20.203.41.96/28 |
| United Kingdom | UK South | 51.11.26.192/26 |
| United Kingdom | UK West | 51.137.139.0/26 |
| United States | Central US | 13.86.98.128/26 |
| United States | East US | 52.255.218.64/26 |
| United States | West US | 52.250.195.128/26 |

<sup>1</sup> For Azure regions with multiple IP prefixes, such as West Europe, outbound requests will utilize IP addresses from any of the listed IP prefixes.

<sup>2</sup> Denotes a BCDR-only Azure region. Outbound requests will only originate from this region in disaster recovery scenarios that require regional failover within the geography.

## What does the downtime look like for self-service migrations?
Self-service migration for any environment takes three hours of 100% downtime, with a six-hour pre-migration window leading up to the actual migration downtime of 3 hours. The environment will be available with limited servicing capabilities during the six-hour pre-migration window, but will be completely unavailable in the three-hour migration window. We recommend that customers do not schedule any servicing activity, like package deployment, during the pre-migration window because it will interfere with migrations and will trigger a migration cancellation.

## Is there a potential impact on the environment's certificates?

Yes, if you are migrating from the previous non self-service deployment, your environment’s certificate may be renewed due to infrastructure differences. Determine if there is any dependence on the certificates in your solution/integration and perform the needed actions after the migration.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
