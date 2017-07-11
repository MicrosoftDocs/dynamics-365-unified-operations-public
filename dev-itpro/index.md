---
# required metadata

title: Development and administration using the Unified Operations platform
description: This page helps developers and IT Pros get started with the Dynamics 365 Unified Operations platform, which underlies Dynamics 365 for Finance and Operations, and Dynamics 365 for Retail.  
author: margoc
manager: AnnBe
ms.date: 06/20/2017
ms.topic: index-page
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: IT Pro, Developer
# ms.devlang: 
ms.reviewer: 71

# ms.tgt_pltfrm: 
ms.custom: 62303
ms.assetid: 3d7dfc2a-4be2-4fdc-ac35-cc96868f56ab
ms.search.region: Global
# ms.industry: 
ms.author: margoc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Development and administration using the Microsoft Dynamics 365 Unified Operations platform 

[!include[banner](includes/banner.md)]

Development and administration for Microsoft Dynamics 365 for Finance and Operations and Microsoft Dynamics 365 for Retail is performed using the Microsoft Dynamics 365 Unified Operations platform. The platform includes:

- Administrator experience and Lifecycle Services
- Developer experience
- Intelligence
- Mobile apps
- Data management and data entities 
- Office integration

## Developer experience
The developer experience is based on modern tooling using Visual Studio and .NET components.
-	The development tools are decoupled from any running environment, which means that you develop against local, XML-based files, not the online database.
-	Microsoft Visual Studio is the development environment. Finance and Operations customizes the Visual Studio environment to provide you with a smooth and familiar experience.
-	The X++ compiler generates Common Intermediate Language (CIL) for all features. CIL is the same intermediate language used by other .NET-based (managed) languages, such as the C# programming language.
-	You can leverage the browser-based client and design patterns for forms to provide an improved end-user experience.
-	The Application Lifecycle Model (ALM) supports build automation, test automation, and deployment of models to the cloud.

For more information, see [Developer home page](dev-tools/developer-home-page.md).

## Administrator experience and Lifecycle Services
Finance and Operations and Retail are cloud-hosted. As an IT professional, you can use Dynamics Lifecycle Services (LCS) to monitor and tune your environments, deploy features, and stay up to date with recent hotfixes. Within your deployment, you can configure security, and manage when processes run. You can also use LCS when you are called on to support business intelligence and reporting, mobile apps, Office, and other integrations. 

## BI & reporting
Finance and Operations provides five distinct reporting experiences. Specialized tools are provided to meet the complex and diverse reporting needs of various functions throughout the organization.
- Operational views – Designed to address the specific needs of a given business persona.
- Business documents – Static documents used to capture and exchange processed business data.
- Analytical tools and visualizations – Personalized presentations of logical calculations that allow the user to explore their data.
- Electronic reporting – Tool used to configure formats for electronic documents.
- Financial reporting – Designed to provide in-depth accounting management tools based on standard views of financial activities across legal entities.

## Mobile apps
The Microsoft Dynamics 365 for Finance and Operations mobile app empowers your organization to mobilize its business processes. After your IT admin enables the mobile workspaces feature for your organization, users can sign in to the app and immediately begin to run business processes from their mobile devices. The Dynamics 365 for Finance and Operations mobile app includes the following features that can help increase productivity:
+ Users can view, edit, and act on business data, even if they have intermittent network connectivity or their mobile devices are offline. When a device reestablishes a network connection, offline data operations are automatically synchronized with Dynamics 365 for Finance and Operations. 
+ IT admins or developers can build and publish mobile workspaces that have been tailored to their organization. The app uses your existing code assets, so you don’t have to re-implement your validation procedures, business logic, or security configuration. 
+ IT admins or developers can easily design mobile workspaces by using the point-and-click workspace designer that is included with the Dynamics 365 for Finance and Operations web client. 
+ IT admins or developers can optionally optimize the offline capabilities of workspaces by using the Business logic extensibility framework. Because data continues to be processed while a device is offline, your mobile scenarios remain rich and fluid, even if devices don’t have constant network connectivity. 

## Data management and data entities
Data from Finance and Operations can easily be integrated with Microsoft and non-Microsoft data sources using the common data service, Power Apps, and Power BI. For more information, see [Data entities](data-entities\data-entities.md).

## Office integration
The Microsoft Office integration capabilities provide users with a productive environment that helps them get the job done by using Office products. For more information, see [Office integration](office-integration/office-integration.md).
