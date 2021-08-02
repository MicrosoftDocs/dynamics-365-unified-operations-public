---
# required metadata

title: Request pipeline hook
description: This topic describes the request pipeline hook providing the ability to interrupt the rendering request sent to the Node server, allowing the ability to redirect or send a response to the render request. 
author: samjarawan
ms.date: 05/28/2021
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

# Request pipline plugin

[!include [banner](../includes/banner.md)]

This topic describes the optional request pipeline plugin hook which provides the ability to intercept the rendering request sent to the Node server.  This will allow the ability to redirect or send a response to the render request.  For example you may want to block requests coming from a specific IP range, redirect based on a geo location of a request or redirect from a retired category to another. 

## Request reader plugin
A request reader plugin can be created with a [CLI](cli-command-reference) tool provided by the online SDK.  The plugin has API access to the request context information and can redirect the request or send a customized response.  Data action can be used within the plugin to fetch data if needed, which also leverage [data action cache](data-action-cache-settings.md) for better performance. The request hook will be executed before the server render process and is created with a **request reader plugin**.

## Create a request reader plugin using the SDK CLI command
The SDK provides a [CLI command](cli-command-reference) **create-request-hook** that will create the request hook file **src/requestHooks/initialRequest.hook.ts** file.  Only one request hook file can be created and used.  

The below sample shows how to use the CLI command to create a request hook file.
```
yarn msdyn365 create-request-hook
```

The below code shows the default request hook file template:
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

The function in requestReaderPlugin can then be modified to intercept the request.  The only valid output in requestReaderPlugin will be Msdyn365.requestHookRegistrar.IRequestReaderOutput.

## Redirect and send actions
The request reader interface supports two actions **redirect** and **send**, the below shows sample code for a request reader plugin.

```ts
const send:Msdyn365.requestHookRegistrar.IRequestReaderOutput = {
    action: Msdyn365.requestHookRegistrar.RequestReaderAction.send,
    parameters: ['<p>TEST</>];
};
const redirect:Msdyn365.requestHookRegistrar.IRequestReaderOutput = {
    action: Msdyn365.requestHookRegistrar.RequestReaderAction.redirect,
    parameters: ['https://www.sample_redirect_URL.com'];
};
```
The above actions can be manually added to the plugin file as shown in the below example:
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

If there is nothing returned from the plugin, the rendering engine will continue the rendering step, otherwise it will redirect or send the new response.

## Configure request reader plugin timeout
The request reader plugin has an execution timeout default value of 500ms, and can be configured in [platform settings file](platform-settings.md) with the **RequestReaderPluginTimeoutInMs** property as shown in the below platform.settings.json example:

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
 
Any error thrown from the the plugin or timeout will result in a 500 status code along with the error message. To suppress the error in a plugin, ensure a try/catch statement is used within the plugin. 


