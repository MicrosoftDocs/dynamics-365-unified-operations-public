---
# required metadata

title: Service protection API limits
description: This topic provides information about limits for service protection application programming interfaces (APIs) for the Finance and Operations apps service.
author: jaredha
ms.date: 05/26/2022
ms.topic: article
audience: Developer
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: jaredha
ms.search.validFrom: 2022-04-21

---

# Service protection API limits

[!include [banner](../includes/banner.md)]

This topic provides information about limits for service protection application programming interfaces (APIs) for the Finance and Operations apps service.

> [!IMPORTANT]
> Resource-based service protection API limits are enabled in Finance and Operations apps environments as of version 10.0.19. The user-based service protection API limits that are described in this topic will be available to enable in environments with version 10.0.28. In version 10.0.29, with Dynamics 365 2022 release wave 2, the API limits will be enabled by default in all environments, but may optionally be disabled. In version 10.0.32, with Dynamics 365 2023 release wave 1, the user-based API limits will be mandatory, and will no longer provide the option to disable the API limits.

To ensure consistent availability and performance of the Finance and Operations apps service, Microsoft applies limits to the way that the service APIs are used. These limits are designed to protect the service when client applications make extraordinary demands on server resources. Sudden bursts of high incoming API traffic or concurrent long-running requests against the server can exhaust server resources, and can cause outages or have other impacts on the availability and performance of the service.

The limits should not affect regular users of interactive clients. They are designed to affect only client applications that perform extraordinary API requests. The limits provide a level of protection from random and unexpected surges in request volume that threaten the availability and performance of the Finance and Operations platform.

> [!NOTE]
> Service protection API limits are available only for the Finance and Operations apps online service, including production and sandbox environments. They aren't available for on-premises or development environments.

## Impact on client applications

Client applications are responsible for managing service protection API limit errors. The way that the errors should be managed depends on the nature of the application.

### Interactive client applications

The service protection limits are high enough that users of an interactive client application should rarely encounter them during normal usage. However, if the client application allows for bulk operations, users might encounter them. Client application developers should be aware of how service protection API limits are enforced, and they should design the user interface (UI) to help reduce the potential for users to send extremely demanding requests to the server. However, they should still expect that service protection API limit errors might occur, and they should be prepared to handle those errors.

Client application developers should not just throw errors so that users receive the error messages, because users aren't the intended audience. For specific strategies that you can use to manage a throttling response when API requests exceed the service protection limits, see [Retry operations](service-protection-retry-operations.md).

### Data integration applications

Applications that are designed to load data into Finance and Operations apps or perform bulk data operations must be able to manage service protection API limit errors. These applications must prioritize throughput, so that they can complete their work in the minimum amount of time. They must have a strategy for retrying operations and achieving maximum throughput.

For more information, see [Maximize API throughput](service-protection-maximizing-api-throughput.md).

### Anonymous users

Some applications will send requests from anonymous users through a service principal account. For the service protection API limits that are evaluated on a per-user basis, these applications can reach the limits because of the volume of traffic that the applications experience across all client users. As for interactive client applications, the expectation is that users should not receive messages about service protection API limit errors. Instead, the UI should disable further requests and show a message that states that the server is busy. The message might include the time when the application can begin to accept new requests.

## Enforcement of the service protection API limits

There are two types of service protection API limits for Finance and Operations apps: user-based and resource-based. User-based limits help prevent individual users or integrations from harming system performance and availability. Resource-based limits help protect the environment by enforcing thresholds of high environment resource utilization. When high thresholds are reached, service requests are limited. 

> [!IMPORTANT]
> Service protection API limits are subject to change and might vary among environments. The numbers represent default values and are provided to give you an idea of the values that you can expect in your environment. These limits aren't configurable, and they aren't specific to legal entities.

### User-based service protection API limits

Two of the user-based service protection API limits are evaluated within a sliding window of five minutes (300 seconds). If either limit is exceeded during the preceding 300 seconds, a service protection API limit error will be returned on subsequent requests to help protect the service until the [Retry-After interval](service-protection-retry-operations.md#retry-after-intervals) has ended.

The service protection API limits are evaluated per user. Each authenticated user is limited independently. Only the user accounts that are making extraordinary demands will be limited. No other users will be affected.

User-based service protection API limits are enforced based on three factors:

- The number of requests that a user sent
- The combined execution time that is required to process the requests that a user sent
- The number of concurrent requests that a user sent

Each web server that is available to your environment will independently enforce the service protection API limits. Most environments will have more than one web server. However, only one web server is allocated to trial environments. The actual number of web servers that are available to your environment depends on multiple factors that are part of the managed Finance and Operations apps service. One of these factors is the number of user licenses that you've purchased. For information about how to use web resources that are available in your environment, see [Monitoring for API throttling](service-protection-monitoring.md).

The following table describes the default user-based service protection API limits that are enforced *per user, per application ID, per web server*.

| Measure | Description | Service protection limit |
| --- | --- | --- |
| Number of requests | The cumulative number of requests that the user has made. | 6,000 within the five-minute sliding window |
| Execution time | The combined execution time of all requests that the user has made. | 20 minutes (1,200 seconds) within the five-minute sliding window |
| Number of concurrent requests | The number of concurrent requests that the user has made. | 52 |

### Resource-based service protection API limits

Whereas user-based service protection API limits are specified per user per web server, resource-based service protection API limits are enforced based on environment resource utilization thresholds. The resource limits will throttle service requests when the aggregate consumption of web server resources reaches levels that threaten service performance and availability. Resource-based service protection API limits work together with user-based limits as protective settings that help prevent the over-utilization of resources. In this way, they help preserve the system's responsiveness and ensure consistent availability and performance for environments that run Finance and Operations apps.

For resource-based service protection API limits, you can define the prioritized order that integrations are throttled in when resource thresholds are reached. For more information, see [Throttling prioritization](priority-based-throttling.md).

## Service protection API response

When client applications make extraordinarily demanding requests, the Finance and Operations apps service returns an error that indicates that too many requests have been made. We follow a common pattern for online services by returning a [429 Too Many Requests response](https://developer.mozilla.org/docs/Web/HTTP/Status/429).

For the 429 Too Many Requests response, a specific error message is returned for each service protection API limit. This section describes the error messages and possible mitigation strategies for each.

### Number of requests

This limit counts the total number of requests during the preceding 300-second period. The following error message is returned together with the API response:

> Number of requests exceeded the limit of 6000 over the time window of 300 seconds.

It isn't expected that a typical user of an interactive application will be able exceed this limit by sending 1,200 requests per minute, unless the application enables users to perform bulk operations.

For example, if a list view enables the selection of 250 records at a time and allows a user to perform an operation on all records in a single action, the user will have to perform this operation 24 times within 300 seconds to reach the service protection API limit.

If your application provides this capability, you should consider one or both of the following strategies:

- Decrease the total number of records that can be selected in a list. If the number of items that are shown in a list is reduced to 50, the user will have to perform this operation 120 times within 300 seconds. In other words, the user will have to complete the operation on each list within 2.5 seconds. 
- Combine the selected operations into a batch. Because a batch can contain up to 5,000 operations, it will avoid the limit on the number of requests. However, you will have to be prepared for the execution time limit.

### Execution time

This limit tracks the combined execution time of incoming requests during the preceding 300-second period. The following error message is returned together with the API response:

> Combined execution time of incoming requests exceeded the limit of 1200 seconds over the time window of 300 seconds. Decrease the number of concurrent requests or reduce the duration of requests and try again later.

Some operations require more resources than others. Batch operations and highly complex queries can be very demanding. These operations might also be performed simultaneously in concurrent requests. Therefore, within the five-minute window, it's possible to request operations that will require more than 20 minutes of combined computation time.

This limit can be encountered when strategies that use batch operations and concurrent requests are used to avoid the limit on the number of requests. If this error is encountered for batch operations, a potential mitigation strategy is to divide the operations into smaller batches and run the individual batches concurrently by using different service principals.

### Concurrent requests

This limit tracks the number of concurrent requests for the user. The following error message is returned together with the API response:

> Number of concurrent requests exceeded the limit of 52.

Client applications aren't limited to sending requests individually in succession. The client can apply parallel programming patterns or various methods to send multiple requests simultaneously. If the limit on the number of concurrent requests is exceeded, the error is returned together with the API response.

Although you can send concurrent requests as a key part of your strategy for maximizing throughput, don't overuse this approach. When [parallel programming in .NET](/dotnet/standard/parallel-programming) is used, the default degree of parallelism depends on the number of CPU cores on the server that runs the code. This number should not exceed 52. You can set the [ParallelOptions.MaxDegreeOfParallelism](/dotnet/api/system.threading.tasks.paralleloptions.maxdegreeofparallelism) property to define the maximum number of concurrent tasks.

### Resource utilization threshold

This limit tracks the cumulative utilization thresholds of server resources. The following error message is returned together with the API response:

> This request could not be processed at this time due to system experiencing high resource utilization.

This error doesn't necessarily indicate that any single user or integration is causing the issue. Instead, it indicates that the cumulative utilization of web server resources across all service integrations has exceeded a threshold that threatens the performance and availability of the service. In this case, general strategies for optimizing API integrations are useful, such as the strategies that are outlined in [Maximize API throughput](service-protection-maximizing-api-throughput.md). Additionally, make sure that you've defined the [throttling prioritization](priority-based-throttling.md) for your API integrations.

## Exceptions to service protection limits

The service protection API limits don't apply to all Microsoft services. The following services are currently exempt from them:

- [Document Routing Agent (DRA)](../analytics/install-document-routing-agent.md)
- [Warehouse Management mobile app (WHSMobile)](../../../supply-chain/warehousing/configure-app-field-names-priorities-warehouse.md)
- [Retail Server API](../../../commerce/dev-itpro/consume-retail-server-api.md)
- [Office Integration](../office-integration/office-integration.md)
- [Data Import/Export Framework (DIXF)](data-import-export-job.md)
- [Data Integrator](/power-platform/admin/data-integrator)
- [Dual-write](dual-write/dual-write-overview.md)
- [Power Platform virtual tables for Finance and Operations apps](../power-platform/virtual-entities-overview.md)
- [Finance and Operations apps Connector](fin-ops-connector.md)

Although these services are currently exempt from the limits, they prioritize implementation of the service protection limits. Notifications will be provided before any changes, and the documentation will be updated when exemptions are removed for these services.

> [!NOTE]
> When service protection limits are applied to them, these services will implement handlers that use Retry-After logic. However, we still recommend that you have client-side handling for throttling when you use these services. Consider implementing the 429 handler that uses Retry-After logic.
