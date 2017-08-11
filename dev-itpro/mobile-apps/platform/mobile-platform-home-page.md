---
# required metadata

title: Mobile platform home page
description: The mobile platform lets you create mobile apps for your workspaces.
author: RobinARH
manager: AnnBe
ms.date: 07/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations, Platform, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 255544
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 9

---

# Mobile platform

Microsoft Dynamics 365 Unified Operations includes support for mobile apps. You can reuse business logic and modeling from the Unified Operations. It also enables rich offline and mobile interactions, and an easy-to-use designer experience. Developers can create simplified forms in Microsoft Visual Studio and then design mobile apps that expose this functionality. The mobile platform makes it easy to change the forms and mobile app definitions to include customizations that are made to the product. 

## Getting started

+ [Getting started](mobile-platform-getting-started.md) 
+ [Architecture and design considerations](mobile-platform-architecture.md) 

We also have a video series about creating a mobile app:

+ [Tutorial 1: Building the sales order page](https://youtu.be/PdegfBxifl8)
+ [Tutorial 2: Building the sales order details page](https://youtu.be/mF-vlbnRte0)
+ [Tutorial 3: Building the create new sales order action](https://youtu.be/VYw9oTv9t3o)
+ [Tutorial 4: Adding a lookup to the create new sales order action](https://youtu.be/eNJKd0IYmZk)
+ [Tutorial 5: Adding a lookup and hiding pages using mobile business logic](https://youtu.be/kIJKk9J8FvI)

## Common configurations

+ [Localize mobile workspaces on the server](scenarios/localize-workspaces-on-server.md)
+ [Secure a mobile app workspace](scenarios/secure-mobile-workspace.md)
+ [Customize the display of a field so that it is clickable](scenarios/make-workspace-field-clickable.md)
+ [Make a field mandatory using workspace classes](scenarios/make-field-mandatory.md)
+ [Display a count in a field](scenarios/display-count-workspace.md)

## Client-side development

Client-side APIs are used in the business logic file which provides an extensibility layer to the mobile workspace in order to allow customizing:
1. Metadata
1. Runtime control/page instances
1. Business data
1. Offline-first business behaviors
1. Layout and style

[Download the sample business logic file for Reservation management workspace](https://github.com/Microsoft/Dynamics365-for-Operations-mobile-FleetManagementSamples) (.js file)

+ [Client-side design APIs overview](scenarios/client-api-design-overview.md)
+ [Client APIs](client-apis/client-apis-reference.md)

## Server-side development

+ [Workspace class overview](scenarios/mobile-workspace-configuration.md)
+ [Server APIs (X++)](mobile-workspace-server-apis.md)


