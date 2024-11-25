---
title: Data action cache settings
description: This article covers cache settings for data actions in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 08/02/2024
ms.topic: how-to
audience: Developer
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---
# Data action cache settings

[!include [banner](../includes/banner.md)]

This article covers cache settings for data actions in Microsoft Dynamics 365 Commerce.

The software development kit (SDK) \\src\\settings\\cache.settings.json file holds cache settings for entities that are returned from data actions calls. After these entities are cached, they are returned from the cache for all data action requests that have the same cache key, provided that their time to refresh (TTR) and time to live (TTL) values are valid.

For core data actions that are provided in the SDK, the cache key is implicitly set within the data action itself. (For information about how to determine the cache key from the SDK, see the [Determine cache keys for data actions](#determine-cache-keys-for-data-actions) section later in this article.) For custom data actions, the cache key can be defined in the action input by overriding the **getCacheKey()** method.

For all entities, the default TTR is 60 seconds, and the default TTL is 600 seconds.

The following example shows a JavaScript Object Notation (JSON) file that includes a section for TTR and TTL settings. Each section contains name of the entity for the data action's cache key followed by the time in seconds. This example might differ from the file that is included in the SDK, because the SDK is regularly updated.

```json
{
    "checkPeriodInSeconds": 1800,
    "ttlInSeconds": {
        "AttributeValue": 43200,
        "Category": 43200,
        "CategoryHierarchy": 43200,
        "CategoryPath": 43200,
        "ChannelConfiguration": 43200,
        "ChannelDeliveryConfiguration": 43200,
        "FeatureState": 43200,
        "FullProduct": 43200,
        "FullProductSearchResult": 43200,
        "MappedSearchInput": 43200,
        "OrgUnit": 43200,
        "OrgUnitLocation": 43200,
        "Product": 43200,
        "ProductCatalog": 43200,
        "ProductDimensionValue": 43200,
        "PRODUCTLIST-RECOMMENDATION":43200,
        "PRODUCTLIST-RELATEDPRODUCTS":43200,
        "ProductRating": 43200,
        "ProductRefiner": 43200,
        "SimpleProduct": 43200
    },
    "ttrInSeconds": {
        "AttributeValue": 900,
        "Category": 900,
        "CategoryHierarchy": 1800,
        "CategoryPath": 900,
        "ChannelConfiguration": 1800,
        "ChannelDeliveryConfiguration": 1800,
        "FeatureState": 900,
        "FullProduct": 900,
        "FullProductSearchResult": 900,
        "MappedSearchInput": 900,
        "OrgUnit": 1800,
        "OrgUnitLocation": 900,
        "Product": 900,
        "ProductCatalog": 900,
        "ProductDimensionValue": 1800,
        "PRODUCTLIST-RECOMMENDATION":900,
        "PRODUCTLIST-RELATEDPRODUCTS":900,
        "ProductRating": 900,
        "ProductRefiner": 900,
        "SimpleProduct": 900
    }
}
```

## Determine cache keys for data actions

You can find the data cache key for a specific core data action by looking at the source code under the SDK \\node_modules\\@msdyn365-commerce-modules\\retail-actions\\dist\\lib directory.

For example, to find the code for the "get-simple-products" data action, look in the get-simple-products.js file. By examining the source code of this file in the following example, you can find the entity name **SimpleProduct**. You can then add this entity to the JSON file for cache settings in the previous example.

```JavaScript
...
export class ProductInput {
    constructor(productId, apiSettings, channelId) {
        this.getCacheKey = () => buildCacheKey(`RecordId-${this.productId.toString()}`, this.apiSettings);
        this.getCacheObjectType = () => 'SimpleProduct';
        this.dataCacheType = () => 'application';
        this.apiSettings = apiSettings;
        this.productId = +productId;
        this.channelId = channelId || apiSettings.channelId;
    }
}
...
```

## Cache settings for specific entities

The following table provides cache setting descriptions for specific data action cache key entities.

| Entity | Description |
| ------ | ----------- |
| AttributeValue | Contains the metadata of the product attributes information shown on a product details page. For better performance, and to reduce round trips to Retail Server, we recommend that you cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the product attributes shown. For information about the APIs returning this entity, see [Products controller](../dev-itpro/retail-server-customer-consumer-api.md#products-controller). |
| Category | Contains the metadata of the category information shown in a navigation module. For better performance, and to reduce round trips to Retail Server, we recommend that you cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the category information shown. For information about the APIs returning this entity, see [Categories controller](../dev-itpro/retail-server-customer-consumer-api.md#categories-controller). |
| CategoryHierarchy | Contains the metadata of the hierarchy of available categories shown in a navigation module. For better performance, and to reduce round trips to Retail Server, we recommend that you cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the categories hierarchy information shown. For information about the APIs returning this entity, see [Categories controller](../dev-itpro/retail-server-customer-consumer-api.md#categories-controller). |
| CategoryPath | Contains the metadata of the category path that is used in the breadcrumb module. For better performance, and to reduce round trips to Retail Server, we recommend that you cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the category path information. |
| ChannelConfiguration | Contains the metadata of the channel information that is used in purchase flows. For better performance, and to reduce round trips to Retail Server, we recommend that you cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the channel configuration that is shown. For information about the APIs that return this entity, see [Org units controller](../dev-itpro/retail-server-customer-consumer-api.md#org-units-controller). |
| ChannelDeliveryConfiguration | Contains the metadata of the channel delivery configuration that is used in checkout and order confirmation. For better performance, and to reduce round trips to Retail Server, we recommend that you cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the channel delivery configuration. |
| FeatureState | Contains the metadata of the feature state that is used in purchase flows and order templates. For better performance, and to reduce round trips to Retail Server, we recommend that you cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the feature state information. |
| FullProduct | Contains the metadata of the full product that is used in order templates and for search scenarios. For better performance, and to reduce round trips to Retail Server, we recommend that you cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the full product that is shown. |
| FullProductSearchResult | Contains the metadata of the full product search results that are used for search scenarios. For better performance, and to reduce round trips to Retail Server, we recommend that you cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the full product search results that are shown. |
| MappedSearchInput | Contains the metadata of the mapped search input that is used for search scenarios. For better performance, and to reduce round trips to Retail Server, we recommend that you cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the mapped search input. |
| OrgUnit | Contains the metadata of the organization unit that is used in "buy online, pick up in store" (BOPIS) scenarios and the store locator module. For better performance, and to reduce round trips to Retail Server, we recommend that you cache the entity with optimum TTR and TTL values. For information about the APIs that return this entity, see [Org units controller](../dev-itpro/retail-server-customer-consumer-api.md#org-units-controller). |
| OrgUnitLocation | Contains the metadata of the organization unit location that is used in the store locator module and purchase flows. For better performance, and to reduce round trips to Retail Server, we recommend that you cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the organization unit location. For information about the APIs that return this entity, see [Org units controller](../dev-itpro/retail-server-customer-consumer-api.md#org-units-controller). |
| Product | Contains the metadata of the product information that is used for search scenarios. For better performance, and to reduce round trips to Retail Server, we recommend that you cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the mapped search input. For information about the APIs that return this entity, see [Products controller](../dev-itpro/retail-server-customer-consumer-api.md#products-controller). |
| ProductDimensionValue | Contains the metadata of the product dimensions information shown on a product details page. For better performance, and to reduce round trips to Retail Server, we recommend that you cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the product dimensions shown. For information about the APIs returning this entity, see [Products controller](../dev-itpro/retail-server-customer-consumer-api.md#products-controller). |
| PRODUCTLIST-RECOMMENDATION | Contains the list of recommended products that is shown on a homepage or a product details page. For better performance, and to reduce round trips to Retail Server, we recommend that you cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the product list recommendations. |
| PRODUCTLIST-RELATEDPRODUCTS | Contains the list of related products that is shown on a product details page. For better performance, and to reduce round trips to Retail Server, we recommend that you cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the related products. | 
| ProductRating | Contains the metadata of the product rating information shown on a product details page. For better performance, and to reduce round trips to Retail Server, we recommend that you cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the product rating information shown. For information about the APIs returning this entity, see [Products controller](../dev-itpro/retail-server-customer-consumer-api.md#products-controller). |
| ProductRefiner | Contains the metadata of the product refiners shown on a product list page. For better performance, and to reduce round trips to Retail Server, we recommend that you cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the product refiners shown. For information about the APIs returning this entity, see [Products controller](../dev-itpro/retail-server-customer-consumer-api.md#products-controller). |
| ProductSearchResult | Contains the metadata of the product search results shown on a product list page. For better performance, and to reduce round trips to Retail Server, we recommend that you cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the product list in search results. For information about the APIs returning this entity, see [Products controller](../dev-itpro/retail-server-customer-consumer-api.md#products-controller).|
| SimpleProduct | Contains the metadata of the product shown on a product details page. For better performance, and to reduce round trips to Retail Server, we recommend that you cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the product information shown. For information about the APIs returning this entity, see [Products controller](../dev-itpro/retail-server-customer-consumer-api.md#products-controller). |

## Inline cache options

The Dynamics 365 Commerce online SDK's data action layer provides flexibility for controlling how a data action response should be cached and what its scope should be (application or request). For all custom data actions, the cache type can be defined as part of the [action input](data-actions.md#key-parts-of-a-data-action). A common scenario is for data actions to invoke a Retail Server proxy data action, or module business logic that will invoke a Retail Server proxy data action. An example of such a scenario would be when a user selects a "find store" button. For these scenarios, a module can set the "bypassCache" option on the action context when invoking the Retail Server proxy data action. This setting tells the SDK to honor the module's given cache preferences. For more information about Retail Server proxy data actions, see [Call Retail Server APIs](call-retail-server-apis.md).

Supported values for bypassCache are: 
 
- **get** - Ignores cache while performing read and fetches the latest information from Retail Server.
- **none** - Action response is cached per request. If byPassCache is not specified runtime defaults to this value.
 
In general, for custom data actions and Retail Server proxy actions that read data from Retail Server (calling APIs with names that start with "get," "search," or "read"), the value of "bypassCache" is set to "none" by default. For all other Retail Server proxy actions configured to fetch the latest data from Retail Server, the value of "bypassCache" is set to "get" by default. These values can be overridden if needed.
 
The following is an example of usage.

```typescript
if (checkoutCartId) {
    try {
        checkoutCart = await readAsync({ callerContext: ctx, bypassCache: 'get' }, checkoutCartId);
    } catch {
        ctx.telemetry.error('Error getting checkout cart based on saved checkout cart ID');
        ctx.telemetry.exception(error);
    }
}
```

## Additional resources

[Data actions overview](data-actions.md)

[Core data actions](core-data-actions.md)

[Data action overrides](data-action-overrides.md)

[Commerce Scale Unit customer and consumer APIs](../dev-itpro/retail-server-customer-consumer-api.md)

[Call Retail Server APIs](call-retail-server-apis.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
