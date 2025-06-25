---
title: Get Started with Headless Commerce Integration
description: This article provides information and samples on how to start your Headless Commerce Integration.
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

This article provides information and samples on how to start your Headless Commerce Integration.

To help you *kickstart and accelerate* the development of custom storefronts using Dynamics 365 Commerce headless engine commonly referred to as Headless Commerce, Microsoft provides a set of sample implementations tailored for headless and composable commerce scenarios.

The [Headless Commerce Integration Samples GitHub repository](https://github.com/microsoft/Dynamics-365-FastTrack-Implementation-Assets/tree/master/Commerce/HeadlessCommerceSamples) includes both technical guidance and working code samples to help you build and integrate with the Retail Server APIs.

The repository includes:

*Guidance and Architecture*

1. *Architecture* – Overview of headless integration patterns and concepts.
1. *Customers* – Working with customer master data and account integration.
1. *Inventory* – Querying real-time product inventory.
1. *Orders* – Order creation and processing via the Headless Commerce Engine (CSU).
1. *Payments* – Strategies for integrating payments in headless scenarios.
1. *Prices* – Handling product pricing, discounts, and price lookups.
1. *Products* – Accessing and managing product master data.

*Code Samples*

1. *HeadlessCommerceCommonAPICollection* – A curated set of common API calls for easy testing and exploration.
1. *SampleCommerceProductPublisher* – An Azure Function and publisher component that uses the Commerce Proxy to retrieve product data via headless APIs.
1. *SampleCustomerCreateSearch* – Logic App samples to demonstrate creating and searching for customers.
1. *HeadlessSampleConsoleApp* – A console-based sample that shows how to ingest orders into CSU.

These samples serve as quick start templates and reference implementations for partners, ISVs, and customers building their own headless commerce experiences. For detailed information on each commerce API endpoint, as well as guidance on packaging, deploying, and operating headless commerce solutions, see [Commerce Scale Unit (CSU) and Core service APIs](retail-server-customer-consumer-api.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
