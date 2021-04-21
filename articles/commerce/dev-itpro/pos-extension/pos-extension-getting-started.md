---
# required metadata

title: POS extension getting started
description: This topic explains how to setup POS extension development environment and getting started with POS extensions.
author: mugunthanm
ms.date: 04/13/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
# ms.tgt_pltfrm: 
ms.custom: 28021
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 04-13-2020
ms.dyn365.ops.version: AX 10.0.18

---

# POS extension Getting started 

[!include [banner](../includes/banner.md)]

This topic explains how to setup POS extension development environment and getting started with POS extensions, this topic applies to Retail software development kit (SDK) version 10.0.18 and later.

## Independent POS extension model:

POS exposes the SDK for extension to independently to develop the extension, deploy and service it. After the extensions are created, extension can use the installer package to create the extension installer to deploy the extensions, the installer is idempotent after any changes/enhancements to the extension, create installer and run it to deploy the extensions.

Extension installers are independent from the core/base POS installer both are separate and packaged differently, this gives advantage for extensions and core POS to be independently serviced and packages. Also, the POS framework supports multiple extension installers, if there is an ISV, Partner, Customer extensions all can be independently installed and serviced.

The independent POS extension model is supported from Dynamics 365 Commerce application version 10.0.18 and later, in earlier versions extension and core POS code are packages as one installer and serviced together, you can’t independently deploy extension and core POS changes both must be combined.

The POS independent extension model isolates the extension from the OOB component using the Windows Optional package framework for MPOS and POS extension framework for CPOS. The Other app types uses the CPOS extension model because the Store Commerce, Hybrid iOS and Android app is a shell which hosts the CPOS.

## Getting started with POS extension:

Depends on your Store topology, choose the right POS application type. The extension developed for one POS app type can be used in other POS application type, if your extension has some dependency with the POS application type then it can’t be used in the other application type (try to avoid such dependencies during extension development).

## Setup the POS development environment:

**Prerequisites**

Operating Systems: Windows 10 1809 or newer or Windows Server 2019 for Modern POS.
**Visual Studio:** Visual Studio 2017 Community, Professional or Enterprise with the following workloads and components:

**VS Workloads:**
- Visual Studio core editor (usually selected by default)
- .NET desktop development
- Desktop development with C++ (POS)
- Universal Windows Platform development (POS)
- [ASP.NET](http://asp.net/)  and web development
- Azure development
- Node.js Development (POS)
- .NET Core cross-platform development

**VS Individual Components:** (This can be selected during the VS installation).
- C# and Visual Basic Roslyn compilers
- MSBuild
- TypeScript 4.0 SDK
- VC++ version 15.8+ latest v141 tools
- Visual C++ ATL for x86 and x64
- Visual C++ MFC for x86 and x64
- Windows 10 SDK (10.0.17763.0)

**.NET Framework/SDK:**
-  [.NET Core 3.1](https://dotnet.microsoft.com/download/dotnet/3.1) 
- [.NET Framework 4.7.2](https://dotnet.microsoft.com/download/dotnet-framework/thank-you/net472-developer-pack-offline-installer) 

- SQL Server Express 2016 local channel database. (Required only for offline deployments).
- SQL Server Data Tools
- Git for Windows (Source control management).

## Develop POS Extensions:

Get the SDK and sample source code from the [POS GitHub repo](https://github.com/microsoft/Dynamics365Commerce.InStore/tree/release/9.28/src/PosSample/Pos.Extension). 

To develop your first extension, use the existing samples from GitHub or follow the step-by-step guide to create the extension.

**GitHub Samples:**
To use the existing sample, clone the release branch samples from the GitHub and follow the steps mentioned in the GitHub readme file to compile and build and to debug follow the steps mentioned in Debug POS extension section.

**Custom extensions:**
To create your own extension, follow the steps mentioned in the [Creating a POS extension package project doc](pos-extension-package.md).

Follow the steps mentioned in [Debug POS extensions document](Debugging-pos-extension.md) to debug the POS extension.