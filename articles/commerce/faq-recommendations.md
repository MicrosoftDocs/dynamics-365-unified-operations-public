---
# required metadata

title: Product recommendations FAQ
description: This article provides information about processes and tools that you can use to troubleshoot issues that are related to product recommendations or their results.
author: bebeale
ms.date: 05/26/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail, Core, Operations
ms.author: bebeale
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 10.0.5

---

# Product recommendations FAQ


[!include [banner](includes/banner.md)]

This article provides information about processes and tools that you can use to troubleshoot issues that are related to [product recommendations](product-recommendations.md) or their results.

## Best practices
It's very important to utilize the concept of product masters and variants. The sensible grouping of variants to a parent product master helps the list algorithms and service create better models. Additionally, the service can serve just one instance of a product instead of putting all closely related variants in a list. When all closely related variants are put in a list, erroneous or duplicate results can occur.

## Why are products missing from my recommendation lists?

Typically, if an item is missing from a product recommendation list, there might be a product configuration issue. For example, there might be an incorrect product start date or end date, a dimension might be misconfigured, or the product might not be in the correct channel assortment, etc.

If an item is missing from a recommendation list that is based on artificial intelligence-machine learning (AI-ML), the item might not fit the criteria of the recommendation list, or it might not have enough purchase transactions for the recommendation list to show it.

We recommend that you check these steps:
1. **Make sure that product recommendations have been enabled in HQ.** For more information about how to enable this service, see [Enable product recommendations](enable-product-recommendations.md).
1. **Make sure that key product properties are set.** For example, product assortments must be set to **Include**.
1. **For newly assorted products, it might take up to 3 hours before the product will start appearing in the new list.**
1. **If a product is still not appearing in Trending, Best selling, People also like, or Frequently bought together, then that product might not have enough transactions.** In this case, you can either wait for more transactions to occur, update the default recommendation list parameters, or use manual intervention to modify the recommendation product list results. For more information about recommendation parameters, see [Manage AI-ML-based product recommendation results](modify-product-recommendation-results.md).
1. **Make sure that the product meets the recommendation criteria for the list.** For more information about product recommendation parameters, see [Manage AI-ML-based product recommendation results](modify-product-recommendation-results.md).

## How can I prevent poor recommendation results from being returned?

Recommendation lists require a large volume of transactions to produce results. Therefore, it's important that users provide full historical transaction data.

Additionally, products that have no transactions or few transactions typically don't have **People also like** or **Frequently bought together** results, and don't appear in **Trending** or **Best selling** recommendation lists. This situation can often occur for very new products, or for old products that have a small number of purchases. Popular new items will easily overcome this issue.

We recommend that you follow these steps:
1. **Make sure that the product meets the recommendation criteria for that list.** For more information about product recommendation parameters, see Modify AI-ML-based product recommendation results.
1. **If the product is new, consider modifying a recommendation list until the product has more transactions.** For more information about how to modify recommendation list results, see [Manage AI-ML-based product recommendation results](modify-product-recommendation-results.md).


- **Make sure that the product meets the recommendation criteria for that list.** For more information about product recommendation parameters, see [Manage AI-ML-based product recommendation results](modify-product-recommendation-results.md).
- **If the product is new, consider modifying a recommendation list until the product has more transactions**. For more information about how to modify recommendation list results, see [Manage AI-ML-based product recommendation results](modify-product-recommendation-results.md).

## Can I remove a product but still see it in the store?

You can adjust lists that are algorithmically generated if a business need arises. However, if a product is removed from a recommendation list, the product will remain discoverable in the store. For more information about how to modify product recommendation results, see [Manage AI-ML-based product recommendation results](modify-product-recommendation-results.md).

If you must block an item from being discovered in the store, you must change the **Item assortments** value to **Exclude**.

## How do I add a list to an e-Commerce page?

For information about how to add product recommendation pages to your e-Commerce website, see [Add product recommendation lists to pages](./product-recommendations.md).

## How do I enable recommendations on POS?

After enabling product recommendations, you will need to add the recommendations panel to the control POS screen. For more information, see [Add a recommendations control to the transaction screen on POS devices](add-recommendations-control-pos-screen.md).

## Additional resources

[Product recommendations overview](product-recommendations.md)

[Enable Azure Data Lake Storage in a Dynamics 365 Commerce environment](enable-adls-environment.md)

[Enable product recommendations](enable-product-recommendations.md)

[Enable personalized recommendations](personalized-recommendations.md)

[Opt out of personalized recommendations](opt-out-personalization.md)

[Enable "shop similar looks" recommendations](shop-similar-looks.md)

[Add product recommendations on POS](product.md)

[Add recommendations to the transaction screen](add-recommendations-control-pos-screen.md)

[Adjust AI-ML recommendations results](modify-product-recommendation-results.md)

[Manually create curated recommendations](create-editorial-recommendation-lists.md)

[Create recommendations with demo data](product-recommendations-demo-data.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
