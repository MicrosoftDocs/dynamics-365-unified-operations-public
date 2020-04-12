---
# required metadata

title: Architectural overview
description: This topic presents an architectural overview of Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Architectural overview

[!include [banner](../includes/banner.md)]

This topic presents an architectural overview of Microsoft Dynamics 365 Commerce.

## Overview

The Dynamics 365 Commerce online extensibility software development kit (SDK) lets partners easily extend their website so that it includes additional business logic and user experience (UX) logic. Partners can do this extension by using open-source technologies that are freely available.

## Component-based architecture

The architecture of the platform takes advantage of a reuse-based approach to define, implement, and compose loosely coupled independent components. In this approach, the emphasis is on separation of concerns.

## High-level design

The extensibility design avoids dependency between the platform and the application by running the application as a microservice that is built on Node.js and that uses React as an underlying UX framework. The platform is run as a separate service, and handles all routing, integration with the content management system (CMS), and security.

![High-level architectural overview](media/architectural-overview.png)

## Request flow

Here is a typical architectural flow when a customer requests a page from an online store that uses the Dynamics 365 Commerce platform.

1. The platform gets a request, and does authentication, routing, and locale detection.
1. The platform generates a hydrated page object that contains page configuration data and data from external services that use data actions.
1. Data actions allow for batching, aggregation, and chaining of multiple service calls, including deduplication.
1. The platform provides a set of core data actions that provide connections to Dynamics 365 Commerce services (for example, the catalog and ratings).
1. After the hydrated page object is generated, the platform calls the React application that is running on a node express server.
1. The React application parses the view model, runs the React views on the server side, and generates HTML.
1. The React application consists of core SDK modules, starter kit modules, and custom modules.
1. The platform sends back the HTML together with the appropriate cookies, headers, and so on.
1. The React script initializes the components, takes over client-side execution on the browser, and renders the modules.
1. Node.js supports tool pages and other developer productivity tools that are provided by the platform.

## Partner application

![Partner application architectural overview](media/architectural-overview-2.png)

The compiled partner package contains both the SDK and a starter kit. The SDK isn't extensible, but starter kit modules can be cloned and completely customized. Partner customizations (modules, data actions, and themes) can be packaged by using a command-line interface (CLI) command. The package can then be uploaded by using Microsoft Dynamics Lifecycle Services (LCS). In this way, the customizations are incorporated into the partner's e-Commerce site.

## Additional resources

[e-Commerce components](ecommerce-components.md)

[CLI command reference](cli-command-reference.md)
