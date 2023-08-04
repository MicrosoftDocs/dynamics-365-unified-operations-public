---
title: Introduction to Commerce Scale Unit (CSU) Core
description: This article provides an introduction to Commerce Scale Unit (CSU) Core in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 04/27/2022
ms.topic: article
audience: Developer
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2022-03-30
ms.dyn365.ops.version: AX 10.0.25
---

# Introduction to Commerce Scale Unit (CSU) Core

[!include [banner](../includes/banner.md)]

This article provides an introduction to Commerce Scale Unit (CSU) Core in Microsoft Dynamics 365 Commerce.

CSU Core is the next-generation, high-performance platform that Dynamics 365 Commerce offers to host the headless commerce engine. CSU Core provides the same functionality as the existing CSU, but it's highly optimized and performant because it uses ASP.NET Core and .NET Core.

## Why CSU Core?

CSU Core is built by using ASP.NET Core, which is a cross-platform, high-performance framework.

CSU Core provides the following benefits:

- It has better application programming interface (API) performance than the existing Commerce Scale Unit.
- It runs on .NET Core and uses .NET version 6.
- It's backward compatible with extensions that were built by using the Commerce software development kit (SDK), .NET Standard 2.0, and Visual Studio 2022.

## CSU Core release plan

CSU Core is available for new deployments as of the Dynamics 365 Commerce version 10.0.22 release. As of the Commerce version 10.0.22 release, all new deployments will use it by default. On-premises or CSU self-hosted installers will use the same CSU Core platform that is built by using ASP.NET core and that runs on .NET Core.

## Deploy or migrate to CSU Core

CSU Core offers highly performant headless commerce APIs and the benefits of .NET Core. To migrate your Microsoft-hosted CSU to CSU Core, or to deploy a new instance of CSU Core, contact the Dynamics 365 Commerce support team for help building an extension that uses the supported .NET framework.

### Extensions

If you plan to create extensions for headless commerce, it must be built by using NET Standard 2.0 as the target framework.

#### Validate your extension compatibility with CSU Core

You can validate that your extensions are compatible with CSU core by running an extension test. To run a test, append the query parameter **healthcheck?testname=extensions** to your Retail Server URL, as shown in the following example that uses **\<MyRetailServerURL\>** to represent the Retail Server URL.

`https://<MyRetailServerURL>/healthcheck?testname=extensions`

The test results will contain a table that shows the status of compatible and non-compatible extensions.

#### Extension target framework

| Extension component | Extension project target framework | Commerce SDK |
|--- | --- | --- |
| Headless commerce APIs | NET Standard 2.0 | Version 10.0.23 or later |
| Commerce runtime (CRT) | NET Standard 2.0 | Version 10.0.23 or later |

#### Migrate extensions to support CSU Core
To run in CSU Core, extensions that were built by using the Retail SDK must be built using NET Standard 2.0 as target framework. The CSU Core runtime is built by using the ASP .NET Core and .NET Core. Therefore, extensions that were created by using the legacy .NET framework and Retail SDK packages won't run in CSU Core.  If you are on Retail SDK, its highly recommended that you [Migrate the Retail SDK extensions to Commerce SDK](retail-sdk/migrate-commerce.sdk.md). Commerce SDK supports CSU core out of the box.

