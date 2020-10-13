---
# required metadata

title: Data action cache settings
description: This topic covers cache settings for data actions in Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 10/13/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Data action cache settings

[!include [banner](../includes/banner.md)]

This topic covers cache settings for data actions in Microsoft Dynamics 365 Commerce.

## Overview

The software development kit (SDK) \\src\\settings\\cache.settings.json file holds cache settings for entities that are returned from data actions calls. After these entities are cached, they are returned from the cache for all data action requests that have the same cache key, provided that their time to refresh (TTR) and time to live (TTL) values are valid.

For core data actions that are provided in the SDK, the cache key is implicitly set within the data action itself. (For information about how to determine the cache key from the SDK, see the [Determine cache keys for data actions](#determine-cache-keys-for-data-actions) section later in this topic.) For custom data actions, the cache key can be defined in the action input by overriding the **getCacheKey()** method.

For all entities, the default TTR is 60 seconds, and the default TTL is 600 seconds.

The following example shows a JavaScript Object Notation (JSON) file that includes a section for TTR and TTL settings. Each section contains name of the entity for the data action's cache key followed by the time in seconds.

```json
{
    "ttlInSeconds": {
        "AttributeValue": 1800,
        "Category": 1800,
        "CategoryHierarchy": 1800,
        "ChannelConfiguration": 1800,
        "FullProduct": 1800,
        "ProductRating": 1800,
        "OrgUnit": 1800,
        "ProductCatalog": 1800,
        "SimpleProduct": 1800      
    },
    "ttrInSeconds": {
        "AttributeValue": 900,
        "Category": 900,
        "CategoryHierarchy": 1800, 
        "ChannelConfiguration": 1800,
        "FullProduct": 900,
        "OrgUnit": 1800,
        "Product": 900,
        "ProductCatalog": 300,
        "ProductDimensionValue": 900,
        "ProductRating": 900,
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
| AttributeValue | Contains the metadata of the product attributes information shown on a product details page. For better performance, and to reduce round trips to Retail Server, we recommended that you cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the product attributes shown. For information about the APIs returning this entity, see [Products controller](../dev-itpro/retail-server-customer-consumer-api.md#products-controller). |
| Category | Contains the metadata of the category information shown in a navigation module. For better performance, and to reduce round trips to Retail Server, it is recommended to cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the category information shown. For information about the APIs returning this entity, see [Categories controller](../dev-itpro/retail-server-customer-consumer-api.md#categories-controller). |
| CategoryHierarchy	| Contains the metadata of the hierarchy of available categories shown in a navigation module. For better performance, and to reduce round trips to Retail Server, we recommended that you cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the categories hierarchy information shown. For information about the APIs returning this entity, see [Categories controller](../dev-itpro/retail-server-customer-consumer-api.md#categories-controller). |
| OrgUnit | Contains metadata of the organization unit used in "buy online, pick up in store" (BOPIS) scenarios and the store locator module. For better performance, and to reduce round trips to Retail Server, we recommended that you cache the entity with optimum TTR and TTL values. For information about the APIs returning this entity, see [Org units controller](../dev-itpro/retail-server-customer-consumer-api.md#org-units-controller).
| ProductDimensionValue	| Contains the metadata of the product dimensions information shown on a product details page. For better performance, and to reduce round trips to Retail Server, we recommended that you cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the product dimensions shown. For information about the APIs returning this entity, see [Products controller](../dev-itpro/retail-server-customer-consumer-api.md#products-controller). |
| Productlist-recommendations | Contains the list of recommended products on a homepage or product details page. For better performance, and to reduce round trips to Retail Server, we recommended that you cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the product list recommendations. |
| productlist-relatedproducts | Contains the list of related products, shown on product details page. For better performance, and to reduce round trips to Retail Server, we recommended that you cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the related products. | 
| ProductRating	| Contains the metadata of the product rating information shown on a product details page. For better performance, and to reduce round trips to Retail Server, we recommended that you cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the product rating information shown. For information about the APIs returning this entity, see [Products controller](../dev-itpro/retail-server-customer-consumer-api.md#products-controller). |
| ProductRefiner | Contains the metadata of the product refiners shown on a product list page. For better performance, and to reduce round trips to Retail Server, we recommended that you cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the product refiners shown. For information about the APIs returning this entity, see [Products controller](../dev-itpro/retail-server-customer-consumer-api.md#products-controller). |
| ProductSearchResult | Contains the metadata of the product search results shown on a product list page. For better performance, and to reduce round trips to Retail Server, we recommended that you cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the product list in search results. For information about the APIs returning this entity, see [Products controller](../dev-itpro/retail-server-customer-consumer-api.md#products-controller).|
| SimpleProduct	 | Contains the metadata of the product shown on a product details page. For better performance, and to reduce round trips to Retail Server, we recommended that you cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the product information shown. For information about the APIs returning this entity, see [Products controller](../dev-itpro/retail-server-customer-consumer-api.md#products-controller). |

## Inline cache options

The Dynamics 365 Commerce online SDK's data action layer provides flexibility for controlling how a data action response should be cached and what its scope should be (application or request). For all custom data actions, the cache type can be defined as part of the [action input](data-actions.md#key-parts-of-a-data-action). A common scenario is for data actions to invoke a [Retail Server proxy action](call-retail-server-apis.md), or module business logic that will invoke a Retail Server proxy action. An example of such a scenario would be when a user selects a "find store" button. For these scenarios, a module can set the "bypassCache" option on the action context when invoking the Retail Server proxy action. This setting tells the SDK to honor the module's given cache preferences. 

Supported values for bypassCache are: 
 
- **get** - Ignores cache while performing read and fetches the latest information from Retail Server.
- **none** - Ignores cache altogether.
 
The following is an example of usage.

```typescript
if (checkoutCartId) {
    try {
        checkoutCart = await readAsync({ callerContext: ctx, bypassCache: 'none' }, checkoutCartId);
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
