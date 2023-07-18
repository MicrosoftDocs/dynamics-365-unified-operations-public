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

Based on your business requirements, you might have to build your own CRT extensions and consume CRT Product service requests. When you work with products, CRT Product service requests are required from your extension. For information about how to build CRT extensions, see [Commerce runtime (CRT) extensibility](dev-itpro/commerce-runtime-extensibility.md).

The CRT Product service consists of many requests and responses that are implemented differently. Consumption of the wrong requests can cause performance issues in Commerce Scale Unit (CSU). 

## Search for products

Typically, you must search for products when you don't have the product identifiers (also known as product record identifiers), or when you don't have item identifiers with product dimensions. You can search for products by using keywords, categories, or product refiners. We recommend that you use the `SearchProductsRequest` request to search for products.

> [!NOTE]
> The `ProductSearchRequest` and `ProductSearchServiceRequest` requests use different implementations that return more product information. However, they also consume more CSU resources and can therefore cause performance issues. Therefore, we recommend that you use alternative requests to retrieve product information.

### SearchProductsRequest input parameters

The following table lists commonly used input parameters of `SearchProductsRequest`.

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| SearchCriteria | ProductSearchCriteria | Required | The product search criteria. |
| SearchForItemIdViaBarcode | bool | Optional | A value that specifies whether the keyword should be matched with bar codes and converted to an item identifier. If you're using SQL full-text based search instead of [Cloud-powered search](cloud-powered-search-overview.md), this parameter also enables remote channel search. |

#### ProductSearchCriteria parameters

The following table lists commonly used parameters of `ProductSearchCriteria`.

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| Context | ProjectionDomain | Required | The search context, which contains the channel identifier and catalog identifier. |
| SearchCondition | string | Optional | The search keyword. |
| CategoryIds | IList\<long\> | Optional | The category identifiers. |
| Refinement | IList\<ProductRefinerValue\> | Optional | The search refinements. |

### SearchProductsRequest response

The response for a `SearchProductsRequest` request is a list of `ProductSearchResult` matching products.

## Retrieve product information

As has been mentioned, you can use keywords, categories, or product refiners to search for products, because you typically don't have the product identifiers or item identifiers with product dimensions in these cases. However, to retrieve detailed product information, you must use the product identifiers or item identifiers with product dimensions. We recommend that you use the `GetProductsServiceRequest` request to retrieve product information.

> [!NOTE]
> `GetProductServiceRequest` differs from `GetProductsServiceRequest` and uses a different implementation that returns more product information. However, it also consumes more CSU resources and can therefore cause performance issues. Therefore, we recommend that you use alternative requests to retrieve product information.

### GetProductsServiceRequest input parameters

The following table lists the input parameters of `GetProductsServiceRequest`.

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| ChannelId | long | Required | The channel identifier. |
| ProductIds | ReadOnlyCollection\<long\> | Optional | The product record identifiers to retrieve. |
| ItemAndInventDimIdCombinations | ReadOnlyCollection\<ProductLookupClause\> | Optional | The item identifier and inventory dimension combinations to retrieve. |
| SearchLocation | SearchLocation | Optional | A value that indicates whether products should be retrieved from other channels if they aren't found in the current channel. |
| CalculatePrice | bool | Optional | A value that indicates whether product prices should be calculated. To help improve performance, set the value to **false** if you don't require price calculation. |
| CatalogId | long | Optional | The catalog identifier. Set the value to **0** if the catalog feature isn't used. |
| InventoryLocationId | string | Optional | The warehouse that's used to retrieve quantity limits of products. |

### GetProductsServiceRequest response

The response for a `GetProductsServiceResponse` request is a list of `SimpleProduct` products.

## Other requests to get specific product information

In some cases, you can't get all product information for your business requirements by consuming `GetProductsServiceRequest`. Here are a few examples of requests that you should use for alternative scenarios.

### Retrieve product attributes

When you must retrieve product attributes, we recommend that you use the `GetProductAttributeValuesServiceRequest` request.

> [!NOTE]
> If your products are configured with a large number of attributes, `GetProductAttributeValuesServiceRequest` can consume more CSU resources. Be careful when you consume this request (especially via high-volume APIs), because it might cause CSU performance issues.

#### GetProductAttributeValuesServiceRequest input parameters

The following table lists the input parameters of `GetProductAttributeValuesServiceRequest`.

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| ChannelId | long | Required | The channel identifier. |
| ProductId | long | Required | The product record identifier. |
| CatalogId | long | Required | The catalog identifier. Set the value to **0** if the catalog feature isn't used. |

#### GetProductAttributeValuesServiceRequest response 

The response for a `GetProductAttributeValuesServiceRequest` request is a list of `AttributeValue` values.

### Retrieve product variants

When you must retrieve product variants for product masters, we recommend that you use the `GetVariantProductsServiceRequest` request.

#### GetVariantProductsServiceRequest input parameters

The following table lists the input parameters of `GetVariantProductsServiceRequest`.

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| ChannelId | long | Required | The channel identifier. |
| MasterProductId | long | Required | The product record identifier of the product master. |
| MatchingDimensionValues | ReadOnlyCollection\<ProductDimension\> | Optional | The product dimension values that must be available in the resulting products. |
| MatchingSlotToComponentRelations | ReadOnlyCollection\<ComponentInSlotRelation\> | Optional | The components that must be available in the resulting products. |

#### GetVariantProductsServiceRequest response

The response for a `GetProductsServiceResponse` request is a list of `SimpleProduct` products.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
