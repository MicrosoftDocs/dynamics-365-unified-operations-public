---
# required metadata

title: Initialize seed data in new Commerce environments
description: This article describes the data that's created as part of the initialization process for Dynamics 365 Commerce.
author: josaw1
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: RetailParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.assetid: 4dc762eb-190e-4485-8f55-b0cafc81bc37
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update


---

# Initialize seed data in new Commerce environments

[!include [banner](includes/banner.md)]

This article describes the data that's created as part of the initialization process for Dynamics 365 Commerce.

After the Commerce solution has been deployed through Microsoft Dynamics Lifecycle Services (LCS), you must initialize the Commerce configuration to create the basic configuration data.

> [!IMPORTANT]
> Before you initialize the commerce configuration, make sure that you've specified a language and a postal address for each legal entity where you will set up stores. This step must be completed for each legal entity that you use for commerce.

To initialize the configuration, follow these steps.

1. Start the Commerce client.
2. Click **Retail and Commerce** &gt; **Headquarters setup** &gt; **Parameters** &gt; **Commerce parameters**.
3. Click **Initialize**.

Initialization creates the following default configuration data:

- Commerce scheduler jobs and subjobs
- Commerce channel schema
- Commerce distribution schedules
- Default screen layouts, which include button grids, images, and themes
- Time zone information
- Point-of-sale (POS) operations
- POS permissions
- Channel reports
- Attribute metadata
- Entity validation templates
- Batch job to purge Commerce Data Exchange session history

Additionally, logging that is related to the payment card industry (PCI) is enabled for the Commerce database.

> [!NOTE]
> There is an option to separately configure the Commerce scheduler. This option lets you reset the Commerce scheduler configuration to its default settings.

After initialization is completed, you must configure additional commerce data. Here are some examples:

- Commerce parameters
- Commerce scheduler parameters
- Commerce channels
- Registers and devices
- Assortments


[!INCLUDE[footer-include](../includes/footer-banner.md)]