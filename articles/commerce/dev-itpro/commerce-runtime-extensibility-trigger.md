---
title: Commerce runtime (CRT) extensibility and triggers
description: This article explains trigger support for the Microsoft Dynamics 365 commerce runtime (CRT). CRT supports pre-triggers and post-triggers for every request.
author: josaw1
ms.date: 08/20/2020
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update
ms.assetid: 2d6ec331-b266-4dbc-97c5-db2919b662dc
ms.search.industry: Retail
---

# Commerce runtime (CRT) extensibility and triggers

[!include [banner](../includes/banner.md)]

This article explains trigger support for the Dynamics 365 commerce runtime (CRT). CRT supports pre-triggers and post-triggers for every request.

## CRT trigger overview

Commerce runtime (CRT) triggers give you a way to extend the CRT workflow, and let you add business logic before and after every CRT request is executed. The following two methods are used:

-   **OnExecuting** – This method is invoked before a request has been processed by a corresponding **IRequestHandler** implementation.
-   **OnExecuted** – This method is invoked after the request has been processed by a corresponding **IRequestHandler** implementation.

## CRT trigger extension
To implement a trigger, you must complete these tasks, as shown in the code example that follows:

1.  Implement **IRequestTriggerAsync**.
2.  Specify **SupportedRequestTypes** to define the request types that the trigger must be executed for.
3.  Write a trigger implementation in the **OnExecuting** method if business logic must be run before the request is addressed.
4.  Write a trigger implementation in the **OnExecuted** method if business logic must be run after the request is addressed.

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

Copy and paste the extension library to **...\RetailServer\webroot\bin\ext folder** and update the **commerceRuntime.ext.config** file with the custom extension library information under composition section. In this example, **Contoso.Commerce.Runtime.Services** is the  custom extension name.

```xml
<add source="assembly" value="Contoso.Commerce.Runtime.Services" /> 
```

For the CRT extension to work in offline mode, update **...\Microsoft Dynamics 365\70\Retail Modern POS\ClientBroker\ext\CommerceRuntime.MPOSOffline.ext.config** with the extension library information under the composition section. Then copy and paste the extension library to **...\Microsoft Dynamics 365\70\Retail Modern POS\ClientBroker\ext**.

### Debugging CRT

To debug CRT from POS, attach the CRT extension project to the w3wp.exe (IIS process for Retail server) when POS is connected to Retail server. For offline mode, attach the CRT extension project to the dllhost.exe process.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
