---
title: Getting started with POS extensions
description: This topic explains how to create a POS extension development environment and get started with POS extensions.
author: mugunthanm
ms.date: 04/13/2021
ms.topic: article
audience: Developer
ms.reviewer: rhaertle
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 04-13-2020
ms.dyn365.ops.version: AX 10.0.18
---

# Getting started with POS extensions

[!include [banner](../../../includes/banner.md)]

This topic explains how to create a POS extension development environment and get started with POS extensions. This topic applies to Retail software development kit (SDK) version 10.0.18 and later.

## Independent POS extension model

POS allows extension through the SDK that lets you independently develop, deploy, and service the extension. After an extension is created, the extension can use the installer package to create the extension installer to deploy the extensions. The installer is idempotent after any changes or enhancements are made to the extension. Just create the installer and run it to deploy the extensions.

Extension installers are independent from the core POS installer. They are separate and are packaged differently. The advantage is that extensions and the core POS can be independently serviced. Also, the POS framework supports multiple extension installers. Extensions from ISVs, partners, and customers can all be independently installed and serviced.

The independent POS extension model is supported ny Dynamics 365 Commerce application version 10.0.18 and later. In earlier versions, extensions and the core POS code are packaged as one installer and serviced together, therefore, you can’t independently deploy extension and core POS changes.

The POS independent extension model isolates the extension from the out-of-box component using the Windows Optional package framework for MPOS and POS extension framework for CPOS. The other app types use the CPOS extension model because the Store Commerce app in Microsoft Dynamics 365 Commerce, Hybrid iOS app, and Android app are shells (wrapper) that host the CPOS.

## Getting started with POS extension

Depending on your store topology, choose the POS application type. The extension developed for one POS app type can be used in other POS app types. If your extension has a dependency on the POS application type, then it can’t be used in another application type. We recommend that you try to avoid such dependencies during extension development.

## Set up the POS development environment

### Prerequisites

+ Windows 10 1809 or newer or Windows Server 2019 for Modern POS.
+ Visual Studio 2017 Community, Professional, or Enterprise with the following workloads and components:
+ Visual Studio workloads
    + Visual Studio core editor (usually selected by default)
    + .NET desktop development
    + Desktop development with C++ (POS)
    + Universal Windows Platform development (POS)
    + [ASP.NET](http://asp.net/)  and web development
    + Azure development
    + Node.js Development (POS)
    + .NET Core cross-platform development
+ Visual Studio components. These can be selected during Visual Studio installation.
    + C# and Visual Basic Roslyn compilers
    + MSBuild
    + TypeScript 4.0 SDK
    + VC++ version 15.8+ latest v141 tools
    + Visual C++ ATL for x86 and x64
    + Visual C++ MFC for x86 and x64
    + Windows 10 SDK (10.0.17763.0)
+ .NET Framework/SDK
    + [.NET Core 3.1](https://dotnet.microsoft.com/download/dotnet/3.1)
    + [.NET Framework 4.7.2](https://dotnet.microsoft.com/download/dotnet-framework/thank-you/net472-developer-pack-offline-installer) 
+ SQL Server Express 2016 local channel database. (Required only for offline deployments).
+ SQL Server Data Tools
+ Git for Windows (Source control management).

## Develop a POS extension

Download the SDK and sample source code from the [POS GitHub repo](https://github.com/microsoft/Dynamics365Commerce.InStore/tree/release/9.28/src/PosSample/Pos.Extension).

To develop your first extension, use the existing samples from GitHub or follow the step-by-step guide to create the extension.

## GitHub sample

To use the sample, clone the **release** branch samples from the GitHub repo and follow the steps in the GitHub readme file. To compile, build, and debug, follow the steps in Debug POS extension section.

## Custom extensions

To create your own extension, follow the steps in [Create a POS extension package project](create-pos-extension-package.md).

To debug your extension, follow the steps in [Debug a POS extension](debug-pos-extension.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
