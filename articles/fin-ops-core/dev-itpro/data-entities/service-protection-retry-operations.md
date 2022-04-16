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

# Retry operations

[!include [banner](../includes/banner.md)]

When a service protection API limit error occurs, it will provide a value indicating the duration before any new requests from the user can be processed. When a 429 error is returned from the Web API, the response will include a [Retry-After](https://developer.mozilla.org/docs/Web/HTTP/Headers/Retry-After) interval with the number of seconds to wait before resubmitting the request.

When requests are resubmitted after the Retry-After interval, they are processed with other incoming requests, and are prioritized as if they were new requests to teh server. Retry requests do not receive higher prioritization over new requests.

## Retry for interactive applications
If the client is an interactive application, you should display a message that the server is busy while you retry the request. You may want to provide an option for the user to cancel the operation. Don't allow the user to submit more requests until the previous request you sent has been completed.

## Retry for non-interactive applications
If the client is not interactive, the common practice is to simply wait for the duration of the provided interval before sending the request again. This is commonly done by pausing the execution of the current task using [Task.Delay](https://docs.microsoft.com/dotnet/api/system.threading.tasks.task.delay) or equivalent methods.

## Retry-After intervals
The Retry-After duration will depend on the nature of the operations that have been sent in the preceding 5-minute period. The more demanding the requests are, the longer it will take for the server to recover.

If a client application continues to send demanding requests after receiving initial 429 responses, the Retry-After interval will be extended to minimize the impact on shared resources. This will cause the individual Retry-After interval period to be longer, which means your application will see longer periods of inactivity while it is waiting.

When possible, it is recommended to work towards a consistent rate by starting with a lower number of requests and gradually increasing until you start hitting the service protection API limits. After that, let the server tell you how many requests it can handle withing a 5-minute period. Keeping your maximum number of requests limited within this 5-minute period and gradually increasing will keep the Retry-After interval low, optimizing your total throughput and minimizing server resource spikes.


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

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
