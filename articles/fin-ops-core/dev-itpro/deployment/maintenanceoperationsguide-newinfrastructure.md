---
# required metadata

title: Maintenance operations for deployments
description: This topic explains how to perform maintenance operations for an environment that was deployed by using the self-service deployment experience.
author: laneswenka
manager: AnnBe
ms.date: 09/20/2019
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
ms.author: laswenka
ms.search.validFrom: 2018-12-31
ms.dyn365.ops.version: 8.1.1

---

# Maintenance operations for deployments

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/limited-availability.md)]

This topic explains how to perform maintenance operations for an environment that was deployed by using the [self-service deployment](infrastructure-stack.md) experience.

## Restart services

You can use the restart services functionality to restart individual services that are associated with a Tier 2, Tier 3, Tier 4, or Tier 5 standard acceptance test (sandbox) environment that is deployed in a Microsoft subscription. The services that you can restart are **AOS service**, **DIXF (Data import export framework service)**, and **MR (Management Reporter service)**.

To restart a service, follow these steps.

1. In Microsoft Dynamics Lifecycle Services (LCS), on the environment details page, select **Maintain \> Restart service**.
2. Select the service to restart, and then select **Confirm**.

    During the restart, the environment's status is updated to **Restarting service**, and you can't start any other maintenance operations. After the service has been restarted, the environment's status is returned to **Deployed**.

## Maintenance mode

Finance and Operations apps includes a system-wide setting that is named [maintenance mode](../sysadmin/maintenance-mode.md). Maintenance mode gives system admins a safe way to make system changes that might affect system functionality. For example, configuration keys can be turned on or off. While maintenance mode is on, only the system admin and users who are assigned to the **Maintenance mode** user role can sign in to the system. By default, maintenance mode is turned off.

To turn maintenance mode on or off, follow these steps.

1. In LCS, on the environment details page, select **Maintain \> Enable Maintenance mode**.

    The environment's status is changed from **Deployed** to **Servicing**. After maintenance mode has been turned on, the environment's status is updated to **In Maintenance**, and only the system admin can sign in.

2. After the system admin has finished making configuration changes, on the environment details page, select **Maintain \> Disable Maintenance mode**.

    The environment's status is changed from **In Maintenance** to **Servicing**. After maintenance mode has been turned off, the environment's status is returned to **Deployed**. The environment history is updated to reflect the fact that the environment was put into maintenance mode.

## Access database

Remote access is turned off for environments that were deployed by using the [self-service deployment](infrastructure-stack.md) experience. During implementation, if you must connect to the database on your Tier 2, Tier 3, Tier 4 or Tier 5 standard acceptance test environments for troubleshooting purposes, access will be granted as it's required. The access won't be persistent.

To connect to a database, follow these steps.

1. Request access to view the database credentials in LCS. On the environment details page, in the **Reason for access** field, select your reason for requesting access. In the **Details** field, enter any additional details. 
2. Select **Request access**.

    A request to create user-specific credentials is submitted. The request is automatically approved as soon as you submit it. It has an expiration time of eight hours. In a few minutes, you will be able to view the database credentials on the environment details page in LCS.

    > [!NOTE]
    > The database credentials are valid for eight hours. After eight hours, the credentials expire, and you must request access again.

3. Refresh the environment details page to view the connection string and access details.

    The access that is granted to you depends on the reason that you selected in the **Reason for access** field. For example, if you selected **AX troubleshooting** as the reason, read-only access to the AX database is granted. If you selected **Performance tuning** as the reason, write access to the AX database is granted.

4. Before you can access Microsoft Azure SQL Database through LCS, the IP address of the computer where you will use Microsoft SQL Server Management Studio to connect to the SQL database must be added to the approved list (sometimes referred to as the "whitelist").

    To complete this step, you can add a new SQL Database firewall rule:

    1. In LCS, on the environment details page, select **Maintain \> Enable access**.
    2. Add a new rule. In the **Service** field, select **Azure SQL**.
    3. Enter a name for the rule, enter the IP address of the computer, and then select **Confirm**.

    This rule also has an expiration time of eight hours.

5. On the computer that has been added to the approved list, open Management Studio, and use the connection details to connect to the required database.
