---
title: Upgrade the Retail channel extension to the latest Retail SDK
description: Learn how to upgrade the Commerce channel extension from earlier releases to the latest update of the Retail SDK.
author: josaw1
ms.date: 02/19/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 09/07/2018
ms.assetid: 72a63836-2908-45fa-b1a6-3b1c499a19a2
ms.custom: 
  - bap-template
---

# Upgrade the Retail channel extension to the latest Retail SDK

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/retail-sdk-deprecation-banner.md)]

This article provides information about how to upgrade to the latest update of the Retail software development kit (SDK) from earlier releases. The overall process and the supported scenario information are included, but this article doesn't provide detailed instructions for every step in the process. This article applies to Dynamics 365 Commerce and Dynamics 365 Finance.

The following sections explain how to manually move your extension to the new Retail SDK. However, you can use any source control system, such as Azure DevOps or Git.

## Update the Retail SDK

If you deploy a new environment, you can find the new Retail SDK in the services volume of the virtual machine (VM) or in the C drive of the downloadable Virtual hard disk (VHD). When you update the Retail SDK by applying a new binary hotfix from Microsoft Lifecycle Services (LCS), the process creates a new **Update** folder inside the existing RetailSDK folder. The process also creates a copy of the new updated SDK inside the Update folder with the name {{Guid.RetailSDKUpdate.Date}}. Rename this folder by using a shorter name. Otherwise, when copying this folder, you might get an error saying the path or file name is too long.

### Retail SDK components

The Retail SDK updates mainly consist of the following components:

- **Assets**: Configuration file changes related to extensions.
- **Build tools**: Customization package and versioning settings.
- **Database**: Extension DB scripts.
- **Documents**: Instructions to run the samples.
- **Package**: Deployment package.
- **Payment externals**: Payment packaging folders.
- **Payment**: Payment sample code.
- **POS**: Store Commerce code and samples.
- **References**: All binary reference and commerce analyzer proxy tool.
- **Sample extensions**: Extension sample projects.

## Upgrade scenarios

You can upgrade for one of the following scenarios:

- Update to a specific binary hotfix.
- Upgrade your custom code.
- Upgrade to the latest application release.

The process for SDK upgrade varies between versions. By using version 7.3 and higher, you seal all of the components and complete customizations only by using the extension points. This approach results in an easier code upgrade experience. However, if you're upgrading from 7.0, 7.1, or 7.2 and you made inline changes, you must move the inline changes to extensions. This change requires extra work.

> [!NOTE]
> When upgrading to a newer version, don't remove any of the existing Commerce Scale Unit, Commerce Runtime, Proxy, Hardware station, CDX, or Database extension code or APIs. Your POS client might depend on this code, and removing it causes runtime exception errors. If you want to remove it, make sure that the client code is also updated to support this change. Otherwise, runtime failure occurs. As a best practice, always write extension code to be backward compatible.

The following tables provide high-level information about which version the code is sealed. If you're upgrading from an unsealed version to a sealed version, identify all your customizations and move any inline customizations to extensions. To move the inline customizations, verify that you have all the necessary extension points. If you don't, submit an extensibility request.

> [!NOTE]
> You might need to rewrite some of the POS inline changes that you made in 7.1 when you upgrade to version 7.3 or higher.

| Application version                     | CRT sealed     | HWS sealed     | POS sealed     | DB sealed     | Proxy sealed |
|-----------------------------------------|----------------|----------------|----------------|---------------|-------------------------|
| Application release 8.1                 | Yes            | Yes            | Yes            | Yes           | Yes                     |
| Application release 8.0                 | Yes            | Yes            | Yes            | Yes           | Yes                     |
| Application 7.3                         | Yes            | Yes            | Yes            | Yes           | Yes                     |
| July 2017 release (Application 7.2)     | Yes            | Yes            | Yes            | Yes           | No                      |
| Release 1611 (Application 7.1)          | Yes            | No             | No             | No            | No                      |
| February 2016 release (Application 7.0) | No             | No             | No             | No            | No                      |

## Upgrade the channel extension from 7.3 to a higher version

If you're upgrading code, you must upgrade the following Retail SDK components. Each of these components is a folder inside the Retail SDK.

> [!NOTE]
> You can complete the code upgrade by using a source control or merge tool. Use a source control tool for this process so that you can track the changes and revert if needed. If you're not using any source control, back up the old and new Retail SDK folders before you upgrade the code.

- **Assets:** If you modified any of the following extension config files to include your custom assemblies, move those changes to the same config files in the new **Asset folder**.

  - CommerceRuntime.Ext.config - CRT extensions.
  - CommerceRuntime.MPOSOffline.Ext.config - CRT offline extensions.
  - HardwareStation.Extension.config - Hardware station and payment extensions.
  - RetailProxy.MPOSOffline.ext.config - Proxy extensions.

- **Build tools:** The **Build tools** folder contains the files related to packaging, build settings, and pfx and snk files. Merge or update the following files if you made any changes in the older versions:

  - Customization.settings
  - Microsoft.Dynamics.RetailSdk.Build.props
  - Any custom pfx or snk files that you created.

- **Database:** Copy and drop all your custom SQL scripts to `...\RetailSDK\Database\Upgrade\Custom`.

- **Online Store:** If you have an online store web project or online extension code, include it in this folder.
  > [!NOTE]
  > The deployable package doesn't include online store code for packaging.

- **Payment externals**: Copy and paste all of your payment extension assemblies to the following **Payment assemblies** folders:

  - IPaymentDeviceAssemblies
  - IPaymentProcessorAssemblies
  - PaymentWebFiles

- **Payments:** Merge all of your payment extension projects into this folder.

  > [!NOTE]
  > If you created a new payment extension project and didn't modify anything in this folder, you can include it as part of the build and packaging process. Update **dirs.proj** in the **RetailSDK** folder to build your custom project. Next, update the **Customization.settings** file with the payment extension drop location so that during package creation your custom project is built. Make sure to include the extension as part of the packaging.

- **POS:** If you have any POS extensions, including the generated proxy, copy your POS extensions from *…\\RetailSDK\\POS\\Extensions* to the new Retail SDK POS extension folder, *RetailSDK\\POS\\Extensions*. After you copy the extensions,  update and merge the extension.json file inside the *POS\\Extensions* folder with the new POS extensions folder you copied.

  For example, if you copied the **CustomExtension** folder, then you update extension.json as shown in the following example.

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

After you upgrade all of the components, deploy the Commerce deployable packages, validate the deployment, and add the Retail SDK files to the repository.

## Upgrade the channel extension from 7.2 to a higher version

The steps described in the previous section, **Upgrade the channel extension from 7.3 to higher versions**, apply to all components except the Commerce proxy. In version 7.2, you must make inline changes in the proxy project if you have CRT with RS extension and the TypeScript proxy was autogenerated based on the **customization.settings** file.

To upgrade your proxy to version 7.3, follow the steps in [TypeScript and C# proxies for Retail point of sale (POS)](typescript-proxy-retail-pos.md). Then, move the proxy to the Retail SDK folder and update the config file, **RetailProxy.MPOSOffline.ext.config**.

## Upgrade the channel extension from 7.1 to a higher version

In version 7.1, you complete most of the POS and Proxy customizations inline. To upgrade to a higher application release, move all of your inline changes to extensions. If you're upgrading a binary hotfix, perform a code merge with the new Retail SDK and then regenerate the package.

## Upgrade the channel extension from 7.0 to a higher version

In version 7.0, you complete most of the customizations inline. To upgrade to a higher application release, move all of your inline changes to extensions. If you're upgrading a binary hotfix, perform a code merge with the new Retail SDK and regenerate the package.

## Generate a deployable package for validation

Follow the steps in [Create deployable packages](retail-sdk/retail-sdk-packaging.md) to generate the deployable package for validation.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
