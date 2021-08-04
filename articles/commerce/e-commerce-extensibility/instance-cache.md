---
# required metadata

title: Data action instance cache
description: This topic describes how to use the data action instance cache in Microsoft Dynamics 365 Commerce to reduce the size of the data action payload sent to the client browser to increase site performance. 
author: samjarawan
ms.date: 08/04/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.13

---

# Data action instance cache

[!include [banner](../includes/banner.md)]

This topic describes how to use the data action instance cache in Microsoft Dynamics 365 Commerce to increase site performance by reducing the size of data action payloads sent to client browsers. 

If a data action result is not needed when rendering a module, setting the data action **dataCacheType** to **instance** will prevent the data action output from being sent to the client. This is useful when a module's parent data action calls a child data action, since modules only require the parent data action result that already includes the child data action results. In this scenario the child data action's **dataCacheType** would be set to **instance**.

The following example shows how to set the **dataCacheType** within the data action typescript code.

```ts
import * as Msdyn365 from '@msdyn365-commerce/core';

/**
 * SampleDataAction Input Action
 */
export class SampleDataActionInput implements Msdyn365.IActionInput {
    // TODO: Construct the input needed to run the action
    constructor() {}

    // TODO: Determine if the results of this get action should cache the results and if so provide
    // a cache object type and an appropriate cache key
    public getCacheKey = () => `TODO`;
    public getCacheObjectType = () => 'TODO';
    public dataCacheType = (): Msdyn365.CacheType => 'instance';
}
...
```

## Instance cache settings for Retail Server proxy data actions

As of the Commerce version 10.0.19 release of the module library, all [Retail Server proxy data actions](call-retail-server-apis.md#retail-server-proxy-data-action-managers) typically called from [core data actions](core-data-actions.md) have had the **dataCacheType** set to **instance** by default to reduce the client data payload.

Custom modules should avoid using Retail Server proxy data actions directly since they are now set to use the instance cache and results will not be sent to clients. Custom modules should instead either use [core data actions](core-data-actions.md) or custom data actions that employ Retail Server proxy data actions.

If using a Commerce module library version prior to version 10.0.19, instance caching can be enabled in the [platform settings file](platform-settings.md) by setting the **shouldUseInstanceCache** property to **true**. 

<!--```JSON-->
<!--   "shouldUseInstanceCache": true -->
<!--```-->

## Additional resources

[Retail Server proxy data action managers](call-retail-server-apis.md#retail-server-proxy-data-action-managers)

[Core data actions](core-data-actions.md)

[Platform settings file](platform-settings.md)
