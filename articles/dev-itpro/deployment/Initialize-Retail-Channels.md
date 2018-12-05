---
# required metadata

title: Initialize cloud-hosted Retail channel components
description: This article will cover the steps to initialize cloud-hosted Retail channel components.
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

This article will cover the steps to initialize cloud hosted Retail channel components.

If you are using a Tier-2 Sandbox or Production environment on application version 8.1.2.x or newer, you will first need to initialize Retail channel components in the cloud, before you can use retail channel functionality for Point of Sale operations, or for E-commerce operations that utilize Retail Server in the cloud.


Pre-requisites

1. You must first deploy a Tier-2 Sandbox or Production environment with application version 8.1.2.x or newer to proceed.
2. In LCS, create a new support request and state the following:

"Access request for cloud hosted Retail channel components"

Request will be completed within 5 business days or less.

Initialize cloud hosted Retail channel components as part of a new environment deployment.

1. In LCS, go to Environment details page and select ***ENVIRONMENT FEATURES > Retail***
2. On the Retail setup deployment page, select ***Initialize***
3. On the selection panel, select a version of Retail channel components to initialize.

Additional considerations when initializing in an existing environment.

If you are already using Retail cloud hosted channel components, initialization will allow for reduced downtime updates for cloud hosted retail channel components. You will require additional planning before you initialize this capability.

1. Ensure all shifts at POS are closed
2. Ensure all P-jobs have successfully completed
3. Log-out of all Point of Sale devices
3. Plan for a 5 hour downtime window for store and any Retail Server dependent online channel operations

During the initialization period, the following will occur:

  - Cloud-hosted retail channels will not function (unless POS offline capability is enabled).
  - POS devices with offline capability enabled will have reduced functionality.
  - Any e-commerce clients dependent on Retail Server will be disrupted
  - Channels hosted on Retail Store Scale Units will remain unaffected.
  - Head office functionality will remain unaffected.

After initlization has completed, 
  - Device activation state of all activated POS devices will be preserved, and will not need to be re-activated
  - Stand-alone hardware station instances will continue to operate
  - POS channel side reports will be reset and not show data from before the initialization
  

