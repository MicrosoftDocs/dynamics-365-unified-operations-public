---
# required metadata

title: Service protection API limits
description: This topic provides information about service protection API limits for the Finance and Operations service.
author: jaredha
ms.date: 04/21/2022
ms.topic: article
audience: Developer
ms.reviewer: sericks
ms.search.region: Global
ms.author: jaredha
ms.search.validFrom: 2022-04-21

---

# Service protection API limits

[!include [banner](../includes/banner.md)]

> [!IMPORTANT]
> Resource-based service protection API limits are enabled in Finance and Operations apps environments, beginning in version 10.0.19. The user-based service protection API limits outlined in this topic will be enabled in environments beginning in version 10.0.30 with 2022 release wave 2.

To ensure consistent availability and performance of the Finance and Operations service we apply limits to how the service APIs are used. These limits are designed to protect the service when client applications make extraordinary demands on server resources. Sudden bursts of high incoming API traffic or concurrent long-running requests against the server can exhaust server resources, causing outages or other impacts on the availability and performance of the service.

The limits should not affect normal users of interactive clients. The limits are designed to impact only client applications that perform extraordinary API requests. The limits provide a level of protection from random and unexpected surges in request volume that threaten the availability and performance of the Finance and Operations platform.

> [!NOTE]
> Service protection API limits are available only for the Finance and Operations online service, including production and sandbox environments. The protection limits are not available for on-premises or development environments.

## Impact on client applications
It is the responsibility of client applications to manage service protection API limit errors. How the error should be managed depends on the nature of the application.

### Interactive client applications
The service protection limits are high enough that it should be rare for an individual using an interactive client application to encounter them during normal usage. However, it is possible if the client application allows for bulk operations. Client application developers should be aware of how service protection API limits are enforced and design the UI to reduce the potential for users to send extremely demanding requests to the server. But they should still expect that service protection API limit errors can occur and be prepared to handle them.

Client application developers should not simply throw the error to display the message to the user. The error message is not intended for end users. See [Retry operations](service-protection-retry-operations.md) for specific strategies on managing a throttling response when API requests exceed the service protection limits.

### Data integration applications
Applications designed to load data into Finance and Operations apps or perform bulk data operations must also be able to manage service protection API limit errors. These applications must prioritize throughput so they can complete their work in the minimum amount of time. They must have a strategy to retry operations and achieve maximum throughput.

For more information, see [Maximizing API throughput](service-protection-maximizing-api-throughput.md).

### Anonymous users
Some applications will send requests from anonymous users through a service principal account. For the service protection API limits that are based on a per-user basis, these applications can hit service protection API limits based on the volume of traffic the application experiences across all client users. Like interactive client applications, it isn't expected that the service protection API limit errors should be displayed to the application end user. It is expected that the UI should disable further requests and display a message that the server is busy. The message may include the time when the application can begin accepting new requests.

## Enforcement of the service protection API limits
There are two types of service protection API limits for Finance and Operations apps: user-based and resource-based. User-based limits provide protection against individual users or integrations harming system performance and availability. Resource-based limits provide protection for the environment by enforcing thresholds of high environment resource utilization, limiting service requests when high thresholds are reached. 

> [!IMPORTANT]
> Service protection API limits are subject to change and may vary between environments. These numbers represent default values and are provided to give you an idea of what values you can expect in your environment. These limits are not configurable and are not specific to legal entities.

### User-based service protection API limits
Two of the user-based service protection API limits are evaluated within a 5 minute (300 seconds) sliding window. If either limit is exceeded within the preceding 300 seconds, a service protection API limit error will be returned on subsequent requests to protect the service until the [Retry-After interval](service-protection-retry-operations.md#retry-after-intervals) has ended.

The service protection API limits are evaluated per user. Each authenticated user is limited independently. Only the user accounts which are making extraordinary demands will be limited. Other users will not be impacted.

User-based service protection API limits are enforced based on three factors:
- The number of requests sent by a user
- The combined execution time required to process requests sent by a user
- The number of concurrent requests sent by a user

Each web server available to your environment will enforce the service protection API limits independently. Most environments will have more than one web server. Trial environments are allocated only a single web server. The actual number of web servers that are available to your environment depends on multiple factors that are part of the Finance and Operations managed service. One of the factors is how many user licenses you have purchased. See [Monitoring for API throttling](service-protection-monitoring.md) for information on utilization of web resources available in your environment.

The following table describes the default user-based service protection API limits enforced *per user per web server*.

| Measure | Description | Service protection limit |
| --- | --- | --- |
| Number of requests | The cumulative number of requests made by the user | 6000 within the 5-minute sliding window |
| Execution time | The combined execution time of all requests made by the user | 20 minutes (1200 seconds) within the 5-minute sliding window |
| Number of concurrent requests | The number of concurrent requests made by the user | 52 |

### Resource-based service protection API limits
While user-based service protection API limits are specified per user per web server, resource-based service protection API limits are enforced based on environment resource utilization thresholds. The resource limits will throttle service requests when the aggregate consumption of web server resources reaches levels that threaten service performance and availability. Resource-based service protection API limits work together with user-based limits as protective settings that prevent the over-utilization of resources. This helps to preserve the system's responsiveness and ensures consistent availability and performance for environments running Finance and Operations apps.

For resource-based service protection API limits, you can define the prioritized order in which integrations are throttled when resource thresholds are reached. See [Throttling prioritization](priority-based-throttling.md) for more information.

## Service protection API response
When client applications make extraordinarily demanding requests, the Finance and Operations service returns an error indicating that too many requests have been made. We follow a common pattern for online services by returning a [429 Too Many Requests response](https://developer.mozilla.org/docs/Web/HTTP/Status/429).

With the 429 Too Many Requests response, there is a specific error message returned for each of the service protection API limits. This section describes the error messages and possible mitigation strategies for each.

### Number of requests
This limit counts the total number of requests during the preceding 300-second period. The following error message is returned with the API response:

```Number of requests exceeded the limit of 6000 over the time window of 300 seconds.```

It is not expected that a typical user of an interactive application will be able to send 1200 requests per minute to exceed this limit unless the application enables users to perform bulk operations. For example, if a list view enables the selection of 250 records at a time and allows a user to perform an operation on all records with a single action, the user would need to perform this operation 24 times in a span of 300 seconds to reach the service protection API limit.

If your application provides this capability, you should consider some of the following strategies:

- Decrease the total number of records that can be selected in a list. If the number of items displayed in a list is reduced to 50, the user would need to perform this operation 120 times within 300 seconds. The user would have to complete the operation on each list within 2.5 seconds. 
- Combine the selected operations into a batch. A batch can contain up to 5000 operations and will avoid the number of requests limit. However, you will need to be prepared for the execution time limit.

### Execution time
This limit tracks the combined execution time of incoming requests during the preceding 300-second period. The following error message is returned with the API response:

```Combined execution time of incoming requests exceeded the limit of 1200 seconds over the time window of 300 seconds. Decrease the number of concurrent requests or reduce the duration of requests and try again later.```

Some operations require more resources than others. Batch operations and highly complex queries can be very demanding. These operations may also be performed simultaneously in concurrent requests. Therefore, within the 5-minute window it is possible to request operations that will require more than 20 minutes of combined computation time.

This limit can be encountered when strategies using batch operations and concurrent requests are used to avoid the limit on the number of requests. If this error is encountered with batch operations, a potential mitigation strategy is to divide the operations into smaller batches and execute the individual batches concurrently with different service principals.

### Concurrent requests
This limit tracks the number of concurrent requests for the user. The following error message is returned with the API response:

```Number of concurrent requests exceeded the limit of 52.```

Client applications are not limited to sending requests individually in succession. The client may apply parallel programming patterns or various methods to send multiple requests simultaneously. If this number of concurrent requests is exceeded, the error is returned with the API response.

Sending concurrent requests can be a key part of a strategy to maximize throughput, but don't overuse this strategy. When using [Parallel Programming in .NET](/dotnet/standard/parallel-programming) the default degree of parallelism depends on the number of CPU cores on the server running the code. It should not exceed 52. The [ParallelOptions.MaxDegreeOfParallelism](/dotnet/api/system.threading.tasks.paralleloptions.maxdegreeofparallelism) property can be set to define a maximum number of concurrent tasks.

### Resource utilization threshold
This limit tracks the cumulative utilization thresholds of server resources. The following error message is returned with the API response:

```This request could not be processed at this time due to system experiencing high resource utilization.```

When this error is received it isn't necessarily an indication of any one user or integration causing the issue. This message indicates that the cumulative utilization of web server resources across all service integrations has exceeded a threshold that threatens the performance and availability of the service. When this occurs, general strategies for optimizing API integrations, like those outlined in [Maximizing API throughput](service-protection-maximizing-api-throughput.md) are useful. Also ensure you have defined the [throttling prioritization](priority-based-throttling.md) for your API integrations.

## Exceptions to service protection limits
The service protection API limits do not apply to some Microsoft services. The following services are currently exempt from the limits:
- [Document Routing Agent (DRA)](../analytics/install-document-routing-agent.md)
- [Warehouse Management mobile app (WHSMobile)](../../../supply-chain/warehousing/configure-app-field-names-priorities-warehouse.md)
- [Retail Server API](../../../commerce/dev-itpro/consume-retail-server-api.md)
- [Office Integration](../office-integration/office-integration.md)
- [Data Import/Export Framework (DIXF)](data-import-export-job.md)
- [Data Integrator](/power-platform/admin/data-integrator)
- [Dual-write](dual-write/dual-write-overview.md)
- [Power Platform virtual tables for Finance and Operations apps](../power-platform/virtual-entities-overview.md)
- [Finance and Operations apps Connector](fin-ops-connector.md)

Though these services are currently exempt from the limits, the services are prioritizing the implementation of the service protection limits. Notifications will be provided ahead of any changes, and the documentation will be updated when exemptions are removed for these services.

> [!NOTE]
> These services will implement handlers with Retry-After logic when service protection limits are applied to the services. However, it is still recommended that you have client-side handling for throttling when using the services. Consider implementing the 429 handler with Retry-After logic.

