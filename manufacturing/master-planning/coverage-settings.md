---
# required metadata

title: Coverage settings
description: Master scheduling uses coverage settings to calculate item requirements. 
author: YuyuScheller
manager: AnnBe
ms.date: 2015-09-10 08 - 46 - 42
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: ReqGroup, ReqItemTable, ReqItemTableWizard
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: YuyuScheller
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 2494
ms.assetid: cc62c000-e640-4121-b1fa-9a0c74c3f627
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: roxanad
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Coverage settings

Master scheduling uses coverage settings to calculate item requirements. 

You can specify coverage settings in several ways:

-   Specify coverage settings for a coverage group. You can create a coverage group that contains settings for all products that are linked to the coverage group. Click **Master planning &gt; Setup &gt; Coverage &gt; Coverage groups** to create a coverage group. You can link a coverage group to a product. If the link is specific to a site, warehouse, or product dimension, use the **Coverage group** field on the **Item coverage** page. If the link is generic, regardless of the product dimensions, use the **Coverage group** on the **Plan** FastTab on the **Product details** page. If you do not link a coverage group to a product, master planning uses the **General coverage group** that is specified on the **Master planning parameters** page as the default.

-   Specify coverage settings for a product. You can create coverage settings for a specific product. Click **Product information management &gt; Products &gt; Released products**. Select the product, on the **Action Pane**, on the **Plan** tab, in the **Coverage group**, click **Item coverage** to open the **Item coverage** page. If the product is already linked to a coverage group, you can override the coverage group settings by using the **Override** field. The coverage settings on the **Item coverage** page take precedence over the settings on the **Coverage group** page.

<!-- -->

-   Specify coverage settings for a product by using a wizard. The wizard is a step-by-step guide to help you set up the primary item coverage parameters. On the **Item coverage** page, click **Wizard** to open the **Item Coverage Wizard**.

<!-- -->

-   Specify coverage settings for a dimension group. Click **Product information management &gt; Common &gt; Released products**. On the **Released product detail **page, on the **General** tab, in the **Administration** group, click the **Storage dimension group** link. On the **Storage dimension group** page, select the **Coverage plan by dimension** field to create the coverage settings for a dimension in the storage dimension group. All product dimensions, such as configuration, color, size, style, must have the **Coverage plan by dimension** field selected.



See also
--------

[Master plans](master-plans.md)

