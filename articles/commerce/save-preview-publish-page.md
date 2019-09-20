---
# required metadata

title: Save, preview, and publish a page
description: This topic describes how to save, preview, and publish a page in Dynamics 365 Commerce.
author: psimolin
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
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

# Save, preview, and publish a page

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to save, preview, and publish a page in Dynamics 365 Commerce.

## Save a page

In order to save a page you need to have it checked out to you and open in the page editor. You should save a page immediately after modifying it to ensure that your changes are stored.

When you save a page, the changes are only visible only to you. Saving a page is primarily meant to be used for storing modifications when the page is not yet ready to be checked in. When you have finished modifying the page, it is recommended to check it in so that the changes become visible to others. It can then also be checked out by others who may need to modify the page.

## Preview a page

The authoring tool offers two kinds of preview features. WYSIWYG preview is visible in the middle pane when you are using the page editor. WYSIWYG preview is automatically refreshed when you save the page and can also be manually refreshed by clicking the **Refresh** button on the action ribbon. WYSIWYG preview renders the page as the end user will see it, but with authoring helpers rendered on top of the page. When you have finished modifying the page, you may want to preview the page to see exactly what the customer would see. To preview, click the **Preview** button on the action ribbon and the page preview will open up in a separate window. The page in the preview window is rendered exactly as the end user would see it. You can resize the browser to confirm that responsive modules are rendering correctly in all view ports. One thing to keep in mind is that previewing unpublished content requires authentication and proper permissions. If you share the URL to the preview, anyone who opens it needs to have proper permissions in order to access the content.

## Publish a page

When you have your page all ready to go, the next step is to publish it so that external users are able to see the content. Before publishing, the page needs to be checked in. You can publish and unpublish pages from either the page inspector or the page editor. Page inspector shows a list of pages and allows bulk operations. The page editor will always operate on the single page that is open in it.

If you want to publish your page(s) from the page inspector, you need to select your page(s), make sure they are checked in, and then click **Publish** on the action ribbon. This will publish the pages and you will see a notification in the authoring tool telling you that.

If you want to publish single page from page editor, the procedure is very similar. With the page open in the page editor, ensure that it has been checked in and then click **Publish** on the action ribbon. This will publish the page and display a publish notification.

When you publish a page, it publishes just the page. In order to be able to navigate to your page and see it, you must have a URL associated with it. The URL will need to be published separately.

One important thing to keep in mind is that to be able to publish a page, any images or fragments referenced by the page must have been published already.

## Save, preview, and publish a home page

To save, preview, and publish a home page, do the following.

1. Under **Sites**, click **Fabrikam** (or your site name).
1. On the left-side navigation pane, click **Pages**. Locate the home page and click it to open it in the page editor.
1. Click **Check Out**.
1. Make desired changes to the page.
1. Click **Save**, then click **Check In**. In the **Comments** text box, enter a note about the changes you made, then click **OK**.
1. Click **Preview** to preview your page. When done, close the preview tab to return to the authoring tool.
1. Click **Publish**.

## Publish a URL

To publish a URL, do the following.

1. Under **Sites**, click **Fabrikam** (or your site name).
1. On the left-side navigation pane, click **URLs**.
1. Locate and select the URL you want to publish.
1. Click **Publish** from the action bar.
