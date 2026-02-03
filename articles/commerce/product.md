---
title: Add product recommendations on POS
description: Learn how to configure and add product recommendations on a Microsoft Dynamics 365 Commerce point of sale (POS) device.
author: bebeale
ms.date: 01/28/2026
ms.topic: how-to
ms.search.form: RetailParameters
ms.reviewer: v-griffinc
ms.assetid: 5dd8db08-cd96-4f7e-9e65-b05ca815d580
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2016-11-30
ms.custom: 
  - bap-template
---

# Add product recommendations on POS

[!include [banner](includes/banner.md)]

This article describes how to configure and add product recommendations on a Microsoft Dynamics 365 Commerce point of sale (POS) device.

At its core, the product recommendations feature is a transformative business application that spans across all commerce spaces to create rich, engaging, and tailored product discovery experiences. To implement this feature on POS, see [How to add recommendations to your POS devices](add-recommendations-control-pos-screen.md).

For more information about product recommendations features, see [Product recommendations overview](../commerce/product-recommendations.md).

## Scenarios

You can enable product recommendations for the following POS scenarios. They're available in the Store Commerce app or Store Commerce for web.

1. On the **Product details** page:

    - If a store associate visits a **Product details** page when they're looking at previous transactions across different channels, the recommendations service suggests more items that are likely to be purchased together. Depending on the add-ons for the service, retailers can show **Shop similar looks** and **Shop similar description** recommendations for products, in addition to personalized recommendations for users who have a previous purchase history.

    :::image type="content" source="./media/proddetails.png" alt-text="Screenshot of recommendations on the Product details page.":::

1. On the **Transaction** page:

    - The recommendation engine suggests items based on the entire list of items in the basket that are frequently bought together.

    > [!NOTE]
    > To display recommendations on the **Transaction** page, the retailer needs to update the screen layout in Dynamics 365 Commerce. The **Recommendations** control must be dropped onto the **Transaction** page.

    :::image type="content" source="./media/transactionscreenmultipleproductslargemessengersbag-5.jpg" alt-text="Screenshot of recommendations on the Transaction page.":::

## Configure Commerce to enable POS recommendations

To set up product recommendations, confirm that you completed the provisioning process for Commerce product recommendations by following the steps in [Enable product recommendations](../commerce/enable-product-recommendations.md). By default, recommendations appear on both the **Product details** page and the **Customer details** page after you complete the provisioning steps and the data is successfully processed.

## Add recommendations to the transaction screen

1. To add recommendations to the transaction screen, follow the steps in [Add recommendations to the transaction screen](add-recommendations-control-pos-screen.md).
1. To reflect changes that you made in the POS screen layout designer, run channel configuration job **1070** in Commerce headquarters.

> [!NOTE]
> To enable POS recommendations by using the RecoMock comma-separated values (CSV) file, you must deploy the CSV file to the Microsoft Dynamics Lifecycle Services (LCS) asset library before you configure the layout manager. If you use the RecoMock CSV file, you don't have to enable recommendations. The CSV file is available only for demo purposes. It's recommended for customers or solution architects who want to mimic the appearance of recommendation lists for demo purposes without having to purchase an add-on stock keeping unit (SKU).

## Additional resources

[Product recommendations overview](product-recommendations.md)

[Enable Azure Data Lake Storage in a Dynamics 365 Commerce environment](enable-adls-environment.md)

[Enable product recommendations](enable-product-recommendations.md)

[Enable personalized recommendations](personalized-recommendations.md)

[Opt out of personalized recommendations](opt-out-personalization.md)

[Enable "shop similar looks" recommendations](shop-similar-looks.md)

[Add recommendations to the transaction screen](add-recommendations-control-pos-screen.md)

[Adjust AI-ML recommendations results](modify-product-recommendation-results.md)

[Manually create curated recommendations](create-editorial-recommendation-lists.md)

[Create recommendations with demo data](product-recommendations-demo-data.md)

[Product recommendations FAQ](faq-recommendations.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
