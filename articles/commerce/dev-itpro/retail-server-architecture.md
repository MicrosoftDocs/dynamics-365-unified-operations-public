---
title: Headless commerce architecture
description: This article provides an overview of the architecture of the headless commerce.
author: aneesa
ms.date: 02/19/2026
ms.topic: article
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: aneesa
ms.search.validFrom: 2021-02-28
ms.custom: 
  - bap-template
---

# Headless commerce architecture

[!include [banner](../includes/banner.md)]

This article provides an overview of the architecture of the headless commerce (also known as Commerce Scale Unit). The headless commerce is an API-driven framework that enables extensible, personalized, friction-free commerce experiences, and integrated, optimized back-office operations.

:::image type="content" source="media/CSUExtensionArchitecture.PNG" alt-text="Diagram of Commerce Scale Unit architecture.":::

## Omnichannel solution provided by the headless commerce

Microsoft Dynamics 365 Commerce (headquarters, in-store, call center, and e-commerce) consumes the commerce APIs of the headless commerce and provides a complete omnichannel solution. Partner applications and Microsoft Power Platform connectors can also consume the APIs.

:::image type="content" source="./media/CSUConsumer.PNG" alt-text="Diagram of Commerce Scale Unit platform integration.":::

## Components

The headless commerce contains these components:

+ Consumer APIs
+ Commerce runtime (CRT)
+ Channel database

### Consumer APIs

The headless commerce exposes Open Data Protocol (OData) APIs for Dynamics 365 Commerce and partner applications to consume. The API layer is built by using ASP.NET Core. It provides different authentication options so that the clients can consume the APIs. The APIs are a wrapper that exposes the business logic. For more information, see the following articles:

+ [Commerce Scale Unit customer and consumer APIs](retail-server-customer-consumer-api.md)
+ [Consume APIs](consume-retail-server-api.md)
+ [Custom APIs](retail-server-icontroller-extension.md)

### Commerce runtime

CRT is a collection of portable .NET libraries that contain the core commerce business logic. The consumer APIs expose the business logic for clients to consume. To add or modify business logic, customize CRT. For more information, see the following articles:

+ [Commerce runtime (CRT) services](crt-services.md)
+ [CRT Extensions](commerce-runtime-extensibility.md)

### Channel database

The channel database holds transactional data and master data from one or more commerce channels, such as an online store or a brick-and-mortar store. Commerce Data Exchange (CDX) pushes master data from Commerce headquarters to the channel database. CDX pulls transactional data that is stored in the channel database back to Commerce headquarters. For more information, see [Channel database extensions](channel-db-extensions.md).

## Headless Commerce Integration

Microsoft provides a set of sample implementations that are tailored to headless and composable commerce scenarios. These samples can help you *kick-start* and *accelerate* the development of custom storefronts by using Dynamics 365 Commerce headless engine (commonly referred to as headless commerce). The [Headless Commerce Samples GitHub repository](https://github.com/microsoft/Dynamics-365-FastTrack-Implementation-Assets/tree/master/Commerce/HeadlessCommerceSamples) includes both technical guidance and hands-on code samples to help you quickly get started.

The samples serve as quick-start templates and reference implementations for partners, software development companies (formerly referred to as independent software vendors or ISVs), and customers. The samples cover core scenarios such as authentication, customer data, product data, pricing, cart, checkout, and order ingestion.

To learn more about each commerce API endpoint, and to read guidance for packaging, deploying, and operating headless commerce solutions, use the resources that are linked in the [Components](#components) section of this article.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
