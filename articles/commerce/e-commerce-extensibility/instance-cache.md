---
# required metadata

title: Data action instance cache
description: his topic describes how to use data action instance cache to reduce the size of the data action payload sent to the client browser to increase site performance. 
author: samjarawan
ms.date: 07/30/2021
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

This topic describes how to use data action instance cache to reduce the size of the data action payload sent to the client browser to increase site performance.  If a data action result is not needed when rendering a module, setting the data action **dataCacheType** to **instance** will prevent the data action output being sent to the client.  

This is useful when a module's data action calls child data action(s), since the module only requires the parent data action result (which combines the child data action results).  In this scenario the child data action's **dataCacheType** should be set to **instance** to ensure the result is not sent back to the client.

The below example shows how to set the **dataCacheType** within the data action typescript code.

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

## Instance cache settings for the retail proxy data actions
As of the release of module library 10.0.19, all [retail proxy data actions](call-retail-server-apis.md#retail-server-proxy-data-action-managers) have been set to **instance** to reduce the client data payload, which are typically called from the [core data actions](core-data-actions.md).

Custom modules should avoid using [retail proxy data actions](call-retail-server-apis.md#retail-server-proxy-data-action-managers) directly since they are now set to use instance cache and results will not be sent to client.  Instead they should leverage either [core data actions](core-data-actions.md) or create a custom data action that will internally leverage the retail proxy data actions.

If using a module libray version prior to version 10.0.19, instance caching can be opted in the [platform settings](platform-settings.md) file with the **shouldUseInstanceCache** property set to **true**. 
{
    ...
    "shouldUseInstanceCache": true
}
