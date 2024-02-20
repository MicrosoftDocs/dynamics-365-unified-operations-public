---
title: Import features from the repository (preview)
description: This article explains how to import Globalization features from the Dataverse repository (preview).
author: ilikond
ms.date: 01/29/2024
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: ikondratenko
ms.search.validFrom: 2024-01-29
ms.dyn365.ops.version: 10.0.39
ms.custom: 
ms.assetid: 
ms.search.form: 
---

# Import features from the repository (preview)

[!INCLUDE[banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The Dataverse repository contains Electronic invoicing features that are shared with your configuration provider. All Electronic invoicing features that Microsoft provides are shared with all companies. You automatically have access to all the Electronic invoicing features that Microsoft releases and publishes to the Dataverse repository.

To start to work with Electronic invoicing features that are shared with your configuration provider, import them into your Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management environment from the Dataverse repository. Then review the feature details, such as the Electronic reporting (ER) configurations and processing pipelines.

## Import a feature from the Dataverse repository

1. In the **Globalization Studio** workspace, select the **Electronic invoicing** tile.
1. Select **Import** to open the **Import feature from Dataverse repository** lookup.
1. To browse the Electronic invoicing features that are available for a specific configuration provider in the Dataverse repository, select **Synchronize** to sync your organization's Finance or Supply Chain Management environment. After synchronization is completed, the list of available Electronic invoicing features is updated from the Dataverse repository. This update might take a few minutes.
1. Select the feature to import, and then select **Import**.

To view the imported Electronic invoicing feature, make sure that the correct configuration provider is selected. By default, features that the active configuration provider created are filtered out. You can adjust the filter to view features that were created by other configuration providers, such as Microsoft.

You can now work with the imported feature. You can review its details and create a new feature by using the imported feature as a template.

> [!NOTE]
> You can modify a feature only if it was created by the configuration provider that's currently active. You can create a new feature by using the original feature as a base. You can then make the required changes or set up the parameters.
