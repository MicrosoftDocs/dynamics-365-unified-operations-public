---
# required metadata

title: Create recommendations with demo data
description: This article provides guidance on how to leverage omni-channel product recommendations in Tier-1 single box environments using pre-populated, customizable demo data.
author: bebeale
ms.date: 09/08/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: RetailStoreTable, RetailTillLayout
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 260624
ms.assetid: a4f9d315-9951-451c-8ee6-37f9b3b15ef0
ms.search.region: global
ms.search.industry: Retail
ms.author: asharchw
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
---

# Create recommendations with demo data

[!include [banner](includes/banner.md)]

This article provides guidance on how to leverage omni-channel product recommendations in Tier-1 single box environments using pre-populated, customizable demo data.

Omni-channel product recommendations provide a set of editorially curated or programmatically generated list of products. These lists can be used in several scenarios, depending on the business need. For more information about product recommendation lists, see [Product recommendations overview](product-recommendations.md).

For Tier-2 and higher Dynamics 365 environments, product recommendations are automatically computed based on customer data. Using product recommendations demo data does not disable any product recommendations solution already provisioned in the environment and any costs associated with its usage.

For Tier-1 environments, product recommendations are based only off the static demo data stored in a .csv file.

## Enabling product recommendations demo data in an environment
To enable product recommendations demo date, you need to deploy the Dynamics 365 Commerce Preview Demo Extension to the respective environment. Doing so automatically enables product recommendations demo data.

## Default demo data
Each OneBox type environment comes with a preloaded set of product recommendations demo data stored in the coma separated 'reco_demo_data.csv' file, located on the Commerce Scale Unit.

The data is structured along the following columns.

| Column name         | Mandatory          | Description                                                                                                                                 | Possible values                                                              |
|---------------------|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------|
| RecoList            | :heavy_check_mark: | The specific product recommendation list type that the demo data point is to generate.                                                    | <ul><li>RecoBestSelling</li><li>RecoNew</li><li>RecoTrending</li><li>RecoCart</li><li>RecoPeopleAlsoBuy</li><li>RecoPicks</li><li>RecoSimilarVisual</li><li>RecoSimilarTextual</li></ul> |
| OperatingUnitNumber | :heavy_check_mark: | The specific operating unit number where product recommendations are expected to be   surfaced.                                        |                                                                              |
| Category            |                    |    The category the specific list should be returned for. If no category is specified, the list is for top of navigation hierarchy only.    |                                                                              |
| SeedItemId          |                    |    For lists that require seed (RecoPeopleAlsoBuy and RecoCart), the product those lists should show additional products for.            |                                                                              |
| CustomerId          |                    |    For lists that require a customer identifier (RecoPicks).  The default value '0' applies to all customers.          |                                                                              |
| ItemIds             | :heavy_check_mark: | One or more products to be returned as the result, separated by ';'.                                                                  |                                                                              |

## Customize demo data
You can edit the default demo data with any product and category information configured in HQ. After you update the .csv, the product recommendations that are returned to customers will immediately reflect the changes.

The extension contains a datafile called 'RecoMockDataset.csv', which allows you to control the dataset used to power the mock recommendations results. The file name can be controlled through extension configuration using the **ext.Recommendations.DemoFilePath** setting. This enables you to have multiple datasets available that can be switched between easily through configuration.


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
