---
title: Unlink and relink dual-write environments
description: Learn how to unlink, clear the key tables, and then relink dual-write environments, including various scenarios and known issues.
author: RamaKrishnamoorthy
ms.author: ramasri
ms.topic: article
ms.date: 04/07/2021
ms.reviewer: sericks
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version: 
---

# Unlink and relink dual-write environments

[!include [banner](../../includes/banner.md)]

When you unlink and relink Dual-write connection between environments, you need to delete the data from the key tables. This requirement applies to sandbox, production, and user acceptance test (UAT) environments during activities like backup and restore. This article describes how to reset the connection, and delete the data in the key tables.

## Scenario: Reset linking

If you want to reset your existing sandbox Dataverse instance that is linked for Dual-write or you want to change the linking to the Dataverse instance currently targeted in Lifecycle Services, then follow these steps:

> [!NOTE]
> If you are receiving a message in Lifecycle Services that "Microsoft has detected that your environment is linked via Dual-write to a different Power Platform environment" the following steps will help you to resolve the issue when a previous link has been established.

1. Sign in to the Finance and Operations app.
2. Navigate to **Data management** > **Dual-write**.
3. Stop all entity maps.
4. Ensure the environment targeted via Lifecycle Services has been properly configured. For more information, see [System requirements and prerequisites](requirements-and-prerequisites.md).
5. Click the **Reset** button to reset all Dual-write connections and configurations. The [Reset dual-write connections](reset.md) documentation provides additional detail on this process.

## Scenario: Backup and restore

When you back up and restore an environment, you may see unexpected data movement or errors if a previous Dual-write connection was established with this environment. This issue occurs because the data in the key tables is not cleared. To mitigate this issue, follow these steps:

1. Sign in to the targeted Finance and Operations app.
2. Delete the data from the following tables:

    - **DualWriteProjectConfiguration**
    - **DualWriteProjectFieldConfiguration**
    - **BusinessEventsDefinition**

3. Sign in to the targeted Dataverse environment.
4. Delete the data from the **Dual Write Runtime Configurations** table.
5. Reset the connection as detailed above to re-establish applicable connections.

## Known issues

### SecureConfig Organization error

When you try to copy, update, or delete records after copying the environment, the following error appears: **SecureConfig Organization (ProjOpsTest4) does not match actual CRM Organization (org6459f7a8_195867911_20200717T174709)**.

Follow these steps to mitigate the error:

1. In the customer engagement app, select **Advanced find**.
2. In the **Look for** field, select **Dual Write Runtime Configurations**.
3. Select **Results**.
4. Rows will be displayed. Select all the rows.
5. Select the **Delete** icon.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
