---
title: Unlink and relink dual-write environments
description: Learn how to unlink, clear the key tables, and then relink dual-write environments, including various scenarios and known issues.
author: RamaKrishnamoorthy
ms.author: johnmichalak
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 01/15/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2021-04-07

---

# Unlink and relink dual-write environments

[!include [banner](../../includes/banner.md)]

When you unlink and relink a Dual-write connection between environments, you need to delete the data from the key tables. This requirement applies to sandbox, production, and user acceptance test (UAT) environments during activities like backup and restore. This article describes how to reset the connection, and how to delete the data in the key tables.

## Scenario: Reset linking

If you want to reset your existing sandbox Dataverse instance that is linked for Dual-write or you want to change the linking to the Dataverse instance currently targeted in Lifecycle Services, follow these steps:

> [!NOTE]
> If you receive a message in Lifecycle Services that states "Microsoft has detected that your environment is linked via Dual-write to a different Power Platform environment" the following steps help you resolve the issue when a previous link exists.

1. Sign in to the finance and operations app.
1. Go to **Data management** > **Dual-write**.
1. Stop all entity maps.
1. Ensure the environment targeted through Lifecycle Services is properly configured. For more information, see [System requirements and prerequisites](requirements-and-prerequisites.md).
1. Select **Reset** to reset all Dual-write connections and configurations. For more information about the reset process, see [Reset dual-write connections](reset.md).

## Scenario: Back up and restore

When you back up and restore an environment, you might see unexpected data movement or errors. These errors occur if a previous Dual-write connection exists with the backup/restore environment and table maps weren't stopped. This connection prevents data clearance in key tables. 

To resolve this problem, follow these steps:

1. Sign in to the targeted Finance and Operations app.
1. Delete the data from the following tables:

    - **DualWriteProjectConfiguration**
    - **DualWriteProjectFieldConfiguration**
    - **BusinessEventsDefinition**

1. Sign in to the targeted Dataverse environment.
1. Delete the data from the **Dual Write Runtime Configurations** table.
1. To re-establish applicable connections, reset the connection as described in the "Reset linking" section.

## Known issues

### SecureConfig Organization error

When you try to copy, update, or delete records after copying the environment, you see the following error: **SecureConfig Organization (ProjOpsTest4) does not match actual CRM Organization (org6459f7a8_195867911_20200717T174709)**.

To resolve the error, follow these steps:

1. In the customer engagement app, select **Advanced find**.
1. In the **Look for** field, select **Dual Write Runtime Configurations**.
1. Select **Results**.
1. Select all the rows.
1. Select the **Delete** icon.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
