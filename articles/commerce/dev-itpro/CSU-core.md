---
title: Introduction to Commerce Scale Unit (CSU) Core
description: This topic explains about Commerce Scale Unit (CSU) Core.
author: mugunthanm
ms.date: 03/30/2022
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 03-30-2022
ms.dyn365.ops.version: AX 10.0.25
---

# Introduction to Commerce Scale Unit (CSU) Core

[!include [banner](../includes/banner.md)]

CSU Core is the next generation high performance platform offered by the Dynamics 365 Commerce to hosts the headless commerce engine. CSU Core provides the same functionality as the existing Commerce Scale Unit but highly optimized and performant using ASP.NET Core and runs using the .NET Core. 

### Why CSU Core?
CSU Core is built using the ASP.NET Core, which is a cross platform, high performance framework.

**CSU Core provides the following benefits:**
- Better API performance when compared to the existing Commerce Scale Unit.
- Runs on .NET Core and uses .NET version 6.
- Backward compatible with extensions built using the Commerce SDK, .NET 6, and Visual studio 2022.

### CSU Core Release plan
CSU Core will be available for new deployment starting Dynamics 365 Commerce application release version 10.0.22 and later and starting application release version 10.0.26 and later all new deployment will be defaulted to CSU Core. 
On-prem or the CSU self-hosted installers will also use the same CSU Core platform built using ASP.NET core and runs on .NET Core. 

### Deploy or migrate to CSU Core
CSU Core offers high performant headless Commerce APIs and the benefits of .NET Core. To migrate your CSU hosted by Microsoft to the CSU Core or to deploy new instance of CSU Core contact the Dynamics 365 Commerce support team and extension must be build using the supported .NET framework. 

Extensions:
If you planning to create extensions for headless Commerce, it must be built using following target frameworks and .NET 6 or later and .NET 6 development is supported only in Visual studio version 2022 or later:

#### Extension Target framework

| Extension Component | Extension project target framework | Commerce SDK |
| ------ | ------ | ------ |
| Headless Commerce APIs | NET Standard 2.0 | Version 10.0.23 or later |
| Commerce Runtime | NET Standard 2.0 | Version 10.0.23 or later |		


#### Migrate Extensions to support CSU Core
Extension built using the Retail SDK must be migrated to the Commerce SDK to run in CSU core, CSU Core runtime is built using the ASP .NET Core and .NET Core so extension created using the legacy .NET framework and Retail SDK packages will not run in CSU Core. Follow the steps documented here to [migrate the Retail SDK extensions to Commerce SDK](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-sdk/migrate-commerce-sdk). 
