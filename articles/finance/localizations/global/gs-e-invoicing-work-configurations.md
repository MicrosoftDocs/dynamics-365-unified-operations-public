---
title: Work with Electronic reporting (ER) configurations 
description: Access an overview of the main scenario for working with Electronic reporting (ER) configurations from the Globalization features workspace.
author: ilikond
ms.author: ikondratenko
ms.topic: article
ms.date: 01/29/2024
ms.custom: 
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2024-01-29
ms.search.form:
ms.dyn365.ops.version: 10.0.39 
---

# Work with Electronic reporting (ER) configurations

[!INCLUDE[banner](../../includes/banner.md)]

Electronic reporting (ER) configurations are one of the main sets of components of Electronic invoicing features. An ER configuration contains the setup of the file structure and a set of transformation rules for transforming data in two ways:

- **Export ER format configuration** – This configuration transforms data from the unified internal structure (ER model) to the electronic file format.
- **Import ER format configuration** – This configuration transforms data from the electronic file format to the unified internal structure (ER model).

In addition to generating outbound electronic files in the predefined format, ER configurations are widely used to parse incoming messages from external web services as responses. This functionality helps build configurable logic to get the results of communication with external channels, convert those results (codes, messages, and logs) to the user-readable structure, and then pass that information to the client application.

To start to use ER configurations in your Electronic invoicing feature, you must link them to the feature and make them available on the **Configurations** tab for the current feature version. You can work with a linked ER configuration by selecting **Add**, **Delete**, **Edit**, or **View**.

Before you can add a link to an ER configuration, the configuration must exist in your Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management environment. To review the available ER configurations, follow these steps.

1. In the **Globalization Studio** workspace, select the **Electronic reporting** tile.
1. In the **Configurations** section, select the **Reporting configurations** tile.

For information about how to create a new ER configuration or import an existing ER configuration from the Global repository, see [Electronic reporting](../../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md).

To adjust a linked ER configuration, select **Edit** on the **Configurations** tab for the current Electronic invoicing feature. The system automatically creates a version of the ER configuration. If the current version was created by the active configuration provider, the system creates a new version. If the current version wasn't created by the active configuration provider, the system creates a derived version that uses your configuration provider. In both cases, you can modify the version that's created and then automatically do all required updates.
