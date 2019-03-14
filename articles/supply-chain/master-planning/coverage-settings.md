---
# required metadata

title: Coverage settings
description: This topic provides information about the coverage settings that master scheduling uses to calculate item requirements.
author: roxanadiaconu
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqGroup, ReqItemTable, ReqItemTableWizard
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 2494
ms.assetid: 5a95ae4f-ca75-47d9-a1c3-68c97b42f166
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: roxanad
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Coverage settings

[!include [banner](../includes/banner.md)]

Master scheduling uses coverage settings to calculate item requirements.

You can specify coverage settings in several ways:

- Specify coverage settings for a coverage group.

    You can create a coverage group that contains settings for all products that are linked to the coverage group. To create a coverage group, go to **Master planning &gt; Setup &gt; Coverage &gt; Coverage groups**. You can link a coverage group to a product. If the link is specific to a site, warehouse, or product dimension, use the **Coverage group** field on the **Item coverage** page. If the link is generic, regardless of the product dimensions, use the **Coverage group** field on the **Plan** FastTab of the **Product details** page. By default, if you don't link a coverage group to a product, master planning uses the general coverage group that is specified on the **Master planning parameters** page.

- Specify coverage settings for a product.

    You can create coverage settings for a specific product. Go to **Product information management &gt; Products &gt; Released products**. Select the product, and then, on the Action Pane, on the **Plan** tab, in the **Coverage** group, select **Item coverage** to open the **Item coverage** page. If the product is already linked to a coverage group, you can override the coverage group settings by using the **Override** field. The coverage settings on the **Item coverage** page take precedence over the settings on the **Coverage group** page.

- Specify coverage settings for a product by using a wizard.

    The wizard guides you step by step through the process of setting up the primary item coverage parameters. On the **Item coverage** page, on the Action Pane, select **Wizard** to open the **Item Coverage Wizard**.

- Specify coverage settings for a dimension group.

    Go to **Product information management &gt; Products &gt; Released products**. On the **Released product details** page, on the **General** FastTab, in the **Administration** section, select the link in the **Storage dimension group** field. On the **Storage dimension groups** page, select the **Coverage plan by dimension** check box to create the coverage settings for a dimension in the storage dimension group. The **Coverage plan by dimension** field must be selected for all product dimensions, such as configuration, color, size, and style.

## Additional resources

[Master plans](master-plans.md)
