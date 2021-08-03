---
# required metadata

title: Request pipeline plug-in hook file
description: This topic describes request pipeline hook files in Microsoft Dynamics 365 Commerce that can interrupt rendering requests sent to the Node server and redirect or send responses to rendering requests. 
author: samjarawan
ms.date: 08/03/2021
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

# Request pipeline plug-in hook file

[!include [banner](../includes/banner.md)]

This topic describes request pipeline hook files in Microsoft Dynamics 365 Commerce that can interrupt rendering requests sent to the Node server and redirect or send responses to rendering requests. For example, you may want to block requests coming from a specific IP address range, redirect requests based on the geolocation of a request, or redirect requests from a retired category. 

## Request reader plug-in

A request reader plug-in can be created with a [CLI](cli-command-reference) tool provided by the online software development kit (SDK). The plug-in has API access to request context information and can redirect requests or send customized responses. Data actions can be used within the plug-in to fetch data if needed, and use [data action caching](data-action-cache-settings.md) for better performance. The request hook will be executed before the server render process and is created with a request reader plug-in.

## Create a request reader plug-in using the SDK CLI command

The SDK provides a [CLI command](cli-command-reference) **create-request-hook** that will create the request hook file **src/requestHooks/initialRequest.hook.ts** file. Only one request hook file can be created and used.  

The following example shows how to use the CLI command to create a request hook file.

```bash
yarn msdyn365 create-request-hook
```

The code below shows the default request hook file result from running the above CLI command:
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

The **requestReaderPlugin** function can then be modified to intercept the request. The only valid output from the **requestReaderPlugin** function is "Msdyn365.requestHookRegistrar.IRequestReaderOutput."

## Configure redirect and send actions

The request reader interface supports two actions **redirect** and **send**, the below shows sample code for a request reader plug-in.

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
The above actions can be manually added to the plug-in file as shown in the below example:

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

If there is nothing returned from the plug-in, the rendering engine will continue the rendering step, otherwise it will redirect or send the new response.

## Configure request reader plug-in timeout

The request reader plug-in has an execution timeout default value of 500ms, and can be configured in [platform settings file](platform-settings.md) with the **RequestReaderPluginTimeoutInMs** property as shown in the below platform.settings.json example:

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
 
Any error thrown from the plug-in or timeout will result in a 500 status code along with the error message. To suppress the error in a plug-in, ensure a try/catch statement is used within the plug-in. 

## Additional resources




