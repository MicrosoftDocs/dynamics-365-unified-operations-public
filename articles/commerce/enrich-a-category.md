---
# required metadata

title: Enrich a category landing page
description: This topic describes what enriching a category means and how you can do that from the authoring tool in Dynamics 365 for Commerce.
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

This topic describes what enriching a category page means and how you can do that from the authoring tool in Dynamics 365 for Commerce e-Commerce.

Commerce provides a default category landing page that is used when rendering category data. A default category page contains required elements such as refiners, categorized product placement, sorting options, choice summary, and pagination controls. Instead of using a default page, you can instead define a different category page for a specific category.

 ![Enriched category landing page](./media/CategoryLandingPages.png)

On the **Retail** page in the authoring tool, there is a list of categories from the channel assigned to the site. If a category page has the status "enriched" selected, that category page has been enriched. If "enriched" is not selected for a page, the category page for that specific category will use the default category page and content. You can preview the category page for both enriched and non-enriched categories by clicking the category name.

In many cases, you will want to enrich a category landing page so that it will have more content and more specific elements. A typical enrichment may include adding category-specific marketing content on the category page, including cross-category product placement for cross-sell purposes, editorial lists, images, videos, and other text. 

To enrich a category page, do the following.

1. In the **Retail** view, click the name of the category you want to entrich. The category page will open in the page editor and render using the default category page. 
1. Click **Enrich category page** on the ribbon. 
1. Select a template for your enriched category page. You can select the default category page if you want to make minor modifications, or you can select a specific category page template if needed. When you select the template, the page editor will open and a new page is created for the category using the template you selected. The page will be checked out to you and you can now make your modifications.

> [!NOTES]
> Modules that use category specification data will use the date from your selected category. 
> The settings of the template you selected will determine what modifications you can make. 
