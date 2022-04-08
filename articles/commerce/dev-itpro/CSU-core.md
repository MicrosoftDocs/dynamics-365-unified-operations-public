---
title: Introduction to Commerce Scale Unit (CSU) Core
description: This topic provides an introduction to Commerce Scale Unit (CSU) Core in Microsoft Dynamics 365 Commerce.
author: mugunthanm
ms.date: 04/08/2022
ms.topic: article
audience: Developer
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 03-30-2022
ms.dyn365.ops.version: AX 10.0.25
---

# Introduction to Commerce Scale Unit (CSU) Core

[!include [banner](../includes/banner.md)]

This topic provides an introduction to Commerce Scale Unit (CSU) Core in Microsoft Dynamics 365 Commerce.

Commerce Scale Unit (CSU) Core is the next generation high performance platform offered by Dynamics 365 Commerce to host the headless commerce engine. CSU Core provides the same functionality as the existing Commerce Scale Unit but is highly optimized and performant because it uses ASP.NET Core and .NET Core. 

## Why CSU Core? 

CSU Core is built using the ASP.NET Core, which is a cross platform, high performance framework.

CSU Core provides the following benefits:
- Better API performance when compared to the existing Commerce Scale Unit.
- Runs on .NET Core and uses .NET version 6.
- Backward compatible with extensions built using the Commerce software development kit (SDK), .NET 6, and Visual Studio 2022.

## CSU Core release plan

CSU Core is available for new deployments starting with the Dynamics 365 Commerce version 10.0.22 release, and starting with Commerce version 10.0.22 release all new deployments will default to using CSU Core. On-premises or CSU self-hosted installers will also use the same CSU Core platform built using ASP.NET core and that runs on .NET Core. 

## Deploy or migrate to CSU Core

CSU Core offers high performant headless Commerce APIs and the benefits of .NET Core. To migrate your CSU hosted by Microsoft to the CSU Core or to deploy a new instance of CSU Core, contact the Dynamics 365 Commerce support team for help building an extension that uses the supported .NET framework. 

### Extensions

If you plan to create extensions for headless commerce, it must be built using following target frameworks and .NET 6 or later. .NET 6 development is only supported in Visual Studio version 2022 or later.

#### Extension target framework

| Extension Component | Extension project target framework | Commerce SDK |
| ------ | ------ | ------ |
| Headless commerce APIs | NET Standard 2.0 | Version 10.0.23 or later |
| Commerce runtime (CRT) | NET Standard 2.0 | Version 10.0.23 or later |		

#### Migrate extensions to support CSU Core

Extensions built using the Retail SDK must be migrated to the Commerce SDK to run in CSU Core. The CSU Core runtime is built using the ASP .NET Core and .NET Core so extensions created using the legacy .NET framework and Retail SDK packages will not run in CSU Core. For more information, see [Migrate the Retail SDK extensions to Commerce SDK](retail-sdk/migrate-commerce-sdk.md). 
