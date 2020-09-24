---
# required metadata

title: Migrate channel to a different Commerce Scale Unit
description: This topic explains how to migrate a Commerce Channel to a different Commerce Scale Unit.
author: AamirAllaq
manager: AnnBe
ms.date: 09/24/2020
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang:
ms.reviewer: sericks
ms.search.scope: Retail, Operations
# ms.tgt_pltfrm:
# ms.custom: 
ms.search.region: Global
# ms.search.industry: retail
ms.author: aamiral
ms.search.validFrom: 2018-4-30
ms.dyn365.ops.version: 8.0
---

# Migrate channel to a different Commerce Scale Unit
This article explains how to migrate a Commerce Store Channel to a different Commerce Scale Unit (CSU) than the one it is currently operating with. You may choose to migrate channel(s) to a different CSU for better load isolation & resource governance between channels, for reduced latency to your Stores, or for managing different update/extension deployment schedules for staged roll-out and pilots. Migrating to a different CSU involves downtime for that channel. This article describes best practices to migrate channels while minimizing business disruption and downtime. This applies to both migration of channels between cloud-hosted Commerce Scale Units to other cloud-hosted CSUs, between self-hosted Commerce Scale Units to other self-hosted CSUs, as well as between cloud-hosted and self-hosted CSUs, and in either direction. 

> [!Note] 
> If you migrate channels between CSUs, temporary sales data used for journal records and POS reports, from prior to the migration, will no longer be available at POS after migration. Journals and Channel reports will start afresh with new data after the migration.

## Planning for downtime
With the steps described in this article, all long running system processes involved in this exercise (including synchronization of master data for products, prices, customers, etc.) are run before the actual migration, while the stores are operational. The critical period of migration during which you must take a planned downtime in your environment will involve data synchronization of a very small payload of channel configuration data to the new Commerce Scale Unit. In most cases, this synchronization can complete in under 10 minutes. However, from an operational perspective, you will need to plan for a longer downtime window to allow for all pre-requisite steps to complete (e.g. closing all shifts, synchronizing transactions to to HQ, posting statements, etc.), which will vary by each organization.

## Pre-requisities
Perform all the below steps first in sandbox UAT environment and then repeat in a production environment. This will allow you to measure and estimate the actual downtime you can expect in a production environment. 

## Migration steps

The following steps can be performed while the stores are still operational.

1. For the desired store, navigate to **Store details** page.
2. Set **Live Channel Database** field to existing CSU.

## Configure data synchronization

The following steps are optional, but recommended.

1. In Commerce HQ, navigate to **Channel Database group** form.
2. Create a new Channel Database group.
3. Set Commerce channel schema as **AX7**.
4. Select **Save** to save the group.
5. Navigate to Channel Database form and select the record for the new Channel Database form.
6. Add desired channel(s) to this new channel database.
7. Set the **Channel database group** field to the newly created Channel database group from Step 2 above.
8. Navigate to **Distribution Schedule** form.
9. For each job, add the newly created Channel database group from Step 2 above to the **Channel database group** list. 
10. Navigate to Channel Database form and select the record for the new Channel Database form.
11. Select **Full data sync** on this new Channel database with **9999 All jobs**.

The following steps must be performed during planned downtime for your channels.

## Prepare for migration

1. On all Point of Sale devices, ensure all Shifts are closed.
2. Logout on all POS devices.
3. Validate all POS offline transactions are synchronized to HQ. Run P-jobs for all existing channel database(s) that will be migrated. If you proceed to migration before P-jobs have completed, your number sequences will not match and you will need to [Reset receipt number sequences](../../../commerce/reset_receipt_number_sequence.md).
4. Validate all Statements are posted.

## Migrate channels to new Commerce Scale Unit

1. Navigate to **Store details** page.
2. Set **Live Channel Database** field to new Commerce Scale Unit.
3. Set **Channel profile** field to the new Commerce Scale Unit.
4. Navigate to the **Distribution Schedule** form.
5. Run **Channel configuration job (1070)** and **POS redeployment job (1160)** by selecting **Run now** (or **Create batch job** for asynchronous processing) for each job. After the jobs complete, your channels have now migrated to the new CSU. 
6. If you are using Cloud Point of Sale, you will need to use the URL of Cloud Point of Sale for the new CSU, and re-active the POS device. 
7. For MPOS, close, re-open and login on each POS device.
8. If you re-activate before P-jobs have completed, your number sequences will not match and you will need to [Reset receipt number sequences](../../../commerce/reset_receipt_number_sequence.md).

## Post migration steps

The following steps can happen outside of planned downtime for your channels.

> [!Note]
> Do not delete previously assigned CSU until all data has sync'd to HQ. It's recommended that you wait for at-least 30 days or end of next calendar month, before you delete previously assigned CSU, or disable P-jobs for that CSU.

> [!Note]
> Do not delete the previously assigned CSU until each POS has at-least logged in once to retrieve the URL of the newly assigned CSU.

The following steps are optional, but recommended.

1. Navigate to Channel Database form and select the previously assigned Commerce Scale Unit channel database.
2. Un-assign store from the previously assigned Channel database.
3. Run Full sync-9999 job for this Channel database.

After you have completed all steps in a sandbox UAT, perform the same steps in your production environment. 
