---
# required metadata

title: Initialize cloud-hosted Retail channel components
description: This topics explains how to initialize cloud-hosted Retail channel components.
author: AamirAllaq
manager: AnnBe
ms.date: 12/05/2018
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


# Initialize cloud-hosted Retail channel components

[!include[banner](../includes/banner.md)]

If you're using a Tier-2 sandbox or production environment that has application version 8.1.2.x or later, you must initialize Retail channel components that are hosted in the cloud before you can use Retail channel functionality either for point of sale (POS) operations or for e-Commerce operations that use Retail Server in the cloud.

This topic describes the steps for initializing cloud-hosted Retail channel components.

## Prerequisites

1. Deploy a Tier-2 sandbox or production environment that has application version 8.1.2.x or later.
2. In Microsoft Dynamics Lifecycle Services (LCS), create a support request, and enter **Access request for cloud-hosted Retail channel components**.

The request will be completed within five business days.

## Initialize cloud-hosted Retail channel components as part of a new environment deployment

1. In LCS, on the Environment details page, select **Environment features \> Retail**.
2. On the Retail setup deployment page, select **Initialize**.
3. Select the version of the Retail channel components to initialize.

## Additional considerations if you initialize cloud-hosted Retail channel components in an existing environment

If you're already using cloud-hosted Retail channel components in an environment, initialization will help reduce the downtime when those components are updated. Additional planning is required before you do the initialization.

1. Make sure that all shifts at the POS are closed.
2. Make sure that all P-jobs have been successfully completed.
3. Sign out of all POS devices.

You should plan for a five-hour downtime window for the store and any online channel operations that depend on Retail Server.

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
