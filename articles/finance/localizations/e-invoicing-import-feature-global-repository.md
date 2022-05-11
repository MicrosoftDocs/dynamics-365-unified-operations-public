---
# required metadata

title: Import features from the Global repository
description: This topic explains how to import Globalization features from the Global repository.
author: dkalyuzh
ms.date: 02/11/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkalyuzh
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Import features from the Global repository

[!include [banner](../includes/banner.md)]

The Global repository contains Electronic invoicing features that are shared with your configuration provider. All Electronic invoicing features that are provided by Microsoft are shared with all companies. You automatically have access to all the Electronic invoicing features that Microsoft releases and publishes to the Global repository.

To start to work with Electronic invoicing features that are shared with your configuration provider, import them into your instance of Regulatory Configuration Service (RCS) from the Global repository. Then review the feature details, such as the Electronic reporting (ER) configurations and processing pipelines.

## Import a feature from the Global repository

1. Sign in to your RCS account.
2. In the **Globalization feature** workspace, in the **Features** section, select the **Electronic invoicing** tile.
3. Select **Import** to open the **Import feature from Global repository** lookup.
4. To browse the Electronic invoicing features in the Global repository that are available for a specific configuration provider, synchronize your organization's RCS instance by selecting **Synchronize**. After synchronization is completed, the list of available Electronic invoicing features is updated from the Global repository. This update might take a few minutes.
5. Select the feature to import, and then select **Import**.

To view the imported Electronic invoicing feature, make sure that the correct configuration provider is selected. By default, features that were created by the active configuration provider are automatically filtered out. You can adjust the filter to view features that were created by other providers, such as the Microsoft configuration provider.

You can now work with the imported feature. You can review its details and create a new feature by using the imported feature as a template.

> [!NOTE]
> You can modify a feature only if it was created by the configuration provider that is currently active. You can create a new feature by using the original feature as a base. You can then make the required changes or set up the parameters.

When Microsoft or another company that shares Globalization features with your company updates features that you've imported, you can check for updated versions by selecting **Check for feature updates** in the **Related settings** section of the **Globalization features** workspace.

If you see that there are updates for a feature you use as a template, you can import a new version after you synchronize the list of published features in the Global repository.
