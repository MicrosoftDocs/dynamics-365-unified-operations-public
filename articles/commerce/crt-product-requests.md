---
title: Consume Commerce runtime (CRT) Product service requests
description: This article describes how to consume Commerce runtime (CRT) Product service requests to search for products and retrieve product information in Microsoft Dynamics 365 Commerce.
author: rickwyang
ms.date: 07/18/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: wenxyang
ms.search.validFrom: 2023-07-05

---

# Consume Commerce runtime (CRT) Product service requests

[!include [banner](includes/banner.md)]

This article describes how to consume Commerce runtime (CRT) Product service requests to search for products and retrieve product information in Microsoft Dynamics 365 Commerce.

Based on your business requirements, you might need to build your own Commerce runtime (CRT) extensions and consume CRT Product service requests. When you are working with products, CRT Product service requests are required from your extension. For information on building CRT extensions, see [Commerce runtime (CRT) extensibility](dev-itpro/commerce-runtime-extensibility.md).

The CRT Product service consists of many requests and responses which are implemented differently. Consuming the wrong requests can lead to performance issues in Commerce Scale Unit (CSU). 

## Search for products

Typically, you'll need to search for products when you don't have the product identifiers (also known as product record identifiers) or item identifiers with product dimensions. You can search for products using keywords, categories, or product refiners. To search for products, Microsoft recommends using the `SearchProductsRequest` request.

> [!NOTE]
> The `ProductSearchRequest` and `ProductSearchServiceRequest` requests use different implementations that return more product information, but they also consume more CSU resources, which can lead to performance issues. Microsoft recommends that you use alternative requests to retrieve product information.

### SearchProductsRequest input parameters

The following table lists commonly used input parameters of `SearchProductsRequest`.

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| SearchCriteria | ProductSearchCriteria | Required | The product search criteria. |
| SearchForItemIdViaBarcode | bool | Optional | Whether or not to match the keyword with barcodes and convert the keyword to an item identifier. When you are using SQL full-text based search instead of [Cloud-powered search](cloud-powered-search-overview.md), this parameter also enables remote channel search. |

#### ProductSearchCriteria parameters

The following table lists commonly used parameters of `ProductSearchCriteria`.

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| Context | ProjectionDomain | Required | The search context contains channel identifier and catalog identifier. |
| SearchCondition | string | Optional | The search keyword. |
| CategoryIds | IList\<long\> | Optional | The category identifiers. |
| Refinement | IList\<ProductRefinerValue\> | Optional | The search refinements. |

### SearchProductsRequest response

The response of a `SearchProductsRequest` request is a list of `ProductSearchResult` matching products.

## Retrieve product information

Unlike when you search for products, when you retrieve product information you must use product identifiers (such as product record identifiers, or item identifiers with product dimensions) to retrieve detailed product information. To retrieve product information, Microsoft recommends that you use the `GetProductsServiceRequest` request.

> [!NOTE]
> `GetProductServiceRequest` (different from `GetProductsServiceRequest`) uses a different implementation than `GetProductsServiceRequest` that returns more product information, but it also consumes more CSU  resources that can lead to performance issues. Microsoft recommends that you use alternative requests to retrieve product information.

### GetProductsServiceRequest input parameters

The following table lists the input parameters of `GetProductsServiceRequest`.

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| ChannelId | long | Required | The channel identifier. |
| ProductIds | ReadOnlyCollection\<long\> | Optional | The product record identifiers to retrieve. |
| ItemAndInventDimIdCombinations | ReadOnlyCollection\<ProductLookupClause\> | Optional | The item identifier and inventory dimension combinations to retrieve. |
| SearchLocation | SearchLocation | Optional | Whether to retrieve products from other channels when they aren't found in the current channel. |
| CalculatePrice | bool | Optional | Whether or not to calculate product prices. Set it to **false** if you don't need it to improve performance. |
| CatalogId | long | Optional | The catalog identifier. Set to "0" if the catalog feature isn't used. |
| InventoryLocationId | string | Optional | The warehouse used to retrieve quantity limits of products. |

### GetProductsServiceRequest response

The response of a `GetProductsServiceResponse` request is a list of `SimpleProduct` products.

## Other requests to get specific product information

In some cases, you can't get all product information for your business requirements by consuming `GetProductsServiceRequest`. Here are a few examples of requests you should use for alternative scenarios.

### Retrieve product attributes

To retrieve product attributes, Microsoft recommends that you use the `GetProductAttributeValuesServiceRequest` request.

> [!NOTE]
> If your products are configured with high number of attributes, `GetProductAttributeValuesServiceRequest` can consume more CSU resources. Be cautious when consuming this request (especially with high-volume APIs) because it might cause CSU performance issues.

#### GetProductAttributeValuesServiceRequest input parameters

The following table lists the input parameters of `GetProductAttributeValuesServiceRequest`.

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| ChannelId | long | Required | The channel identifier. |
| ProductId | long | Required | The product record identifier. |
| CatalogId | long | Required | The catalog identifier. Set to "0" if catalog feature isn't used. |

#### GetProductAttributeValuesServiceRequest response 

The response of a `GetProductAttributeValuesServiceRequest` request is a list of `AttributeValue` values.

### Retrieve product variants

To retrieve product variants for product masters, Microsoft recommends that you use the `GetVariantProductsServiceRequest` request.

#### GetVariantProductsServiceRequest input parameters

The following table lists the input parameters of `GetVariantProductsServiceRequest`.

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| ChannelId | long | Required | The channel identifier. |
| MasterProductId | long | Required | The product record identifier of the product master. |
| MatchingDimensionValues | ReadOnlyCollection\<ProductDimension\> | Optional | The product dimension values that must be available in the resultant products. |
| MatchingSlotToComponentRelations | ReadOnlyCollection\<ComponentInSlotRelation\> | Optional | The components that must be available in the resultant products. |

### GetVariantProductsServiceRequest response

The response of a `GetProductsServiceResponse` request is a list of `SimpleProduct` products.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
