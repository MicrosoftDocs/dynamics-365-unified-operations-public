---
title: Manage SEO metadata
description: This article describes how to manage search engine optimization (SEO) metadata in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 04/21/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application user
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5
ms.custom: 
ms.assetid: 
---

# Manage SEO metadata

[!include [banner](includes/banner.md)]

This article describes how to manage search engine optimization (SEO) metadata in Microsoft Dynamics 365 Commerce.

SEO metadata for a site can be managed by using site maps and page metadata.
	
## Site maps

A site map is a machine-readable list, in XML format, of the pages on your website. It's intended to be consumed by search engines, so that they can provide better search results from your site. Site maps can be manually ingested by search engines or published in a robots.txt file.

Dynamics 365 Commerce supports either automatic generation of site maps or manual curation. When the automated site map feature is enabled, site maps are automatically updated when pages are published and unpublished.

### Option 1: Enable automated site map generation

1. Sign in to the **site builder** authoring toolset.
1. Under **Sites**, select the name of your site (example: Adventure Works).
1. In the navigation pane on the left, expand the **Site settings** control at the bottom.
2. Select the **General** tab.
3. Set the **Site maps enabled** control to **On**.
4. Click the **Save and publish** button in the command bar.

> [!NOTE]
> Once automated site maps are enabled, it will take some time for the initial site map to be written.  This can be monitored in the **[Your site] > Site settings > General > Site map additional data** where the site map generation state, status, last execution datetime, and content update datetime is displayed. Any new content publish action (example: new page or URL published), will trigger an update to the site map file. Once the sitemap is generated, the URL(s)s to the file(s) can be found by navigating to **[Your site] > Site settings > General > Site map URLs**


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
1. On the command bar, select **Edit**.
1. In the page editor, at the top of the page outline control on the left, select the **Outline mode option** (gear symbol), and then select **Advanced outline view**.
1. In the outline view, expand the tree controls to show the contents of the **HTML head** slot.
1. In the **HTML head** slot, select the desired SEO module (for example, **Page summary**, **Product page summary**, **Category page summary**, or **Metatags**).
1. In the properties pane on the right, edit the desired SEO data for the selected SEO module (for example, **Title**, **Description**, or **Sharing image**).
1. Select **Save**, and then select **Finish editing**.
1. In the **Comments** field, enter **Updated SEO data**, and then select **OK**.
1. Select **Preview** to preview your page. When you've finished, close the preview tab to return to the authoring tool.
1. Select **Publish**.

> [!TIP]
> Authors can use the **Outline mode option** (gear symbol) at the top of the left outline control in the page editor to switch between **Basic outline view** and **Advanced outline view**. **Basic outline view** is the default setting and filters the outline so that it shows only modules in the **Body** HTML slot for a page. **Advanced outline view** shows the whole page module, including **HTML head**, **Body begin**, and **Body end** slots. This view is useful when authors must edit specific SEO or script module settings for a page.

## Additional resources

[Modify an existing site page](modify-existing-page.md)

[Add a new site page](add-new-page.md)

[Select page layouts](select-page-layouts.md)

[Save, preview, and publish a page](save-preview-publish-page.md)

[Enrich a product page](enrich-product-page.md)

[Enrich a category landing page](enrich-category-page.md)

[Verify page content accessibility](verify-accessibility.md)

[Create dynamic e-commerce pages based on URL parameters](create-dynamic-pages.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
