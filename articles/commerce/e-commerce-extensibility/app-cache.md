---
# required metadata

title: Data action cache
description: This topic describes provide details on the supported Dynamics 365 Commerce e-Commerce data action cache options. 
author: samjarawan
manager: annbe
ms.date: 09/15/2020
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
# Data action cache

[!include [banner](../includes/banner.md)]
This topic describes provide details on the supported Dynamics 365 Commerce e-Commerce data action cache options.

## Overview
The Dynamics 365 Commerce online SDK supports caching entities at the app level to enable caching of data action responses to improve rendering performance and reduce server load. For more information see the [data actions](data-actions.md) overview.

## Caching a data action
A data action can choose to save its data in either the request or app cache based on its action input. The **dataCacheType** property of ActionInput enables the underlying
action runtime to make this decision on action's behalf. By default the action responses go into request cache.

``` ts
export class FullProductInput implements IActionInput {
    public productId: number;
    public channelId: number;
    public ProductDetailsCriteria: ProductDetailsCriteria;

    constructor(productId: number | string, channelId: number, criteria: ProductDetailsCriteria) {
        this.productId = typeof productId === 'string' ? parseInt(productId, 10) : productId;
        this.channelId = channelId;
        this.ProductDetailsCriteria = criteria;
    }

    public getCacheKey = () => `${this.productId.toString()}-${this.channelId.toString()}-${this.ProductDetailsCriteria}`;
    public getCacheObjectType = () => 'FullProduct';
    public dataCacheType = (): CacheType => 'request';
}

```

## Supported Cache Types

The following cache types are supported and can be set on the **dataCacheType**:

**request**: action input caches the entity for the life cycle of the request i.e. all the subsequent data action inputs with same cachekey (within same request) shall be served from request cache.

**application**: action input caches the entity for the life cycle of the application (subject to TTR/TTL defined in cache settings, see below) i.e. all the subsequent data action inputs with same cachekey shall be served from application cache.

**instance**: instance is a special cache type setting primarily used for aggregator data actions that do not make a request and extract information from other data actions eg: categories hierarchy. Such data actions are run on server and client independently. If instance is not specifed then such aggregator data actions would contain duplicate data.

**none**: used to skip/bypass request cache. An action with cache type 'none' skips the caching layer completely.

## Cache settings

Cache settings can be configured using the \src\settings\cache-settings.json. Below is the format of the cache-settings.json

``` json
{
    "checkPeriodInSeconds": 120,
    "ttlInSeconds": {
        "entity-with-ttl": 4,
        "category": 60
    },
    "ttrInSeconds": {
        "entity-with-ttr": 2
    }
}
```

For more details see the [Data action cache settings](data-action-cache-settings.md) document.

#### checkPeriodInSeconds
This setting represents the time interval in seconds, at which SDK will do a pass on the app-cache to nudge TTL expired items from the cache. Default value is 600 seconds.

#### ttlInSeconds - TTL (Time to Live)
This setting indicates the duration an entity can stay in the app cache. This value is configurable both at the app level and also per entity. Please refer cache-settings section below for more details. Default value is 600 seconds.

#### ttrInSeconds - TTR (Time to Refresh)
TTR tells the action runtime to keep the data fresh, in the sense that the cache value is retained in the app-cache but a fresh call is made to update the cache data. In the event of an unexpected error, you can still choose to return the data in the cache. Default value is 60 seconds.

#### defaultTTLInSeconds
Default Time To Live(in seconds) for all the cache items. Default value is 600 seconds.

#### defaultTTRInSeconds
Default Time To Refresh(in seconds) for all the cache items. Default value is 60 seconds.
