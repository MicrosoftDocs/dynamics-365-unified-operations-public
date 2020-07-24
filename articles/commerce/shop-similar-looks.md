---
# required metadata

title: Shop similar looks recommendations
description: This topic describes how to enable shop similar looks product recommendations in Microsoft Dynamics 365 Commerce. 
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

# Shop similar looks recommendations

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic describes how to enable shop similar looks product recommendations in Microsoft Dynamics 365 Commerce.

## Overview

"Shop similar looks" recommendations in Dynamics 365 Commerce deliver customers visually similar product recommendations using the power of artificial intelligence and machine learning (AI-ML). By making "shop similar looks" recommendations available for all retail channels in Commerce, retailers can increase customer satisfaction by helping shoppers feel like they can easily find what they want. 

## How it works

**Shop similar looks** is an AI-ML capability for Commerce recommendations that uses the product images of a seed product variant to find and recommend visually similar products in a retailer's product catalog. The Commerce recommendations system also provides "selectors" (filters) for types of products that can be used by the shopper to further refine their journey. For example, fashion selectors might include color and type of clothing that customers can use to filter results.

### Example scenarios

- A customer views a black striped sweater, is recommended a similar red sweater, selects that color instead, and is then recommended similar products in red. 
- A retailer provides a selector for a type of jewelry that helps the customer find suitably matching earrings to go with a ring that the customer is interested in. 

## Enable shop similar looks recommendations

Product recommendations are only supported for Commerce users who have migrated their storage to Microsoft Azure Data Lake Store. 

Before customers can receive "shop similar looks" recommendations, retailers must first enable product recommendations in Commerce headquarters. For more information, see [Enable product recommendations](enable-product-recommendations.md).

Before you make **Shop Similar Looks** available for customers, note that

> [!NOTE]
> If you turn off "shop similar looks" recommendations, this will not impact other types of product recommendations. For more information about product recommendations, see [Product recommendations overview](product-recommendations.md).

### Turn on shop similar looks

**Shop similar looks** is available on both POS and eComm experiences, as outlined below. 

In order to gain access to this feature, it will need to be enabled from within Feature Management in the Back office.

To 

1. Go to **Feature Management Workspace**.
1. In the list of available features, search for and select **shop similar looks**.
1. Set the **Enable** option to turn on the service.

![Enable Shop Similar Looks Feature](./media/enableshopsimilarlooks.png)

> [!NOTE]
> When you turn on this recommendations feature, the process of generating product recommendation lists will begin. Up to one day might be required before these lists are available and visible online and at the POS kiosks.
### How to expose shop similar looks to customers

### Add shop similar looks panel to POS 

After enabling the **Shop similar looks** feature from the back office, POS product details pages are automatically enhanced with a contextual "shop similar products" panel. 
The following illustration shows an example of a "Shop similar products" panel on a POS terminal. 
Selecting "see more" will take a user to a dedicated shop similar looks page that can be further filtered based on selectors. 

### Add a "shop similar looks" button to Commerce PDPs

After enabling "shop similar looks" recommendations, a retailer has the option of adding a buy box "shop similar looks" button to any product detail page (PDP). Selecting the button will take customers to a dedicated "shop similar looks" page that returns visually similar products that can be further filtered based on selectors.

To enable **Shop similar looks** for a product in the Commerce site builder, follow these steps.

1. Open an existing site builder page that contains a buybox module.
1. In the left navigation pane, select the buybox module.
1. In the right navigation pane, select the checkbox that says **enable shop similar looks link**. 
1. Save the page, finish editing it, and then publish it. After the page is published, the product detail page will now show a shop similar looks button.

![Shop Similar Looks on Tooling page](./media/SSLecomtooling.png)

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
