---
# required metadata

title: Enrich a category landing page
description: This topic covers the enrichment of category pages in Dynamics 365 Commerce.
author: v-chgri
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope:  Operations, Retail, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5
---

# Enrich a category landing page


[!include [banner](includes/banner.md)]

This topic covers the enrichment of category pages in Dynamics 365 Commerce.

## Overview

Commerce provides a default category landing page that is used when category data is shown. A default category page contains required elements, such as refiners, categorized product placement, sorting options, a choice summary, and pagination controls. 

However, instead of using the default category page, you might want to use an "enriched" category landing page that has more content and more specific elements. A typical enrichment might involve adding category-specific marketing content to the category page. This content might include cross-category product placement for cross-sell purposes, editorial lists, images, videos, and other text. You can either modify the default category page or define a different category page for a specific category.

![Enriched category landing page](./media/CategoryLandingPages.png)

In the authoring tool, the **Product** page includes a list of categories from the channel that are assigned to the site. If the **Enriched** status is selected for a category page, that category page has been enriched. Otherwise, the default category page and content are used for the category. You can preview both the enriched and non-enriched category pages for a category by selecting the category name.

To enrich a category page, do the following.

1. On the **Products** page, select the name of the category that you want to enrich the category page for. The default category page for the selected category is opened in the page editor.
2. Select **Enrich category page**.
3. Select a template for the enriched category page. If you're making only minor changes, you can select the default category page. Alternatively, you can select a specific category page template. When you select the template, the page editor is opened, and the selected template is used to create a new category page for the selected category. The page is checked out to you, and you can now make your changes.

> [!NOTE]
> Modules that use category specification data use the data from your selected category.
>
> The settings of the template that you select determine the changes that you can make.

## Additional resources

[Modify an existing site page](modify-existing-page.md)

[Add a new site page](add-new-page.md)

[Select page layouts](select-page-layouts.md)

[Manage SEO metadata](manage-seo-metadata.md)

[Save, preview, and publish a page](save-preview-publish-page.md)

[Enrich a product page](enrich-product-page.md)

[Verify page content accessibility](verify-accessibility.md)
