---
title: Create recommendations with demo data
description: Learn how to use omnichannel product recommendations in Tier-1 single box environments using prepopulated, customizable demo data.
author: bebeale
ms.date: 01/28/2026
ms.topic: how-to
ms.search.form: RetailStoreTable, RetailTillLayout
ms.reviewer: v-griffinc
ms.assetid: a4f9d315-9951-451c-8ee6-37f9b3b15ef0
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2016-11-30
ms.custom: 
  - bap-template
---

# Create recommendations with demo data

[!include [banner](includes/banner.md)]

This article provides guidance on how to use omnichannel product recommendations in Tier-1 single box environments by using prepopulated, customizable demo data.

Omnichannel product recommendations provide a set of editorially curated or programmatically generated list of products. You can use these lists in several scenarios, depending on the business need. For more information about product recommendation lists, see [Product recommendations overview](product-recommendations.md).

For Tier-2 and higher Dynamics 365 environments, customer data automatically drives product recommendations. Using product recommendations demo data doesn't disable any product recommendations solution already provisioned in the environment, and it doesn't affect any costs associated with its usage.

For Tier-1 environments, product recommendations rely only on static demo data stored in a .csv file.

## Enable product recommendations demo data in an environment
To enable product recommendations demo data, deploy the Dynamics 365 Commerce Preview Demo Extension to the environment. This action automatically enables product recommendations demo data.

## Default demo data
Each OneBox type environment includes a preloaded set of product recommendations demo data stored in the comma separated `reco_demo_data.csv` file, located on the Commerce Scale Unit.

The data is structured along the following columns.

| Column name         | Mandatory          | Description                                                                                                                                 | Possible values                                                              |
|---------------------|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------|
| RecoList            | :heavy_check_mark: | The specific product recommendation list type that the demo data point generates.                                                    | <ul><li>RecoBestSelling</li><li>RecoNew</li><li>RecoTrending</li><li>RecoCart</li><li>RecoPeopleAlsoBuy</li><li>RecoPicks</li><li>RecoSimilarVisual</li><li>RecoSimilarTextual</li></ul> |
| OperatingUnitNumber | :heavy_check_mark: | The specific operating unit number where product recommendations surface.                                        |                                                                              |
| Category            |                    |    The category the specific list should be returned for. If no category is specified, the list is for top of navigation hierarchy only.    |                                                                              |
| SeedItemId          |                    |    For lists that require seed (RecoPeopleAlsoBuy and RecoCart), the product for which those lists show more products.            |                                                                              |
| CustomerId          |                    |    For lists that require a customer identifier (RecoPicks). The default value '0' applies to all customers.          |                                                                              |
| ItemIds             | :heavy_check_mark: | One or more products to return as the result, separated by ';'.                                                                  |                                                                              |

## Customize demo data
You can edit the default demo data with any product and category information configured in HQ. After you update the CSV file, the product recommendations that the system returns to customers immediately reflect the changes.

The extension contains a data file called `RecoMockDataset.csv`, which you use to control the dataset that powers the mock recommendations results. You can control the file name through extension configuration by using the **ext.Recommendations.DemoFilePath** setting. By using this setting, you can have multiple datasets available that you can switch between easily through configuration.


```xml
<settings>
    <add name="ext.Recommendations.DemoFilePath" value="RecoMockDataset.csv" />
</settings>
```

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

[Product recommendations FAQ](faq-recommendations.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
