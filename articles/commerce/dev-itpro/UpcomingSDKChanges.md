---
# required metadata

title: Upcoming changes in the Retail SDK
description: This topic contains a list of upcoming changes in the Retail software development kit (SDK).
author: mugunthanm 
manager: AnnBe
ms.date: 02/22/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: mumani
ms.search.validFrom: 2018-09-11
ms.dyn365.ops.version: AX 8.0, AX 8.1

---
# Upcoming changes in the Retail SDK
[!include [banner](../includes/banner.md)]

In a future release of Dynamics 365 Commerce, a new set of features is planned to simplify the development and servicing process for commerce channel customization. To uptake some of these features, you may need to upgrade, recompile, or do some minor code changes in the extensions that you've built. No changes will be required in the extension logic files or manifest that you've created. However, you will have to move your extension files to the new templates, update the packaging model, and recompile Commerce runtime, proxy, and Commerce Scale Unit extensions to map to the new library reference model and integrated development environment (IDE).

Microsoft is publishing this topic before the new features are released, so that you can plan and prepare to uptake them.

Here is the list of new features that are planned for enhancement of the Retail software development kit (SDK), and that will require some work on your side before you uptake them.

## Independent packaging model
Microsoft is developing a new feature that is named the *independent packaging model*. This packaging model helps separate the extensions from the core and services independently. Microsoft plans eventually to support separate packages for extensions too. If there are independent software vendor (ISV) solutions and partner extensions, they can be packaged and serviced separately. ISV solutions and partner extensions no longer have to be combined. 

To enable Retail Modern POS to support this new packaging model, Microsoft is changing the point of sale (POS) framework so that it supports the Microsoft Windows optional package extension model. The way that extensions are developed won't change. Only the way that extensions are packaged and deployed will change. In the new model, all Modern POS extensions will be created as separate .appx files. Core POS will load those files as add-ins, and it will run under the core Modern POS app identity. Previously, core POS and extensions were packaged as one .appx file. Now, there will be .appx files for both core and extension add-ins, so that developers can independently service just your extension .appx files. The extensions that are developed will work for both Cloud POS and Modern POS. Although the template might differ, the code is shared between both apps.

> [!NOTE] 
> When you uptake the new feature, changes are required in the extensions that you previously built. You must move your extension files to the new project type in a separate package and then complete a configuration update. No change is required in the extension logic files or the manifest that you created. However, you must move your extension logic files and manifest to the new template, and then rebuild, test, and validate them.

Independent package model development is not supported in Windows server operating system or LCS development box, you must use your own Windows 10 box. 

## Prerequisites

- Visual Studio 2017, version 15.1
- Windows 10, version 1703
- Windows 10, version 1703 SDK

## Development tools
Currently, the Retail SDK samples and other templates inside the Retail SDK work only with Microsoft Visual Studio 2015. To support some of the upcoming changes in the Retail SDK and the new independent packaging model, Microsoft is planning to upgrade from Visual Studio 2015 to either Microsoft Visual Studio 2017 or the latest version.

The new templates and Retail SDK samples can be compiled only in Visual Studio 2017 or the latest supported version. **Therefore, you should plan to upgrade from Visual Studio 2015 to Visual Studio 2017 on your development virtual machines (VMs) when this new feature is released.** **Starting 10.0.11, Retail SDK components can be developed and compiled only in VS 2017, it will not work in VS 2015.**


## Retail SDK reference folder to NuGet Gallery
All the reference binaries for the Commerce runtime, Commerce Scale Unit, Commerce proxy, commerce tool, and so on, are published in the Retail SDK\\Reference folder. Currently, your extensions reference that folder. However, Microsoft is planning to move away from this model and publish the SDK references in the NuGet Gallery instead. **Therefore, for this new model, you should change your extension project so that it references the NuGet Gallery instead of the Retail SDK\\reference folder. This change will require a reference update and recompilation in your extension project.**

This new model will simplify the update process. For example, if you require any updated references in the Retail SDK, you must currently go to Microsoft Dynamics Lifecycle Services (LCS), apply the latest binaries updates, and so on. In the NuGet approach, you can just right-click to get the updated version.

## Commerce packaging tool
The channel installers are being enhanced so that you can use them to install just the extensions. You will be able to decide whether to use one combined installer for core and all extensions, or whether to install extensions and core separately.

## Retail SDK samples to GitHub
Microsoft is planning to move the samples from the Retail SDK to GitHub. Because the samples are published only as sample code, this change won't affect your extensions. GitHub makes it easy to get the latest samples. You will no longer have to go through the LCS process.
