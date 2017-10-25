---
# required metadata

title: Integrate the Retail SDK with the Dynamics 365 Unified Operations platform build definition using Visual Studio Team Services
description: This article describes the steps for merging the build systems for both Dynamics 365 for Finance and Operations, Enterprise edition, and Dynamics 365 for Retail using Visual Studio Team Services.  
author: andreash1
manager: AnnBe
ms.date: 09/19/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: AX 7.0.0, Operations, Retail, UnifiedOperations
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: andreash
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---

# Integrate the Retail SDK with the continuous build system (VSTS)

[!include[banner](../../includes/banner.md)]

This article describes the steps for merging the build systems for both Dynamics 365 for Finance and Operations, Enterprise edition, and Dynamics 365 for Retail. The Lifecycle Services (LCS)-integrated build experience supports both code upgrades and new projects. The Retail SDK is a self-contained MSBuild-based build system. Many customizers want to make productive changes in both Microsoft Dynamics 365 for Finance and Operations and Retail components. This article outlines the manual steps for merging both build systems using Visual Studio Team Services. 

## Enable the build system

To get started, you must follow all the steps to get a full continuous build system up and running. For information, see [Developer topology deployment with continuous build and test automation](../../../dev-itpro/perf-test/continuous-build-test-automation.md). After deployment, you create the build definition and build steps. Build at least one time, so that you become familiar with it and are sure that you can build without errors. Then move to the next step.

## Prepare the Retail SDK
### Getting the Retail SDK
If you don't already have the Retail software development kit (SDK) in the same Microsoft Visual Studio Team Services (VSTS) project, add it now. You will find the Retail SDK in any developer or build topology. Follow the branching documentation in [Retail SDK overview](retail-sdk-overview.md). We recommend that you create your Retail SDK mirror and your Retail SDK customization branch at this time. After your Retail SDK customization branch is ready, and it has been submitted in the same VSTS project as Retail, you can start.

## Add a repository mapping for the Retail SDK
Edit the build definition so that it includes the location of the Retail SDK. (In other words, add a map.) [![Adding a repository mapping for the Retail SDK](./media/build-map-addition.png)](./media/build-map-addition.png)

## Add a new build step to build the Retail SDK
Add a new step at the beginning of the build pipeline, as shown in the following screen shot. [![Adding a new build step to build the Retail SDK](./media/new-build-step-1024x527.png)](./media/new-build-step.png)

## Add a copy step for binaries from the Retail SDK to the Retail  build
This build step enables Microsoft to copy the latest built Retail binaries to the Retail bin folder, if Microsoft shares files/binaries. Make sure that you complete this step immediately after you add a build step for the Retail SDK, as described in the previous section. [![Adding a copy step for binaries from the Retail SDK to the Dynamics 365 for Retail build](./media/binary-drop-to-ax.png)](./media/binary-drop-to-ax.png)

## Add a copy step for all Retail packages
Make sure that this step occurs after the “PowerShell: Generate packages” step (see image below). Here are the arguments.

    -BuildPackagePath "$(Agent.BuildDirectory)\Packages" -BuildVersion "$(Build.BuildNumber)"

[![Adding a copy step for all Retail packages](./media/package-drop-1024x473.png)](./media/package-drop.png)

## Optional: Referencing a Retail DLL from Retail
You must complete this task only if you must add built Retail binaries to the Retail package. In this case, you must follow these three steps:

1.  Use a normal AXReference in your Retail project.
2.  Add the corresponding AXReference folder and the XML file inside it to VSTS.
3.  Update the Copy-RetailBinaries.ps1 file with the appropriate file commands to get the binary file from the Retail SDK to the Retail bin folder. The Microsoft Windows PowerShell file includes a sample that copies the PricingEngine.dll file into the ApplicationSuite bin folder. Depending on the modules that you're building, the files and folders must be changed so that they are in a different location.
