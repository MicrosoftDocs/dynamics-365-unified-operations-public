---
title: Retry operations
description: Learn about retry operations that can be implemented if application programming interface (API) requests are throttled because they reach service protection API limits.
author: jaredha
ms.author: sumadhey
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 06/19/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2022-04-16
ms.dyn365.ops.version: Platform update 52
---

# Retry operations

[!include [banner](../includes/banner.md)]

This article describes retry operations that can be implemented if application programming interface (API) requests are throttled because they have reached service protection API limits.

If a service protection API limit error occurs, it provides a value that indicates the amount of time until new requests from the user can be processed. If a 429 error is returned from the web API, the response header includes a [Retry-After](https://developer.mozilla.org/docs/Web/HTTP/Headers/Retry-After) interval that indicates the number of seconds that the user must wait before they resubmit the request.

Requests that are resubmitted after the **Retry-After** interval are processed together with other incoming requests and prioritized as if they are new requests to the server. Retry requests don't receive higher priority than new requests.

## Retry for interactive applications

If the client is an interactive application, you should show a message that states that the server is busy while you retry the request. You might want to provide an option that lets the user cancel the operation. Don't allow the user to submit more requests until the previous request that you sent has been completed.

## Retry for non-interactive applications

If the client isn't an interactive application, a typical practice is to wait until the specified interval has passed before the request is sent again. This behavior is typically implemented by using [Task.Delay](/dotnet/api/system.threading.tasks.task.delay) or equivalent methods to pause the execution of the current task.

## Retry-After intervals

The duration of the **Retry-After** interval depends on the nature of the operations that have been sent in the preceding five-minute period. The more demanding the requests are, the longer the server will take to recover.

If a client application continues to send demanding requests after it receives initial 429 responses, the **Retry-After** interval will be extended to help minimize the impact on shared resources. Because this extension will cause the individual **Retry-After** interval to be longer, your application will see longer periods of inactivity while it's waiting.

We recommend that you aim for a consistent rate whenever you can, by starting with a lower number of requests and then gradually increasing that number until you start to hit the service protection API limits. Then let the server tell you how many requests it can handle within a five-minute period. By keeping your maximum number of requests limited during this five-minute period and gradually increasing it, you will help keep the **Retry-After** interval low. In this way, you will help optimize your total throughput and minimize server resource spikes.

## Implement retry operations

The following example shows how to retry a request after the number of seconds that is specified for the **Retry-After** interval.

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
