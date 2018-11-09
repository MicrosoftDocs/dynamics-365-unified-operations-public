---
# required metadata

title: Upcoming chnages in Retail SDK
description: This topic contains a list of upcoming changes in Retail SDK.
author: mugunthanm 
manager: AnnBe
ms.date: 11/o9/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
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
# Upcoming changes in Retail SDK
[!include [banner](../includes/banner.md)]

We planned set of new features to simplify the development and servicing process for the retail channel customization. To uptake some of this new feature planned you may require you to upgrade, recompile or do some minor code changes in the extension you built (no changes would be required on the extension logic files or manifest you created but changes would be required in moving your extension files to this new templates, packaging model, recompile to map to the new reference model and development IDE. We are publishing this ahead of the release so that you can plan and be prepared to uptake this new change. Below is the list of new features planned for the Retail SDK enhancement which will require some work from your side before your uptake these features:

## Independent package:
We are developing a new feature called independent packaging model which helps to separate the extensions from the core and service independently and we will also be planning to support separate packages by extensions in the future. When there is ISV solutions and partner extensions, now both can be packaged separately and serviced.  There is no need to combine ISV solution and partner extensions. 
For Modern POS to support this new packaging model we are changing the POS framework to support Windows optional package extension model. There will not be any change on how extensions are developed, but changes will be done in the packaging and deployment. With this new model all modern POS extensions will be created as separate appx files and core POS will load these appx files as add-ins and it will run under the core modern POS app identity. Previously the core POS and extensions were packaged as one appx now there will be core appx and extension add-ins appx so that developers can independently service your extension appx alone. The extensions developed will work for both Cloud POS and Modern POS, the template may be different, but the code is shared between both.

> [!NOTE] 
> When you uptake the new feature, changes are required on the extension you previously built. You will need to move your extension files to the new project type in a separate package and then complete a configuration update. No change is required on the extension logic files or the manifest you created. However, you need to move your extension logic(files) and manifest to the new template and then rebuild, test, and validate.

## Development tools:
Currently the Retail SDK samples and other templates inside the Retail SDK works only with VS 2015, to support some of the upcoming changes in the Retail SDK and the new independent package model we are planning to upgrade the Visual studio (VS) from VS 2015 to either VS 2017 or the latest. **The new templates and Retail SDK samples will only compile in VS 2017 or the other supported latest version. So please plan to upgrade the VS from VS 2015 to VS 2017 in your dev VMs when we release this new feature.**

## Retail SDK reference to NuGet Gallery:
All the reference binaries for CRT, RS, Retail proxy, commerce tool etc. are published inside the Retail SDK\Reference folder and your extension so far was referencing from this folder but soon we are planning to go away from this model and publish the SDK references in NuGet gallery. **With this new model you should change your extension project to refer the NuGet gallery instead of the Retail SDK\reference folder this will require reference update and recompilation in your extension project.**
This will simplify the update process, Ex: Currently if you need any updated reference in the Retail SDK you need to go LCS, apply the latest binaries updates etc. now with the NuGet approach you can just right click and get the updated version.

## Retail packaging tool:
We are making some enhancement in the channel installers to support installing only the extensions. We will provide option either you can choose to install as one combined installer (core + all extensions) or extension and core separately.

## Retail SDK sample to GitHub:
We are planning to move the samples from Retail SDK to GitHub, since these are published only as sample code it will not have any impact in your extensions. With the GitHub you can get any latest samples easily instead of going through the LCS process.
