---
title: Service protection API limits
description: Learn about limits for service protection application programming interfaces (APIs) for the finance and operations apps service.
author: jaredha
ms.author: johnmichalak
ms.topic: article
ms.date: 01/20/2026
audience: Developer
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2022-04-21
---

# Service protection API limits

[!include [banner](../includes/banner.md)]

This article provides information about limits for service protection application programming interfaces (APIs) for the finance and operations apps service.

> [!IMPORTANT]
> Finance and operations apps environments version 10.0.19 and later enable resource-based service protection API limits. Resource-based API limits continue to protect the finance and operations service from unexpected spikes in usage that threaten the availability and performance of the service.
> 
> User-based service protection API limits, as described in this article, were previously announced as mandatory in all finance and operations apps environments in version 10.0.33 as an additional layer of service protection. As of March 31, 2023, **user-based service protection API limits are no longer being implemented in finance and operations apps environments.** The limits are currently optional and can be enabled or disabled by using the **User-based service protection API limits** feature in **Feature management**. In version 10.0.35, the API limits are disabled by default but can still be optionally enabled for environments. In version 10.0.36, the limits are disabled on all environments, and the option to enable the limits is removed.

To ensure consistent availability and performance of the finance and operations apps service, Microsoft applies limits to the way that the service APIs are used. These limits protect the service when client applications make extraordinary demands on server resources. Sudden bursts of high incoming API traffic or concurrent long-running requests against the server can exhaust server resources. These conditions can cause outages or have other impacts on the availability and performance of the service.

The limits don't affect regular users of interactive clients. They affect only client applications that perform extraordinary API requests. The limits provide a level of protection from random and unexpected surges in request volume that threaten the availability and performance of the finance and operations platform.

> [!NOTE]
> Service protection API limits are available only for the finance and operations apps online service, including production and sandbox environments. They aren't available for on-premises or development environments.

## Impact on client applications

Client applications are responsible for managing service protection API limit errors. How you manage the errors depends on the nature of the application.

### Interactive client applications

The service protection limits are high enough that users of an interactive client application rarely encounter them during normal usage. However, if the client application allows for bulk operations, users might encounter them. Client application developers should be aware of how service protection API limits are enforced, and they should design the user interface (UI) to help reduce the potential for users to send extremely demanding requests to the server. However, they should still expect that service protection API limit errors might occur, and they should be prepared to handle those errors.

Client application developers shouldn't just throw errors so that users receive the error messages, because users aren't the intended audience. For specific strategies that you can use to manage a throttling response when API requests exceed the service protection limits, see [Retry operations](service-protection-retry-operations.md).

### Data integration applications

Applications that load data into finance and operations apps or perform bulk data operations must handle service protection API limit errors. These applications must prioritize throughput so they can finish their work as quickly as possible. They need a strategy for retrying operations and achieving maximum throughput.

For more information, see [Maximize API throughput](service-protection-maximizing-api-throughput.md).

### Anonymous users

Some applications send requests from anonymous users through a service principal account. For the service protection API limits that the system evaluates on a per-user basis, these applications can reach the limits because of the volume of traffic that the applications experience across all client users. As with interactive client applications, users shouldn't receive messages about service protection API limit errors. Instead, the UI should disable further requests and show a message that states that the server is busy. The message might include the time when the application can begin to accept new requests.

## Enforcement of the service protection API limits

Finance and operations apps have two types of service protection API limits: user-based and resource-based. User-based limits help prevent individual users or integrations from harming system performance and availability. Resource-based limits help protect the environment by enforcing thresholds of high environment resource utilization. When high thresholds are reached, the system limits service requests. 

> [!IMPORTANT]
> Service protection API limits can change and might vary among environments. The numbers in this article represent default values and give you an idea of the values that you can expect in your environment. These limits aren't configurable, and they're not specific to legal entities.

### User-based service protection API limits

Two user-based service protection API limits use a sliding window of five minutes (300 seconds) for evaluation. If either limit is exceeded during the preceding 300 seconds, subsequent requests return a service protection API limit error. This error helps protect the service until the [Retry-After interval](service-protection-retry-operations.md#retry-after-intervals) ends.

The service protection API limits apply to each user. Each authenticated user has an independent limit. Only the user accounts that make extraordinary demands are limited. No other users are affected.

User-based service protection API limits depend on three factors:

- The number of requests that a user sends
- The combined execution time required to process the requests that a user sends
- The number of concurrent requests that a user sends

The following table describes the default user-based service protection API limits that apply *per user, per application ID, per web server*.

| Measure | Description | Service protection limit |
| --- | --- | --- |
| Number of requests | The cumulative number of requests that the user makes. | 6,000 within the five-minute sliding window |
| Execution time | The combined execution time of all requests that the user makes. | 20 minutes (1,200 seconds) within the five-minute sliding window |
| Number of concurrent requests | The number of concurrent requests that the user makes. | 52 |

Each web server that's available to your environment independently enforces the service protection API limits. Most environments have more than one web server. However, trial environments allocate only one web server. Multiple factors determine the actual number of web servers that are available to your environment as part of the managed finance and operations apps service. One of these factors is the number of user licenses that you purchase. For information about how to use web resources that are available in your environment, see [Monitoring for API throttling](service-protection-monitoring.md).

To track API usage and enforce service protection API limits, each web server in the environment tracks a throttling key for API requests. The throttling key combines the following values:

- **User** – The user who makes the API request.

    - If the application authenticates by using user authentication, this value is the object ID of the Microsoft Entra user principal of the user who makes the API request.
    - If the application authenticates by using app authentication, this value is the object ID of the application in Microsoft Entra ID.

- **Application** – The client ID of the application from the app registration in Microsoft Entra ID.

The access token used for the API request provides these values. For example, a company has an employee portal that's a web application that uses the OData API to connect to finance and operations data. Each employee signs in to the web app by using a company email address and password. In this scenario, the API request uses the user object ID and the application client ID to track usage against the service protection API limits. Each user of the application has API usage tracked and throttled independently. For more information about the authentication flow for this scenario, see [Authentication](services-home-page.md#authentication).

If the application uses app authentication instead of user authentication, so that a user doesn't sign in to the application, the throttling key user is the object ID of the application in Microsoft Entra ID. For information about how to find the application object ID, see [Application and service principal objects in Microsoft Entra ID](/azure/active-directory/develop/app-objects-and-service-principals).

### Resource-based service protection API limits

User-based service protection API limits apply per user per web server. Resource-based service protection API limits enforce thresholds based on environment resource utilization. The resource limits throttle service requests when the aggregate consumption of web server resources reaches levels that threaten service performance and availability. The thresholds are based on percentage utilization of resources such as memory and CPU on the environment web servers. If the utilization of the server resources exceeds defined thresholds when the API request is made, the request is throttled and receives a "Too Many Requests" response.

Resource-based service protection API limits work together with user-based limits as protective settings that help prevent the over-utilization of resources. In this way, they help preserve the system's responsiveness and ensure consistent availability and performance for environments that run finance and operations apps.

For resource-based service protection API limits, you can define the prioritized order that integrations are throttled in when resource thresholds are reached. For more information, see [Throttling prioritization](priority-based-throttling.md).

## Service protection API response

When client applications make extraordinarily demanding requests, the finance and operations apps service returns an error that indicates that too many requests have been made. The service follows a common pattern for online services by returning a [429 Too Many Requests response](https://developer.mozilla.org/docs/Web/HTTP/Status/429).

For the 429 Too Many Requests response, a specific error message is returned for each service protection API limit. This section describes the error messages and possible mitigation strategies for each.

### Number of requests

This limit counts the total number of requests during the preceding 300-second period. The following error message is returned together with the API response:

> Number of requests exceeded the limit of 6000 over the time window of 300 seconds.

A typical user of an interactive application isn't expected to exceed this limit by sending 1,200 requests per minute, unless the application enables users to perform bulk operations.

For example, if a list view enables the selection of 250 records at a time and allows a user to perform an operation on all records in a single action, the user must perform this operation 24 times within 300 seconds to reach the service protection API limit.

If your application provides this capability, consider one or both of the following strategies:

- Decrease the total number of records that can be selected in a list. If the number of items that are shown in a list is reduced to 50, the user must perform this operation 120 times within 300 seconds. In other words, the user must complete the operation on each list within 2.5 seconds. 
- Combine the selected operations into a batch. Because a batch can contain up to 5,000 operations, it avoids the limit on the number of requests. However, be prepared for the execution time limit.

### Execution time

This limit tracks the combined execution time of incoming requests during the preceding 300-second period. The API response returns the following error message:

> Combined execution time of incoming requests exceeded the limit of 1200 seconds over the time window of 300 seconds. Decrease the number of concurrent requests or reduce the duration of requests and try again later.

Some operations require more resources than others. Batch operations and highly complex queries can be very demanding. You might also perform these operations simultaneously in concurrent requests. Therefore, within the five-minute window, it's possible to request operations that require more than 20 minutes of combined computation time.

This limit can be encountered when strategies that use batch operations and concurrent requests are used to avoid the limit on the number of requests. If this error is encountered for batch operations, a potential mitigation strategy is to divide the operations into smaller batches and run the individual batches concurrently by using different service principals.

### Concurrent requests

This limit tracks the number of concurrent requests for the user. The following error message is returned together with the API response:

> Number of concurrent requests exceeded the limit of 52.

Client applications aren't limited to sending requests individually in succession. The client can apply parallel programming patterns or various methods to send multiple requests simultaneously. If the limit on the number of concurrent requests is exceeded, the error is returned together with the API response.

Although you can send concurrent requests as a key part of your strategy for maximizing throughput, don't overuse this approach. When [parallel programming in .NET](/dotnet/standard/parallel-programming) is used, the default degree of parallelism depends on the number of CPU cores on the server that runs the code. This number shouldn't exceed 52. You can set the [ParallelOptions.MaxDegreeOfParallelism](/dotnet/api/system.threading.tasks.paralleloptions.maxdegreeofparallelism) property to define the maximum number of concurrent tasks.

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
- [Data Import/Export Framework (DIXF)](../../fin-ops/data-entities/data-import-export-job.md)
- [Recurring integrations](recurring-integrations.md)
- [Data Integrator](/power-platform/admin/data-integrator)
- [Power Platform virtual tables for finance and operations apps](../power-platform/virtual-entities-overview.md)
- [Finance and operations apps Connector](fin-ops-connector.md)

The exemption for virtual tables applies only when the [Microsoft Power Platform integration with Finance and Operations apps](../power-platform/overview.md) is enabled. The service protection API limits apply to virtual tables if the integration isn't enabled for the Finance and Operations apps environment. When the integration is enabled, the exemption applies only to the Finance and Operations apps API endpoints that the virtual entity plugin invokes. The Finance and Operations apps service doesn't throttle the request. However, because the request is made through the Microsoft Dataverse API, [Service protection API limits](/power-apps/developer/data-platform/api-limits) might still apply to the request.

Although these services are currently exempt from the limits, they prioritize implementation of the service protection limits. Notifications are provided before any changes, and the documentation is updated when exemptions are removed for these services.

Services that don't use finance and operations OData or custom service API endpoints, such as the [Inventory Visibility Add-in](../../../supply-chain/inventory/inventory-visibility.md), aren't exempt from throttling, because no exemption is needed. Service protection API limits are applied only for finance and operations OData and custom service API endpoints. Services that don't use these endpoints aren't subject to throttling.

> [!NOTE]
> When service protection limits are applied to these services, they implement handlers that use Retry-After logic. However, you should still have client-side handling for throttling when you use these services. Consider implementing the 429 handler that uses Retry-After logic.
