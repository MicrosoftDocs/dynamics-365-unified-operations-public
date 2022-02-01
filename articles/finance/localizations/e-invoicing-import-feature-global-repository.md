---
# required metadata

title: Import feature from Global repository
description: This topic provides description of the process of importing Globalization features from Global repo.
author: dkalyuzh
ms.date: 02/01/2022
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
ms.custom: 
ms.author: dkalyuzh
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Import a feature from the Global repository

[!include [banner](../includes/banner.md)]


The Global repository contains Electronic invoicing features that are shared with your configuration provider. All Electronic invoicing features delivered by Microsoft are shared with all companies. You automatically have access to all of the Electronic invoicing features that released and published to the Global repository by Microsoft.

To start working with Electronic invoicing features that are shared with your configuration provider, import the features to your Regulatory configuration service (RCS) instance from the Global repository. Then review the feature details, including Electronic reporting configurations and processing pipelines.


## Import feature from the Global repository

1. Sign in to your RCS account.
2. In the **Globalization feature** workspace, in the **Features** section, select the **Electronic invoicing** tile.
3. Select **Import** menu to open the **Import feature from Global repository** lookup.
4. To browse the electronic invoicing features that are available in the Global repository for a specific configuration provider, synchronize your organization's RCS instance. After synchronization is complete, the list of available electronic invoicing features is updated. In the lookup, select **Synchronize**. Refreshing the list of features from the Global repository might take a few minutes.
5. Select feature you want to import, and then select **Import**.

To see imported Electronic invoicing features, make sure that the proper configuration provider is selected. Features created by the active configuration provider are automatically filtered out. You can adjust the filter to see other providers, including the Microsoft configuration provider.


Now you are ready to work with the imported feature. You can review the details of the feature on selected tabs and create a new feature using an imported feature as a template.

> [!NOTE]
> You can't modify a feature if it's created by configuration provider that isn't active. Create a new feature using the original feature as a base. Then you can make the necessary modifications or set up the parameters.
	
	
When Microsoft or other companies that share Globalization features with your company update the features that you imported, check for updated versions by selecting **Check for feature updates** under **Related settings**.

If you see that there are updates of the feature you use as a template, import a new version after you synchronize the list of published features in the Global repository.
