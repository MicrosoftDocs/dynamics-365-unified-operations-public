---
# required metadata

title: Known issues with Retail SDK.
description: This topic explains some of the known issues in Retail SDK.
author: mugunthanm 
manager: AnnBe
ms.date: 06/18/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: mumani
ms.search.validFrom: 2020-06-10
ms.dyn365.ops.version: 10.0.9
---

# Known issues with Retail SDK.

[!include [banner](../../includes/banner.md)]

This topic describes the known issues with Retail SDK.


### Runtime error thrown when using ISupportedTypesAware in SDK version (10.0.420.10003~10.0.420.10033)

Error message: 

Exception: System.MissingMethodException: Method not found: 'System.Collections.Generic.IEnumerable`1<System.Type> 
Microsoft.Dynamics.Commerce.Runtime.ISupportedTypesAware.get_SupportedRequestTypes()'


When extending/implementing CRT handlers please don't use ISupportedTypesAware, use  IRequestHandlerAsync. 
Also don't use  explicit implementations. ISupportedTypesAware is not supported and if used in extension it may cause runtime error.

To fix this issue use IRequestHandlerAsync instaed of ISupportedTypesAware.

```C#
Recommended:

     public class MyHandler : IRequestHandlerAsync
        {
            public IEnumerable<Type> SupportedRequestTypes
            {
                get
                {
                    return new[]
                    {
                        typeof(MyRequest)
                    };
                }
            }

            public Task<Response> Execute(Request request)
            {
                // return response.
            }
        }

Not recommended:

 public class MyHandler : IRequestHandlerAsync, ISupportedTypesAware
        {
            public IEnumerable<Type> SupportedRequestTypes
            {
                get
                {
                    return new[]
                    {
                        typeof(MyRequest)
                    };
                }
            }

            Task<Response> IRequestHandlerAsync.Execute(Request request)
            {
                return null;
            }
        }
        
```
