---
title: Commerce runtime (CRT) extensibility and triggers
description: Learn about trigger support for the Microsoft Dynamics 365 commerce runtime (CRT).
author: josaw1
ms.date: 02/13/2026
ms.topic: how-to
ms.author: josaw
ms.reviewer: v-griffinc
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.assetid: 2d6ec331-b266-4dbc-97c5-db2919b662dc
ms.custom: 
  - bap-template
---

# Commerce runtime (CRT) extensibility and triggers

[!include [banner](../includes/banner.md)]

This article explains trigger support for the Dynamics 365 commerce runtime (CRT). CRT supports pre-triggers and post-triggers for every request.

## CRT trigger overview

Commerce runtime (CRT) triggers give you a way to extend the CRT workflow. You can add business logic before and after every CRT request. Use the following two methods:

-   **OnExecuting** – Invokes this method before a request is processed by a corresponding **IRequestHandler** implementation.
-   **OnExecuted** – Invokes this method after a request is processed by a corresponding **IRequestHandler** implementation.

> [!NOTE]
> If you extend a CRT request that's used by a high-volume API (for example, Carts/AddCartLines or Products/GetByIds), and your extension needs to read from the channel database, enable the cache for the database reading. Otherwise, the extension consumes too many Retail Server and channel database resources, which can cause overall Commerce Scale Unit (CSU) performance issues that affect your business.

## CRT trigger extension
To implement a trigger, complete these tasks, as shown in the following code example:

1. Implement **IRequestTriggerAsync**.
1. Specify **SupportedRequestTypes** to define the request types that the trigger must execute for.
1. Write a trigger implementation in the **OnExecuting** method if business logic must run before the request.
1. Write a trigger implementation in the **OnExecuted** method if business logic must run after the request.

### Sample trigger implementation for Get customer data request:

```C#

        using Microsoft.Dynamics.Commerce.Runtime;
        using Microsoft.Dynamics.Commerce.Runtime.DataServices.Messages;
        using Microsoft.Dynamics.Commerce.Runtime.Messages;
        using System;
        using System.Collections.Generic;
        using System.Threading.Tasks;

        public class GetCustomerTriggers : IRequestTriggerAsync
        {
            /// <summary>
            /// Gets the supported requests for this trigger.
            /// </summary>
            public IEnumerable<Type> SupportedRequestTypes
            {
                get
                {
                    return new[] { typeof(GetCustomerDataRequest) };
                }
            }

            /// <summary>
            /// Post trigger code.
            /// </summary>
            /// <param name="request">The request.</param>
            /// <param name="response">The response.</param>
            public async Task OnExecuted(Request request, Response response)
            {
                //Custom logic

            // The only stub to handle async signature
                await Task.CompletedTask;
            }

            /// <summary>
            /// Pre trigger code
            /// </summary>
            /// <param name="request">The request.</param>
            public async Task OnExecuting(Request request)
            {
                // custom logic
                await Task.CompletedTask;
            }
        }
  ```

### Register the extension

Copy and paste the extension library to the **...\RetailServer\webroot\bin\ext folder**. Update the **commerceRuntime.ext.config** file with the custom extension library information under the composition section. In this example, **Contoso.Commerce.Runtime.Services** is the custom extension name.

```xml
<add source="assembly" value="Contoso.Commerce.Runtime.Services" />
```

For the CRT extension to work in offline mode, update **...\Microsoft Dynamics 365\70\Retail Modern POS\ClientBroker\ext\CommerceRuntime.MPOSOffline.ext.config** with the extension library information under the composition section. Then, copy and paste the extension library to **...\Microsoft Dynamics 365\70\Retail Modern POS\ClientBroker\ext**.

### Debugging CRT

To debug CRT from POS, attach the CRT extension project to the w3wp.exe (IIS process for Retail server) when POS is connected to Retail server. For offline mode, attach the CRT extension project to the dllhost.exe process.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
