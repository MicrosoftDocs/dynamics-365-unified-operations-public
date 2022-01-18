---
# required metadata

title: Import feature from Global repository
description: This topic provides description of the process of importing Globalization features from Global repo.
author: dkalyuzh
ms.date: 12/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
---

# Import feature from Global repository

[!include [banner](../includes/banner.md)]


Global repository contains Electronic invoicing featured (Globalization features) shared with your Configuration provider ([Setup Regulatory Configuration Services (RCS)](e-inv_tut-setup-electronic-invoicing_setup-RC.md)). All Electronic invoicing features delivered by Microsoft are shared with all companies, thus you will have an access by default to all Electronic invoicing features released and published to Global repository by Microsoft.

To start working with Electronic invoicing feature shared with your company (Configuration provider), you need to import it to your RCS instance from Global repository. Then you will be able to review the feature details, including Electronic reporting configurations, and Processing pipelines, in a view mode.


## Import feature from Global repository
  1. Sign in to your RCS account.
  2. In the **Globalization feature** workspace, in the **Features** section, select the **Electronic invoicing** tile.
  3. Select **Import** menu item to open **Import feature from Global repository** lookup.
  4. To browse the electronic invoicing features that are available in the Global repository for a specific configuration provider, sync your organization's RCS instance. After synchronization is completed, the list of available electronic invoicing features is updated. In the lookup select **Synchronize** button. It may take some time to refresh the list of features from Global repository.

  
  5. Select feature you want to import in select **Import** button.

To see imported Electronic invoicing features, make sure that proper Configuration provider is selected. By default, features created by active Configuration provider are filtered out. You can adjust the filter to see other providers, including Microsoft Configuration provider.

	

You are ready to work with the imported feature:
  - You can review the details of the feature on the right tabs
  - You can create new feature from imported one using it as a template

> [!NOTE]
> You can't do any modifications of the feature if it is created by configuration provider different from Active one. You must create a new feature using the original one as a base feature. Then you will be able to do all necessary modifications or setup of parameters.
	
	
When Microsoft or other company that shares Globalization features with your company update the features that you imported, you can easily check for updated version by selecting **Check for feature updates** under **Related settings**.



If you see that there are updates of the feature you use as a template, you can import new version after synchronization of the  list of published features in Global repository.
