---
# required metadata

title: Maintenance operations for deployments
description: This topic explains how to perform maintenance operations for an environment on the modern infrastructure stack.
author: manado
manager: AnnBe
ms.date: 12/11/2018
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
ms.dyn365.ops.version: 8.1

---

# Maintenance operations for deployments

[!include [banner](../includes/banner.md)]

This document explains how to perform maintenance operations for a Dynamics 365 for Finance and Operations environment deployed on the [modern infrastructure stack](infrastructure-stack.md).

> [!Note] 
> This topic applies to deployments of Finance and Operations 8.1 and above.

# Restart services
You can use the restart services functionality to restart individual services that are associated with a Tier 2, Tier 3, Tier 4, or Tier 5 standard acceptance test (sandbox) environment that is deployed in a Microsoft subscription.

To restart a service, create a support ticket and provide the following details:

- **Project ID**: ID of the LCS project.
- **Environment ID**: GUID available in the URL (EnvironmentID) for the environment.
- **Service to restart**: AOS, DIXF, MR, Batch.
- **Downtime start**: Provide a start downtime in Universal Time Coordinated (UTC).
- **Downtime end**: Provide an end downtime in UTC.

> [!NOTE]
> This flow will be self-service through Lifecycle Services (LCS) in early 2019.

# Maintenance mode
Finance and Operations includes a system-wide setting that is named **Maintenance Mode**. When maintenance mode is turned on, it provides a safe way for system administrators to make system changes that might affect system functionality. For example, configuration keys can be enabled or disabled. While maintenance mode is on, only system administrators and users assigned to the Maintenance mode user role can sign in to the system. By default, maintenance mode is turned off.

To enable/disable maintenance mode, create a support ticket and provide the following details:

- **Project ID**: ID of the LCS project.
- **Environment ID**: GUID available in the URL (EnvironmentID) for the environment.
- **Start time for enabling maintenance mode**: Provide a start time in UTC for when you want to enable maintenance mode.
- **Start time for disabling maintenance mode**: Provide a start time in UTC for when you want to disable maintenance mode.

> [!NOTE]
> This flow will be self-service through Lifecycle Services (LCS) in early 2019.

# Access database
Environments deployed on the [modern infrastructure stack](infrastructure-stack.md) have Remote Desktop Access turned off. As part of implementing Finance and Operations, if you need to connect to the database on your Standard Acceptance Test environments for troubleshooting, create a support ticket and provide the following details:

- **Project ID**: ID of the LCS project.
- **Environment ID**: GUID available in the URL (EnvironmentID) for the environment.
- **Query that needs to be executed**: Query that you want to execute.

> [!NOTE]
> This flow will be self-service through Lifecycle Services (LCS) in early 2019.
