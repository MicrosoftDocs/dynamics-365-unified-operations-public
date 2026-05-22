---
title: E-commerce architectural overview
description: This article provides an architectural overview of Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 02/20/2026
ms.topic: overview
ms.author: asharchw
ms.reviewer: v-griffinc
ms.search.region: Global
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# E-commerce architectural overview

[!include [banner](../includes/banner.md)]

This article provides an architectural overview of Microsoft Dynamics 365 Commerce.

The Dynamics 365 Commerce online extensibility software development kit (SDK) helps partners easily extend their website to include extra business logic and user experience (UX) logic. Partners can create these extensions by using open-source technologies that are freely available.

This architectural overview focuses on the "Web Storefront" box highlighted in the following [Commerce architecture](../commerce-architecture.md) illustration.

:::image type="content" source="media/architecture-overview-web-storefront.jpg" alt-text="e-commerce-extensibility/architectural-overview of Dynamics 365 Commerce component overview with Web Storefront box highlighted.":::

## Web storefront component-based architecture

The platform architecture uses a reuse-based approach to define, implement, and compose loosely coupled independent components. This approach emphasizes separation of concerns.

## High-level design

The extensibility design avoids dependency between the platform and the application by running the application as a microservice. The application is built on Node.js and uses React as an underlying UX framework. The platform runs as a separate service. It handles all routing, integration with the content management system (CMS), and security.

:::image type="content" source="media/architectural-overview.png" alt-text="Diagram of the high-level architectural overview.":::

## Request flow

Here's a typical architectural flow when a customer requests a page from an online store that uses the Dynamics 365 Commerce platform.

1. The platform gets a request, and it authenticates, routes, and detects the locale.
1. The platform generates a hydrated page object that contains page configuration data and data from external services that use data actions.
1. Data actions allow for batching, aggregation, and chaining of multiple service calls, including deduplication.
1. The platform provides a set of core data actions that provide connections to Dynamics 365 Commerce services, such as the catalog and ratings.
1. After the platform generates the hydrated page object, it calls the React application that runs on a node express server.
1. The React application parses the view model, runs the React views on the server side, and generates HTML.
1. The React application consists of core SDK modules, module library modules, and custom modules.
1. The platform sends back the HTML together with the appropriate cookies, headers, and other data.
1. The React script initializes the components, takes over client-side execution on the browser, and renders the modules.
1. Node.js supports tool pages and other developer productivity tools that the platform provides.

## Partner application

:::image type="content" source="media/architectural-overview-2.png" alt-text="Diagram of the partner application architectural overview.":::

The compiled partner package contains both the SDK and a module library. The SDK isn't extensible, but you can clone and completely customize module library modules. Use a command-line interface (CLI) command to package partner customizations, such as modules, data actions, and themes. Then, use Microsoft Dynamics Lifecycle Services (LCS) to upload the package. By using this process, you can incorporate customizations into the partner's e-Commerce site.

## Additional resources

[E-commerce components](ecommerce-components.md)

[CLI command reference](cli-command-reference.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
