---
# required metadata

title: Maximizing API throughput
description: This topic provides information on strategies for managing throttling responses for service protection API limits and maximizing API throughput.
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

# Maximizing API throughput

[!include [banner](../includes/banner.md)]

When you have an application that must prioritize throughput to move the most data in the shortest period, there are some strategies you can apply.

## Let the server tell you when to retry the request
Don't try to calculate how many requests to send at a time. Each environment can be different. Gradually increase the rate you send requests until you begin to hit limits and then depend on the service protection API limit Retry-After interval value to tell you when to send more. This value will keep your total throughput at the highest possible level. 

See [Retry operations](service-protection-retry-operations) for more information.

## Use multiple threads
The higher limit on the number of concurrent threads is something your application can use to have significant improvement in performance. This is true if your individual operations are relatively quick. Depending on the nature of the data you are processing, you may need to adjust the number of threads ot get optimum throughput.

## Distribute workloads across multiple service principals
User-based service protection API limits are implemented on a per-user basis. If your integration is performing large bulk data operations using a single service principal, or is an interactive client application that uses a single service principal to send all user requests to the server, then it's possible to reach the service protection API limits fairly quickly. This can be avoided by distributing the workload in smaller batches across multiple service principals.

## Avoid large batches
*Batching* refers to sending multiple operations in a single request. Most scenarios will be fastest sending single requests with a high degree of parallelism. If you feel batch size might improve performance, it is best to start with a small batch size and increase concurrency until you start getting service protection API limit errors indicating the need to retry the operation. Batch size in Finance and Operations apps is limited to 5000 operations.

See [Batch requests](./odata#batch-requests) for more information on batch requests with Finance and Operations service endpoints.

## Remove the affinity cookie
When you make a connection to a service on Azure a cookie is returned with the response and all your subsequent requests will attempt to be routed to the same server unless capacity management forces it to go to another server. If you remove this cookie, each request you send will be routed to any of the elegible servers. This increases throughput because limits are applied per server. This simply allows you to use more servers if they are available.

> [!NOTE]
> This strategy should only be used by applications that are seeking to optimize throughput. Interactive client applications benefit from the affinity cookie because it allows for reusing cached data that would otherwise need to be recreated, leading to poorer performance.

The following code shows how to disable cookies when initializing an HttpClient with web services, assuming you are using a custom HttpMessageHandler to manage authentication.

```C#
HttpMessageHandler messageHandler = new OAuthMessageHandler(
    config,
    new HttpClientHandler() { UseCookies = false }
    );
HttpClient httpClient = new HttpClient(messageHandler)
```

## Optimize your connection
You can expect greater throughput by optimizing the connection. Supporting .NET sample code uses these settings:

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

See [Managing Connections](https://docs.microsoft.com/dotnet/framework/network-programming/managing-connections) for more information.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
