---
# required metadata

title: Enrich a category landing page
description: This topic describes what is meant by enrichment of a category page and explains how you can enrich a category page by using the authoring tool in Microsoft Dynamics 365 for Commerce e-Commerce.
author: josaw1
manager: annbe
ms.date: 08/30/2019
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Consumer
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: Ashish Harchwani
ms.search.validFrom: 2019-08-30
ms.dyn365.ops.version: 
---

# Enrich a category landing page

This topic describes what is meant by enrichment of a category page. It also explains how you can enrich a category page by using the authoring tool in Microsoft Dynamics 365 for Commerce e-Commerce.

Dynamics 365 for Commerce provides a default category landing page that is used when category data is shown. A default category page contains required elements, such as refiners, categorized product placement, sorting options, choice summary, and pagination controls. 

However, instead of using the default category page, you might want to use an "enriched" category landing page that has more content and more specific elements. A typical enrichment might involve adding category-specific marketing content to the category page. This content might include cross-category product placement for cross-sell purposes, editorial lists, images, videos, and other text. You can either modify the default category page or define a different category page for a specific category.

![Enriched category landing page](./media/CategoryLandingPages.png)

In the authoring tool, the **Retail** page includes a list of categories from the channel that are assigned to the site. If the **Enriched** status is selected for a category page, that category page has been enriched. Otherwise, the default category page and content are used for the category. You can preview both the enriched and non-enriched category pages for a category by selecting the category name.

To enrich a category page, follow these steps.

1. On the **Retail** page, select the name of the category that you want to enrich the category page for. The default category page for the selected category is opened in the page editor.
2. Select **Enrich category page**.
3. Select a template for the enriched category page. If you're making only minor changes, you can select the default category page. Alternatively, you can select a specific category page template. When you select the template, the page editor is opened, and the selected template is used to create a new category page for the selected category. The page is checked out to you, and you can now make your changes.

> [!NOTE]
> Modules that use category specification data use the date from your selected category.
>
> The settings of the template that you select determine the changes that you can make.
