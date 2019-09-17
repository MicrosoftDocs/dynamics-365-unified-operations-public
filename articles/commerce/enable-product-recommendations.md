---
# required metadata

title: Enable omni-channel product recommendations
description: This topic explains how to make product recommendations that are based on artificial intelligence-machine learning (AI-ML) available for Microsoft Dynamics 365 for Commerce customers. 
author: bebeale
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

# Enable omni-channel product recommendations

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic explains how to make product recommendations that are based on artificial intelligence-machine learning (AI-ML) available for Microsoft Dynamics 365 for Commerce customers. For more information about product recommendation lists, see [Product recommendations overview](product-recommendations.md).

## Recommendations pre-check
Before enabling, please note that product recommendations are only supported for F&O customers supporting build 10.0.6 and have migrated their storage to using BDL. 

Additionally, ensure that RetailSale measurements have been enabled. To Learn more about this set up process, go [here.](https://docs.microsoft.com/en-us/dynamics365/ai/customer-insights/pm-measures)


## Turn on recommendations

To turn on product recommendations, follow these steps.

1. Go to **Retail** &gt; **Product recommendations** &gt; **Recommendation parameters**.
1. In the list of retail shared parameters, select **Recommendation Lists**.
1. Set the **Enable recommendations** option to **Yes**.

![enable product recommendations](enableproductrecommendations.png)

> [!NOTE]
> This procedure starts the process of generating product recommendation lists. Up to several hours might be required before the lists are available and can be seen at the point of sale (POS) or in Dynamics 365 for Commerce.

## Configure recommendation list parameters
By default, the AI-ML-based product recommendation list provides suggested values. You can change the default suggested values to suit the flow of your business. To learn more about how to change the default parameters, go to [Modify AI-ML based product recommendation lists.](modify-product-recommendation-results.md)

## Show recommendations on POS devices
After enabling recommendations in the back office, the recommendations pannel must be added to the control POS screen via the layout tool. To learn about this process, go [here.](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/add-recommendations-control-pos-screen)


## Additional resources

[Product recommendations overview](product-recommendations.md)

[Add product recommendation lists to pages](add-reco-list-to-page.md)

[Add recommendations panel to POS devices](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/add-recommendations-control-pos-screen)


