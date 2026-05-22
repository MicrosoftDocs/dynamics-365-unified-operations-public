---
# required metadata

title: Adjust AI-ML-based product recommendation results
description: Learn how to adjust product recommendation results based on artificial intelligence-machine learning (AI-ML) in Microsoft Dynamics 365 Commerce. 
author: bebeale
ms.date: 01/23/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: global
ms.search.industry: Retail
ms.author: bebeale
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 
ms.custom: 
  - bap-template
---

# Adjust AI-ML-based product recommendation results

[!include [banner](includes/banner.md)]

This article explains how to adjust product recommendation results based on artificial intelligence-machine learning (AI-ML) in Microsoft Dynamics 365 Commerce.

After you enable product recommendations, the default settings take effect. These parameters work for many needs. Spend some time evaluating whether the results fit the selling motion of products. Evaluate results for a few days before changing parameters as needed and testing again.

## Understanding recommendation list parameters

Before changing the parameters, learn about how they affect the results.

### "Trending" product list

The "Trending" product list has two parameters that you can change:

:::image type="content" source="./media/exampletrendingparameters.png" alt-text="Screenshot of example Trending list default parameters.":::

1. **Include new products from last X days** - The system uses products that you add within the specified number of days before the current date to select product candidates. The default value in the picture suggests that products as old as 180 days can be used in the trending product list.
1. **Include sales from last X days** - The system uses sales transactions that occur within the specified number of days before the current date to order the products. The default value suggests that all purchases made of a product in the last 30 days are used to determine the placement of the product in the trending product list. 

### "Best selling" product list

Depending on your business, the "Best selling" list can bring different results than trending, even though they both use transaction data to order products. Because best selling doesn't have a cutoff based on assortment date, it can still highlight popular, older products that might be dropped from the trending list. 

The "Best selling" product list has one parameter that you can change:

:::image type="content" source="./media/examplebestsellingparameters.PNG" alt-text="Screenshot of example Best selling list default parameter.":::

1. **Include sales from last X days** - Sales transactions that occur within the specified number of days before the current date order the products. The default value suggests that all purchases made of a product in the last 30 days determine the placement of the product in the Best selling product list. 

## Manually add or remove products from recommendation lists

### For "New," "Trending," or "Best selling" lists

1. Go to **Retail and Commerce** > **Product recommendations** > **Recommendation parameters**.
1. In the list of shared parameters, select **Recommendation lists**.
1. Select the list to add or remove products from.
1. Select **Add line** to add products to the table. 
1. Under the Product column, search for a product by **Name** or **Product number**.

   :::image type="content" source="./media/examplenewlistconfiguration1.png" alt-text="Screenshot of searching for a product on the New product list.":::

1. Under the Line type column, select one of two options:
   - **Include** – puts a product at the front of the list
   - **Exclude** – removes a product from appearing in the list
    
    :::image type="content" source="./media/examplenewlistconfiguration2.png" alt-text="Screenshot of including or excluding a product from the New product list.":::

1. Changing the **Display order** changes the order that products marked **include** appear in the list.
   - If two products have the same **display order** value, then the final order of those two results might differ from the back office.
1. To remove products from the table, select the line to remove and select **Remove**.

### For "People also like" or "Frequently bought together" lists

In the context of "Frequently bought together" or "People also like" lists, machine learning analyzes consumer purchase patterns to recommend related products that customers commonly buy together for a unique seed product. 

A *seed product* is the product you want to generate results for. When you manually adjust recommendation lists, you add or remove results for this product. 

Follow these steps to manually add or remove results for a seed product:
1. Select the **Seed product**. 
1. Under the **Product** column, search for a product by **Name** or **Product number.**
:::image type="content" source="./media/exampleFBTlistconfiguration1.png" alt-text="Screenshot of searching for a product on the Frequently bought together list.":::
1. Under the **Line type** column, select one of two options:
    - **Include** – puts a product at the front of the list
    - **Exclude** – removes a product from appearing in the list     
:::image type="content" source="./media/exampleFBTlistconfiguration2.png" alt-text="Screenshot of including or excluding a product on the Frequently bought together list.":::
1. To remove products from the table, select **Remove**.

## Additional resources

[Product recommendations overview](product-recommendations.md)

[Enable Azure Data Lake Storage in a Dynamics 365 Commerce environment](enable-adls-environment.md)

[Enable product recommendations](enable-product-recommendations.md)

[Enable personalized recommendations](personalized-recommendations.md)

[Opt out of personalized recommendations](opt-out-personalization.md)

[Enable "shop similar looks" recommendations](shop-similar-looks.md)

[Add product recommendations on POS](product.md)

[Add recommendations to the transaction screen](add-recommendations-control-pos-screen.md)

[Manually create curated recommendations](create-editorial-recommendation-lists.md)

[Create recommendations with demo data](product-recommendations-demo-data.md)

[Product recommendations FAQ](faq-recommendations.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
