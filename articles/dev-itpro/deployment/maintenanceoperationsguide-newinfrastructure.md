---
# required metadata

title: Maintenance operations for deployments
description: This topic explains how to perform maintenance operations for an environment deployed using the self-service deployment experience.
author: manado
manager: AnnBe
ms.date: 12/14/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 24211
ms.search.region: Global
# ms.search.industry: 
ms.author: manado
ms.search.validFrom: 2018-12-31
ms.dyn365.ops.version: 8.1.1

---

# Maintenance operations for deployments

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/limited-availability.md)]

This document explains how to perform maintenance operations for a Dynamics 365 for Finance and Operations environment deployed using the [self-service deployment](infrastructure-stack.md) experience.

## Restart services
You can use the restart services functionality to restart individual services that are associated with a Tier 2, Tier 3, Tier 4, or Tier 5 standard acceptance test (sandbox) environment that is deployed in a Microsoft subscription.

To restart a service, create a support ticket and provide the following details:

- **Project ID**: ID of the LCS project.
- **Environment ID**: GUID available in the URL (EnvironmentID) for the environment.
- **Service to restart**: AOS, DIXF, MR, Batch.
- **Downtime start**: Provide a start downtime in Universal Time Coordinated (UTC).
- **Downtime end**: Provide an end downtime in UTC.

> [!NOTE]
> This functionality will be self-service through Lifecycle Services (LCS) in early 2019.

## Maintenance mode
Finance and Operations includes a system-wide setting that is named [Maintenance mode](../sysadmin/maintenance-mode.md). When maintenance mode is turned on, it provides a safe way for system administrators to make system changes that might affect system functionality. For example, configuration keys can be enabled or disabled. While maintenance mode is on, only system administrators and users assigned to the Maintenance mode user role can sign in to the system. By default, maintenance mode is turned off.

To enable/disable maintenance mode, create a support ticket and provide the following details:

- **Project ID**: ID of the LCS project.
- **Environment ID**: GUID available in the URL (EnvironmentID) for the environment.
- **Start time for enabling maintenance mode**: Provide a start time in UTC for when you want to enable maintenance mode.
- **Start time for disabling maintenance mode**: Provide a start time in UTC for when you want to disable maintenance mode.

> [!NOTE]
> This functionality will be self-service through Lifecycle Services (LCS) in early 2019.

## Access database
Environments deployed using the [self-service deployment](infrastructure-stack.md) experience have Remote Desktop Access turned off. As part of implementing Finance and Operations, if you need to connect to the database on your Standard Acceptance Test environments for troubleshooting, create a support ticket and provide the following details:

- **Project ID**: ID of the LCS project.
- **Environment ID**: GUID available in the URL (EnvironmentID) for the environment.
- **Query that needs to be executed**: Query that you want to execute.

> [!NOTE]
> This functionality will be self-service through Lifecycle Services (LCS) in early 2019. The access to the Azure SQL database will not be persistent; however, you can request access to the database directly through the Lifecycle Services environment details page.   The process of getting access will be as follows:
>- Enable access to Azure SQL through LCS by whitelisting the IP address of the machine that you will use to connect to the Azure SQL database using SQL Management Studio. 
>- After this is done, you can request access to see the database credentials through LCS by entering a reason for requesting access. 
>- As soon as you submit the request, it gets **auto-approved**. You will be able to see the database access credentials within a few minutes, on the LCS environment details page. 
>- Note that the credentials are valid for 8 hours and will expire after that duration. After 8 hours the access expires and you will need to request access again. 
> Additional information on how to perform the above steps  will be published as soon as this feature is made available in January, through Lifecycle Services.

