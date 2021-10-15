---
# required metadata

title: Enable "shop similar description" recommendations
description: This topic describes how to enable "shop similar description" product recommendations in Microsoft Dynamics 365 Commerce.
author: bsokolov
ms.date: 01/13/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
#ms.search.scope: 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail, eCommerce
ms.author: bebeale
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.16

---

# Enable "shop similar description" recommendations

[!include [banner](includes/banner.md)]

This topic describes how to enable "shop similar description" product recommendations in Microsoft Dynamics 365 Commerce.

The "shop similar description" recommendations feature in Dynamics 365 Commerce uses artificial intelligence and machine learning (AI-ML) to deliver recommendations for products that have descriptions that are similar to what the customer is looking for. By making "shop similar description" recommendations available for all retail channels in Commerce, retailers can help customers easily find what they want.

The functionality for "shop similar description" recommendations uses the product name and description of seed products to find and recommend similar products in a retailer's product catalog.

"Shop similar description" recommendations are available in both the point of sale (POS) and e-commerce experiences.

## Example scenarios

The following example scenarios show the types of recommendations that the "shop similar description" functionality can provide:

- A customer views a pair of retro-style horn-rimmed glasses and receives a set of recommendations for other glasses that have a similar design, in the context of the retailer's industry.
- A customer uses "shop similar description" recommendations to discover coffee flavors that are similar to a flavor that they previously purchased from the retailer.

## Set up "shop similar description" recommendations

Product recommendations are supported only for Commerce users who have migrated their storage to Azure Data Lake Storage Gen2.

### Prerequisites

Before "shop similar description" recommendations can be shown to customers, you must complete the following prerequisites:

- [Enable product recommendations](enable-product-recommendations.md) in Commerce headquarters.
- Confirm that the media server supports HTTPS calls.

### Turn on the "shop similar description" recommendations feature

To turn on the "shop similar description" recommendations feature in Commerce headquarters, follow these steps.

1. In the **Feature management** workspace, in the list of available features, search for and select **Shop similar description**.
1. In the right pane, select **Enable**.

> [!NOTE]
> When you turn on the feature, the system starts to generate product recommendation lists. It might take up to a day for those lists to become available and visible online and on POS terminals.
>
> If you turn off the feature, other types of product recommendations aren't affected. For more information about product recommendations, see [Product recommendations overview](product-recommendations.md).

## Add a Shop similar description button to product details pages

After you turn on the "shop similar description" recommendations feature in Commerce headquarters, you can add a **Shop similar description** button to the buy box on any product details page (PDP). A customer who selects this button is taken to a dedicated **Shop similar description** page that shows visually similar products. The customer can then use selectors to further filter the products.

To add a **Shop similar description** button to a PDP by using Commerce site builder, follow these steps.

1. Open an existing site builder page that contains a buy box module.
1. In the left navigation pane, select the buy box module.
1. In the right pane, select the **Enable Shop Similar description Link** check box.
1. Select **Save**.
1. Select **Finish editing** to check in the page, and then select **Publish** to publish it. After the page is published, the PDP will include a **Shop similar description** button.

The following illustration shows the **Enable shop similar description Link** check box and the **Shop similar description** button on an example PDP in site builder.

![Enable shop similar description Link check box and Shop similar description button on a PDP in site builder.](./media/ter_site_builder_buybox_button.png)

## Additional resources

[Product recommendations overview](product-recommendations.md)

[Enable Azure Data Lake Storage in a Dynamics 365 Commerce environment](enable-adls-environment.md)

[Enable product recommendations](enable-product-recommendations.md)

[Enable "shop similar looks" recommendations](shop-similar-looks.md)

[Adjust AI-ML recommendations results](modify-product-recommendation-results.md)

[Manually create curated recommendations](create-editorial-recommendation-lists.md)

[Product recommendations FAQ](faq-recommendations.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]