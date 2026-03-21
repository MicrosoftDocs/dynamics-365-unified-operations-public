---
title: Enable master data lookup for tax calculation configuration
description: Learn how to set up and enable the tax calculation master data lookup functionality, including an overview on installing finance and operations virtual entities.
author: kai-cloud
ms.author: pashao
ms.topic: how-to
ms.date: 03/19/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2021-04-01
ms.custom:
  - sfi-image-nochange
  - bap-template
---

# Enable master data lookup for tax calculation configuration 

[!include [banner](../../includes/banner.md)]

This article explains how to set up and enable the tax calculation master data lookup functionality. A dropdown list is available to select values in the tax calculation configuration for fields such as **Legal entity**, **Vendor account**, **Item code**, and **Delivery term**.

1. In the **Feature management** workspace, enable the **Enable applicability rules value lookup for Tax Calculation** feature.
    > [!NOTE]
    > Starting from version 10.0.43, you can't enable this feature through feature management. Instead, use the **Enable lookups in applicability rules** parameter in the **Tax feature setup**.

1. Make sure that you imported the latest configuration and model mapping versions. If you didn't, follow the steps in [Import Electronic reporting (ER) configurations from Dataverse](workspace/gsw-import-er-config-dataverse.md) to import them.

    - Tax Data Model.version.40.xml
    - Tax Calculation Data Model 40.65.xml
    - FNO Model Mapping 40.65.35.xml (For this model mapping, set the **Default for model mapping** parameter to **Yes**.)
    - Tax Calculation Configuration 40.65.249.xml

1. On the tax **Feature version** setup page, select configuration version 40.65.249.

    > [!NOTE] 
    > If you have a customized configuration, you must rebase the configuration and then use the customized configuration. 

1. In the **Source legal entity** field, select legal entities. You can choose master data from these legal entities.

:::image type="content" source="../media/tax-calculation-feature-master-data-lookup.png" alt-text="Screenshot of the Legal entity dropdown list in tax calculation feature master data lookup.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
