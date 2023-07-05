---
title: Consuming requests of Commerce runtime (CRT) Product service
description: This article describes how to consume requests of Commerce runtime (CRT) Product service for searching products and retrieving product information in Microsoft Dynamics 365 Commerce.
author: rickwyang
ms.date: 07/05/2023
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: wenxyang
ms.search.validFrom: 2023-07-05
---

# Consuming requests of Commerce runtime (CRT) Product service

Based on your business requirements, you might need to build your own Commerce runtime (CRT) extensions and consume requests of CRT services. When you are working with products, requests of Product service will be required from your extension. To build CRT extensions, please follow [Commerce runtime (CRT) extensibility](dev-itpro/commerce-runtime-extensibility.md).

Product service consists of many requests and responses which are implemented differently. Consuming wrong requests can lead to performance issues in Commerce Scale Unit. In this article, we will provide a general guidance on consuming requests of Product service to search products or retrieving product information.

## Searching for products

Typically, you will need to search for products when you don't have the product identifiers, i.e., product record identifier, or item identifier with product dimensions. You can search for products using keywords, categories, or product refiners. To search for products, `SearchProductsRequest` is recommended to use.

> [!NOTE]
> `ProductSearchRequest` and `ProductSearchServiceRequest` use different implementations that return more product information, but will consume more Commerce Scale Unit resources and lead to performance issues. We recommend to use alternative requests to retrieve product information.

### Input parameters

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| SearchCriteria | ProductSearchCriteria | Required | The product search criteria. |
| SearchForItemIdViaBarcode | bool | Optional | Whether to match the keyword with bar codes and convert the keyword to item identifier. When you are using SQL full-text based search instead of [Cloud-powered search](cloud-powered-search-overview.md), this parameter also enables remote channel search. |

#### ProductSearchCriteria

Here are the commonly used parameters of `ProductSearchCriteria`.

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| Context | ProjectionDomain | Required | The search context contains channel identifier and catalog identifier. |
| SearchCondition | string | Optional | The search keyword. |
| CategoryIds | IList\<long\> | Optional | The category identifiers. |
| Refinement | IList\<ProductRefinerValue\> | Optional | The refinements. |

### Response

The response of `SearchProductsRequest` is a list of `ProductSearchResult` containing matching products.

## Retrieving product information

Unlike searching for products, you will need to retrieve detailed product information when you already have the product identifiers, i.e., product record identifier, or item identifier with product dimensions. To retrive product information, `GetProductsServiceRequest` is recommended to use.

> [!NOTE]
> `GetProductServiceRequest` (note the Products/Product plural difference with `GetProductsServiceRequest`) uses a different implementation that return more product information, but will consume more Commerce Scale Unit resources and lead to performance issues. We recommend to use alternative requests to retrieve product information.

### Input parameters

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| ChannelId | long | Required | The channel identifier. |
| ProductIds | ReadOnlyCollection\<long\> | Optional | The product record identifiers to retrieve. |
| ItemAndInventDimIdCombinations | ReadOnlyCollection\<ProductLookupClause\> | Optional | The item identifier and inventory dimension combinations to retrieve. |
| SearchLocation | SearchLocation | Optional | Whether to retrieve products from other channels when they are not found in current channel. |
| CalculatePrice | bool | Optional | Whether to calculate product prices. Disable it to improve performance if you don't need it. |
| CatalogId | long | Optional | The catalog identifier. Set to 0 if catalog feature is not used. |
| InventoryLocationId | string | Optional | The warehouse to retrieve quantity limits of product behavior. |

### Response

`GetProductsServiceResponse` with a list of `SimpleProduct` inside.

### Other requests to get specific product information

In some cases, you cannot get all product information for your business requirements by consuming `GetProductsServiceRequest`. Here are a few examples.

#### Retrieving product attributes

To retrieve product attributes, `GetProductAttributeValuesServiceRequest` is recommended to use.

> [!NOTE]
> If your products are configured with high number of attributes, `GetProductAttributeValuesServiceRequest` will consume more Commerce Scale Unit resources. Be cautious when consuming this request, especially on the high-volume APIs because it might cause Commerce Scale Unit performance issues.

Input parameters:

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| ChannelId | long | Required | The channel identifier. |
| ProductId | long | Required | The product record identifier. |
| CatalogId | long | Required | The catalog identifier. Set to 0 if catalog feature is not used. |

Response: `GetProductAttributeValuesServiceResponse` with a list of `AttributeValue` inside.

#### Retrieving product variants

To retrieve product variants for product masters, `GetVariantProductsServiceRequest` is recommended to use.

Input parameters:

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| ChannelId | long | Required | The channel identifier. |
| MasterProductId | long | Required | The product record identifier of the product master. |
| MatchingDimensionValues | ReadOnlyCollection\<ProductDimension\> | Optional | The product dimension values that must be available in the resultant products. |
| MatchingSlotToComponentRelations | ReadOnlyCollection\<ComponentInSlotRelation\> | Optional | The components that must be available in the resultant products. |

Response: `GetProductsServiceResponse` with a list of `SimpleProduct` inside.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
