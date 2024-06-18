---
title: Work with configurations
description: Learn about the main scenario for working with Electronic reporting (ER) configurations from the Globalization features workspace (RCS).
author: ilikond
ms.author: ikondratenko
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 06/17/2024
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Global
ms.search.validFrom: 
ms.dyn365.ops.version: 
---

# Work with configurations

[!include [banner](../../includes/banner.md)]

Electronic reporting (ER) configurations are one of the main sets of components of electronic invoicing features. An ER configuration contains the setup of the file structure and a set of transformation rules for transforming data in two ways:

- **Export ER format configuration** – This configuration transforms data from the unified internal structure (ER model) to the electronic file format.
- **Import ER format configuration** – This configuration transforms data from the electronic file format to the unified internal structure (ER model).

In addition to generating outbound electronic files in the predefined format, ER configurations are widely used to parse incoming messages from external web services as responses. This functionality helps build configurable logic to get the results of communication with external channels, convert those results (codes, messages, and logs) to the user-readable structure, and then pass that information to the client application.

To start to use ER configurations in your electronic invoicing feature, you must link them to the feature and make them available on the **Configurations** tab for the current feature version. You can work with a linked ER configuration by selecting **Add**, **Delete**, **Edit**, or **View**.

Before you can add a link to an ER configuration, the configuration must exist in your Regulatory Configuration Service (RCS) repository. To review the ER configurations that are available in your RCS repository, follow these steps.

1. Sign in to your RCS account.
2. In the **Electronic reporting** workspace, in the **Configurations** section, select the **Reporting configurations** tile.

For information about how to create a new ER configuration or import an existing ER configuration from the Global repository, see [Electronic reporting](../../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md).

To adjust a linked ER configuration, select **Edit** on the **Configurations** tab for the current electronic invoicing feature. The system automatically creates a version of the ER configuration. If the current version wasn't created by the active configuration provider, the system creates a derived version that uses your configuration provider. If the current version was created by the active configuration provider, the system creates a new version. In both cases, you can modify the version that is created and then automatically do all required updates.
