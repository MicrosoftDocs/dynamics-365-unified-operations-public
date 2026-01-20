---
title: Service request tracing
description: Learn about the client request identifier that you should include in headers to enable requests to be traced through the finance and operations service.
author: jaredha
ms.author: johnmichalak
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 01/20/2026
ms.reviewer: johnmichalak
audience: IT Pro, Developer
ms.search.region: Global
ms.search.validFrom: 2022-04-07
---

# Service request tracing

[!include[banner](../includes/banner.md)]

As a best practice when you develop data integrations with finance and operations service endpoints, include a request identifier in the request header. By using this identifier, you can trace the request through the service. Your client application should generate and log a client request ID (`x-ms-client-request-id`) value and send it in the application programming interface (API) request header. This value is a globally unique identifier (GUID) that uniquely identifies each client request.

The finance and operations service logs the `x-ms-client-request-id` value that it receives in the request header. This value becomes an identifier for the request in service telemetry.

## Troubleshooting API operations

If a request consistently fails, and you verify that it's correctly formulated, you might need to open a support ticket so that Microsoft can help troubleshoot the issue. In your support ticket, include the following values:

- The `x-ms-client-request-id` value that your client application generated and sent in the request header.
- The `ms-dyn-aid` value, which is the finance and operations activity ID. The finance and operations service generates this unique identifier for the request and sends it back to the client application in the response header.
- The approximate time when the request was made.

These values enable Microsoft to trace the request through service telemetry and troubleshoot the cause of the request failure. If the service doesn't return a response to the client, so that no `ms-dyn-aid` value is provided, be sure to provide at least the `x-ms-client-request-id` value and the approximate time of the request in your support ticket to enable Microsoft to trace the API request.

