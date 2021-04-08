---
title: Unlink and relink dual-write environments
description: This topic describes how to unlink, clear the key tables, and then relink dual-write environments.
author: RamaKrishnamoorthy
ms.date: 04/07/2021
ms.topic: article
audience: Developer
ms.reviewer: rhaertle
ms.custom:
ms.search.region: Global
ms.author: ramasri
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version:
---

# Unlink and relink dual-write environments

[!include [banner](../../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

When you unlink and relink two dual-write environments, you need to clear the data from the key tables. This applies to sandbox, production, and user acceptance test environments, and linking changes like regular backup and restore, and go-live releases. This topic describes how to unlink, clear the key tables, and then relink dual-write environments.

You can relink the Finance and Operations and customer engagement environments and resume your work. The mappings will be preserved, because the mappings are stored in Dataverse.

## Scenario: Dual-write is enabled between production environments

In this scenario, dual-write is enabled between Finance and Operations and Dataverse production environments. You want to back up the Finance and Operations environment and restore it to Finance and Operations UAT environment, then Finance and Operations UAT becomes your destination system. (Note: These steps are applicable for Prod/Sandbox/Dev instances).

 Whenever you run a backup and restore process, you should follow the steps in the relevant scenario on the destination system.


Do the following on the destination system: 

1. Stop all entity maps.
2. Unlink Finance and Operations and Dataverse.
3. Perform database restore.
4. Clear out the key tables in Finance and Operations

    - **DualWriteProjectConfiguration**
    - **DualWriteFieldConfiguration**
    - **BusinessEventsDefinition**

5. Relink dual-write.
6. Enable the maps.

If the backup and restore is happening for Dataverse, then do this step on the destination Dataverse environment:

1. Login to Finance and Operations
2. Stop all entity maps.
3. Unlink Finance and Operations and Dataverse.
4. Perform database restore in Dataverse
5. Clear out the following table.
6. Re-link Finance and Operations and Dataverse

## Scenario: Reset or change linking

If you wish to reset your existing sandbox Dataverse instance that is linked for dual-write or wish to change the linking to a different Dataverse instance, then do the following:

1. Finance and Operations instance.
2. Login to Finance and Operations
3. Stop all entity maps.
4. Unlink Finance and Operations and CDS.
5. Reset the CDS environment.
6. Clear out these tables in Finance and Operations - DualWriteProjectConfiguration, DualWriteProjectFieldConfiguration and BusinessEventsDefinition
7. Follow these instructions for setting up dual-write for the reset environment -
    [<span class="underline">https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/requirements-and-prerequisites</span>](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/requirements-and-prerequisites)

## Known issues

### SecureConfig Organization error

When you try to copy, update, or delete records after copying the environment, the following error appears: **SecureConfig Organization (ProjOpsTest4) does not match actual CRM Organization (org6459f7a8_195867911_20200717T174709)**.

Follow these steps to mitigate the error:

1. In the customer engagement app, select **Advanced find**.
2. In the **Look for** field, select **Dual Write Runtime Configurations**.
3. Select **Results**.
4. Select all the results.
5. Select the **Delete** icon.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
