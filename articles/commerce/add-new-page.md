---
# required metadata

title: Add a new site page
description: This topic describes how to add a new site page in Microsoft Dynamics 365 Commerce.
author: psimolin
ms.date: 02/03/2022
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

# Add a new site page

[!include [banner](includes/banner.md)]

This topic describes how to add a new site page in Microsoft Dynamics 365 Commerce.

After you've created templates and fragments for your site, the next step is to start to create pages that use them. To get started, you must select a template or layout, a page name, and a page URL.

## Template or layout

You can use either a template or a layout for your new page. For more information, see [Templates and layouts overview](templates-layouts-overview.md).

## Specify the page name

The page name must be unique to your site and should be descriptive so you can find it easily and other people know what the page is intended for. You can rename your page later by editing it and then selecting the pen symbol next to the page name in the property pane.

## Specify the page URL

You can have the option to enter a URL for your new page. When you create a page, you can enter a string that will be used to form a complete URL. This string is known as a relative URL or a URL slug. A complete URL is then generated based on the URL slug, and the new page is assigned to it. You can change the URL slug later, before you publish the page. For more information, see [Create a page URL](create-page-URL.md).

> [!NOTE]
> Dynamics 365 Commerce decouples URLs and content. In other words, a page can be created that isn't associated with an URL, and a URL can be created that isn't associated with a page. Therefore, content swapping can be done for a URL and doesn't require downtime, and redirects are easier to manage.

## Add a new page

To add a new site page to your site, follow these steps.

1. Under **Sites**, select **Fabrikam** (or the name of your site).
1. Select **New Page**.
1. In the **New Page** dialog box, select a template, and then select **OK**.
1. In the **Page Name** field, enter a page name (for example, **My New Page**).
1. In the **URL** field, enter a string (URL slug) to complete the URL (for example, **mynewpage**).
1. Select **OK**. The page editor appears. Notice that a header and a footer are automatically added to the page, based on the template that you selected.
1. In the page outline, select the **Main** slot, select the ellipsis button (**...**), and then select **Add Module**.
1. Select **Container**, and then select **OK**
1. Select **Fluid Container**, select the ellipsis button, and then select **Add Module**.
1. Select **Content Rich block**, and then select **OK**.
1. Select **Content Rich Block**, select the ellipsis button, and then select **Add Module**.
1. Select **Content rich block item**, and then select **OK**.
1. In the properties pane on the right, select **Paragraph**, and then, in the field, enter **My test text**.
1. Select **Save**, and then select **Finish editing**.
1. In the **Comments** field, enter **Added new page**, and then select **OK**.
1. Select **Preview** to preview your page. When you've finished, close the preview tab to return to the authoring tool.
1. Select **Publish**.
1. In the navigation path (breadcrumbs), select **Fabrikam** (or the name of your site).
1. In the navigation pane on the left, select **URLs**.
1. Find and select your URL (**mynewpage**) in the list.
1. Select **Publish**.

## Additional resources

[Modify an existing site page](modify-existing-page.md)

[Select page layouts](select-page-layouts.md)

[Manage SEO metadata](manage-seo-metadata.md)

[Save, preview, and publish a page](save-preview-publish-page.md)

[Enrich a product page](enrich-product-page.md)

[Enrich a category landing page](enrich-category-page.md)

[Verify page content accessibility](verify-accessibility.md)

[Create dynamic e-commerce pages based on URL parameters](create-dynamic-pages.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
