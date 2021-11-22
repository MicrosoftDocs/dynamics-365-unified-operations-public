---
# required metadata

title: Enrich a product page
description: This topic describes how to enrich a product page in Microsoft Dynamics 365 Commerce.
author: psimolin
ms.date: 04/14/2020
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

# Enrich a product page

[!include [banner](includes/banner.md)]

This topic describes how to enrich a product page in Microsoft Dynamics 365 Commerce.

By default, your site uses a generic page to show product data. This page includes the basic information about the product and the controls that are required to sell it. However, you can supplement the information that comes from the Commerce Scale Unit with additional images or text for a specific product. This process is known as enriching the product page.

In many cases, you will want to use specific additional content for your products. When you go to **Retail and Commerce** in the authoring tool, you will see a list of products from the channel that is assigned to the site. In this list, the **Enriched** column indicates whether the product page for a product has been enriched. If a check mark appears in the column, an enriched product page exists for the product. If no check mark appears, the default product page and content are used for the product. You can preview both enriched and non-enriched product pages by selecting a product name in the list.

## Enrich a product page

To enrich a product page, follow these steps.

1. Under **Sites**, select **Fabrikam** (or the name of your site).
1. In the navigation pane on the left, select **Products**.
1. Select any product that doesn't have an enriched product page.
1. On the Action Pane, select **Enrich product page**.
1. Select **PDP-template**, and then select **OK**.
1. In the page outline tree on the left, expand the **Main** slot.
1. Select the ellipsis button (**...**) for the **Main** slot, and then select **Add Module**.
1. Select **Container 2**, and then select **OK**.
1. Select the ellipsis button for **Container 2**, and then select **Add Module**.
1. Select **Feature**, and then select **OK**.
1. In the properties pane on the right, in the **Rich Text** field, enter the updated description of the product.
1. In the **Heading** field, enter heading text, and then select **OK**.
1. Select **Save**, and then select **Finish editing**.
1. In the **Comments** field, enter **Enriched a product**, and then select **OK**.
1. Select **Preview** to preview the enriched product page. When you've finished, close the preview tab to return to the authoring tool.
1. Select **Publish**.

## Additional resources

[Modify an existing site page](modify-existing-page.md)

[Add a new site page](add-new-page.md)

[Select page layouts](select-page-layouts.md)

[Manage SEO metadata](manage-seo-metadata.md)

[Save, preview, and publish a page](save-preview-publish-page.md)

[Enrich a category landing page](enrich-category-page.md)

[Verify page content accessibility](verify-accessibility.md)

[Create dynamic e-commerce pages based on URL parameters](create-dynamic-pages.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
