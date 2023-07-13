---
title: Migrate channels to a different Commerce Scale Unit
description: This article explains how to migrate a Microsoft Dynamics 365 Commerce channel to a different Commerce Scale Unit.
author: jashanno
ms.date: 06/27/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2018-04-30
ms.dyn365.ops.version: 8

---

# Migrate channels to a different Commerce Scale Unit

[!include[banner](../includes/banner.md)]

This article explains how to migrate Microsoft Dynamics 365 Commerce store channels from the Commerce Scale Unit (CSU) that they are currently working with to a different CSU. You might want to migrate channels to a different CSU for better load isolation and resource governance between channels, to reduce latency to your stores, or to manage different update/extension deployment schedules for staged roll-out and pilots. Migration to a different CSU involves downtime for the channels.

This article describes best practices that will help you minimize business disruption and downtime while you migrate channels. It applies to the migration of channels between cloud-hosted CSUs, between self-hosted CSUs, from cloud-hosted CSUs to self-hosted CSUs, and from self-hosted CSUs to cloud-hosted CSUs.

> [!NOTE]
> If you migrate channels between CSUs, temporary sales data that was used for journal records and point of sale (POS) reports before the migration will no longer be available at the POS after migration. After the migration is completed, journals and channel reports will be started afresh by using new data.

In the following procedures, the terms *origin* and *destination* are used to distinguish the CSUs and corresponding channel databases that are involved in the migration.

## Planning for downtime

When you follow the procedures that are described in this article, all long-running system processes that are involved are run before the actual migration, while the stores are still operational. These processes including synchronization of master data for products, prices, and customers. Then, during the migration, the critical period when you must take planned downtime in your environment involves data synchronization of a very small payload of channel configuration data to the new CSU. In most cases, this synchronization can be completed in under 10 minutes. However, from an operational perspective, you must plan for a longer downtime window to ensure that all prerequisite steps have enough time to be completed. These steps include closing all shifts, syncing transactions to Commerce headquarters, and posting statements. The amount of time that is required will vary by organization.

## Prerequisites

First, complete all the following procedures in a sandbox user acceptance testing (UAT) environment. Then repeat them in your production environment. In this way, you can measure and estimate the downtime that you should expect in the production environment.

## Migration

### Configure data synchronization

The following steps can be completed while the stores are still operational. They synchronize master data to the destination CSU.

1. In Commerce headquarters, on the **Channel database** page, select the record for the channel database for the destination CSU. 
2. Add the desired channels to the destination channel database.
3. Select **Full data sync**, and specify that job **9999** (**All jobs**) should be used.

> [!NOTE]
> If your destination CSU is self-hosted, consider creating separate channel database groups to reduce the volume of unnecessary master data synchronization. Regardless of your channel database groups configuration, the steps in this document presume that the groups containing the source CSU and the destination CSU will both have all jobs listed below performed across them. For example, if the source and destination CSUs are in different channel database groups, then both groups must have the distribution schedule jobs run together for all instances of jobs needing to be run.

### Prepare for migration

This procedure and the next procedure must be completed during the planned downtime for your channels.

1. On all POS devices, make sure that all shifts are closed.
2. Sign out of all POS devices.
3. Confirm that all POS offline transactions are synced to Commerce headquarters. Run P-jobs for all existing channel databases that will be migrated. If you start the migration before P-jobs are completed, and if you use Cloud POS, you might lose transactions because of duplicate transaction numbers.
4. Confirm that all statements are posted.

### Migrate channels to a new CSU

To migrate channels to a new CSU, follow these steps.

1. On the **Store details** page, set the **Live channel database** field to the destination CSU database. Ensure that the modified CSU database is in the same database group as the original CSU database. You can find all database group settings on the **Retail and Commerce \> Headquarters setup \> Commerce scheduler \> Channel database group** form in headquarters.
1. Set the **Channel profile** field to the channel profile that is associated with the destination CSU.
1. On the **Distribution schedule** page, for synchronous processing, select **Run now** for both the **Channel configuration job (1070)** and **Global configuration (1110)** jobs. For asynchronous processing, select **Create batch job** (instead of **Run now**). After the jobs have completed, your channels will be migrated to the new CSU.
1. If you're using Cloud POS, you must use the Cloud POS URL for the new CSU and reactivate the POS device. If you reactivate the POS device before all P-jobs in the origin channel database have completed, you might lose transactions because of duplicate transaction numbers.
1. If you're using Modern POS, close each POS device, reopen it, and then sign in.

## Post-migration

You can continue to use the origin CSU to serve other channels. 

> [!NOTE]
> Do not delete the origin CSU. Doing so may make the store unoperable.

After you've completed all the procedures in a sandbox UAT environment, repeat them in your production environment.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
