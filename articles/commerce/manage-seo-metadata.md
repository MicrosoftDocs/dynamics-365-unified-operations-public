---
# required metadata

title: Manage SEO metadata
description: This topic describes how to manage search engine optimization (SEO) metadata in Microsoft Dynamics 365 Commerce.
author: psimolin
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
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: psimolin
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# Manage SEO metadata


[!include [banner](includes/banner.md)]

This topic describes how to manage search engine optimization (SEO) metadata in Microsoft Dynamics 365 Commerce.

## Overview

SEO metadata for a site can be managed by using site maps and page metadata.
	
## Site maps

A site map is a machine-readable list, in XML format, of the pages on your website. It's intended to be consumed by search engines, so that they can provide better search results from your site. Site maps can be manually ingested by search engines or published in a robots.txt file.

Dynamics 365 Commerce supports automatic generation of site maps. Site maps are automatically updated when pages are published and unpublished.

### Turn on site map generation

1. Sign in to the authoring tool.
1. Under **Sites**, select **Fabrikam** (or the name of your site).
1. In the navigation pane on the left, select **Site Management**.
1. Make sure that the **Site maps enabled** option is turned on.

## Page metadata

Dynamics 365 Commerce lets you manage SEO metadata for individual pages. You can view and modify this information in the **SEO Properties** section of a page container. The following SEO metadata properties are supported:

- Title
- Description
- SEO keywords
- Aria labels
- noindex
- nofollow
- noarchive
- nocache
- noOpenDirectoryProject
- nosnippet
- noImageIndex
- unavailableAfter

### Modify page metadata

To modify page metadata, follow these steps.

1. Under **Sites**, select the **Fabrikam** (or the name of your site).
1. In the navigation pane on the left, select **Pages**.
1. Select the home page to open it in the page editor.
1. On the Action Pane, select **Check Out**.
1. In the properties pane on the right, expand **Default metatags**.
1. To add a new metatag, select **Add**, and then enter the tag in the field.

    To remove an existing metatag, select the trash can symbol to the right of it.

1. Select **Save**, and then select **Check In**.
1. In the **Comments** field, enter **Updated metatags**, and then select **OK**.
1. Select **Preview** to preview your page. When you've finished, close the preview tab to return to the authoring tool.
1. Select **Publish**.

## Additional resources

[Modify an existing site page](modify-existing-page.md)

[Add a new site page](add-new-page.md)

[Select page layouts](select-page-layouts.md)

[Save, preview, and publish a page](save-preview-publish-page.md)

[Enrich a product page](enrich-product-page.md)

[Enrich a category landing page](enrich-category-page.md)

[Verify page content accessibility](verify-accessibility.md)
