---
title: Introduction to Commerce Scale Unit (CSU) Core
description: This article provides an introduction to Commerce Scale Unit (CSU) Core in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 07/17/2024
ms.topic: how-to
audience: Developer
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: aneesa
ms.search.validFrom: 2022-03-30
ms.custom: 
  - bap-template
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

CSU Core is available for new deployments as of the Dynamics 365 Commerce version 10.0.22 release. As of the Commerce version 10.0.22 release, all new deployments use it by default. On-premises or CSU self-hosted installers use the same CSU Core platform that is built by using ASP.NET core and that runs on .NET Core.

## Deploy or migrate to CSU Core

CSU Core offers highly performant headless commerce APIs and the benefits of .NET Core. 

> [!WARNING]
> Using or relying on outbound Internet Protocol (IP) addresses for cloud-hosted CSUs isn't supported. IP addresses can change at any time and shouldn't be used as a stable identifier of network traffic. Dependence on any IP value for cloud-hosted CSUs might negatively impact your environment.

### Migrate your existing Microsoft-hosted CSU to CSU Core

The following instructions describe how to switch an existing CSU deployment from the legacy .NET Framework to .NET Core. 

> [!IMPORTANT]
> You can only migrate to CSU Core if your extensions are compatible with the Commerce SDK, or .NET Standard 2.0/.NET 6.

To migrate your existing Microsoft-hosted CSU to CSU Core, follow these steps. 

1. Sign in to [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com). 
1. On the LCS page where you manage CSUs, select **Update**.
1. In the **Update** dialog box, set the **Disable CSU Core** option to **No**.
1. Select **Update**.

> [!NOTE]
> - By default, Commerce SDK objects are already configured to use .NET 6.
> - New CSU deployments on Commerce version 10.0.38 and later have the **Disable CSU Core** option set to **No** by default. The option can't be set to **Yes**.
> - If you are running Commerce version 10.0.37 and earlier and your extensions are still using the Retail SDK or aren't compatible with .NET Standard 2.0/.NET 6, you are allowed to set the **Disable CSU Core** option to **Yes**. However, if you want to update your CSU to Commerce version 10.0.38 or later, you must set this option to **No** after ensuring that your extensions are compatible with the Commerce SDK.
> - The switch to CSU Core doesn't require you to run the **Commerce Initialize** function or execute the **9999** job after switching.

### Extensions

If you plan to create extensions for headless commerce, it must be built by using .NET Standard 2.0 as the target framework.

#### Validate your extension compatibility with CSU Core

You can validate that your extensions are compatible with CSU core by running an extension test. To run a test, append the query parameter `healthcheck?testname=extensions` to your Retail Server URL, as shown in the following example that uses **\<MyRetailServerURL\>** to represent the Retail Server URL.

`https://<MyRetailServerURL>/healthcheck?testname=extensions`

The test results contain a table that shows the status of compatible and incompatible extensions.

#### Extension target framework

| Extension component | Extension project target framework | Commerce SDK |
|--- | --- | --- |
| Headless commerce APIs | .NET Standard 2.0 | Version 10.0.23 or later |
| Commerce runtime (CRT) | .NET Standard 2.0 | Version 10.0.23 or later |

#### Migrate extensions to support CSU Core

To run in CSU Core, extensions that were built by using the Retail SDK must be built using .NET Standard 2.0 as the target framework. The CSU Core runtime is built by using the ASP.NET Core and .NET Core. Therefore, extensions that were created by using the legacy .NET framework and Retail SDK packages don't run in CSU Core. If you're using the Retail SDK, Microsoft highly recommends that you [Migrate the Retail SDK extensions to Commerce SDK](retail-sdk/migrate-commerce-sdk.md). Commerce SDK supports CSU core out of the box.

