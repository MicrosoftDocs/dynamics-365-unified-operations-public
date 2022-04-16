---
# required metadata

title: Service protection API limits
description: This topic provides information about service protection API limits for the Finance and Operations service.
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

To ensure consistent availability and performance of the Finance and Operations service we apply limits to how the service APIs are used. These limits are designed to protect the service when client applications make extraordinary demands on server resources. Sudden bursts of high incoming API traffic or concurrent long-running requests against the server can exhaust server resources, causing outages or other impacts on teh availability and performance of the service.

The limits should not affect normal users of interactive clients. The limits are designed to impact only client applications that perform extraordinary API requests. The limits provide a level of protection from random and unexpected surges in request volume that threaten the availability and performance of teh Finance and Operations platform.

When client applications make extraordinarily demanding requests, the Finance and Operations service returns an error indicating that too many requests have been made. We follow a common pattern for online services by returning a [429 Too Many Requests response](https://developer.mozilla.org/docs/Web/HTTP/Status/429).

> [!Note]
> Service protection API limits are available only for the Finance and Operations online service, including production and sandbox environments. The protection limits are not available for on-premises or development environments.

## Impact on client applications
It is the responsibility of client applications to manage service protection API limit errors. How teh error should be managed depends on teh nature of the application.

### Interactive client applications
The service protection limits are high enough that it should be rare for an individual using an interactive client application to encounter them during normal usage. However, it is possible if the client application allows for bulk operations. Client application developers should be aware of how service protection API limits are enforced and design the UI to reduce the potential for users to send extremely demanding requests to the server. But they should still expect that service protection API limit errors can occur and be prepared to handle them.

Client application developers should not simply throw the error to display the message to the user. The error message is not intended for end users. See [Retry operations](service-protection-retry-operations) for specific strategies on managing a throttling response when API requests exceed the service protection limits.
