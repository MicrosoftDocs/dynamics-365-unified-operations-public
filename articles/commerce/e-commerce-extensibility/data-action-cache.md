---
title: Data action cache options
description: This article provides an overview of supported data action cache options in Microsoft Dynamics 365 Commerce.
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
# Data action cache options

[!include [banner](../includes/banner.md)]

This article provides an overview of supported data action cache options in Microsoft Dynamics 365 Commerce.

The Dynamics 365 Commerce online software development kit (SDK) supports caching entities at the application level, which enables caching of data action responses to improve rendering performance and reduce server load. For more information, see [Data actions overview](data-actions.md).

## Caching a data action

A data action can save data in either the request or application cache, based on its action input. The **dataCacheType** property of `IActionInput` enables the underlying action runtime to make this decision on the action's behalf. By default, the action responses go into the request cache.

``` typescript
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
## Supported cache types

The following cache types are supported and can be set on the **dataCacheType** property:

- **request**: Action input caches the entity for the life cycle of the request. All of the subsequent data action inputs with the same cachekey (within the same request) will be served from the request cache.

- **application**: Action input caches the entity for the life cycle of the application (subject to time to refresh (TTR) and time to live (TTL) values as defined in cache settings. All of the subsequent data action inputs with the same cachekey will be served from the application cache.

- **instance**: Instance is a special cache type setting primarily used for aggregator data actions that do not make a request and extract information from other data actions, for example a categories hierarchy. Such data actions are run on server and client independently. If the instance is not specified, then such aggregator data actions would contain duplicate data.

- **none**: Used to skip or bypass the request cache. An action with cache type "none" skips the caching layer completely.

## Cache settings

Cache settings can be configured using the \src\settings\cache-settings.json file. The following example shows the format of a cache-settings.json file.

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

For more information, see [Data action cache settings](data-action-cache-settings.md).

#### checkPeriodInSeconds

This setting represents the time interval in seconds, at which the SDK will do a pass on the application cache to nudge TTL expired items from the cache. The default value is 600 seconds.

#### ttlInSeconds - TTL (Time to Live)

This setting indicates the duration an entity can stay in the application cache. This value is configurable at the application level and also per entity. The default value is 600 seconds.

#### ttrInSeconds - TTR (Time to Refresh)

TTR tells the action runtime to keep the data fresh, in the sense that the cache value is retained in the application cache but a fresh call is made to update the cache data. In the event of an unexpected error, you can still choose to return the data in the cache. The default value is 60 seconds.

#### defaultTTLInSeconds

This setting indicates the default time to live (in seconds) for all the cache items. The default value is 600 seconds.

#### defaultTTRInSeconds

This setting indicates the default time to refresh (in seconds) for all the cache items. The default value is 60 seconds.

## Additional resources

[Data actions overview](data-actions.md)

[Test data actions with mocks](test-data-action-mocks.md)

[Page load data actions](page-load-data-action.md)

[Event-based data actions](event-based-data-actions.md)

[Core data actions](core-data-actions.md)

[Call Retail Server APIs](call-retail-server-apis.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
