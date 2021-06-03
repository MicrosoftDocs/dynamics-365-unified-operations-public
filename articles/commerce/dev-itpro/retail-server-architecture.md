---
title: Headless commerce engine architecture
description: This topic describes the architecture of headless commerce engine.
author: mugunthanm
ms.date: 06/20/2017
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: rhaertle
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 2021-02-28
ms.dyn365.ops.version: AX 10.0.16
---

# Headless commerce engine architecture

[!include [banner](../includes/banner.md)]

This topic describes the architecture of the headless commerce engine (also known as the Commerce Scale Unit). The headless commerce engine is an API-driven engine that enables extensible, personalized, friction-free commerce experiences, and integrated, optimized back-office operations.

![Commerce Scale Unit architecture diagram](./media/CSU.PNG)

## Omnichannel solution with headless commerce engine

The headless commerce engine commerce APIs which are consumed by Dynamics 365 Commerce (back-office, in-store, call center, and e-commerce), provide a complete omnichannel solution. The APIs can be consumed by third-party applications and Power Platform connectors.

![Commerce Scale Unit plateform integration diagram](./media/CSUConsumer.PNG)

## Components

The engine contains these components:

+ Consumer APIs
+ Commerce Runtime (CRT)
+ Channel databse

### Consumer APIs

The engine exposes OData APIs for Dynamics 365 Commerce and third-party applications to consume. The engine's API layer is built using ASP.NET Core and provides different authentication options for the clients to consume the APIs. The APIs are a wrapper which exposes the business logic. For more information on the APIs and extension, see:

+ [Commerce Scale Unit customer and consumer APIs](retail-server-customer-consumer-api.md)
+ [Consume APIs](consume-retail-server-api.md)
+ [Custom APIs](retail-server-icontroller-extension.md)

### Commerce runtime (CRT)

Commerce runtime (CRT) is a collection of portable .NET libraries that contain the core commerce business logic. The business logic is exposed through the consumer APIs of the engine for the clients to consume. To add or modify business logic, customize CRT. For more information, see:

+ [Commerce runtime (CRT) services](crt-services.md)
+ [CRT Extensions](commerce-runtime-extensibility.md)

### Channel database

The channel database (channel DB) holds transactional and master data from one or more commerce channels, such as an online store or a brick-and-mortar store. The master data is pushed down from the Headquarters (HQ) to the channel database using the commerce data exchange (CDX). The transactional data stored in the channel database is pulled back to the headquarters using the CDX. For more information, see [Channel database extensions](channel-db-extensions).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
