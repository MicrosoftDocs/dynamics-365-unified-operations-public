---
# required metadata

title: Initialize Retail Cloud Scale Unit
description: This topics explains how to initialize Retail Cloud Scale Unit.
author: AamirAllaq
manager: AnnBe
ms.date: 04/05/2019
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
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: retail
ms.author: aamiral
ms.search.validFrom: 2018-4-30 
ms.dyn365.ops.version: 8.0 
---


# Initialize Retail Cloud Scale Unit

[!include[banner](../includes/banner.md)]

If you're using a Tier-2 sandbox or production environment that has application version 8.1.2.x or later, you must initialize Retail Cloud Scale Unit before you can use retail channel functionality either for point of sale (POS) operations or for e-Commerce operations that use Retail Server in the cloud. Initialization will deploy a Retail Cloud Scale Unit.

This topic describes the steps for initializing Retail Cloud Scale Unit.

## Prerequisites

1. Deploy a Tier-2 sandbox or production environment that has application version 8.1.2.x or later.
2. In Microsoft Dynamics Lifecycle Services (LCS), create a support request, and enter **Access request for Retail Cloud Scale Unit**.

The request will be completed within five business days.

## Initialize Retail Cloud Scale Unit as part of a new environment deployment

1. In LCS, on the environment details page, select **Environment features \> Retail**.
2. On the Retail setup deployment page, select **Initialize**.
3. Select the version of the Retail Cloud Scale Unit to initialize.
4. Select a desired region to initialize Retail Cloud Scale Unit in.

## Configure retail channels to use RCSU

1. After Retail Cloud Scale Unit has been deployed, in the head office client naviate to **Retail > Retail Headquarters > Retail Scheduler setup > Channel database** to review that your retail channels are configured to use the database for this Retail Cloud Scale Unit.
2. Navigate to each retail channel and select the Channel Profile for the corresponding Retail Cloud Scale Unit. 

## Deploy additional Retail Cloud Scale Units (optional)

After you have initialized the first Retail Cloud Scale Unit (RCSU), you may optionally deploy 1 additional RCSU. If you need more than 2 RCSUs, please file a support request to increase the limit, stating the number of RCSUs needed, environment name, and desired regions.

For each additional RCSU that you deploy, it is also recommended that you create a separate channel database group for each RCSU. To do this, follow these steps: 

1. In Retail head office, navigate to **Retail > Retail Headquarters > Retail Scheduler setup > Channel database group**.
2. Create a new channel database group. 
3. Navigate to the **Retail > Retail Headquarters > Retail Scheduler setup > Channel database** form and select the channel database that corresponds to the just created RCSU. 
4. Select **Edit** and select the just created channel database group. 
5. Select **Save**.
6. Select **Run Full data sync** for the selected channel database.

## Additional considerations if you initialize cloud-hosted Retail channel components in an existing environment

If you're already using cloud-hosted Retail channel components in an environment, initialization of Retail Cloud Scale Unit will help reduce the downtime when those components are updated. Additional planning is required before initialization of Retail Cloud Scale Unit.

1. Make sure that all shifts at the POS are closed.
2. Make sure that all P-jobs have been successfully completed.
3. Sign out of all POS devices.

You should plan for a five-hour downtime window for the store and any online channel operations that use Retail Server.

Here is what occurs during the initialization period:

- Cloud-hosted Retail channels won't work (unless POS offline capability is turned on).
- POS devices that offline capability is turned on for will have reduced functionality.
- Any e-Commerce clients that depend on Retail Server will be disrupted.
- Channels that are hosted on Retail Store Scale Units won't be affected.
- Head office functionality won't be affected.

Here is what occurs after initialization is completed:

- The device activation state of all activated POS devices will be preserved. Therefore, the devices won't have to be reactivated.
- Stand-alone hardware station instances will continue to work.
- POS channel–side reports will be reset and won't show data from before the initialization.
- Show journal operation will also be reset and won't show data from before the initialization.
