---
# required metadata

title: Create a request pipeline plug-in hook
description: This topic explains how to create and configure a request pipeline plug-in hook in Microsoft Dynamics 365 Commerce. The request pipeline plug-in hook can intercept rendering requests that are sent to the Node server, and redirect them or send responses to them.
author: samjarawan
ms.date: 08/12/2021
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
ms.dyn365.ops.version: Release 10.0.5

---

# Create a request pipeline plug-in hook

[!include [banner](../includes/banner.md)]

This topic explains how to create and configure a request pipeline plug-in hook in Microsoft Dynamics 365 Commerce. The request pipeline plug-in hook can intercept rendering requests that are sent to the Node server, and redirect them or send responses to them. For example, you might want to block requests that come from a specific IP address range, redirect requests based on their geolocation, or redirect requests from a retired category.

## Create the request pipeline plug-in hook file

The online software development kit (SDK) provides a **create-request-hook** [command line interface (CLI)](cli-command-reference.md) command. This command creates a request pipeline plug-in hook file that is named **src/requestHooks/initialRequest.hook.ts**. Only one request pipeline plug-in hook file can be created and used.

The plug-in has API access to request context information, and can redirect requests or send customized responses. Data actions can be used in the plug-in to fetch data as required. Those data actions use [data action caching](data-action-cache-settings.md) for better performance. Request pipeline hooks are run before the server render process.

The following example shows the CLI command to create a request pipeline plug-in hook file.

```bash
yarn msdyn365 create-request-hook
```

The following example shows the contents of the default request pipeline plug-in hook file that is created by the **create-request-hook** CLI command.

```ts
/*!
 * Copyright (c) Microsoft Corporation.
 * All rights reserved. See LICENSE in the project root for license information.
 */

import * as Msdyn365 from '@msdyn365-commerce/core';

const requestReaderPlugin = async (
    ctx: Msdyn365.IRequestContext
): Promise<Msdyn365.requestHookRegistrar.IRequestReaderOutput | undefined> => {
    return undefined;
};

Msdyn365.requestHookRegistrar.createInitialHook({
    requestReaderPlugin: requestReaderPlugin
});
```

The **requestReaderPlugin** function can then be modified so that it intercepts requests. The only valid output from the **requestReaderPlugin** function is **Msdyn365.requestHookRegistrar.IRequestReaderOutput**.

## Configure the redirect and send data actions

The interface for the request pipeline plug-in hook supports two data actions, **redirect** and **send**, as shown in the following example.

```ts
const send:Msdyn365.requestHookRegistrar.IRequestReaderOutput = {
    action: Msdyn365.requestHookRegistrar.RequestReaderAction.send,
    parameters: ['<p>TEST</p>'];
};
const redirect:Msdyn365.requestHookRegistrar.IRequestReaderOutput = {
    action: Msdyn365.requestHookRegistrar.RequestReaderAction.redirect,
    parameters: ['https://www.sample_redirect_URL.com'];
};
```

The **redirect** and **send** data actions can be manually added to the plug-in file, as shown in the following example.

```ts
/*!
 * Copyright (c) Microsoft Corporation.
 * All rights reserved. See LICENSE in the project root for license information.
 */

import * as Msdyn365 from '@msdyn365-commerce/core';

const requestReaderPlugin = async (
    ctx: Msdyn365.IRequestContext
): Promise<Msdyn365.requestHookRegistrar.IRequestReaderOutput | undefined> => {

    const send : Msdyn365.requestHookRegistrar.IRequestReaderOutput = {
        action: Msdyn365.requestHookRegistrar.RequestReaderAction.send,
        parameters: ['<p>TEST</P>']
    }
    
    const redirect : Msdyn365.requestHookRegistrar.IRequestReaderOutput = {
        action: Msdyn365.requestHookRegistrar.RequestReaderAction.redirect,
        parameters: ['/category']
    }

    if (ctx.canonicalUrl == 'https://sampleUrl'){
        return redirect
    } else {
        return send
    }
};

Msdyn365.requestHookRegistrar.creatInitialHook({
    requestReaderPlugin: requestReaderPlugin
});
```

If nothing is returned from the plug-in, the rendering engine will continue the rendering step. Otherwise, it will redirect the request or send a new response.

## Configure the time-out value

The request pipeline plug-in hook has a default execution time-out value of 500 milliseconds. The time-out value can be configured in the **RequestReaderPluginTimeoutInMs** property of the [platform settings file](platform-settings.md), as shown in the following example from a **platform.settings.json** file.

```json
{
    "dataActionTimeoutInMs": 4000,
    "minClientChunkSize": 5000,
    "excludeModules": [ ],
    "namespaceExtensions" : [ ],
    "secretsManagerOUN" : 128,
    "clientSideDataActionTimeoutInMs": 4000,
    "RequestReaderPluginTimeoutInMs": 500
}
```

Any error that is generated from the plug-in or time-out will have a 500 status code. To suppress this type of error, make sure that a try/catch statement is used in the plug-in.

## Additional resources

[CLI command reference](cli-command-reference.md)

[Data action caching settings](data-action-cache-settings.md)

[Platform settings file](platform-settings.md)
