---
title: Customize product detail pages (PDPs)
description: This article describes how to customize product detail pages (PDPs) in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 07/28/2023
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

# Customize product detail pages (PDPs)

[!include [banner](includes/banner.md)]

This article describes how to customize product detail pages (PDPs) in Microsoft Dynamics 365 Commerce.

By default, your Dynamics 365 Commerce e-commerce site uses a generic PDP to display product data. This PDP includes basic information about the product, and page controls (for example, an add to cart button) that site visitors use to select and purchase the product. 

You can customize PDPs by supplementing them with information from the Commerce Scale Unit (CSU) such as additional images or product-specific text.

In many cases, you'll want to use specific additional content for your products. When you go to the **Products** tab in Commerce site builder, you'll see a list of products from the currently selected channel. You can preview product pages by selecting a product name in the list.

The following video provides an overview of PDP and category page customization rusing site builder.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RW1863o]

## Customize a product page

To customize a product page, follow these steps.

1. Under **Sites**, select **Fabrikam** (or the name of your site).
1. In the navigation pane on the left, select **Products**.
1. Select any product that doesn't have a customized product page.
1. On the Action Pane, select **Customize product page**.
1. Select a template for your custom product page, and then select **OK**.

    > [!NOTE]
    > To make a template automatically show up in the list that appears when the **Customize product page** button is selected, add the tag "product" to the desired product page template. Alternately, if you want to see all templates when choosing one for your custom product page, clear the filter at the top of the template picker modal by selecting the **X** next to the "product" tag filter.

1. Edit your new custom product page by adding and configuring marketing modules and content to the page.
1. When finished, select **Save**, and then select **Finish editing**.
1. Select **Preview** to preview the preview the new product page in a browser or to send to test on a mobile device. When you've finished, close the preview tab to return to the authoring tool.
1. Select **Publish** to publish your page.

## Additional resources

[Modify an existing site page](modify-existing-page.md)

[Add a new site page](add-new-page.md)

[Select page layouts](select-page-layouts.md)

[Manage SEO metadata](manage-seo-metadata.md)

[Save, preview, and publish a page](save-preview-publish-page.md)

[Customize a category landing page](enrich-category-page.md)

[Verify page content accessibility](verify-accessibility.md)

[Create dynamic e-commerce pages based on URL parameters](create-dynamic-pages.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
