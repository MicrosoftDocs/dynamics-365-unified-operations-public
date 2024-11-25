---
title: Save, preview, and publish a page
description: This article describes how to save, preview, and publish a page in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 07/31/2024
ms.topic: how-to
audience: Application user
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Save, preview, and publish a page

[!include [banner](includes/banner.md)]

This article describes how to save, preview, and publish a page in Microsoft Dynamics 365 Commerce.

## Save a page

To save a page, you must have it checked out to yourself and open in the page editor. To check out a page, select **Edit** on the command bar. After you've finished editing a page, you should immediately save it to ensure that your changes are stored.

When you save a page, the changes are visible only to you. The save operation is intended primarily to store changes while the page isn't yet ready to be checked in. When you've finished modifying the page, we recommend that you check it in, so that the changes become visible to others. At that point, the page can also be checked out by other users who must modify it.

## Preview a page

The authoring tool offers two kinds of preview features: visual page builder, which is a "what you see is what you get" (WYSIWYG) preview pane in the page editor, and a separate preview window.

While you're using the page editor, a "what you see is what you get" (WYSIWYG) preview appears in the center pane. This preview is automatically updated whenever you save the page. You can also manually update it by selecting **Refresh** on the command bar. The preview renders the page just as the site's users will see it, but authoring helpers are rendered on top of it.

When you've finished modifying the page, you might want to preview it to see what customers will see. To preview a page, select **Preview** on the command bar. The preview will appear in a separate browser window. The page in the preview window is rendered just as the site's user will see it. You can resize the window to make sure that responsive modules are correctly rendered in all view ports.

> [!NOTE]
> Authentication and correct permissions are required to preview unpublished content. Therefore, if you share the URL of the preview with someone, that person must have the correct permissions to access the content.

## Publish a page

When your page is ready, the next step is to publish it, so that external users can view the content. Before you can publish a page, you must check it in by selecting **Finish editing** on the command bar.

You can publish and unpublish pages from either the page inspector or the page editor. The page inspector shows a list of pages and allows for bulk operations. The page editor can be used to publish or unpublish only the single page that is open in it.

To publish one or more pages from the page inspector, select the pages, make sure that they are checked in, and then select **Publish** on the command bar. The pages are published, and you receive a notification about the operation in the authoring tool.

To publish a single page from the page editor, the procedure is similar. While the page is open in the page editor, make sure that it has been checked in, and then select **Publish** on the command bar. The page is published, and you receive a notification about the operation.

When you publish a page, just the page content is published. You and other users can go to the page and view it only after a URL is associated with it. The URL must be published separately.

> [!IMPORTANT]
> Before you can publish a page, any images or fragments that the page references must already be published.

## Save, preview, and publish a home page

To save, preview, and publish a home page, follow these steps.

1. Under **Sites**, select **Fabrikam** (or the name of your site).
1. In the navigation pane on the left, select **Pages**.
1. Find and select the home page to open it in the page editor.
1. Select **Edit**.
1. Modify the page as you require.
1. Select **Save**, and then select **Finish editing**.
1. In the **Comments** field, enter a note about the changes that you made, and then select **OK**.
1. Select **Preview** to preview your page. When you've finished, close the preview tab to return to the authoring tool.
1. Select **Publish**.

## Publish a URL

To publish a URL, follow these steps.

1. Under **Sites**, select **Fabrikam** (or the name of your site).
1. In the navigation pane on the left, select **URLs**.
1. Find and select the URL to publish.
1. On the command bar, select **Publish**.

## Additional resources

[Modify an existing site page](modify-existing-page.md)

[Add a new site page](add-new-page.md)

[Select page layouts](select-page-layouts.md)

[Manage SEO metadata](manage-seo-metadata.md)

[Enrich a product page](enrich-product-page.md)

[Enrich a category landing page](enrich-category-page.md)

[Verify page content accessibility](verify-accessibility.md)

[Create dynamic e-commerce pages based on URL parameters](create-dynamic-pages.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
