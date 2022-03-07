---
# required metadata

title: Manage SEO metadata
description: This topic describes how to manage search engine optimization (SEO) metadata in Microsoft Dynamics 365 Commerce.
author: psimolin
ms.date: 03/07/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
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
1. On the command bar, select **Edit**.
1. At the top of the left page outline, select the gear icon and choose **Advanced outline view**.
1. In the outline view, expand the the tree controls to show contents of the **HTML head** slot.
1. Select the desired SEO module within the HTML head slot (examples: "Page summary", "Product page summary, "Category page summary", "Metatags", etc.).
1. In the property pannel on the right, edit the desired SEO data for the chosen SEO module (examples: "Title", "Description", "Sharing image", etc.).
1. Select **Save**, and then select **Finish editing**.
1. In the **Comments** field, enter **Updated SEO data**, and then select **OK**.
1. Select **Preview** to preview your page. When you've finished, close the preview tab to return to the authoring tool.
1. Select **Publish**.

> [!TIP]
> The **gear icon** at the top of the left **outline** control in the page editor allows switching between **Advanced outline view** and a **Basic outline view**.  The **Basic outline view** is the default setting.  The basic view filters the outline to only display modules within the **Body** HTML slot for a page.  Selecting the **Advanced outline view** shows the entire page module, including **HTML head, Body begin, and Body end** slots.  This is useful when authors need to edit specific SEO or script module settings for a page.

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
