---
# required metadata

title: Maintenance operations for deployments
description: This topic explains how to perform maintenance operations for an environment deployed using the self-service deployment experience.
author: manado
manager: AnnBe
ms.date: 02/21/2019
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

You can use the restart services functionality to restart individual services that are associated with a Tier 2, Tier 3, Tier 4, or Tier 5 standard acceptance test (sandbox) environment that is deployed in a Microsoft subscription. The services that you can restart are **AX (AOS service)**, **DIXF (Data import export framework service)** and **MR (Management Reporter service)**.

To restart a service, use the following steps:

1. Navigate to the environment details page and under **Maintain** select **Restart service.**
2. Select the **service** you want to restart and click **Confirm**.

During the restart you will be unable to trigger any other maintenance operations and the environment status is updated to **Restarting service**. Once the service restart is complete the environment state is returned to **Deployed**.

## Maintenance mode

Finance and Operations includes a system-wide setting that is named [Maintenance mode](../sysadmin/maintenance-mode.md). When maintenance mode is turned on, it provides a safe way for system administrators to make system changes that might affect system functionality. For example, configuration keys can be enabled or disabled. While maintenance mode is on, only system administrators and users assigned to the Maintenance mode user role can sign in to the system. By default, maintenance mode is turned off.

To enable/disable maintenance mode, use the following steps:

1. Navigate to the environment details page and under **Maintain** select **Enable Maintenance mode**.
2. Environment status will change from Deployed to Servicing.
3. On completion, the environment status is set to be **In Maintenance** and only the system administrator will be able to login.
4. After the system administrator is done making configuration changes, one can come to LCS environment details page and under **Maintain** select **Disable Maintenance mode**.
5. Environment status will change from In Maintenance to Servicing.
6. On completion, the environment status is set back to Deployed. The environment history is updated to reflect that environment was put in maintenance mode.

## Access database

Environments deployed using the [self-service deployment](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/Manali-Branch/articles/dev-itpro/deployment/infrastructure-stack.md) experience have Remote Desktop Access turned off. As part of implementing Finance and Operations, if you need to connect to the database on your Tier 2, Tier 3, Tier 4 or Tier 5 Standard Acceptance Test environments for troubleshooting, access will be granted as needed and will not be persistent. Following process provides an overview of how you can connect to the database:

- Enable access to Azure SQL through LCS by whitelisting the IP address of the machine that you will use to connect to the Azure SQL database using SQL Management Studio.
- After this is done, you can request access to see the database credentials through LCS by entering a reason for requesting access.
- As soon as you submit the request, it gets  **auto-approved**. You will be able to see the database access credentials within a few minutes, on the LCS environment details page.
- Note that the credentials are valid for 8 hours and will expire after that duration. After 8 hours the access expires and you will need to request access again.

To connect to a database, use the following steps:

1. Navigate to the environment details page where you will see two new fields – **Reason for access** and **Details**.
2. Select the reason for wanting access, enter additional details and click **Request access**.
3. At this point a request to create user specific credentials is submitted. The request is auto-approved and has an **expiration of 8 hours**.
4. **Refresh the page** to view the connection string and access details. Note that the access granted will be based on the reason selected. For example, if the reason is AX troubleshooting then you will be granted read only access to AX database. If the reason is performance tuning you will be granted write access to the AX database.
5. Now to connect to the Azure SQL database you will need to whitelist the IP address of the machine that will be used to launch SQL management studio. This can be done by adding **a new Azure SQL firewall rule**. Under the **Maintain** menu select **Enable access**. **Add** a new rule and select Azure SQL from the drop down. Give the **rule a name** and **enter the IP address** of the machine and click **Confirm**. This rule also has an **expiration of 8 hours**.
6. Once this is done you can go the whitelisted machine, launch SQL management studio and use the connection details to connect to the required database.
