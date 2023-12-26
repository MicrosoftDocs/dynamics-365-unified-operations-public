---
title: Upgrade the Retail channel extension to the latest Retail SDK
description: This article explains how to upgrade the commerce channel extension from earlier releases to the latest update of the Retail SDK.
author: josaw1
ms.date: 05/03/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 209/07/2018
ms.dyn365.ops.version: AX 7.3.5
ms.assetid: 72a63836-2908-45fa-b1a6-3b1c499a19a2
---

# Upgrade the Retail channel extension to the latest Retail SDK

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/retail-sdk-deprecation-banner.md)]

This article provides information about how to upgrade to the latest update of the Retail SDK from earlier releases. The overall process and the supported scenario information are included, but this article doesn’t provide detailed instructions of every step in the process. This article is applicable for Dynamics 365 Commerce and Dynamics 365 Finance.


The following sections will walk through how to manually move your extension to the new Retail SDK, however you can do this using any source control system like Azure DevOps or Git.

## Update the Retail SDK
If you deploy a new environment, the new Retail SDK is located in the services volume of the virtual machine (VM) or in the C drive of the downloadable VHD. When you update the Retail SDK by applying a new binary hotfix from Lifecycle Services (LCS), a new **Update** folder is created inside the existing RetailSDK folder and a copy of the new updated SDK is created inside the Update folder with name {{Guid.RetailSDKUpdate.Date}}. We recommend that you rename this folder using a shorter name otherwise when copying this folder you may get an error saying the path or file name is too long.

### Retail SDK components

The Retail SDK updates consist mainly of the following components:

-   Assets: Configuration file changes related to extensions.
-   Build tools: Customization package and versioning settings.
-   Database: Extension DB scripts.
-   Documents: Instructions to run the samples.
-   Package: Deployment package.
-   Payment externals: Payment packaging folders.
-   Payment: Payment sample code.
-   POS: Store Commerce code and samples.
-   References: All binary reference and commerce analyzer proxy tool.
-   Sample extensions: Extension sample projects.

## Upgrade scenarios
Upgrade can be completed for one of the following scenarios:

  - Update to a specific binary hotfix.
  - Upgrade your custom code.
  - Upgrade to the latest application release.

The process for SDK upgrade varies between versions. With version 7.3 and higher, we sealed all of the components and customizations must be completed only by using the extension points. This should result in an easier code upgrade experience. However, if you are upgrading from 7.0, 7.1, or 7.2 and if you have made inline changes, you must move the inline changes to extensions. This will require additional work.

> [!NOTE] 
> When upgrading to newer version, do not remove any of the existing Commerce Scale Unit, Commerce Runtime, Proxy, Hardware station, CDX, or Database extension code/APIs. Your POS client may depend on this code and removing it will cause runtime exception errors. If you want to remove it then during code upgrade, make sure that the client code is also updated to support this change, otherwise runtime failure will occur. As a best practice, extension code must be written in such a way that it is always backward compatible.

The following tables provide some high-level information about which version the code is sealed. If you are upgrading from an unsealed version to a sealed version, you should identify all of your customizations and move any inline customizations to extensions. To move the inline customizations, verify that you have all of the necessary extension points to do this. If you don't, submit an extensibility request. 

> [!NOTE]
> You might have to rewrite some of the POS inline changes that were completed in 7.1 when you upgrade to version 7.3 or higher.

| Application version                     | CRT sealed     | HWS sealed     | POS sealed     | DB sealed     | Proxy sealed |
|-----------------------------------------|----------------|----------------|----------------|---------------|-------------------------|
| Application release 8.1                 | Yes            | Yes            | Yes            | Yes           | Yes                     |
| Application release 8.0                 | Yes            | Yes            | Yes            | Yes           | Yes                     |
| Application 7.3                         | Yes            | Yes            | Yes            | Yes           | Yes                     |
| July 2017 release (Application 7.2)     | Yes            | Yes            | Yes            | Yes           | No                      |
| Release 1611 (Application 7.1)          | Yes            | No             | No             | No            | No                      |
| February 2016 release (Application 7.0) | No             | No             | No             | No            | No                      |

## Upgrade the channel extension from 7.3 to a higher version

If you are completing a code upgrade, the following Retail SDK components must be upgraded. Each of these components are folders inside the Retail SDK.

> [!NOTE]
> Code upgrade can be completed using a source control/merge tool. We recommend using a source control tool for this process so that you can track the changes and revert if required. If you are not using any source control, before you upgrade the code, be sure to make a back up of the old and new Retail SDK folder.

- **Assets:** If you have modified any of the following extension config files to include your custom assemblies, you must move those changes to the same config files in the new **Asset folder**.

  - CommerceRuntime.Ext.config - CRT extensions.
  - CommerceRuntime.MPOSOffline.Ext.config - CRT offline extensions.
  - HardwareStation.Extension.config - Hardware station and payment extensions.
  - RetailProxy.MPOSOffline.ext.config - Proxy extensions.

- **Build tools:** The **Build tools** folder contains the files related to packaging, build settings and pfx, and snk files. Merge or update the following files if you have made any changes in the older versions:

  - Customization.settings
  - Microsoft.Dynamics.RetailSdk.Build.props
  - Any custom pfx or snk files that you have created.

- **Database:** Copy and drop all your custom SQL scripts: ...\\RetailSDK\\Database\\Upgrade\\Custom

- **Online Store:** If you have an online store web project or online extension code, include it in this folder. 
  > [!NOTE]
  > Deployable package will not include online store code for packaging.

- **Payment externals**: Copy and paste all of your payment extension assemblies to the following **Payment assemblies** folders:

  - IPaymentDeviceAssemblies
  - IPaymentProcessorAssemblies
  - PaymentWebFiles

- **Payments:** Merge all of your payment extension projects into this folder.

  > [!NOTE]
  > If you created a new payment extension project and did not modify anything in this folder, you can include it as part of the build and packaging process. Update **dirs.proj** in the **RetailSDK** folder to build your custom project. Next, update the **Customization.settings** file with the payment extension drop location so that during package creation your custom project is built. Make sure to include the extension as part of the packaging.

- **POS:** If you have any POS extensions, including the generated proxy, copy your POS extensions from *…\\RetailSDK\\POS\\Extensions* to the new Retail SDK POS extension folder, *RetailSDK\\POS\\Extensions*. After you copy the extensions,  update and merge the extension.json file inside the *POS\\Extensions* folder with the new POS extensions folder you copied.

  For example, if you copied the **CustomExtension** folder, then you would update extension.json as shown below.

  ```typescript
   {
   "extensionPackages": [
   {
     "baseUrl": "SampleExtensions"
   },
   {
    "baseUrl": "SampleExtensions2"
   },
   {
    "baseUrl": "CustomExtension"
   }
  ]
   }
  ```
 
 You should also update tsconfig.json with the custom extension package so that the POS can compile the changes during build.

- **Reference:** Copy all of your extension output assemblies, such as **Commerce runtime**, **Hardware station**, **proxy**, and any external assemblies, to the reference folder. Include any assemblies that you want included as part of your deployment and packaging.

- **Commerce runtime (CRT) and Commerce Scale Unit extensions:** Copy all of your CRT and extension projects under the **Retail SDK** folder. Make sure to include the CRT and RS extension solution file details in the dirs.proj file under the **RetailSDK folder** so that during msbuild, all of the extension project is built and the output path for the project assemblies is set to the *RetailSDK\\Reference* folder.

- **Hardware station (HWS) and payment extensions:** Copy all of your hardware station (HWS) and payment extension projects under the **Retail SDK** folder. Make sure to include the HWS and payment extension solution file details in the dirs.proj file under the **RetailSDK** folder so that during msbuild, all of the extension projects are built and the output path for the project assemblies is set to the *RetailSDK\\Reference* folder.

- **Retail proxy extensions:** Copy all of your proxy extension projects under the **Retail SDK** folder. Make sure to include the proxy solution file details in the dirs.proj file under the **RetailSDK** folder so that during msbuild, all of the extension projects are built and the output path for the project assemblies is set to the *RetailSDK\\Reference* folder.

> [!NOTE]
> Run **msbuild** on the root of the Retail SDK folder. Use the Microsoft Visual Studio developer command-line tool to generate the  deployable packages.

After you have upgraded all of the components, deploy the Commerce deployable packages, validate the deployment, and add the Retail SDK files to the repository.

## Upgrade the channel extension from 7.2 to a higher version
The steps mentioned  in the previous section, **Upgrade the channel extension from 7.3 to higher versions**, will remain same for all the components except the Commerce proxy. In 7.2, you must have completed inline changes in the proxy project if you have CRT with RS extension and the typescript proxy was auto-generated based on the **customization.settings** file.

To upgrade your proxy to 7.3, complete the steps in the article, [Typescript and C# proxies for Retail point of sale (POS)](typescript-proxy-retail-pos.md) and then move the proxy to the Retail SDK folder and then update the config file, **RetailProxy.MPOSOffline.ext.config**.

## Upgrade the channel extension from 7.1 to a higher version
In 7.1, you should have completed most of the POS and Proxy customizations inline. To upgrade to higher a application release, you should move all of your inline changes to extensions. If it is a binary hotfix upgrade, then you must perform a code merge with the new Retail SDK and then regenerate the package.

## Upgrade the channel extension from 7.0 to a higher version
In 7.0, you should have completed most of the customizations inline. To upgrade to higher a application release, you should move all of your inline changes to extensions. If it is binary hotfix upgrade, you must perform a code merge with the new Retail SDK and regenerate the package.

## Generate a deployable package for validation
Complete the steps in the article, [Create deployable packages](retail-sdk/retail-sdk-packaging.md), to generate the deployable package for validation.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
