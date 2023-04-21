---
# required metadata

title: Product recommendations overview
description: This article provides general information about product recommendations. Product recommendations let customers easily and quickly find products that they want, and even products that they didn't originally intend to buy.
author: Moonma
ms.date: 04/21/2023
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 

ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: moonma
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 10.0.5

---

# Product recommendations overview

[!include [banner](includes/banner.md)]

Microsoft Dynamics 365 Commerce can be used to show product recommendations on the e-Commerce website and point of sale (POS) device. Product recommendations are items that a customer might be interested in. The recommendations are based on the purchase trends of other customers in online and brick-and-mortar stores.

Product recommendations allow customers to easily and quickly find products that they want while they have an experience that serves them well. Cross-selling and upselling can even be used to assist customers find additional products that they didn't originally intend to buy. When recommendations are used to enhance product discovery, they create more conversion opportunities, help increase sales revenue, and even amplify customer satisfaction and retention.

In e-Commerce, product recommendations are powered by Microsoft Recommendations machine learning technologies on a large scale.

This service is an add-on to Dynamics 365 Commerce. For more information, download the latest [Microsoft Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544).


## Recommendation service

The product recommendations service utilizes artificial intelligence and machine learning (AI-ML) technologies in the following way:

- Data in the format that the Recommendation service requires is extracted from the Commerce operational database and sent to Azure Data Lake Storage or Entity store.
- The recommendations service uses the stored data to train recommendation models for the **People also like**, **Frequently bought together**, **New**, **Best selling**, and **Trending** lists.

## Scenarios

Product recommendations are available for the following scenarios:

- **On any store page for browsing or landing page in e-Commerce:** If customers or store associates visit a store page, the recommendation engine can suggest products in the **New**, **Best Selling**, and **Trending** lists.
- **On the Product details page:** If customers or store associates visit a **Product details** page, the recommendation engine suggests additional items that are also likely to be purchased. These items appear in the **People also like** list.
- **On the Transaction page or the checkout page:** The recommendation engine suggests items, based on the whole list of items in the basket. These items appear in the **Frequently bought together** list.
- **Personalized recommendations:** Merchandisers can provide signed-in customers a personalized **picks for you** list, in addition to new functionality that allows for existing list scenarios to be personalized based on that customer. To learn more, see [Enable personalized recommendations.](personalized-recommendations.md).

### Types of product recommendations

The following table describes various types of automated product recommendations available for retailers to implement in their Dynamics 365 Commerce solution via the [product collection module](product-collection-module-overview.md). Retailers can also show personalized results for a signed-in user if the site author chooses that option.

| Product collection module  | Type | Description |
|----------------------------|------|-------------|
| New                        | Algorithmic | This module shows a list of the newest products that have been recently assorted to channels and catalogs. |
| Best selling               | Algorithmic | This module shows a list of products that are ranked by the highest number of sales. |
| Trending                   | Algorithmic | This module shows a list of the highest-performing products for a given period, ranked by highest number of sales.  |
| Frequently bought together | AI-ML | This module recommends a list of products that are commonly purchased together with the contents of the consumers current cart. |
| People also like           | AI-ML | This module recommends products for a given seed product based on consumer purchase patterns. |
| Picks for you              | AI-ML | This module recommends a personalized list of products based on purchase patterns of the signed-in user. For a guest user, this list will be collapsed. |

## Additional resources

[Enable Azure Data Lake Storage in a Dynamics 365 Commerce environment](enable-adls-environment.md)

[Enable product recommendations](enable-product-recommendations.md)

[Enable personalized recommendations](personalized-recommendations.md)

[Opt out of personalized recommendations](personalization-opt-out.md)

[Enable "shop similar looks" recommendations](shop-similar-looks.md)

[Add product recommendations on POS](product.md)

[Add recommendations to the transaction screen](add-recommendations-control-pos-screen.md)

[Adjust AI-ML recommendations results](modify-product-recommendation-results.md)

[Manually create curated recommendations](create-editorial-recommendation-lists.md)

[Create recommendations with demo data](product-recommendations-demo-data.md)

[Product recommendations FAQ](faq-recommendations.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
