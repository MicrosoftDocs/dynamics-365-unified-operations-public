---
# required metadata

title: Data action cache settings
description: This topic covers cache settings in Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 10/01/2019
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

This topic covers cache settings in Microsoft Dynamics 365 Commerce.

## Overview

The SDK \\src\\settings\\cache.settings.json file holds cache settings for entities returned from data actions calls. These entities, once cached would be returned from cache for all data action requests with the same cache key as long as their TTR(time to refresh) TTL(time to live) are valid. The cache key for core data actions provided in the SDK are implicitly set within the data action itself, see below on how to determine the cache key from the SDK. For custom data actions, the cache key can be defined in the action input by overriding getCacheKey() method.

The following example shows a JavaScript Object Notation (JSON) file that includes a section for the **time to refresh** and **time to live** settings.  Each section contains the data action cache key entity name followed by the time in seconds.

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

## Data action cache keys
The data cache key for specific core data actions can be found by looking at the source code under the SDK "\node_modules\@msdyn365-commerce-modules\retail-actions\dist\lib" directory.

In the below example, the **get-simple-products** data action code is found in the 'get-simple-products.js' file.  Examining the source code, the entity name **SimpleProduct** can be added to the cache settings file above.

```
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
