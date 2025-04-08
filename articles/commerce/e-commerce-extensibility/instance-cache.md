---
title: Data action instance cache
description: This article describes how to use the data action instance cache in Microsoft Dynamics 365 Commerce to increase site performance by reducing the size of data action payloads that are sent to client browsers.
author: samjarawan
ms.date: 07/26/2024
ms.topic: how-to
audience: Developer
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Data action instance cache

[!include [banner](../includes/banner.md)]

This article describes how to use the data action instance cache in Microsoft Dynamics 365 Commerce to increase site performance by reducing the size of data action payloads that are sent to client browsers.

If a data action result isn't required when a module is rendered, you can set the data action's **dataCacheType** value to **instance** to prevent the data action output from being sent to the client. This approach is useful when a module's parent data action calls a child data action, because modules require only the parent data action result that already includes the child data action results. In this scenario, the child data action's **dataCacheType** value will be set to **instance**.

The following example shows how to set the **dataCacheType** value in the TypeScript code for the data action.

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

As of the Commerce version 10.0.19 release of the module library, the **dataCacheType** value is set to **instance** by default for all [Retail Server proxy data actions](call-retail-server-apis.md#retail-server-proxy-data-action-managers) that are typically called from [core data actions](core-data-actions.md), to reduce the client data payload.

Because Retail Server proxy data actions are now set to use the instance cache, and results won't be sent to clients, custom modules should not use them directly. Instead, custom modules should use either [core data actions](core-data-actions.md) or custom data actions that use Retail Server proxy data actions.

If the version of the Commerce module library that you're using is earlier than 10.0.19, you can enable instance caching in the [platform settings file](platform-settings.md) by setting the **shouldUseInstanceCache** property to **true**.

<!--```JSON-->
<!--   "shouldUseInstanceCache": true -->
<!--```-->

## Additional resources

[Retail Server proxy data action managers](call-retail-server-apis.md#retail-server-proxy-data-action-managers)

[Core data actions](core-data-actions.md)

[Platform settings file](platform-settings.md)
