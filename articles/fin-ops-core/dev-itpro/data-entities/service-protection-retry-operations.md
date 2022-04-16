---
# required metadata

title: Retry operations
description: This topic provides information retry operations when API requests are throttled due to reaching service protection API limits.
author: jaredha
ms.date: 04/06/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jaredha
ms.search.validFrom: 2022-04-16
ms.dyn365.ops.version: Platform update 52

---

# Service protection API limits

[!include [banner](../includes/banner.md)]

## Retry-After intervals



## Implementing retry operations
The following example shows how to retry a request after the number of seconds specified for the Retry-After interval.

```C#
    if (!response.IsSuccessStatusCode) 
            { 
                if ((int)response.StatusCode == 429) 
                { 
                    int seconds = 30; 
                    //Try to use the Retry-After header value if it is returned. 
                    if (response.Headers.Contains("Retry-After")) 
                    { 
                        seconds = int.Parse(response.Headers.GetValues("Retry-After").FirstOrDefault()); 
                    } 
                    Thread.Sleep(TimeSpan.FromSeconds(seconds)); 

                    // Retry sending the request.
                } 
            } 
```
