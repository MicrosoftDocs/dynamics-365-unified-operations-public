---
# required metadata

title: Enable "shop similar looks" recommendations
description: This topic describes how to enable "shop similar looks" product recommendations in Microsoft Dynamics 365 Commerce. 
author: bebeale
manager: AnnBe
ms.date: 07/31/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail, eCommerce
ms.author: bebeale
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 10.0.5

---

# Enable "shop similar looks" recommendations

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic describes how to enable "shop similar looks" product recommendations in Microsoft Dynamics 365 Commerce.

## Overview

The "shop similar looks" recommendations feature in Dynamics 365 Commerce delivers customers visually similar product recommendations using the power of artificial intelligence and machine learning (AI-ML). By making "shop similar looks" recommendations available for all retail channels in Commerce, retailers can increase customer satisfaction by helping customers to easily find what they want. 

"Shop similar looks" recommendations functionality uses product images of seed product variants to find and recommend visually similar products in a retailer's product catalog. The Commerce recommendations system also provides "selectors" or filters for product types that can be used by customers to further refine their searches. For example, fashion selectors might include color and type of clothing that customers could use to filter results.

"Shop similar looks" recommendations are available on both the point of sale (POS) and e-Commerce experiences.

### Example scenarios

- A customer views a black striped sweater, is recommended a similar red sweater, selects that color instead, and is then recommended similar products in red. 
- A retailer provides a selector for a type of jewelry that helps the customer find suitably matching earrings to go with a ring that the customer is interested in. 

## Enable "shop similar looks" recommendations in Commerce headquarters

Product recommendations are only supported for Commerce users who have migrated their storage to Microsoft Azure Data Lake Store. 

Before customers can receive "shop similar looks" recommendations, retailers must first enable product recommendations in Commerce headquarters. For more information, see [Enable product recommendations](enable-product-recommendations.md).

> [!NOTE]
> When you turn on the "shop similar looks" recommendations feature, the process of generating product recommendation lists will begin. Up to one day might be required before these lists are available and visible online and on POS terminals.

To enable the "shop similar looks" feature in Commerce headquarters, follow these steps.

1. Go to **Feature management**.
1. In the list of available features, search for and select **Shop similar looks**.
1. In the right pane, select **Enable** to turn on the service.

The following image shows the **Shop similar looks** feature on the **Feature management** page in Commerce headquarters. 

![The **Shop similar looks** feature on the **Feature management** page in Commerce headquarters](./media/enableshopsimilarlooks.png)

After enabling the **Shop similar looks** feature in Commerce headquarters, POS terminals are automatically enhanced with a contextual **Shop similar products** panel. Selecting **See more** will take the POS terminal user to a dedicated "shop similar looks" page that can be further filtered based on selectors. 

> [!NOTE]
> If you turn off "shop similar looks" recommendations, this will not impact other types of product recommendations. For more information about product recommendations, see [Product recommendations overview](product-recommendations.md).

## Add a "Shop similar looks" button to PDPs using Commerce site builder

After enabling the "shop similar looks" recommendations feature in Commerce headquarters, retailers have the option in Commerce site builder of adding a **Shop similar looks** button to any product details page (PDP) buy box. Selecting the button will take customers to a dedicated "shop similar looks" page that returns visually similar products that can be further filtered based on selectors.

To add a **Shop similar looks** button to a PDP using Commerce site builder, follow these steps.

1. Open an existing site builder page that contains a buy box module.
1. In the left navigation pane, select the buy box module.
1. In the right navigation pane, select the **Enable Shop Similar Looks Link** check box. 
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it. After the page is published, the product detail page will show a **Shop similar looks** button.

The following image shows an example page in site builder with the **Enable Shop Similar Looks Link** check box and **Shop similar looks** PDP button highlighted. 

![Example page in site builder with the **Enable Shop Similar Looks Link** check box and **Shop similar looks** PDP button highlighted](./media/SSLecomtooling.png)

## Additional resources

[Product recommendations overview](product-recommendations.md)

[Enable Azure Data Lake Storage in a Dynamics 365 Commerce environment](enable-adls-environment.md)

[Enable product recommendations](enable-product-recommendations.md)

[Opt out of personalized recommendations](personalization-gdpr.md)

[Add product recommendations on POS](product.md)

[Add recommendations to the transaction screen](add-recommendations-control-pos-screen.md)

[Adjust AI-ML recommendations results](modify-product-recommendation-results.md)

[Manually create curated recommendations](create-editorial-recommendation-lists.md)

[Create recommendations with demo data](product-recommendations-demo-data.md)

[Product recommendations FAQ](faq-recommendations.md)
