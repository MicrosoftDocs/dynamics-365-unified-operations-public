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
ms.search.scope: Operations
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

By using a mobile apps, you can reuse business logic and modeling from Microsoft Dynamics 365 for Finance and Operations. Mobile apps enable rich offline and mobile interactions, and an easy-to-use designer experience. Developers can create simplified forms in Microsoft Visual Studio and then design mobile apps that expose this functionality. The mobile platform makes it easy to change the forms and mobile app definitions to include customizations that are made to the product. 

## Get started

+ [Getting started](mobile-platform-getting-started.md) 
+ [Architecture](mobile-platform-architecture.md) 
+ [Page design guidelines](page-design-guidelines.md)
+ [Action design guidelines](action-design-guidelines.md)
+ [Form design requirements](form-design-requirements.md)

Check out the following series of how-to videos that show how to create a mobile app.

+ [Tutorial 1: Building the sales order page](https://youtu.be/PdegfBxifl8)
+ [Tutorial 2: Building the sales order details page](https://youtu.be/mF-vlbnRte0)
+ [Tutorial 3: Building the create new sales order action](https://youtu.be/VYw9oTv9t3o)
+ [Tutorial 4: Adding a lookup to the create new sales order action](https://youtu.be/eNJKd0IYmZk)
+ [Tutorial 5: Adding a lookup and hiding pages using mobile business logic](https://youtu.be/kIJKk9J8FvI)

## Common configurations
These topics describe some common customizations that you can add to your mobile app.
+ [Localize mobile workspaces](scenarios/localize-workspaces-on-server.md)
+ [Help secure mobile workspaces](scenarios/secure-mobile-workspace.md)
+ [Set up clickable fields](scenarios/make-workspace-field-clickable.md)
+ [Set up mandatory fields through workspace classes](scenarios/make-field-mandatory.md)
+ [Display item counts in a field](scenarios/display-count-workspace.md)

## Client-side development

Client-side APIs are used in the business logic file, which provides an extensibility layer to the mobile workspace that allows for customization. Some things that you can access through the client-side APIs include:
+ Metadata
+ Runtime control/page instances
+ Business data
+ Offline-first business behaviors
+ Layout and style

The process for client-side development is described in these topics:
+ [Client-side design APIs overview](scenarios/client-api-design-overview.md)
+ [Business logic events overview](business-logic-events-overview.md)
+ [Client APIs](client-apis/client-apis-reference.md)

You can download a sample business logic file (a .js file) for the Reservation management workspace. Go to [Dynamics365-for-Operations-mobile-FleetManagementSamples](https://github.com/Microsoft/Dynamics365-for-Operations-mobile-FleetManagementSamples), open the **business_logic folder**, and locate the FM.js file

## Server-side development

Workspace attributes and classes are used to create, configure, and publish workspaces on the server. Server-side development is described in these topics:
+ [Workspace class overview](scenarios/mobile-workspace-configuration.md)
+ [Server APIs (X++)](mobile-workspace-server-apis.md)

You can download the sample project (an .axpp file) for the Fleet Management mobile app. Go to from [Dynamics365-for-Operations-mobile-FleetManagementSamples](https://github.com/Microsoft/Dynamics365-for-Operations-mobile-FleetManagementSamples) and download the **FMMobileApp.axpp** file.

## Additional resources
### What's new and in development
Go to the [Microsoft Dynamics 365 Roadmap](https://roadmap.dynamics.com/) to see what new features have been released and what new features are in development.

### Blogs
You can find opinions, news, and other information about Retail and other solutions on the [Microsoft Dynamics 365 blog](https://community.dynamics.com/b/msftdynamicsblog).

