---
# required metadata

title: Self-service deployment FAQ
description: This article provides answers to some frequently asked questions about self-service deployment.
author: rashmansur
ms.date: 11/30/2021
ms.topic: faq
ms.custom: 
  - bap-template
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this article to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: johnmichalak
ms.search.region: Global 
# ms.search.industry: 
ms.author: rashmim
ms.search.validFrom: 2018-12-31
ms.dyn365.ops.version: 8.1.1

---

# Self-service deployment FAQ

[!include[banner](../includes/banner.md)]

This article provides answers to some frequently asked questions about [self-service deployment](infrastructure-stack.md). Refer to the [known issues](known-issues-new-deployment-experience.md) list if your scenario isn't listed here.  

## What if my deployment fails with an “environment already exists” error? 

You may be trying to reuse the environment name of a deployment that you just deleted. Wait 5–10 minutes before retrying the deployment. 

### Access the Azure SQL database
You can access the Microsoft Azure SQL database by following these steps.

1. From LCS, add a safe list of the IP address of the machine that you use to connect to the Azure SQL database using SQL Management Studio.
2. Use LCS to request access to see the database credentials. You must provide a reason for requesting access. 

As soon as you submit the request, it's automatically approved. Within a minute or two, you are able to see the database access credentials on the LCS environment details page. You can use the credentials to connect to the SQL database.

> [!NOTE]
> The credentials are valid for eight hours, and then they expire. After the credentials expire, you have to request access again. 

### Access log files
You can view and download all log files from the **Activity** tab on the LCS environment monitoring page.

### Access self-service logs
All logs that are related to self-service operations that are performed on the environment through LCS are available for download from LCS. These self-service operations include deployment, servicing, and database movement. You can download the log folders from the LCS environment history page.

## For my Microsoft-managed environments, I have external components that have dependencies on an explicit outbound IP safe list. How can I ensure my service is not impacted after the move to self-service deployment?
* If none of your external components have dependencies on an explicit inclusion list of IPs or special handling of outbound IP addresses for routing or firewall, no action is required.
* If any of your external components have special handling for the outbound IP addresses to communicate to the AOS, add the new outbound IP addresses where the existing ones appear. Don’t replace the existing IP addresses. You can find the new outbound IP addresses by using the Service Tag Discovery API or using the downloadable JSON files. For example, an outbound IP address may be explicitly included in a firewall outside your AOS, or an external service may have an allowed list that contains the outbound IP address for your AOS.

The inbound IP address to the AOS is dynamic. This can, and will, change over time as infrastructure changes occur.

> [!NOTE]
> The outbound IP address from the AOS is an IP address from the listed ranges based on the Azure region of your deployment. The specific outbound IP address may vary across outbound requests, even from within the same session.

Infrastructure hosting your Microsoft-managed environments is registered as part of the `PowerPlatformPlex` Service Tag. For more information, see the [Service Tag Documentation](/azure/virtual-network/service-tags-overview), such as how to get the specific IP address ranges for components that don't support Service Tags.

> [!NOTE]
> Outbound requests may originate from multiple regions within a geo in disaster recovery scenarios that require regional failover within the geography.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

