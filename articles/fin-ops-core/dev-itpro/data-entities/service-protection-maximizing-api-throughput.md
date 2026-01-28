---
title: Maximize API throughput
description: Learn about strategies that can help you manage throttling responses for service protection application programming interface (API) limits and maximize API throughput.
author: jaredha
ms.author: johnmichalak
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 01/20/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2022-04-16
ms.dyn365.ops.version: Platform update 52
---

# Maximize API throughput

[!include [banner](../includes/banner.md)]

This article describes strategies that can help you manage throttling responses for service protection application programming interface (API) limits and maximize API throughput.

If you have an application that must prioritize throughput to move the most data in the shortest period, apply these strategies.

## Let the server tell you when to retry the request

Don't try to calculate the number of requests that you should send at a time. Each environment can differ. Gradually increase the rate that you send requests at until you begin to hit limits. Then depend on the **Retry-After** interval value of the service protection API limit to tell you when to send more. That value helps keep your total throughput at the highest possible level. 

For more information, see [Retry operations](service-protection-retry-operations.md).

## Use multiple threads

If your individual operations are relatively quick, your application can use the higher limit on the number of concurrent threads to significantly improve performance. Depending on the nature of the data that you're processing, you might have to adjust the number of threads to achieve optimum throughput.

## Distribute workloads across multiple service principals

User-based service protection API limits are implemented on a per-user basis. If your integration uses a single service principal to perform large bulk data operations, or if it's an interactive client application that uses a single service principal to send all user requests to the server, you can reach the service protection API limits fairly quickly. You can help prevent this situation by distributing the workload in smaller batches across multiple service principals.

## Avoid large batches

*Batching* refers to the process of sending multiple operations in a single request. Most scenarios are fastest if you send single requests and use a high degree of parallelism. If you think that batch size might help improve performance, start with a small batch size and then increase concurrency until you start to receive service protection API limit errors that indicate that the operation must be retried. In finance and operations apps, batch size is limited to 5,000 operations.

For more information about batch requests that have finance and operations apps service endpoints, see [Batch requests](../data-entities/odata.md#batch-requests).

## Remove the affinity cookie

When you connect to a service in Azure, the response includes a cookie. All your subsequent requests try to go to the same server, unless capacity management sends them to another server. If you remove the cookie, you can route each request to any eligible server. Throughput increases because limits apply per server. This strategy lets you use more servers if they're available.

> [!NOTE]
> Use this strategy only for applications that need to optimize throughput. Interactive client applications benefit from the affinity cookie because it allows reuse of cached data that you'd otherwise need to re-create. Performance suffers if the data must be re-created.

The following code shows how to disable cookies when you initialize an **HttpClient** with web services. It assumes that you're using a custom **HttpMessageHandler** to manage authentication.

```C#
HttpMessageHandler messageHandler = new OAuthMessageHandler(
    config,
    new HttpClientHandler() { UseCookies = false }
    );
HttpClient httpClient = new HttpClient(messageHandler)
```

## Optimize your connection

You can expect greater throughput if you optimize your connection. The supporting .NET sample code uses the following settings.

```C#
//Change max connections from .NET to a remote service default: 2
System.Net.ServicePointManager.DefaultConnectionLimit = 65000;
//Bump up the min threads reserved for this app to ramp connections faster - minWorkerThreads defaults to 4, minIOCP defaults to 4 
System.Threading.ThreadPool.SetMinThreads(100, 100);
//Turn off the Expect 100 to continue message - 'true' will cause the caller to wait until it round-trip confirms a connection to the server 
System.Net.ServicePointManager.Expect100Continue = false;
//Can decrease overall transmission overhead but can cause delay in data packet arrival
System.Net.ServicePointManager.UseNagleAlgorithm = false;
```

For more information, see [Managing connections](/dotnet/framework/network-programming/managing-connections).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

