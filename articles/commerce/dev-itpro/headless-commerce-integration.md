---
title: Get started with Headless Commerce Integration
description: Learn about the information and samples that are available to help you start your Headless Commerce Integration.
author: ritakimani1
ms.date: 06/18/2025
ms.topic: how-to
audience: Developer
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: ritakimani
ms.search.validFrom: 2025-06-18
ms.custom: 
  - bap-template
---

# Get started with Headless Commerce Integration

[!include [banner](../includes/banner.md)]

This article describes the information and samples that are available to help you start your Headless Commerce Integration.

Microsoft provides a set of sample implementations that are tailored to headless and composable commerce scenarios. These samples can help you *kick-start* and *accelerate* the development of custom storefronts by using Microsoft Dynamics 365 Commerce headless engine (commonly referred to as headless commerce).

The [Headless Commerce Integration Samples GitHub repository](https://github.com/microsoft/Dynamics-365-FastTrack-Implementation-Assets/tree/master/Commerce/HeadlessCommerceSamples) includes both technical guidance and working code samples to help you build and integrate with the Retail Server APIs.

## Guidance and architecture

The Docs folder of the repo contains technical guidance and architecture information.

- *Architecture* – An overview of headless integration patterns and concepts.
- *Customers* – Information about how to work with customer master data and account integration.
- *Inventory* – Information about how to query real-time product inventory.
- *Orders* – Information about order creation and processing via the Headless Commerce Engine (CSU).
- *Payments* – Strategies for integrating payments in headless scenarios.
- *Prices* – Information about how to handle product pricing, discounts, and price lookups.
- *Products* – Information about how to access and manage product master data.

## Code samples

The Assets folder of the repo contains working code samples.

- *HeadlessCommerceCommonAPICollection* – A curated set of common API calls for easy testing and exploration.
- *SampleCommerceProductPublisher* – An Azure Function and publisher component that uses the Commerce Proxy to retrieve product data via headless APIs.
- *SampleCustomerCreateSearch* – Logic App samples that show how to create and search for customers.
- *HeadlessSampleConsoleApp* – A console-based sample that shows how to ingest orders into CSU.

These samples serve as quick-start templates and reference implementations for partners, software development companies (formerly referred to as independent software vendors or ISVs), and customers that build their own headless commerce experiences. You can find detailed information about each commerce API endpoint in [Commerce Scale Unit (CSU) and Core service APIs](retail-server-customer-consumer-api.md). There, you can also find guidance for packaging, deploying, and operating headless commerce solutions.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
