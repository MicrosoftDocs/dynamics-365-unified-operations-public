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

Based on your business requirements, you might need to build your own Commerce runtime (CRT) extensions and consume requests of CRT services. When you are working with products, requests of CRT Product service will be required from your extension. For information on building CRT extensions, see [Commerce runtime (CRT) extensibility](dev-itpro/commerce-runtime-extensibility.md).

CRT Product service consists of many requests and responses which are implemented differently. Consuming the wrong requests can lead to performance issues in Commerce Scale Unit (CSU). 

## Search for products

Typically, you will need to search for products when you don't have the product identifiers (also known as product record identifiers) or item identifiers with product dimensions. You can search for products using keywords, categories, or product refiners. To search for products, Microsoft recommends using the `SearchProductsRequest` request.

> [!NOTE]
> `ProductSearchRequest` and `ProductSearchServiceRequest` requests use different implementations that return more product information, but they can also consume more CSU resources that leads to performance issues. Microsoft recommends that you use alternative requests to retrieve product information.

### SearchProductsRequest input parameters

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| SearchCriteria | ProductSearchCriteria | Required | The product search criteria. |
| SearchForItemIdViaBarcode | bool | Optional | Whether to match the keyword with bar codes and convert the keyword to item identifier. When you are using SQL full-text based search instead of [Cloud-powered search](cloud-powered-search-overview.md), this parameter also enables remote channel search. |

#### ProductSearchCriteria parameters

Here are the commonly used parameters of `ProductSearchCriteria`.

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| Context | ProjectionDomain | Required | The search context contains channel identifier and catalog identifier. |
| SearchCondition | string | Optional | The search keyword. |
| CategoryIds | IList\<long\> | Optional | The category identifiers. |
| Refinement | IList\<ProductRefinerValue\> | Optional | The refinements. |

### SearchProductsRequest response

The response of a `SearchProductsRequest` request is a list of `ProductSearchResult` containing matching products.

## Retrieve product information

Unlike searching for products, you will need to retrieve detailed product information when you already have the product identifiers, i.e., product record identifier, or item identifier with product dimensions. To retrive product information, Microsoft recommends that you use the `GetProductsServiceRequest` request.

> [!NOTE]
> `GetProductServiceRequest` (note the Products/Product plural difference with `GetProductsServiceRequest`) uses a different implementation that returns more product information, but can also consume more CSU  resources and lead to performance issues. Microsoft recommends that you use alternative requests to retrieve product information.

### GetProductsServiceRequest input parameters

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| ChannelId | long | Required | The channel identifier. |
| ProductIds | ReadOnlyCollection\<long\> | Optional | The product record identifiers to retrieve. |
| ItemAndInventDimIdCombinations | ReadOnlyCollection\<ProductLookupClause\> | Optional | The item identifier and inventory dimension combinations to retrieve. |
| SearchLocation | SearchLocation | Optional | Whether to retrieve products from other channels when they are not found in current channel. |
| CalculatePrice | bool | Optional | Whether to calculate product prices. Disable it to improve performance if you don't need it. |
| CatalogId | long | Optional | The catalog identifier. Set to 0 if catalog feature is not used. |
| InventoryLocationId | string | Optional | The warehouse to retrieve quantity limits of product behavior. |

### GetProductsServiceRequest response

The response of a `GetProductsServiceResponse` request is a list of `SimpleProduct` products.

## Other requests to get specific product information

In some cases, you can't get all product information for your business requirements by consuming `GetProductsServiceRequest`. Here are a few examples.

### Retrieve product attributes

To retrieve product attributes, Microsoft recommends that you use the `GetProductAttributeValuesServiceRequest` request.

> [!NOTE]
> If your products are configured with high number of attributes, `GetProductAttributeValuesServiceRequest` can consume more CSU resources. Be cautious when consuming this request, especially on the high-volume APIs because it might cause CSU performance issues.

#### GetProductAttributeValuesServiceRequest input parameters

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| ChannelId | long | Required | The channel identifier. |
| ProductId | long | Required | The product record identifier. |
| CatalogId | long | Required | The catalog identifier. Set to 0 if catalog feature is not used. |

#### GetProductAttributeValuesServiceRequest response: 

The response of a `GetProductAttributeValuesServiceRequest` request is a list of `AttributeValue` values.

### Retrieve product variants

To retrieve product variants for product masters, Microsoft recommends that you use the `GetVariantProductsServiceRequest` request.

#### GetVariantProductsServiceRequest input parameters

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| ChannelId | long | Required | The channel identifier. |
| MasterProductId | long | Required | The product record identifier of the product master. |
| MatchingDimensionValues | ReadOnlyCollection\<ProductDimension\> | Optional | The product dimension values that must be available in the resultant products. |
| MatchingSlotToComponentRelations | ReadOnlyCollection\<ComponentInSlotRelation\> | Optional | The components that must be available in the resultant products. |

### GetVariantProductsServiceRequest response

The response of a `GetProductsServiceResponse` request is a list of `SimpleProduct` products.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
