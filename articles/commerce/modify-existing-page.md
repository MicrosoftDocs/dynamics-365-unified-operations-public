---
title: Modify an existing site page
description: Learn how to modify an existing site page in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 01/23/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Modify an existing site page

[!include [banner](includes/banner.md)]

This article describes how to modify an existing site page in Microsoft Dynamics 365 Commerce.

When you need to modify a page, open it in the page editor. Go to the site that contains your page, and then, in the list of pages, find the page that you want. If you can't find the page, use the authoring tool's rich search functionality. Either type the exact page name, or type the first few letters of it and then an asterisk (*). A filtered list of pages appears. You can use this list to find the page that you want. After you find the correct page, select the page name to open the page in the page editor.

> [!TIP]
> If your page is visible in the page inspector, you can select **Edit** and check out the page before you open it in the page editor. In this way, you can check out multiple pages at the same time.

After you open the page in the page editor, make sure that you check out the page. The command bar in the authoring tool is dynamic, context-sensitive, and state-sensitive. Therefore, it shows only the actions that you can currently perform on the page. For example, if you don't check out the page, the **Save** and **Finish editing** buttons don't appear on the command bar. The state of the page is also shown on the right side of the window.

If you didn't check out the page, select **Edit** on the command bar. The command bar changes to reflect the new state of the page. You also receive a notification that states that you checked out the page.

Next, make your changes. Often, you use the page outline tree to find and select the module that you want to change, and then make changes in the properties pane on the right. 

However, your change might sometimes involve adding or removing models or fragments. To add a fragment or module, use the page outline tree to find the slot that you want to add the module or fragment to, and then select the ellipsis button (**...**) for that slot. A menu appears that includes commands for adding a module or fragment. To remove a module or fragment, find and select it in the page outline tree, select the ellipsis button, and then select the command to delete the module or fragment.

> [!TIP]
> You can also view and edit the properties for any module that's visible in the visual page builder preview by selecting it directly.

After you finish making your changes and previewing their effect, check in the page by selecting **Finish editing** on the command bar. 

To publish your changes immediately, select **Publish** on the command bar. The latest checked-in version of the page that you modified is published and becomes available to external users who view your site. 

## Example: Change the video on the home page

The following example shows how to modify the home page by changing the video that appears in the video player module.

1. Under **Sites**, select **Fabrikam** (or the name of your site).
1. In the navigation pane on the left, select **Pages**.
1. Find and select the home page to open it in the page editor.
1. On the command bar, select **Edit**.
1. In the page outline, select the **Main** slot.
1. Under the **Main** slot, expand all the fluid container modules.
1. Find and select the video player module.
1. In the properties pane on the right, select the **video** property. The asset picker appears.
1. In the asset picker, select an available video asset, or select **Upload new asset** to upload a new video asset.
1. Select **OK**.
1. Select **Save**, and then select **Finish editing**.
1. In the **Comments** field, enter **Changed the video**, and then select **OK**.
1. Select **Preview** to preview the updated page. When you finish, close the preview tab to return to the authoring tool.
1. Select **Publish**.

## Additional resources

[Add a new site page](add-new-page.md)

[Select page layouts](select-page-layouts.md)

[Manage SEO metadata](manage-seo-metadata.md)

[Save, preview, and publish a page](save-preview-publish-page.md)

[Enrich a product page](enrich-product-page.md)

[Enrich a category landing page](enrich-category-page.md)

[Verify page content accessibility](verify-accessibility.md)

[Create dynamic e-commerce pages based on URL parameters](create-dynamic-pages.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
