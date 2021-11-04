---
title: Migrate to the Commerce SDK
description: This topic explains how to migrate to the Commerce SDK.
author: mugunthanm
ms.date: 11/02/2021
ms.topic: article
audience: Developer
ms.reviewer: rhaertle
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 02-11-2021
ms.dyn365.ops.version: AX 10.0.19
---

# Migrate to the Commerce SDK

[!include [banner](../../includes/banner.md)]

## Overview

The Commerce SDK and sealed installers simplify the Commerce developer and upgrade experience. The new Commerce SDK minimizes the effort involved to upgrade and reduces the time and effort spent on the upgrade process. It brings the .NET development experience to the Commerce SDK with integration to Git, Azure DevOps, and Visual Studio Code.

The main difference between the Commerce SDK and the legacy Retail SDK is that extensions can be developed and deployed independently. This process reduces the upgrade and deployment time and the new sealed installers separate the extension from the base installers. As a result, the base and extension installers can be independently installed and serviced, you don't need a code merge or combined packaging.

In the Retail SDK, to develop a Point of Sale (POS) extension you would need the Core POS app projects and extensions must use these projects to develop extensions. If there are multiple ISV, partner, or customers extensions involved, then all of the different extensions must be merged to the core POS app extension project. The project is integrated into one build pipeline to generate the combined package or installers that include the core POS app and the extension. If the new Microsoft upgrade for POS is available, then the extensions must be merged with the Core POS app to generate the combined installers. This process is time consuming, involves development effort, and must be repeated for every upgrade.

The Commerce SDK and sealed installers solve the preceding problem by isolating the base app and extensions. Extensions can be developed independently by consuming the packages available in the public feed. Extensions don’t need any of the core POS app or core classes from Commerce runtime or Retail Server.

An extension can be developed as an add-in. It can be developed independently and deployed, using the new sealed installer framework. Extensions can create their own headless installers for extension code and multiple extensions can be installed separately, except for Cloud Scale Unit - Microsoft hosted extension packages. In a self-hosted Cloud Scale unit (CSU), multiple extensions can be independently installed and deployed.

The Commerce SDK samples and packages are published on [GitHub](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/tree/release/9.33/src/ScaleUnitSample) and on a [public feed](https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/nuget/v3/index.json) for easier consumption. You don't need to access Lifecycle Services (LCS) to get the latest update. Downloading the latest update of the SDK through LCS can take several hours, but with this new approach downloading the latest SDK or packages is only a few steps. The GitHub repo is a sample repo, you don't have to clone the repo to create your extension development. All extensions can be develops by consuming the packages from the public feed.

## Benefits of the Commerce SDK

The Commerce SDK provides these benefits:

- A seamless update experience. The core application and extensions can be independently updated without a code merge. No need to update extensions to update the core applications. This new process reduces the time spent on update.
- Improved performance. If extensions are migrated to the Commerce SDK and .NET Standard 2.0, then the CSU can be upgraded to the new ASP.NET Core 3.1, which provides better API performance.
- Extensions are published to GitHub and public feed. You can download the SDK in minutes instead of hours.
- The new sealed installers are headless (there is no user interface). Sealed installers work great for mass deployment.
- Separate headless installers for extensions using the new installer framework.
- Automated packaging and configuration of Commerce runtime and Hardware station extensions for Modern POS.
- Improved build times.
- Improved developer experience. CSU extensions can be developed using Visual Studio Code, Git for source code management, and Azure DevOps for build automation.

## Comparison between the Commerce and Retail SDKs

| Components | Commerce SDK (new) | Retail SDK (legacy) |
| ------ | ------ |-----------------------|
| Samples | Samples are published in GitHub | Samples are published in the Retail SDK\Sample extension folder.|
| How to get the SDK | Available in GitHub and Public feed. | Available in LCS development virtual machine. |
| Packages or reference libraries | Packages are published to the public feed and can be consumed via NuGet.| Reference libraries and packages required for Commerce development are available in the Retail SDK `/Pkgs` folder.|
| Deployable package | Separate packages and installers for Cloud and on-prem components. No need to update any config files for extensions. Config files are autogenerated. Packages can be generated by consuming the packages in the public feed. No dependency with any samples/projects in GitHub.| One combined deployable package and you must update several config files to generate the package.|
| Installers | Separate installers for Core apps and extensions. Uses the new sealed installer framework to generate the installers. Works only with the new sealed installer. Installers can be generated by consuming the packages in the public feed. No dependency with any samples/projects in GitHub. | Combined installers for extensions and core app. For example, there is one combined Modern POS installer for Core POS and extensions.|
| Build pipeline | Sample YAML files are available in GitHub to set up the pipeline, but the Commerce SDK is designed to work with your own Azure DevOps pipeline setup. | Based on the `dirs.proj` file available in the Retail SDK. |
| Update | To update the extensions, consume the latest package available in the public feed. | Must be done from LCS. LCS update process must be followed.|

## Brief steps for migration

1. Set up your [local development environment](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/blob/release/9.33/src/ScaleUnitSample/Readme.md) or configure the [LCS development environment](../../../fin-ops-core/dev-itpro/dev-tools/access-instances.md).
2. Uninstall the Modern POS, Hardware Station, and Cloud Scale Unit - Self-hosted, which were installed using the old installers. Install the required application using the [new sealed installers](https://community.dynamics.com/ax/b/axforretail/posts/introducing-sealed-installers).
3. Migrate the Commerce runtime, API, channel database, Proxy, POS, and HWS extensions using the Commerce SDK.

    Most of the code written using the old SDK can be migrated easily, and you do not need to rewrite the code. For example, the Commerce runtime extension can be updated by changing the project to **NET standard 2.0** and updating the reference package to be consumed from the public feed. Similarly, the API extension can be updated by using new interface and removing the **EDMModel** extender code because it's automated in the backend.

4. Package the extensions for Cloud or On-prem using the new [installer](https://community.dynamics.com/ax/b/axforretail/posts/introducing-sealed-installers) and [packaging framework](retail-sdk-packaging.md#deployable-package-types).
5. Deploy the extensions.

## How to migrate

### Developer environment changes

The LCS 10.0.21 developer virtual machine (VM) doesn't have Visual studio 2017. Manually install Visual Studio 2017 and the dependencies as documented in the "Prerequisites" section of [Retail software development kit (SDK)](retail-sdk-overview.md#prerequisites), or set up a local development environment. We recommend the [local development environment](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/blob/release/9.33/src/ScaleUnitSample/Readme.md). In the future, Commerce components will not be available in the LCS VM. Either you can manually install those components in the LCS dev VM or use your own local development machine.

### Commerce Runtime extensions

Commerce runtime extensions, consumes the packages or reference libraries from the Retail SDK\Pkgs folder but in the Commerce SDK all the required packages are published to this [public feed](https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/nuget/v3/index.json) and CRT samples are available for reference in the [GitHub](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/tree/release/9.33/src/ScaleUnitSample).

Your extension code must use the packages from the public feed instead of the Retail `SDK\Pkgs` folder and you must update the project to NET standard 2.0. No changes should be required on the core business logic or contracts if you followed the best practices. The packages in the public feed will not have any services or workflow classes. Your extension must not consume these classes.

Edit your project file and manually add the package reference or use the NuGet manager to consume the packages, as shown in the following XML example:

```xml
<PackageReference Include="Microsoft.Dynamics.Commerce.Sdk.Runtime" Version="$(CommerceSdkPackagesVersion)" />
```

Packages available in the public feed for extension to consume can be found on [GitHub](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/blob/release/9.33/README.md).

#### Why we made this change to Commerce Runtime extensions

This new implementation simplifies the upgrade and development process. To download the latest version of the packages, choose the version from your package management solution like NuGet instead of using LCS to upgrade the SDK, which can take several hours.

Commerce extension development for CRT is more streamlined and follows the standard .NET development best practices.

### Retail Server or Headless Commerce API extensions

In older versions of Retail SDK extensions, you have to consume the packages from the Retail `SDK\Pkgs` folder and extend from the `CommerceController` class to create new API extensions. Using the Commerce SDK, an extension uses the packages from the public feed and extends the API controller class from the `IController` interface. For more information, see [Create a Retail Server extension API (Retail SDK version 10.0.11 and later)](../retail-server-icontroller-extension.md).

#### Why we made this change to the API extensions

With this change, there is no need to create `EdmModel` factory and extender, it was complex for the extensions to add these and set appropriate attributes now all the EDM process is automated and no need to generate separate offline proxy library for Modern POS, the API extension library can be used directly in the offline and the proxy generation process is simplified.

### Channel Database

No changes are required in the offline database scripts created for extensions, but you must create a channel database project and include the script in it for packaging. The sample project can be found on [GitHub](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/tree/release/9.33/src/ScaleUnitSample/ChannelDatabase).

### Offline

Previously you have to create separate Modern POS C# proxy library to consume the API and Commerce Runtime extensions but with the new API extension model, you can directly use the Headless Commerce API.

### Hardware Station (HWS)

In older versions of Retail SDK extension, you have to use the packages from the Retail `SDK\Pkgs` folder and extend from the `HardwareStationController` class to create new HWS extensions. Using the Commerce SDK, an extension must use the packages from the public feed and extend the HWS controller class by using the `IController` interface. For more information, see [Integrate the POS with a new hardware device and generate the extension installer](../hardware-device-extension.md).

### New sealed installers

The new sealed installers are available from LCS for download by navigating to **LCS > Shared Asset library >  Retail Self-service package**, or to the [Shared Asset Library](https://lcs.dynamics.com/V2/SharedAssetLibrary). The legacy installers or the apps (Modern POS, Hardware Station, Cloud Scale Unit - Self-hosted) must be uninstalled before installing the new sealed installers. The Commerce SDK for POS will work only with the sealed installers.

### POS

We've made a few improvements in the Commerce SDK to the POS extension development process that will require changes when migrating existing extensions. Below is a summary of the most important changes to know. For a complete list of changes and steps to migrate an extension, see [https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/pos-extension/migrate-pos-extension](../pos-extension/migrate-pos-extension.md)

| Change | Description | Purpose |
|---|---|---|
| Removal of POS app Code from the SDK | In older versions of the Retail SDK, the POS extension solution contains both Microsoft-developed code and the extensions. In the Commerce SDK, we have changed this model so that the extension solutions only include the POS extensions code. | This change simplifies the update process by removing the need for a code merge, and it enables the POS main package to be updated independently from the extension packages. It also enables POS to support multiple extension packages without a code merge. |
| POS API updates | In addition to the packaging changes we made a two changes to the POS API. The first change is that we removed the all references to `knockout.js` from the POS public contracts. This change included enabling an extension's user interface to use common POS controls through a new set of APIs under `PosApi/Consume/Controls`. With the availability of these new APIs, the `Pos.UI.Sdk` library is now obsolete, and it is not found in the Commerce SDK. The second key change was the introduction of a simplified API to create custom views. | The change to remove `knockout.js` library references from the POS public contracts enables us to iterate and improve on the POS control implementations without the risk of breaking any extensions. This is especially key as the upgrade process will no longer require recompiling the POS main package and extensions together. This does not mean that extensions cannot use `knockout.js`, and we have documented how to use `knockout.js` with the Commerce SDK. For more information, see  [Consume external or third party libraries like Knockout.js in POS extensions](../pos-extension/knockout-pos-extension.md). |

### Build pipeline

To set up the build pipeline for the Commerce SDK, see [Set up a build pipeline for the independent-packaging SDK](../build-pipeline.md). YAML and script files are added as a sample to simplify the build pipeline setup, and steps are added to use the certificate from Azure Key Vault and sign the build artifacts.

### Package Deployment

A new packaging type is added to separate the self-service components from the Cloud Scale unit extensions (CSU). The new ScaleUnit Package will only contain the CSU components.  The self-service components can be uploaded to LCS using the build pipeline or manually and synced to the back office.

If you use the Retail SDK to generate the package, then you must update the `Customization.Settings` file and the extension config files. In the Commerce SDK packaging all these steps are automated, you don't have to include or update these configuration files.

For more information, see [Generate a separate package for Commerce Cloud Scale Unit (CSU)](retail-sdk-packaging.md#generate-a-separate-package-for-commerce-cloud-scale-unit-csu).

### FAQ

#### Do I have to migrate?

The Commerce SDK provides several benefits when compared to the Retail SDK, including a simplified development and update experience, and improved performance. The Retail SDK and installers will be deprecated in October 2022, and all extensions must be migrated before this date. The Retail SDK will not be shipped or supported after October 2022.

#### When do I have to migrate?

Extensions must be migrated to the new Commerce SDK and new installers by October 2022.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
