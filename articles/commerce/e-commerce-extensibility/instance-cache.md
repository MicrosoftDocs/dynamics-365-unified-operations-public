---
# required metadata

title: Instance cache
description: This topic describes...
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

This topic describes how to use data action instance cache to reduce the size of the data action payload sent to the client browser to increase site performance.  

This is useful when a module's data action calls child data action(s).  In this scenario the module only requires the parent data action result which combines the child results when rendering the module, however the child data action result will also be returned to the client.  Setting the data action **dataCacheType** to **instance** to prevent the data action output being sent to the client.  

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
As of the release of module library 10.0.19, all retail proxy data actions have been set to **instance** to reduce the client data payload.
Custom modules should avoid using OOB retail proxy data actions, instead they should use @msdyn365-commerce-modules/retail-actions
or create data action wrapper to call retail proxy data actions to prevent render issue.

If using a module libray version < 10.0.19, instance caching can be enabled in the [platform settings](platform-settings.md) file with the **shouldUseInstanceCache** property. 
{
    "dataActionTimeoutInMs": 4000,
    "minClientChunkSize": 5000,
    "excludeModules": [ ],
    "namespaceExtensions" : [ ],
    "secretsManagerOUN" : 128,
    "clientSideDataActionTimeoutInMs": 4000,
    "RequestReaderPluginTimeoutInMs": 500,
    "shouldUseInstanceCache": true
}




