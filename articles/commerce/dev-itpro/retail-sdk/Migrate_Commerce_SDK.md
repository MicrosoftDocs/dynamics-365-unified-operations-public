---
# required metadata

title: Migrate to Commerce SDK
description: This topic explains how to migrate to the Commerce SDK.
author: mugunthanm
ms.date: 11/02/2021
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
ms.search.validFrom: 02-11-2021
ms.dyn365.ops.version: AX 10.0.19

---

# Migrate to Commerce SDK

## Overview

The Commerce SDK and sealed installers simplify the Commerce developer and upgrade experience, with the new Commerce SDK the effort involved to upgrade is greatly minimized and it will reduce the time and effort spent on the upgrade process and brings the .NET development experience to the Commerce SDK with integration to Git, Azure DevOps, VS code etc. 

The big difference between the  Commerce SDK and the legacy Retail SDK is extensions can be developed and deployed independently, this will reduce the upgrade and deployment time and the new Sealed installers separates the extension from the base installers, so base and extension installers can be independently installed and serviced, no need of any code merge or combined packaging.

In the legacy SDK, to develop POS extension you would need the Core POS app projects and extensions must use these projects to develop extensions and if there is multiple ISVs, partners or customers extension are involved then all of the different extensions must be merged to the core pos app extension project and integrated in one build pipeline to generate the combined package or installers which includes the core POS app and the extensions and if new Microsoft upgrade for POS available then extensions must be merged with the Core POS app to generate the combined installers and this process is time consuming and involves development effort and this has to be repeated for every upgrade.

The new SDK and sealed installers solves the above problem by isolating the base app and extensions. Now extension can be independently developed by consuming the packages available in the public feed, extensions don’t need any of the core POS app, core classes from Commerce runtime or Retail Server to develop extensions. 

Extensions can be developed as add-ins, and it can be independently developed and deployed, using the new Sealed installer framework extensions can create their own headless installers for extensions code and multiple extensions can be installed separately, except for Cloud Scale Unit - Microsoft hosted extension packages. In Self hosted Cloud Scale unit, multiple extensions can be independently installed and deployed.

The new SDK samples and packages are published [GitHub](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/tree/release/9.33/src/ScaleUnitSample) and [public feed](https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/nuget/v3/index.json) for easier consumption, so no need of LCS to get the latest update, getting the latest update of SDK through LCS process takes multiple hours but with this new approach getting the latest SDK or packages is few clicks. The GitHub repo is just a sample repo, you don't have to clone the repo to do your extension development, all extension can be done by consuming the packages from the public feed.

## Benefits of new SDK:

### Why should I migrate:

- Seamless update experience, core application and extensions can be independently updated without any code merge. No need to update extensions to update the core applications. This will reduce the time spent on update.
- Improved performance, if extensions are migrated to the new SDK and .NET Standard 2.0 then CSU can be upgraded to the new ASP. Net Core 3.1 which provides better API performance.
- Extensions are published to GitHub and public feed, so no need of LCS to get the SDK updates which will take multiple hours, SDK updates can be done in minutes.
- The new Sealed installers are headless, there is no UI, Sealed installers works great for Mass deployment.
- Separate headless installers for extensions using the new installer framework.
- Automated packaging and configuration of Commerce runtime and Hardware station extensions for Modern POS.
- Improved build times.
- Improved Dev experience, extensions can now use VS Code for CSU extensions, Git for Source code management and Azure DevOps for build automation.

## Comparison between Old and New SDK

| Components | README | Legacy Retail SDK |
| ------ | ------ |-----------------------|
| Samples | Samples are published in GitHub | Samples are published in the Retail SDK\Sample extension folder.|
| How to get the SDK | Available in GitHub and Public feed. | Available in LCS development VM |
| Packages or reference libraries | Packages are published to the public feed and can be consumed vis NuGet.| Reference libraries and packages required for commerce development is available in the Retail SDK /Pkgs folder.|
| Deployable package | Separate packages and installers for Cloud and on-prem components. No need to update any config files for extensions, config files are auto generated. Package can be generated by consuming the packages in the public feed, no dependency with any samples/projects in GitHub.| One combined deployable package and must update different config files to generate the package.|
| Installers | Separate installers for Core apps and extensions. Uses the new Sealed installer framework to generate the installers. New Commerce SDK will work only with the new Sealed installer. Installers can be generated by consuming the packages in the public feed, no dependency with any samples/projects in GitHub. | Combined installers for extensions and core app. Ex: One combined Modern POS installer for Core POS and extensions.|
| Build pipeline | Sample YAML files are available in GitHub to setup the pipeline but the new SDK is designed to work with your own Azure DevOps pipeline setup. | Based on the dirs.proj file available in the Retail SDK |
| Update | To update the extensions consume the latest package available in the public feed. | Must be done from LCS, LCS update process must be followed.|

## Brief steps for Migration:

1. Setup your [local development environment](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/blob/release/9.33/src/ScaleUnitSample/Readme.md) or configure the [LCS development environment.](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/dev-tools/access-instances)
2. Uninstall the Modern POS, Hardware Station and Cloud Scale Unit - Self hosted, installed using the old installers and install the required application using the [new Sealed installers.](https://community.dynamics.com/ax/b/axforretail/posts/introducing-sealed-installers)
3. Migrate the Commerce runtime, API, channel database, Proxy, POS and HWS extensions using the new Commerce SDK. 
	
	Most of the code written using the old SDK can be easily migrated, no need rewrite the code. Ex: Commerce runtime extension can be updated by changing the project to >NET standard 2.0 and updating the reference package to be consumed form the public feed. Similarly API extension can be updated to use the new interface and by removing the EDMModel extender code because its automated in the backend. 
4. Package the extensions for Cloud or On-prem using the new [installer](https://community.dynamics.com/ax/b/axforretail/posts/introducing-sealed-installers) and [packaging framework.](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-sdk/retail-sdk-packaging#deployable-package-types)
5. Deploy the extensions.


## How to migrate

### Dev environment changes

The LCS 10.0.21 dev VM doesn't have Visual studio 2017, manually install the Visual Studio 2017 and dependencies as documented [here](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-sdk/retail-sdk-overview#prerequisites) or Setup a local development environment, we recommend to use the [local development environment.](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/blob/release/9.33/src/ScaleUnitSample/Readme.md) In the future, Commerce components will not be available in the LCS VM, either you can manually install those components in the LCS dev VM or use your own local development machine.

### Commerce Runtime extensions

Commerce runtime extensions, consumes the packages or reference libraries from the Retail SDK\Pkgs folder but in the new SDK all the required packages are published to this [public feed](https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/nuget/v3/index.json) and CRT samples are available for reference in the [GitHub.](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/tree/release/9.33/src/ScaleUnitSample) 

Extension code must consume the packages from the public feed instead of the Retail SDK\Pkgs folder and update the project to NET standard 2.0. Update your extension project to consume the packages from the public feed instead of the Retail SDK\Folder.  No changes should be required on the core business logic/contracts if you followed the best practices. The packages in the public feed will not have any services or workflow classes and extension must not consume these classes.

Edit your project file and manually add the package reference or use the NuGet manager to consume the packages.
 <PackageReference Include="Microsoft.Dynamics.Commerce.Sdk.Runtime" Version="$(CommerceSdkPackagesVersion)" />

Packages available in the public feed for extension to consume can be found [here.](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/blob/release/9.33/README.md)

**Why we made this change**

This simplifies the upgrade and development process, to get the latest version of the packages just chose version from your package management solution like NuGet instead of using LCS to upgrade the SDK which takes multiple hours.

The Commerce extension development for CRT is more streamlined to follow the standard .NET development best practices.
 
### Retail Server or Headless Commerce APIs
 
In older versions of Retail SDK extension you have to consume the packages from Retail SDK\Pkgs folder  and extended from CommerceController class to create new API extensions but in the new SDK extension must consume the packages from the public feed as mentioned in Commerce Runtime extensions sections and extend the API controller class from IController interface. Please follow this document on how to [create new API extension.](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-server-icontroller-extension)

**Why we made this change**

With this changes there is no need to create EdmModel factory and extender, it was complex for the extensions to add these and set appropriate attributes now all the EDM process is automated and no need to generate separate offline proxy library for Modern POS, the API extension library can be used directly in the offline and the proxy generation process is simplified. 

### Channel Database
No changes required in the offline database scripts created for extensions but create channel database project and include the script in it for packaging. The sample project can be found [here.](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/tree/release/9.33/src/ScaleUnitSample/ChannelDatabase)
 
### Offline

Previously you have to create separate Modern POS C# proxy library to consume the API and Commerce Runtime extensions but with the new API extension model, you can directly use the Headless Commerce API.

### Hardware Station (HWS)

In older versions of Retail SDK extension you have to consume the packages from Retail SDK\Pkgs folder  and extended from HardwareStaiotn Controller class to create new HWS extensions but in the new SDK extension must consume the packages from the public feed as mentioned in Commerce Runtime extensions sections and extend the HWS controller class from IController interface. Please follow this document on how to [create new HWS extension.](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/hardware-device-extension)


### New Sealed installers:

The new sealed installers are available in [LCS > Shared Asset library >  Retail Self-service package](https://lcs.dynamics.com/V2/SharedAssetLibrary) for download. The Old installers or the apps (Modern POS, Hardware Station, Cloud Scale Unit - Self hosted) must be uninstalled before installing the new Sealed installers and new Commerce SDK for POS will work only with the Sealed installers.

### POS
In the new Commerce SDK we've made a few improvements to the POS extension development process that will require changes when migrating existing extensions. Below is a summary of the most important changes to know, and a complete list of changes and steps to migrate an extension can be found in the documentation [here.](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/pos-extension/migrate-pos-extension)

**Removal of POS App Code from the SDK**
In older versions of the Retail SDK the POS extension solutions contains both Microsoft developed code and the extensions, in the new Commerce SDK we have changed this model so that the extension solutions will only include the POS extensions code. 

**Why we made this change**
This will greatly simplify the update process by removing the need for any code merge, and it enables the POS main package to be updated independently from the extension packages. It also enables POS to support multiple extension packages without requiring any code merge.

#### PosApi Updates
In addition to the packaging changes we made a two changes to the POS API. The first change is that we removed the all references to knockout.js from the POS public contracts. This included enabling extensions UI to use common POS controls through a new set of APIs under PosApi/Consume/Controls. With the availability of these new APIs the Pos.UI.Sdk library is now obsolete and we have removed it in the Commerce SDK. The second key change was the introduction of a simplified API to create custom views.

**Why we made these changes**
The change to remove knockout library references from the POS public contracts enables us to iterate and improve on the POS control implementations without the risk of breaking any extensions. This is especially key as the upgrade process will no longer require recompiling the POS main package and extensions together. This does not mean that extensions cannot use knockout.js, and we have documented how to use knockout.js with the Commerce SDK [here.](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/pos-extension/knockout-pos-extension)

### Build pipeline

To setup the build pipeline for the Commerce SDK, follow this [document.](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/build-pipeline) YAML and scripts files are added as sample to simplify the build pipeline setup, steps added to use the certificate from Azure Key Vault and sign the build artifacts.

### Package Deployment
New packaging type added to separate the Self-service components from the Cloud Scale unit extensions (CSU), the new ScaleUnit Package will only contain the CSU components.  The self-service components can be uploaded LCS using the build pipeline or manually and synced to the back office.

In the legacy SDK to generate the package you must update the Customization.Settings and the extension config files but in the new SDK packaging all these steps are automated, you don't have to include/update these config files.

Steps to generate the new CSU package is documented [here.](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-sdk/retail-sdk-packaging#generate-a-separate-package-for-commerce-cloud-scale-unit-csu) 

### Resources

### FAQ

#### Do I have to migrate
The new Commerce SDK provides lot of benefits when compared to the legacy SDK, simplified development  and update experience, improved performance etc. The legacy SDK and installers are getting deprecated in October 2022, all extensions must be migrated before this date. The legacy SDK will not be shipped or supported after October 2022.

#### By when should migrate

Extensions must be migrated to the new Commerce SDK and installers by October 2022.
