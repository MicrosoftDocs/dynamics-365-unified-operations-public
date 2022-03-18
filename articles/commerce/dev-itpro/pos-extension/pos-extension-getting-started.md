---
title: Getting started with POS extensions
description: This topic explains how to create a Point of Sale (POS) extension development environment and get started with POS extensions.
author: mugunthanm
ms.date: 04/13/2021
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.custom: "intro-internal"
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 04-13-2020
ms.dyn365.ops.version: AX 10.0.18
---

# Getting started with POS extensions

[!include [banner](../../includes/banner.md)]

This topic explains how to create a Point of Sale (POS) extension development environment and get started with POS extensions. It applies to version 10.0.18 and later of the Retail software development kit (SDK).

## Independent POS extension model

POS allows for extension through the SDK. Therefore, you can independently develop, deploy, and service extensions. After an extension is created, it can use the installer package to create the extension installer that deploys the extensions. The installer is idempotent after any changes or enhancements are made to the extension. Just create the installer, and then run it to deploy the extensions.

Extension installers are independent of the core POS installer. They are separate and are packaged differently. The advantage is that extensions and the core POS can be independently serviced. Additionally, the POS framework supports multiple extension installers. Extensions from independent software vendors (ISVs), partners, and customers can be independently installed and serviced.

The independent POS extension model is supported by Microsoft Dynamics 365 Commerce application version 10.0.18 and later. In earlier versions, extensions and the core POS code are packaged as one installer and serviced together. Therefore, you can't independently deploy extension changes and core POS changes.

The POS independent extension model isolates an extension from the out-of-box component by using the Windows Optional package framework for Modern POS (MPOS) and the POS extension framework for Cloud POS (CPOS). The other app types use the CPOS extension model, because the Store Commerce app in Dynamics 365 Commerce, the iOS hybrid app, and the Android hybrid app are shells (wrappers) that host CPOS.

## Get started with POS extensions

Depending on your store topology, select the POS app type. In general, an extension that was developed for one POS app type can be used for other POS app types. However, if your extension has a dependency on the POS app type, it can't be used for another POS app type. We recommend that you try to avoid dependencies of this type during extension development.

## Set up the POS development environment

### Prerequisites

+ Windows 10 1809 or later, or Windows Server 2019 for MPOS
+ Visual Studio 2017 Community, Professional, or Enterprise that has the following workloads and components:

    + Visual Studio workloads:

        + Visual Studio core editor (usually selected by default)
        + .NET desktop development
        + Desktop development with C++ (POS)
        + Universal Windows Platform (UWP) development (POS)
        + [ASP.NET](http://asp.net/) and web development
        + Azure development
        + Node.js development (POS)
        + .NET Core cross-platform development

    + Visual Studio components. These components can be selected during Visual Studio installation.

        + C# and Visual Basic Roslyn compilers
        + MSBuild
        + TypeScript 4.0 SDK
        + Visual C++ version 15.8+ latest v141 tools
        + Visual C++ ATL for x86 and x64
        + Visual C++ MFC for x86 and x64
        + Windows 10 SDK (10.0.17763.0)

+ The .NET Framework/SDK

    + [.NET Core 3.1](https://dotnet.microsoft.com/download/dotnet/3.1)
    + [.NET Framework 4.7.2](https://dotnet.microsoft.com/download/dotnet-framework/thank-you/net472-developer-pack-offline-installer)

+ SQL Server Express 2016 local channel database (required only for offline deployments)
+ SQL Server Data Tools
+ Git for Windows (source control management)

## Develop a POS extension

Download the SDK and sample source code from the [POS GitHub repository (repo)](https://github.com/microsoft/Dynamics365Commerce.InStore/tree/release/9.28/src/PosSample/Pos.Extension).

To develop your first extension, use the existing samples from GitHub. Alternatively, follow the step-by-step guide to create the extension.

## GitHub sample

To use the sample, clone the **release** branch samples from the GitHub repo, and follow the steps in the GitHub readme file.

## Custom extensions

To create your own extension, follow the steps in [Create a POS extension package project](create-pos-extension-package.md).

To debug your extension, follow the steps in [Debug POS extensions](debug-pos-extension.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
