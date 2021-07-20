---
# required metadata

title: Migrate channels to a different Commerce Scale Unit
description: This topic explains how to migrate a Microsoft Dynamics 365 Commerce channel to a different Commerce Scale Unit.
author: AamirAllaq
ms.date: 11/17/2020
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

# ms.search.form: [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang:
ms.reviewer: sericks
# ms.tgt_pltfrm:
# ms.custom: 
ms.search.region: Global
# ms.search.industry: retail
ms.author: aamiral
ms.search.validFrom: 2018-4-30
ms.dyn365.ops.version: 8.0
---

# Migrate channels to a different Commerce Scale Unit

[!include[banner](../includes/banner.md)]

This topic explains how to migrate Microsoft Dynamics 365 Commerce store channels from the Commerce Scale Unit (CSU) that they are currently working with to a different CSU. You might want to migrate channels to a different CSU for better load isolation and resource governance between channels, to reduce latency to your stores, or to manage different update/extension deployment schedules for staged roll-out and pilots. Migration to a different CSU involves downtime for the channels.

This topic describes best practices that will help you minimize business disruption and downtime while you migrate channels. It applies to the migration of channels between cloud-hosted CSUs, between self-hosted CSUs, from cloud-hosted CSUs to self-hosted CSUs, and from self-hosted CSUs to cloud-hosted CSUs.

> [!NOTE]
> If you migrate channels between CSUs, temporary sales data that was used for journal records and point of sale (POS) reports before the migration will no longer be available at the POS after migration. After the migration is completed, journals and channel reports will be started afresh by using new data.

In the following procedures, the terms *origin* and *destination* are used to distinguish the CSUs and corresponding channel databases that are involved in the migration.

## Planning for downtime

When you follow the procedures that are described in this topic, all long-running system processes that are involved are run before the actual migration, while the stores are still operational. These processes including synchronization of master data for products, prices, and customers. Then, during the migration, the critical period when you must take planned downtime in your environment involves data synchronization of a very small payload of channel configuration data to the new CSU. In most cases, this synchronization can be completed in under 10 minutes. However, from an operational perspective, you must plan for a longer downtime window to ensure that all prerequisite steps have enough time to be completed. These steps include closing all shifts, syncing transactions to Commerce headquarters, and posting statements. The amount of time that is required will vary by organization.

## Prerequisites

First, complete all the following procedures in a sandbox user acceptance testing (UAT) environment. Then repeat them in your production environment. In this way, you can measure and estimate the downtime that you should expect in the production environment.

## Migration

### Configure data synchronization

The following steps can be completed while the stores are still operational. They synchronize master data to the destination CSU.

1. In Commerce headquarters, on the **Channel database** page, select the record for the channel database for the destination CSU. 
2. Add the desired channels to the destination channel database.
3. Select **Full data sync**, and specify that job **9999** (**All jobs**) should be used.

> [!NOTE]
> If your destination CSU is self-hosted, consider creating separate channel database groups to reduce the volume of unnecessary master data synchronization. 

### Prepare for migration

This procedure and the next procedure must be completed during the planned downtime for your channels.

1. On all POS devices, make sure that all shifts are closed.
2. Sign out of all POS devices.
3. Confirm that all POS offline transactions are synced to Commerce headquarters. Run P-jobs for all existing channel databases that will be migrated. If you start the migration before P-jobs are completed, and if you use Cloud POS, you might lose transactions because of duplicate transaction numbers.
4. Confirm that all statements are posted.

### Migrate channels to a new CSU

1. On the **Store details** page, set the **Live channel database** field to the destination CSU database.
2. Set the **Channel profile** field to the channel profile that is associated with the destination CSU.
3. On the **Distribution schedule** page, run job **1070** (**Channel configuration job**) and job **1110** (**Global configuration job**). Select **Run now** for each job. (For asynchronous processing, select **Create batch job** instead of **Run now**.) After the jobs are completed, your channels have been migrated to the new CSU.
4. If you're using Cloud POS, you must use the URL of Cloud POS for the new CSU and reactivate the POS device. If you reactivate the POS device before all P-jobs on the origin channel database are completed, you might lose transactions because of duplicate transaction numbers.

    If you're using Modern POS, close each POS device, reopen it, and sign in.

## Post-migration

You can continue to use the origin CSU to serve other channels. 

> [!NOTE]
> Do not delete the origin CSU. Doing so may make the store unoperable.

After you've completed all the procedures in a sandbox UAT environment, repeat them in your production environment.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]