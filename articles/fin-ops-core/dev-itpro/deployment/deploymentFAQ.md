---
title: Self-service deployment FAQ
description: This frequently asked questions article answers to some frequently asked questions about self-service deployment.
author: rashmansur
ms.author: rashmim
ms.topic: faq
ms.date: 04/02/2026
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
audience: IT Pro
# ms.devlang: 
ms.search.region: Global 
ms.search.validFrom: 2018-12-31
# ms.search.form:  [Operations AOT form name to tie this article to]
ms.dyn365.ops.version: 8.1.1
---

# Self-service deployment FAQ

[!include[banner](../includes/banner.md)]

This article provides answers to some frequently asked questions about [self-service deployment](infrastructure-stack.md). If your scenario isn't listed here, see the [known issues](known-issues-new-deployment-experience.md).  

## Access the Azure SQL database

You can access the Microsoft Azure SQL database by following these steps:

1. From Microsoft Dynamics Lifecycle Services, add a safe list of the IP address of the machine that you use to connect to the Azure SQL database by using SQL Management Studio.
1. Use Lifecycle Services to request access to see the database credentials. You must provide a reason for requesting access.  

As soon as you submit the request, it's automatically approved. Within a minute or two, you can see the database access credentials on the Lifecycle Services environment details page. Use the credentials to connect to the SQL database.

> [!NOTE]
> The credentials are valid for eight hours, and then they expire. After the credentials expire, you must request access again.

### What are the outbound IP ranges for my finance and operations environment?

For any of your external components that have special handling for the outbound IP addresses of requests originating from the AOS, such as a firewall, you can find the outbound IP addresses by using the Service Tag Discovery API or using the downloadable JSON files. For example, an outbound IP address might be explicitly included in a firewall outside your AOS, or an external service might have an allow list that contains the outbound IP address for your AOS.

The inbound IP address to the AOS is dynamic. This address can change over time as infrastructure changes occur.

> [!NOTE]
> The outbound IP address from the AOS is an IP address from the listed ranges based on the Azure region of your deployment. The specific outbound IP address might vary across outbound requests, even from within the same session.

Infrastructure hosting your Microsoft-managed environments is registered as part of the `PowerPlatformPlex` Service Tag. For more information, see the [Service Tag Documentation](/azure/virtual-network/service-tags-overview), such as how to get the specific IP address ranges for components that don't support Service Tags.

> [!NOTE]
> Outbound requests might originate from multiple regions within a geo in disaster recovery scenarios that require regional failover within the geography.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
