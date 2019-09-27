---
# required metadata

title: Product recommendations overview
description: This topic provides general information about product recommendations. Product recommendations let customers easily and quickly find products that they want, and even products that they didn't originally intend to buy.
author: Moonma
manager: AnnBe
ms.date: 10/1/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: moonma
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 10.0.5

---

# Product recommendations overview

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

Microsoft Dynamics 365 for Commerce can be used to show product recommendations on the e-Commerce website and point of sale (POS) device. Product recommendations are items that a customer might be interested in. The recommendations are based on the purchase trends of other customers in online and brick-and-mortar stores.

Product recommendations let customers easily and quickly find products that they want while they have an experience that serves them well. Cross-selling and upselling can even be used to help customers find additional products than they didn't originally intend to buy. When recommendations are used to help with product discovery, they can create more conversion opportunities, help increase sales revenue, and even help enhance customer satisfaction and retention.

In Dynamics 365 for Commerce, product recommendations are powered by Microsoft Recommendations machine learning technologies on a large scale.


## Scenarios

Product recommendations are available for the following scenarios:

- **On any store page for browsing or landing page in e-Commerce:** If customers or store associates visit a store page, the recommendation engine can suggest products in the **New**, **Best Selling**, and **Trending** lists.
- **On the Product details page:** If customers or store associates visit a **Product details** page, the recommendation engine suggests additional items that are also likely to be purchased. These items appear in the **People also like** list.
- **On the Transaction page or the checkout page:** The recommendation engine suggests items, based on the whole list of items in the basket. These items appear in the **Frequently bought together** list.

## Recommendation service

Product recommendations use the Recommendations machine learning technologies in the following way:

- Data in the format that the Recommendation service requires is extracted from the Dynamics 365 for Commerce operational database and sent to the Entity store.
- The Recommendation service uses the data to train recommendation models for the **People also like**, **Frequently bought together**, **New**, **Best selling**, and **Trending** lists.

## Additional resources

[Enable omni-channel product recommendations](enable-product-recommendations.md)

[Create editorial-based product recommendation lists](create-editorial-recommendation-lists.md)

[Modify AI-ML-based product recommendation results](modify-product-recommendation-results.md)

[Add product recommendation lists to an eCommerce page](add-reco-list-to-page.md)
