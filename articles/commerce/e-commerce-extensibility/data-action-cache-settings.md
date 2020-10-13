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
| AttributeValue | Contains the metadata of the product attributes information shown on a product details page. For better performance, and to reduce round trips to Retail Server, it is recommended to cache the entity with optimum TTR and TTL values. Longer TTR affects the freshness of the product attributes shown. For information on the APIs returning this entity, see [Products controller](../dev-itpro/retail-server-customer-consumer-api.md#products-controller). |
| Category | Entity containing the metadata of the category information shown in navigation-module. For better performance, and to reduce round trips to retail server, it is recommended to cache the entity with good TTR and TTL values. However, one should be mindful of the fact that longer TTR affects the freshness of the category information shown. To see the retail apis returning this entity, please visit: https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-server-customer-consumer-api#categories-controller |
| CategoryHierarchy	| Entity containing the metadata of the hierarchy of available categories shown in navigation-module. For better performance, and to reduce round trips to retail server, it is recommended to cache the entity with good TTR and TTL values. However, one should be mindful of the fact that longer TTR affects the freshness of the categories hierarchy information shown. To see the retail apis returning this entity, please visit: https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-server-customer-consumer-api#categories-controller |
| OrgUnit | Contains metadata of the organization unit used in BOPIS scenarios and store locator module. For better performance, and to reduce round trips to retail server, it is recommended to cache the entity with good TTR and TTL values. To see the retail apis returning this entity, please visit: https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-server-customer-consumer-api#org-units-controller
| ProductDimensionValue	| Entity containing the metadata of the product dimensions information shown on product details page. For better performance, and to reduce round trips to retail server, it is recommended to cache the entity with good TTR and TTL values. However, one should be mindful of the fact that longer TTR affects the freshness of the product dimensions shown. To see the retail apis returning this entity, please visit: https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-server-customer-consumer-api#products-controller |
| Productlist-recommendations | Entity containing the list of recommended products on homepage, product details page, etc. For better performance, and to reduce round trips to retail server, it is recommended to cache the entity with good TTR and TTL values. However, one should be mindful of the fact that longer TTR affects the freshness of the product list recommendations. |
| productlist-relatedproducts | Entity containing the list of related products, shown on product details page. For better performance, and to reduce round trips to retail server, it is recommended to cache the entity with good TTR and TTL values. However, one should be mindful of the fact that longer TTR affects the freshness of the related products. | 
| ProductRating	| Entity containing the metadata of the product rating information shown on product details page. For better performance, and to reduce round trips to retail server, it is recommended to cache the entity with good TTR and TTL values. However, one should be mindful of the fact that longer TTR affects the freshness of the product rating information shown. To see the retail apis returning this entity, please visit: https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-server-customer-consumer-api#products-controller |
| ProductRefiner | Entity containing the metadata of the product refiners shown on product list page. For better performance, and to reduce round trips to retail server, it is recommended to cache the entity with good TTR and TTL values. However, one should be mindful of the fact that longer TTR affects the freshness of the product refiners. To see the retail apis returning this entity, please visit: https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-server-customer-consumer-api#products-controller |
| ProductSearchResult | Entity containing the metadata of the product search results shown on product list page. For better performance, and to reduce round trips to retail server, it is recommended to cache the entity with good TTR and TTL values. However, one should be mindful of the fact that longer TTR affects the freshness of the product list in search results. To see the retail apis returning this entity, please visit: https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-server-customer-consumer-api#products-controller |
| SimpleProduct	 | Product entity containing the metadata of the product shown in product details page. For better performance, and to reduce round trips to retail server, it is recommended to cache the entity with good TTR and TTL values. However, one should be mindful of the fact that longer TTR affects the freshness of the product information shown. To see the retail apis returning this entity, please visit: https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-server-customer-consumer-api#products-controller |

## Inline cache options

The Dynamics 365 online SDK's data action layer provides flexibility on controlling how a data action response should be cached and its scope (application or request). For all the custom data actions, the cache type can be defined as part of the [action input](data-actions#key-parts-of-a-data-action.md) and it is a common scenario for data actions to invoke a [Retail proxy action](call-retail-server-apis.md), or the module business logic which will invoke a Retail proxy action.  An example might be a user clicks on a "find store" button. For these scenarios, module can set the "bypassCache" option on the action context when invoking the Retail proxy action. This setting tells SDK to honor the module's given cache preferences. 

Supported values for bypassCache are: 
 
* get - ignores cache while performing read and fetches the latest information from Retail server.
* none - ignores cache altogether.
 
Usage example:

```typescript
if (checkoutCartId) {
    try {
        checkoutCart = await readAsync({ callerContext: ctx, bypassCache: 'none' }, checkoutCartId);
    } catch {
        ctx.telemetry.error('Error getting checkout cart based on saved checkout cart id');
        ctx.telemetry.exception(error);
    }
}
```

## Additional resources

[Data actions overview](data-actions.md)

[Core data actions](core-data-actions.md)

[Data action overrides](data-action-overrides.md)
