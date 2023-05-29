---
# required metadata

title: Maintenance operations for deployments
description: This article explains how to perform maintenance operations for an environment that was deployed by using the self-service deployment experience.
author: laneswenka
ms.date: 03/16/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2018-12-31
ms.dyn365.ops.version: 8.1.1

---

# Maintenance operations for deployments

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/limited-availability.md)]

This article explains how to perform maintenance operations for an environment that was deployed by using the [self-service deployment](infrastructure-stack.md) experience.

## Restart services

You can use the restart services functionality to restart individual services that are associated with a Tier 2, Tier 3, Tier 4, or Tier 5 standard acceptance test (sandbox) environment that is deployed in a Microsoft subscription. The services that you can restart are **finance and operations apps service**, **Data management workspace**, and **Financial reporting service**.

To restart a service, follow these steps.

1. In Microsoft Dynamics Lifecycle Services (LCS), on the environment details page, select **Maintain \> Restart service**.
2. Select the service to restart, and then select **Confirm**.

    During the restart, the environment's status is updated to **Restarting service**, and you can't start any other maintenance operations. After the service has been restarted, the environment's status is returned to **Deployed**.

## Maintenance mode

finance and operations apps includes a system-wide setting that is named [maintenance mode](../sysadmin/maintenance-mode.md). Maintenance mode gives system admins a safe way to make system changes that might affect system functionality. For example, configuration keys can be turned on or off. While maintenance mode is on, only the system admin and users who are assigned to the **Maintenance mode** user role can sign in to the system. By default, maintenance mode is turned off.

To turn maintenance mode on or off, follow these steps.

1. In LCS, on the environment details page, select **Maintain \> Enable Maintenance mode**.

    The environment's status is changed from **Deployed** to **Servicing**. After maintenance mode has been turned on, the environment's status is updated to **In Maintenance**, and only the system admin can sign in.

2. After the system admin has finished making configuration changes, on the environment details page, select **Maintain \> Disable Maintenance mode**.

    The environment's status is changed from **In Maintenance** to **Servicing**. After maintenance mode has been turned off, the environment's status is returned to **Deployed**. The environment history is updated to reflect the fact that the environment was put into maintenance mode.

## Access database

Remote access is turned off for environments that were deployed by using the [self-service deployment](infrastructure-stack.md) experience. During implementation, if you must connect to the database on your Tier 2, Tier 3, Tier 4 or Tier 5 standard acceptance test environments for troubleshooting purposes, access will be granted as it's required. The access won't be persistent.

To connect to a database, follow the instructions in [Enable just-in-time access](../database/database-just-in-time-jit-access.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

