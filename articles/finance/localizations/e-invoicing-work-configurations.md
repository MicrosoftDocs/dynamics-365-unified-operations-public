---
# required metadata

title: Work with Configurations
description: This topic provides main scenario overview of working with ER configurations from Globalization features workspace.
author: dkalyuzh
ms.date: 12/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
---

# Work with Configurations

[!include [banner](../includes/banner.md)]


One of the main set of components of Electronic invoicing feature are Electronic reporting (ER) configurations. ER configuration contains the setup of the file structure and a set of transformation rules to transform data:
 - from unified internal structure (ER Model) to the electronic file format - export ER Format configuration
 - from electronic file to the unified internal structure (ER Model) - import ER Format configuration

In addition to outbound electronic file generation in the predefined format, ER configurations are widely used for parsing incoming messages from external Web services as responses. This helps to build configurable logic on getting the results of communication with external channels, and convert results (codes, messages, logs) to the user-readable structure, and further pass it over to the client application.

To start using ER configurations in your Electronic invoicing feature, they must be linked to the feature and available in **Configurations** tab for the current feature version. You can work with the linked ER configuration by selecting **Add**, **Delete**, **Edit**, and **View** buttons.

To **Add** a link to ER configuration, it must exist in your RCS repository. To review ER configurations available in your RCS repository:
 1. Sign in to your RCS account.
 2. In the **Electronic reporting** workspace, in the **Configurations** section, select the **Reporting configurations** tile.

If you want to create a new ER configuration, or import existing ER configuration from Global repository, follow instructions in documentation [Electronic reporting](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md).

If you want to adjust a linked ER configuration, select **Edit** in the Configurations tab for the current Electronic invoicing feature. System will automatically create a derived version of ER configuration with your Configuration provider, if the current version is created by not active configuration provider, or create a new version, if the current version is created by active configuration provider. Then system will allow you to modify the new version of the configuration and then automatically do all necessary updates.
