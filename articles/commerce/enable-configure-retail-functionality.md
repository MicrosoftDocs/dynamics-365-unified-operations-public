---
title: Initialize seed data in new Commerce environments
description: Learn about the data created as part of the initialization process for Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 01/22/2026
ms.topic: how-to
ms.search.form: RetailParameters
ms.reviewer: v-griffinc
ms.assetid: 4dc762eb-190e-4485-8f55-b0cafc81bc37
ms.search.region: Global
ms.author: anvenkat
ms.search.validFrom: 2016-02-28
ms.custom: 
  - bap-template
---

# Initialize seed data in new Commerce environments

[!include [banner](includes/banner.md)]

This article describes the data created as part of the initialization process for Microsoft Dynamics 365 Commerce.

After you deploy the Commerce solution through Microsoft Dynamics Lifecycle Services (LCS), initialize the Commerce configuration to create the basic configuration data.

> [!IMPORTANT]
> Before you initialize the Commerce configuration, make sure that you specify a language and a postal address for each legal entity where you set up stores. You must complete this step for each legal entity that you use for commerce.

To initialize the configuration, follow these steps:

1. Start the Commerce client.
1. Select **Retail and Commerce > Headquarters setup > Parameters > Commerce parameters**.
1. Select **Initialize**.

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

Additionally, the process enables logging that relates to the payment card industry (PCI) for the Commerce database.

> [!NOTE]
> You can separately configure the Commerce scheduler. This option lets you reset the Commerce scheduler configuration to its default settings.

After initialization is complete, you must configure additional commerce data. Here are some examples:

- Commerce parameters
- Commerce scheduler parameters
- Commerce channels
- Registers and devices
- Assortments

[!INCLUDE[footer-include](../includes/footer-banner.md)]
