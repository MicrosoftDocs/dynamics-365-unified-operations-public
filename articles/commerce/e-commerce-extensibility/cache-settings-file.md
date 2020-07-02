---
# required metadata

title: Data action cache settings
description: This topic covers cache settings in Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 07/02/2020
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

This topic covers date action cache settings in Microsoft Dynamics 365 Commerce.

## Overview

The software development kit (SDK) \\src\\settings\\cache.settings.json file holds cache settings for entities returned from data actions calls. Once cached, these entities are returned from cache for all data action requests with the same cache key as long as their time to refresh (TTR) and time to live (TTL) values are valid. The cache key for core data actions provided in the SDK is implicitly set within the data action itself (see [Determine data action cache keys](#Determine-data-action-cache-keys) below for information on how to determine the cache key from the SDK). For custom data actions, the cache key can be defined in the action input by overriding the **getCacheKey()** method.

For all entities, the default TTR is 60 seconds and the default TTL is 600 seconds.

The following example shows a JavaScript Object Notation (JSON) file that includes a section for TTR and TTL settings. Each section contains the data action cache key entity name followed by the time in seconds.

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

## Determine data action cache keys

The data cache key for specific core data actions can be found by looking at the source code under the SDK \\node_modules\\@msdyn365-commerce-modules\\retail-actions\\dist\\lib directory.

For example, the "get-simple-products" data action code would be found by looking in the get-simple-products.js file. By examining the source code of the get-simple-products.js file in the example below, the entity name **SimpleProduct** can be located and then added to the cache settings JSON file in the example above.

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

## Additional resources

[Data actions overview](data-actions.md)

[Core data actions](core-data-actions.md)

[Data action overrides](data-action-overrides.md)
