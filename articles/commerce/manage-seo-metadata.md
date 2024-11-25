---
title: Manage SEO metadata
description: This article describes how to manage search engine optimization (SEO) metadata in Microsoft Dynamics 365 Commerce.
author: phinneyridge
ms.date: 01/31/2024
ms.topic: how-to
audience: Application user
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Manage SEO metadata

[!include [banner](includes/banner.md)]

This article describes how to manage search engine optimization (SEO) metadata in Microsoft Dynamics 365 Commerce.

SEO metadata for a site can be managed by using site maps and page metadata.
	
## Site maps

A site map is a machine-readable list, in XML format, of the pages on your website. It's intended to be consumed by search engines, so that they can provide better search results from your site. Site maps can be manually ingested by search engines or published in a robots.txt file.

Dynamics 365 Commerce supports both the automatic generation and manual curation of site maps. When the automated site map feature is enabled, site maps are automatically updated when pages are published and unpublished.

### Option 1: Enable automated site map generation

To enable automated site map generation in Commerce site builder, follow these steps.

1. Under **Sites**, select the name of your site (for example, **Adventure Works**).
1. In the left navigation pane, select **Site settings \> General**.
1. Set the **Site maps enabled** option to **On**.
1. Select **Save and publish**.

> [!NOTE]
> After automated site maps are enabled, the initial automated site map creation job takes some time to be completed, depending on the size of your site. You can monitor the job's progress in site builder at **Site settings \> General \> Site map additional data**. The site map generation state, status, last execution date/time, and content update date/time are shown. Any new content publish action (for example, if a new page or URL is published) automatically updates the site map file. After the site map is generated, you can find the URLs to the site map files at **Site settings \> General \> Site map URLs**.

### Option 2: Manually manage your site map

The automated site map solution works for most scenarios. However, in some cases, manual management of a site map is preferable, because it gives you more control over which pages you include or exclude. You can manually manage your site map by hosting the custom site map as a document binary in the site builder Media library and then updating your site's robots.txt file so that it points to the site map's URL.

> [!NOTE]
> Before you manually manage your site map, ensure that the automated site map generation feature is disabled.

To manually manage your site map and host it in the site builder Media library, follow these steps.

1. In the left navigation pane, select **Media library**.
1. Select **Upload \> Upload media items**.
1. In the File Explorer window, browse to your custom sitemap XML file, select it, and then select **Open**.
1. In the **Upload file** dialog box, select **Publish media items after upload**, and then select **Upload now**.
1. In the left navigation pane, select **URLs**.
1. On the command bar, select **New \> New URL**.
1. In the **Create new URL** flyout menu, under **Enter URL Path**, enter a URL segment name for your sitemap (for example, `https://<yourdomain.com>/<channelname>/<sitemapname>`).
1. Under **What are you creating a URL for?**, select **Media library document**, and then select **Next**.
1. In the **Select a document to link to** flyout menu, find and select the custom sitemap XML file that you uploaded previously, and then select **Create** to create a domain-specific URL for your sitemap file.
1. On the **URLs** page, select the new sitemap URL from the list, and then on the command bar select **Publish** 	to publish the URL.
1. From the URL properties pane on the right, under **Channel and locale variants**, right-click on the correct variant, and then select **Copy link** to save it for later.
    > [!NOTE]
    > If you don't see the  URL properties pane on the right, select the **i** symbol on the upper right next to the search box. This action toggles the URL properties pane between hidden and visible.
1. To validate that the URL is correctly linked to your sitemap XML file, open a new browser tab, paste in the sitemap URL, and select enter. If the sitemap doesn't appear or doesn't render correctly, review the previous steps to check your work.
1. Download your site's [robots.txt file](go-live/add-robots-txt.md), following the instructions in [Download a robots.txt file](manage-robots-txt-files.md#download-a-robotstxt-file). 
1. Open the robots.txt file in a text editor, and paste in the sitemap file URL that you copied to your clipboard in step 11 above into the **Sitemap** key-value pair, as shown in the following example.


```Plaintext
    User-agent: *
    Disallow: /editservice.asmx/
    Disallow: /images/
    Disallow: /scripts/
    Disallow: /syndicationservice.asmx/
    Disallow: /editconfig.aspx
    Disallow: /login.aspx
    
    Sitemap: <Your site map URL>
```

15. Save the robots.txt file, and then upload it to your site following the instructions in [Upload a robots.txt file](manage-robots-txt-files.md#upload-a-robotstxt-file). For go-live information about robots.txt files, see [Add or update a robots.txt file](go-live/add-robots-txt.md).

> [!TIP]
> Follow these steps to keep the URL of your site map file static. In this way, you can avoid having to update the robots.txt file the next time that you manually update your site map file.
>
> 1. Update the site map file on your local machine.
> 1. Go to the site builder Media library, and select your original site map file. 
> 1. On the command bar, select **Replace binary**. 
> 1. In the File Explorer window, browse to and select the updated site map file on your local machine.

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
