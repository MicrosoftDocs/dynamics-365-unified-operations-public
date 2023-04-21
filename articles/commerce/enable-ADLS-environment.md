---
title: Enable Azure Data Lake Storage in a Dynamics 365 Commerce environment
description: This article provides instructions on how to connect an Azure Data Lake Storage Gen 2 solution to a Dynamics 365 Commerce environment's Entity store. This is a required step before enabling product recommendations.
author: bebeale
ms.date: 04/21/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: global
ms.author: bebeale
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 10.0.5
ms.custom: 
ms.assetid: 
ms.search.industry: Retail, eCommerce
ms.search.form: 
---

# Enable Azure Data Lake Storage in a Dynamics 365 Commerce environment

[!include [banner](includes/banner.md)]

This article provides instructions on how to connect an Azure Data Lake Storage Gen2 solution to a Dynamics 365 Commerce environment's Entity store. This is a required step before enabling product recommendations.

In the Dynamics 365 Commerce solution, the data necessary to compute recommendations, products, and transactions are aggregated in the environment's Entity store. To make this data accessible to other Dynamics 365 services, such as data analytics, business intelligence, and personalized recommendations, it is necessary to connect the environment to a customer-owned Azure Data Lake Storage Gen2 solution.

After the steps above have been completed, all customer data in the environment's Entity store is automatically mirrored to the customer's Azure Data Lake Storage Gen 2 solution. When recommendations features are enabled via the Feature management workspace in Commerce headquarters, the recommendations stack will be granted access to the same Azure Data Lake Storage Gen2 solution.

During the entire process customers' data remains protected and under their control.

## Prerequisites

A Dynamics 365 Commerce environment's Entity store must be connected to an Azure Data Lake Gen Storage Gen2 account and accompanying services.

For more information about Azure Data Lake Storage Gen2 and how to set it up, see [Azure Data Lake Storage Gen2 official documentation](https://azure.microsoft.com/pricing/details/storage/data-lake).
  
## Configuration steps

This section covers the configuration steps necessary for enabling Azure Data Lake Storage Gen2 in an environment as it relates to product recommendations.
For a more in-depth overview of the steps required to enable Azure Data Lake Storage Gen2, see [Make entity store available as a Data Lake](../fin-ops-core/dev-itpro/data-entities/entity-store-data-lake.md).

### Enable Azure Data Lake Storage in the environment

1. Log in to the environment's back office portal.
1. Search for **System Parameters** and navigate to the **Data connections** tab. 
1. Set **Enable Data Lake integration** to **Yes**.
1. Next, enter the following required information:
    1. **Application ID** // **Application Secret** // **DNS Name** - Needed to connect to KeyVault where the Azure Data Lake Storage secret is stored.
    1. **Secret name** - The secret name stored in KeyVault and used to authenticate with Azure Data Lake Storage.
1. Save your changes in the top left corner of the page.

The following image shows an example Azure Data Lake Storage configuration.

![Example of Azure Data Lake Storage configuration.](./media/exampleADLSConfig1.png)

### Test the Azure Data Lake Storage connection

1. Test the connection to KeyVault using the **Test Azure Key Vault** link.
1. Test the connection to Azure Data Lake Storage using the **Test Azure Storage** link.

> [!NOTE]
> If either of the tests above fail, confirm that all of the KeyVault information added above is correct and then try again.

Once the connection tests are successful, you must enable automatic refresh for Entity store.

To enable automatic refresh for Entity store, follow these steps.

1. Search for **Entity Store**.
1. In the list on the left, navigate to the **RetailSales** entry, and select **Edit**.
1. Ensure that **Automatic Refresh Enabled** is set to **Yes**, select **Refresh**, and then select **Save**.

The following image shows an example of Entity store with automatic refresh enabled.

![Example of Entity store with automatic refresh enabled.](./media/exampleADLSConfig2.png)

Azure Data Lake Storage is now configured for the environment. 

If not completed already, follow the steps for [enabling product recommendations and personalization](enable-product-recommendations.md) for the environment.

## Additional resources

[Make entity store available as a data lake](../fin-ops-core/dev-itpro/data-entities/entity-store-data-lake.md)

[Product recommendations overview](product-recommendations.md)

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
