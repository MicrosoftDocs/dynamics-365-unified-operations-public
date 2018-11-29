---
# required metadata

title: How to upgrade Retail channel extension to the latest Retail SDK
description: This topic explains the process of upgrading the retail channel extension from earlier releases to the latest update of Retail SDK. 
author: mugunthanm
manager: AnnBe
ms.date: 11/28/2018
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
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 68673
ms.assetid: 72a63836-2908-45fa-b1a6-3b1c499a19a2
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 209/07/2018
ms.dyn365.ops.version: AX 7.3.5

---

# How to upgrade Retail channel extension to the latest Retail SDK

[!include [banner](../includes/banner.md)]

**Retail SDK upgrade:**

This topic explains the process of upgrading from earlier releases to the latest update of Retail SDK. It describes the overall process and the supported scenarios but doesn’t provide detailed instructions of every step of the process and this topic is applicable for Dynamics 365 for Retail and Dynamics 365 for Finance and Operations 7.3 version and higher, we will walkthrough how to manually move your extension to the new Retail SDK, but you can do this using any source control system like VSTS or Git.

Update Retail SDK:
------------------

When you update the Retail SDK by applying a new binary hotfix, we create a new **Update** folder inside the existing RetailSDK folder and copy the updated SDK. Or if you deploy a new environment you should be able to find the new RetailSDK in that VM in services volume or in C drive for downloadable VHD.

**Retail SDK components:**

Retail SDK updates consist mainly of the following components:

-   Assets - Configuration files changes related to extensions.

-   Build tools – Customization package and versioning settings.

-   Database – Extension DB scripts.

-   Documents – Instructions to run the samples.

-   Package – Deployment package.

-   Payment Externals – Payment packaging folders.

-   Payment – Payment sample code.

-   POS – Modern and Cloud POS App code and samples.

-   References – All binary reference and commerce analyzer proxy tool.

-   SampleExtensions – Extension sample projects.

**Introduction to the upgrade scenarios:**

  - Update to a specific binary hotfix.
  - Upgrade your custom code.
  - Upgrade to the latest application release.

The process for SDK upgrade varies between different version, starting form 7.3 and higher versions we sealed all the Retail components and customization must be done only using the extension points, so code upgrade should be easy. But if you are upgrading from 7.0 or 7.1 and if you have done inline changes then you must move the inline changes to extensions, this should require some additional work:

Below tables provide some high-level info on which version the code is sealed, if you are upgrading from the unsealed version to sealed version then you should consider the below steps:

  1.  First identify all your customizations.

  2.  Move all your inline customizations to extensions.

      a.  Validate if you all the necessary extension point to do this, if not raise a support request:

        <https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/extensibility/extensibility-requests>

**Note:** Sometimes you need to rewrite some of the POS inline changes done in 7.1 when you want to upgrade to 7.3 or higher versions.

| **Application version**                 | **CRT Sealed** | **HWS Sealed** | **POS Sealed** | **DB Sealed** | **Retail proxy Sealed** |
|-----------------------------------------|----------------|----------------|----------------|---------------|-------------------------|
| Application release 8.1                 | Yes            | Yes            | Yes            | Yes           | Yes                     |
| Application release 8.0                 | Yes            | Yes            | Yes            | Yes           | Yes                     |
| Application 7.3                         | Yes            | Yes            | Yes            | Yes           | Yes                     |
| July 2017 release (Application 7.2)     | Yes            | Yes            | Yes            | Yes           | No                      |
| Release 1611 (application 7.1)          | Yes            | No             | No             | No            | No                      |
| February 2016 release (Application 7.0) | No             | No             | No             | No            | No                      |

**How to upgrade the retail channel extension from 7.3 to higher versions:**

For code upgrade you must Consider upgrading the below Retail SDK components (each of these components are folders inside Retail SDK):

**Note:** The code upgrade can be done using some source control/merge tool, we recommend using some source control tool for this process, so that you can keep track of the changes and revert if required. If you are not using any source control, please take the backup of the old and new retail SDK folder before your upgrade the code.

1.  **Assets:** If you have modified any of the below extension config files to include your custom assemblies then you must move those changes to the same config files in the new Asset folder.

    1.  CommerceRuntime.Ext.config - CRT extensions.

    2.  CommerceRuntime.MPOSOffline.Ext.config - CRT offline extensions.

    3.  HardwareStation.Extension.config - Hardware station and payment extensions.

    4.  RetailProxy.MPOSOffline.ext.config - Retail proxy extensions.

2.  **Build tools:** In the Build tools folder we have the files related to the packaging, build settings and pfx, snk files. Merge or update the below files if you have done any changes in the older versions:

    1.  Customization.settings

    2.  Microsoft.Dynamics.RetailSdk.Build.props

    Also include any custom pfx, snk created.

3.  **Database:** Copy and drop all your custom SQL scripts: ...\\RetailSDK\\Database\\Upgrade\\Custom

4.  **Online Store:** If you have any online store web project or online extension code then include it part of this folder. **Note:** Retail deployable package will not include online store code for packaging.

5.  **Payment Externals:** Copy and paste all your payment extension assemblies to the below Payment assemblies folder:

       1.  IPaymentDeviceAssemblies
       2.  IPaymentProcessorAssemblies
       3.  PaymentWebFiles

6.  **Payments:** Merge/drop all your payment extension project to this folder.

**Note:** If you have created completely new payment extension project and not modified anything in this folder then you can just include it part of the build and packaging process. Update the dirs.proj in the RetailSDK folder to build your custom project and update the Customization.settings file with the payment extension drop location, so that during package creation we build your custom project and include the extension part of the packaging.

7.  **POS:** If you have any POS extensions including the generated proxy, then copy your POS extensions from …\\RetailSDK\\POS\\Extensions to the new Retail SDK POS extension folder (RetailSDK\\POS\\Extensions). After you copied the extensions update/merge the extension.json file inside the POS\\Extensions folder with your new POS extensions folder you copied.

Ex: If you copied one of your extension say "**CustomExtension**" folder the you will update the extension.json like below:
```Typescript

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
Also update the tsconfig.json with the custom extension package so the POS can compile those changes during build.

8.  **Reference:** Copy all your extension output assemblies like Commerce runtime, Hardware station, proxy and any external assemblies to reference folder. Include any assemblies which you want to include part of your deployment and packaging.

9.  **Commerce runtime (CRT) and retail server (RS) extensions:** Copy all your CRT and RS extension project under the Retail SDK folder and make sure you include the CRT and RS extension solution file details in the dirs.proj file under the RetailSDK folder, so that during msbuild we build all the extension project and set output path for the project assemblies to the RetailSDK\\Reference folder

10.  **Hardware station (HWS) and payment extensions:** Copy all your HWS and payment extension project under the Retail SDK folder and make sure you include the HWS and payment extension solution file details in the dirs.proj file under the RetailSDK folder, so that during msbuild we build all the extension project and set output path for the project assemblies to the RetailSDK\\Reference folder

11.  **Retail proxy extensions:** Copy all your retail proxy extension project under the Retail SDK folder and make sure you include the proxy solution file details in the dirs.proj file under the RetailSDK folder, so that during msbuild we build all the extension project and set output path for the project assemblies to the RetailSDK\\Reference folder.

**Note:** Run **msbuild** on the root of the Retail SDK folder. Use the Microsoft Visual Studio developer command-line tool to generate the retail deployable packages.

12.  Deploy the retail deployable packages and validate.

13.  Add Retail SDK files to the repository.

**How to upgrade the retail channel extension from 7.2 to higher versions:**

The steps mentioned above will remain same for all the retail components except the Retail proxy. In 7.2 you must have done inline changes in the retail proxy project if you have CRT with RS extension and the typescript proxy was auto generated based on the customization.settings file.

To upgrade your proxy to 7.3, follow the below steps mentioned in the below link and then move it to the Retail SDK folder and update the RetailProxy.MPOSOffline.ext.config config file.

<https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/typescript-proxy-retail-pos>

**How to upgrade the retail channel extension from 7.1 to higher versions:**

In 7.1 you should have done most of the POS and Proxy customization are done inline, if you want to upgrade to higher application release then you should move all your inline changes to extensions. If its binary hotfix upgrade, then you must do code merge with the new RetailSDK and regenerate the package.

**How to upgrade the retail channel extension from 7.0 to higher versions:**

In 7.0 you should have done most of the customization are done inline, if you want to upgrade to higher application release then you should move all your inline changes to extensions. If its binary hotfix upgrade, then you must do code merge with the new RetailSDK and regenerate the package.

**Generate Deployable package for validation:**

Follow the below steps mentioned in the below link to generate the retail deployable package:

<https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/retail-sdk/retail-sdk-packaging>
