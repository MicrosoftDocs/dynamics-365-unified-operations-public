---
# required metadata

title: Omni-channel product recommendations demo data
description: This document aims to provide guidance on how to leverage omni-channel product recommendations in Tier-1 single box environments using pre-populated, customizable demo data.
author: bebeale
manager: AnnBe
ms.date: 10/1/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
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
ms.search.validFrom: 2019-07-31
ms.dyn365.ops.version: 10.0.5

---

# Omni-channel product recommendations demo data

This document aims to provide guidance on how to leverage omni-channel product recommendations in Tier-1 single box 
environments using pre-populated, customizable demo data.

Omni-channel product recommendations provide a set of editorially curated or programmatically generated ordered list of products. 
These lists can be used in several scenarios, depending on the business need. 
For more information about product recommendation lists, see [Product recommendations overview.](product-recommendaitons-overview.md)

For Tier-2 and higher Dynamics Environments product recommendations are automatically computed based on customer data.
Using product recommendations demo data does not disable any product recommendations solution already provisioned in the environment
and any costs associated with its usage.

For Tier-1 environments product recommendations are based only off the static demo data stored in a csv file.

## Enabling product recommendations demo data in an environment

Customers need to deploy the **Dynamics 365 Commerce Preview Demo Extension** to the respective environment, 
which automatically enables product recommendations demo data.

## Default demo data
Each Onebox type environment comes with a preloaded set of product recommendations demo data stored in the 
coma separated **‘reco_demo_data.csv’** file, located in the same folder as this document on Retail Server.

This data is structured along the following columns

| Column name         | Mandatory          | Description                                                                                                                                 | Possible Values                                                              |
|---------------------|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------|
| RecoList            | :heavy_check_mark: | The specific product   recommendation list type that the demo data point is to generate.                                                    | <ul><li>RecoBestSelling</li><li>RecoNew</li><li>RecoTrending</li><li>RecoCart</li><li>RecoPeopleAlsoBuy</li></ul> |
| OperatingUnitNumber | :heavy_check_mark: | The specific   operating unit number where product recommendations are expected to be   surfaced in.                                        |                                                                              |
| Category            |                    |    The category the   specific list should be returned for. If no category is specified, list is   for top of navigation hierarchy only.    |                                                                              |
| SeedItemId          |                    |    For lists that   require seed (RecoPeopleAlsoBuy and RecoCart) the product those lists should   show additional products for.            |                                                                              |
| ItemIds             | :heavy_check_mark: | One or more products   to be returned as the result, separated by **‘;’**.                                                                  |                                                                              |


## Customize demo data
Customers can edit the default demo data with any product and category information that is configured in HQ. 
Once the CSV is updated, the Product Recommendations returned to customers will immediately reflect the changes.

The extension contains a datafile called RecoMockDataset.csv which allows the customer to control the dataset used to power the
mock recommendations results. The file name can be controlled through extension configuration using the 
**ext.Recommendations.DemoFilePath** setting. This enables the customers to have multiple datasets available that can be switched
between easily through configuration.

```
  <settings>
    <add name="ext.Recommendations.DemoFilePath" value="RecoMockDataset.csv" />
  </settings>
```

## Additional resources

[Product recommendations overview](product-recommendations-overview.md)

[Environment planning](environment-planning.md)
