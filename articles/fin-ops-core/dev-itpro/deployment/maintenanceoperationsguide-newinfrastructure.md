---
title: Maintenance operations for deployments
description: Learn how to perform maintenance operations for an environment that was deployed by using the self-service deployment experience.
author: laneswenka
ms.author: laswenka
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 04/02/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2018-12-31
ms.search.form: 
ms.dyn365.ops.version: 8.1.1
---

# Maintenance operations for deployments

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/limited-availability.md)]

This article explains how to perform maintenance operations for an environment that you deployed by using the [self-service deployment](infrastructure-stack.md) experience.

## Restart services

Use the restart services functionality to restart individual services that are associated with a Tier 2, Tier 3, Tier 4, or Tier 5 standard acceptance test (sandbox) environment that you deployed in a Microsoft subscription. You can restart the **finance and operations apps service**, **Data management workspace**, and **Financial reporting service** services.

To restart a service, follow these steps:

1. In Microsoft Dynamics Lifecycle Services, on the environment details page, select **Maintain \> Restart service**.
1. Select the service to restart, and then select **Confirm**.

    During the restart, the environment's status is updated to **Restarting service**, and you can't start any other maintenance operations. After the service restarts, the environment's status returns to **Deployed**.

## Maintenance mode

Finance and operations apps include a system-wide setting named [maintenance mode](../sysadmin/maintenance-mode.md). Maintenance mode gives system admins a safe way to make system changes that might affect system functionality. For example, you can turn configuration keys on or off. While maintenance mode is on, only the system admin and users who are assigned to the **Maintenance mode** user role can sign in to the system. By default, maintenance mode is turned off.

To turn maintenance mode on or off, follow these steps:

1. In Lifecycle Services, on the environment details page, select **Maintain** > **Enable Maintenance mode**.

    The environment's status changes from **Deployed** to **Servicing**. After you turn on maintenance mode, the environment's status updates to **In Maintenance**, and only the system admin can sign in.

1. After the system admin finishes making configuration changes, on the environment details page, select **Maintain** > **Disable Maintenance mode**.

    The environment's status changes from **In Maintenance** to **Servicing**. After you turn off maintenance mode, the environment's status returns to **Deployed**. The environment history updates to reflect the fact that the environment was put into maintenance mode.

## Access database

Remote access is turned off for environments that you deploy by using the [self-service deployment](infrastructure-stack.md) experience. During implementation, if you must connect to the database on your Tier 2, Tier 3, Tier 4, or Tier 5 standard acceptance test environments for troubleshooting purposes, you can request access. The access isn't persistent.

To connect to a database, follow the instructions in [Enable just-in-time access](../database/database-just-in-time-jit-access.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

