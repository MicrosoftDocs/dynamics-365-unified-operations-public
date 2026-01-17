---
title: Configure ratings and reviews
description: Learn how to configure your e-commerce site to show customer ratings and reviews in Microsoft Dynamics 365 Commerce.
author: gvrmohanreddy
ms.date: 01/16/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Configure ratings and reviews

[!include [banner](includes/banner.md)]

This article describes how to configure your e-commerce site to show customer ratings and reviews in Microsoft Dynamics 365 Commerce.

Ratings and reviews on e-commerce websites help customers learn about products before they make a purchase decision by showing them what other customers think about those products. For e-commerce websites, ratings and reviews are also a mechanism for collecting customer feedback about products.

## Configure a site to show ratings and reviews

You configure ratings and reviews, such as the tenant ID, review text length, and review title length, at the site level.

To configure a site to show ratings and reviews, follow these steps:

1. Go to **Home \> Sites**.
1. Select the name of your site.
1. Go to **Site settings \> Extensions**.
1. In the **Review text max length** field, enter the maximum number of characters that review text can have (for example, **1000**).
1. In the **Review title max length** field, enter the maximum number of characters that review titles can have (for example, **55**).
1. Select **Save and Publish**.

The following illustration shows what this configuration looks like in Dynamics 365 Commerce.

:::image type="content" source="media/rnr-eCommerce-site-appsettings.png" alt-text="Screenshot of configuring a site to show ratings and reviews.":::

## Link a product rating to the Reviews section of a product detail page (PDP)

A product rating appears below the product title at the top of a PDP. You can configure the product rating so that it links to the **Reviews** section of the same PDP.

To link a product rating to the **Reviews** section of the PDP, follow these steps:

1. Open the PDP template.
1. Go to **Buy box container module settings**.
1. Under **Buy box**, select **Product ratings**, and then select the **Link the click to full reviews module** check box.

The following illustration shows what this configuration looks like in Dynamics 365 Commerce.

:::image type="content" source="media/rnr-eCommerce-buy-box-rating-summary.png" alt-text="Screenshot of linking a product rating to the Reviews section of a PDP.":::

## Configure the link for the privacy and policy page

To configure the link for the privacy and policy page, follow these steps:

1. Go to **Home \> Sites**.
1. Select the name of your site.
1. Go to **Site settings \> Extensions**.
1. On the **Routes** tab, under **RNR Privacy and Policy**, select **Add a link**. If a link is already entered, and you want to replace it, select the link.
1. In the **Add a link** dialog box, select the link for the privacy and policy page, and then select **OK**.
1. Select **Save and Publish**.

The following illustration shows what this configuration looks like in Dynamics 365 Commerce.

:::image type="content" source="media/rnr-eCommerce-rnr-privacy-policy-link.png" alt-text="Screenshot of configuring the link for the privacy and policy page.":::

## Configure ratings and reviews modules on product details pages

For information on configuring ratings and reviews modules on product details pages, see [Ratings and reviews modules](ratings-reviews-modules.md).

## Additional resources

[Ratings and reviews overview](ratings-reviews-overview.md)

[Opt in to use ratings and reviews](opt-in-ratings-reviews.md)

[Manage ratings and reviews](manage-reviews.md)

[Sync product ratings in Dynamics 365 Retail](sync-product-ratings.md)

[Enable manual publishing of ratings and reviews by a moderator](manual-publish-rating-reviews.md)

[Import and export ratings and reviews](import-export-reviews.md)

[Configure Service-to-Service authentication](service-to-service-auth.md)

[Ratings and reviews FAQ](ratings-reviews-faq.md)

[Ratings and reviews modules](ratings-reviews-modules.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
