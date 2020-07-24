---
# required metadata

title: Shop similar looks recommendations
description: This topic describes how to enable visually similar product recommendations, or shop similar looks, available for customers in Microsoft Dynamics 365 Commerce. 
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

This topic describes how to enable visually similar product recommendations, or **shop similar looks**, available for customers in Microsoft Dynamics 365 Commerce.

## Overview

**Shop similar looks** brings fresh and appealing choices to the forefront of the shopping experience, using the power of artificial intelligence and machine learning (AI-ML). 
Making **Shop similar looks** available for all retail channels in Commerce, retailers can increase customer satisfaction by helping shoppers feel like they can easily find what they want. 
The impact is transformative and can create additional lift as shoppers find more of the things they want in an easy-to-use experience.

## How it works

**Shop similar looks** is an AI-ML capability for Commerce Recommendations that uses the product images of a seed product variant to then discover visually similar products in the retailer's product catalog.
The Recommendations system also infers "selectors" (filters) for types of product (for example in fashion, these might include color and type of clothing), which can be used by the shopper to further refine their journey. 

### Example Scenarios

- Suppose a shopper is viewing a black striped sweater; they might be presented with a red sweater and decide to select that color instead in order to see similarly colored products in red. 
- Retailers can also benefit from selectors. For example, they can use a selector for the type of jewelry that helps the shopper find suitably matching earrings that go with a ring the shopper is interested in. 

## How to enable shop similar looks

Before you make **Shop Similar Looks** available for customers, note that product recommendations are supported only for Commerce users who have migrated their storage to Azure Data Lake Store. 

Before customers can receive shop similar looks recommendations, retailers must [turn on product recommendations](enable-product-recommendations.md).

> [!NOTE]
> If you turn off **shop similar looks**, it will not impact other types of product recommendations.
For more information about product recommendations, see the [Product recommendations overview](product-recommendations.md).

### Turn on shop similar looks

**Shop similar looks** is available on both POS and eComm experiences, as outlined below. 
In order to gain access to this feature, it will need to be enabled from within Feature Management in the Back office.

1. Go to **Feature Management Workspace**.
1. In the list of available features, search for and select **shop similar looks**.
1. Set the **Enable** option to turn on the service.

![Enable Shop Similar Looks Feature](./media/enableshopsimilarlooks.png)

> [!NOTE]
> When you turn on this recommendations feature, the process of generating product recommendation lists will begin. Up to one day might be required before these lists are available and visible online and at the POS kiosks.
### How to expose shop similar looks to customers

#### Add shop similar looks panel to POS 

After enabling the **Shop similar looks** feature from the back office, POS product details pages are automatically enhanced with a contextual "shop similar products" panel. 
The following illustration shows an example of a "Shop similar products" panel on a POS terminal. 
Selecting "see more" will take a user to a dedicated shop similar looks page that can be further filtered based on selectors. 


#### Add shop similar looks button to eCommerce PDPs

After enabling this feature, the Retailer now has the option to add a Buybox "shop similar looks" button to any product detail page. 

Selecting the button will take a shopper to a deticated shop similar looks page that returns visually similar products, and which can be further filtered based on selectors.


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
