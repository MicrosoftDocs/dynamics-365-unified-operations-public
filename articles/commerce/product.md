---
# required metadata

title: Add product recommendations on POS
description: This topic describes using product recommendations on a point of sale (POS) device.
author: bebeale
ms.date: 05/26/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: RetailParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 259664
ms.assetid: 5dd8db08-cd96-4f7e-9e65-b05ca815d580
ms.search.region: global
ms.search.industry: Retail
ms.author: asharchw
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Add product recommendations on POS

[!include [banner](includes/banner.md)]

At its core, product recommendations are a transformative business application that span across all commerce spaces to create rich, engaging, and tailored product discovery experiences. To implement this feature on POS, follow the steps on [how to add recommendations to your POS devices.](add-recommendations-control-pos-screen.md) 

For more information about product recommendations features, read the [product recommendations overview.](../commerce/product-recommendations.md) 

## Scenarios

Product recommendations are enabled for the following POS scenarios. They are available in Cloud POS or Modern POS (MPOS).

1. On the **Product details** page:

    - If a store associate visits a **Product details** page when looking at previous transactions across different channels, the recommendations service suggests additional items that are likely to be purchased together.

    [![Recommendations on the Product details page.](./media/proddetails.png)](./media/proddetails.png)

2. On the **Transaction** page:

    - The recommendation engine suggests items based on the entire list of items in the basket that are frequently bought together.

    > [!NOTE]
    > To display recommendations on the **Transaction** page, the retailer needs to update the screen layout in Dynamics 365 Commerce. The **Recommendations** control must be dropped onto the **Transaction** page.

    [![Recommendations on the Transaction page.](./media/transactionscreenmultipleproductslargemessengersbag-5.jpg)](./media/transactionscreenmultipleproductslargemessengersbag-5.jpg)

## Configure Commerce to enable POS recommendations

To set up product recommendations, follow these steps:

1. Ensure your service has been updated to the **10.0.6 build.**
2. Follow the instructions on how to [enable product recommendations](../commerce/enable-product-recommendations.md) for your business.
3. Optional: To display recommendations on the transaction screen, go to **Screen Layout**, choose your screen layout, launch the **Screen layout designer**, and then drop the **recommendations** control where needed.
4. Go to **Commerce parameters**, select **Machine-learning**, select **Yes** under **Enable POS recommendations**.
5. To see recommendations on POS, run global configuration job **1110**. To reflect changes made to POS screen layout designer, run channel configuration job **1070**.

## Troubleshoot issues where you have Product recommendations already enabled

- Navigate to **Commerce Parameters** \> **Recommendation lists** \> **Disable product recommendations** and run **Global configuration job \[9999\]**. 
- If you added the **Recommendations control** to your transaction screen using the **Screen layout designer**, please remove that as well.
- If you have additional questions, check out the [Product recommendations FAQ](../commerce/faq-recommendations.md) for more information.

## Additional resources

[Product recommendations overview](product-recommendations.md)

[Enable Azure Data Lake Storage in a Dynamics 365 Commerce environment](enable-adls-environment.md)

[Enable product recommendations](enable-product-recommendations.md)

[Enable personalized recommendations](personalized-recommendations.md)

[Opt out of personalized recommendations](personalization-gdpr.md)

[Enable "shop similar looks" recommendations](shop-similar-looks.md)

[Add recommendations to the transaction screen](add-recommendations-control-pos-screen.md)

[Adjust AI-ML recommendations results](modify-product-recommendation-results.md)

[Manually create curated recommendations](create-editorial-recommendation-lists.md)

[Create recommendations with demo data](product-recommendations-demo-data.md)

[Product recommendations FAQ](faq-recommendations.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]