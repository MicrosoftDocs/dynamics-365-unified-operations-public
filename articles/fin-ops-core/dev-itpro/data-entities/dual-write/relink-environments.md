---
title: Unlink and relink dual-write environments
description: This topic describes how to unlink, clear the key tables, and then relink dual-write environments.
author: RamaKrishnamoorthy
ms.date: 04/07/2021
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: ramasri
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version:
---

# Unlink and relink dual-write environments

[!include [banner](../../includes/banner.md)]



When you unlink and relink dual-write connection between environments, you need to delete the data from the key tables. This requirement applies to sandbox, production, and user acceptance test (UAT) environments during activities like backup and restore. This topic describes how to unlink, delete the data in the key tables, and then relink the dual-write environments.

The mappings are preserved when you unlink and relink, because the mappings are stored in Dataverse.

## Scenario: Dual-write is enabled between production environments

In this scenario, dual-write is enabled between Finance and Operations and Dataverse production environments. You want to back up the Finance and Operations production environment (source) and restore it to Finance and Operations UAT environment (destination). Once you restore, follow these steps on the Finance and Operations UAT environment:

1. Stop all table maps.
2. Unlink the dual-write connection as the Finance and Operations UAT environment will be pointing towards Dataverse production environment.
3. Delete the data from the key tables.

    - **DualWriteProjectConfiguration**
    - **DualWriteProjectFieldConfiguration**
    - **BusinessEventsDefinition**

4. You may want to relink Finance and Operations UAT environment against Dataverse UAT environment. 
5. Enable the maps.

If the backup and restore processes are running on Dataverse, then follow these steps:

1. Sign in to Finance and Operations UAT environment.
2. Stop all table maps.
3. Unlink the dual-write connection as the Dataverse UAT environment will be pointing towards Finance and Operations production environment.
4. Delete the data from the **Dual Write Runtime Configurations** table on Dataverse.
5. You may want to relink Finance and Operations UAT environment against Dataverse UAT environment.
6. Enable the maps.

## Scenario: Reset or change linking

If you want to reset your existing sandbox Dataverse instance that is linked for dual-write or you want to change the linking to a different Dataverse instance, then follow these steps:

1. Sign in to the Finance and Operations app.
2. Stop all entity maps.
3. Unlink the dual-write connection between Finance and Operations app and Dataverse.
5. Reset the Dataverse environment.
6. Delete the data from the key tables in the Finance and Operations app.

    - **DualWriteProjectConfiguration**
    - **DualWriteProjectFieldConfiguration**
    - **BusinessEventsDefinition**

7. Set up dual-write on the environment that you want to reset. For more information, see [System requirements and prerequisites](requirements-and-prerequisites.md).

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
