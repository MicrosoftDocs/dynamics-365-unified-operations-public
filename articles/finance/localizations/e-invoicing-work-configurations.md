---
# required metadata

title: Work with Configurations
description: This topic provides main scenario overview of working with ER configurations from Globalization features workspace.
author: dkalyuzh
ms.date: 01/26/2022
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

# Work with Configurations

[!include [banner](../includes/banner.md)]


A main set of components in the Electronic invoicing feature are the Electronic reporting (ER) configurations. ER configurations contain the setup of the file structure and a set of transformation rules to transform data in two ways:
 
    - Export ER Format configuration: From a unified internal structure (ER Model) to the electronic file format. 
    - Import ER Format configuration: From the electronic file to the unified internal structure (ER Model). 

In addition to outbound electronic file generation in the predefined format, ER configurations are widely used to parse incoming messages from external Web services as responses. This parsing helps to build configurable logic to receive the results of communication with external channels. The logic can also convert the codes, messages, and logs to the user-readable structure and then pass that information to the client application.

To start using ER configurations in your Electronic invoicing feature, the configurations must be linked to the feature and available on the **Configurations** tab for the current feature version. Work with the linked ER configuration by selecting **Add**, **Delete**, **Edit**, or **View**.

To add a link to ER configuration, the link must exist in your RCS repository. To review ER configurations available in your RCS repository, complete the following steps.

 1. Sign in to your RCS account.
 2. In the **Electronic reporting** workspace, in the **Configurations** section, select the **Reporting configurations** tile.

To create a new ER configuration, or import an existing ER configuration from the Global repository, see [Electronic reporting](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md).

To adjust a linked ER configuration, select **Edit** on the **Configurations** tab for the current Electronic invoicing feature. The system automatically creates a derived version of the ER configuration with your Configuration provider, if the current version is created by a configuration provider that isn't active. Or, a new version is created if the current version is created by the active configuration provider. You can modify the new version of the configuration and then automatically complete the necessary updates.
