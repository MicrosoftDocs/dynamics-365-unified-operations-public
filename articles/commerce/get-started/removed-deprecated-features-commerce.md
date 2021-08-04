---
# required metadata

title: Removed or deprecated features in Dynamics 365 Commerce 
description: This topic describes features that have been removed, or that are planned for removal from Dynamics 365 Commerce.
author: josaw
ms.date: 01/11/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: josaw
ms.search.validFrom: 2020-04-30
ms.dyn365.ops.version: Platform update 33

---

# Removed or deprecated features in Dynamics 365 Commerce

[!include [banner](../includes/banner.md)]

This topic describes features that have been removed, or that are planned for removal from Dynamics 365 Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

This list is intended to help you consider these removals and deprecations for your own planning. 

> [!NOTE]
> Detailed information about objects in Finance and Operations apps can be found in the [Technical reference reports](/dynamics/s-e/). You can compare the different versions of these reports to learn about objects that have changed or been removed in each version of Finance and Operations apps.


## Features removed or deprecated in the Commerce 10.0.21 release

## Retail SDK distributed using LCS 

Retail SDK shipped in LCS Development, Build and Demo VMs, LCS Updates/Hotfix or Downloadable Vhd is deprecated in 10.0.21. Retail SDK reference packages/libraries and samples will be published in public repository and GitHub. 

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Retail SDK shipped in LCS Development, Build and Demo VMs, LCS Updates/Hotfix or Downloadable Vhd will be deprecated in 10.0.21. Retail SDK reference packages/libraries and samples will be published in public repository and GitHub. Extension samples and reference packages can be easily consumed from GitHub and public feed, LCS process requires few hours to get the updates and need to be repeated for every update but with the packages in the public feed, updates can be done in few minutes. |
| **Replaced by another feature?**   |  [Download Retail SDK samples and reference packages from GitHub and NuGet.]( https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-sdk/sdk-github). |
| **Product areas affected**         | Retail SDK. |
| **Deployment option**              | All |
| **Status**                         | Deprecated: As of release 10.0.21. The SDK shipped via the LCS VMs will be removed in Oct 2022. |


## Retail deployable package and combined POS, Hardware station and Cloud Scale unit installers

Retail deployable package generated using the Retail SDK msbuild is deprecated in 10.0.21, use the Cloud Scale Unit package for Cloud Scale unit extensions (Commerce Runtime, channel database, Headless commerce APIs, Payments and Cloud POS) and Extension only installers for POS, Hardware station and Clous scale unit self-hosted)

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Retail deployable package is combined package contains all different extensions packages and installers which make the deployment complex, CSU extensions goes to cloud scale unit, installers are deployed in stores, to simplify this the extension packages are separated by components for easy deployment and management. Installers includes extension and base product, this makes the updates difficult, with every upgrade, code merge and package generation are required, with the new approach extensions and base product installers are separated and can be independently serviced and upgraded without the need of any code merge and repackaging.|
| **Replaced by another feature?**   | <ul>[CSU Extensions](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-sdk/retail-sdk-packaging#generate-a-separate-package-for-commerce-cloud-scale-unit-csu)</ul> <ul>[POS Extension installers](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/pos-extension/mpos-extension-packaging)</ul><ul>[HWS Extension installers](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/hardware-device-extension)</ul> <ul>Code samples:</ul><ul><li>[Cloud Scale Unit](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit)</li></ul> <ul><li>[POS, CSU and HWS](https://github.com/microsoft/Dynamics365Commerce.InStore)</li></ul> |
| **Product areas affected**         | Dynamics 365 Commerce extension and deployment. |
| **Deployment option**              | All |
| **Status**                         | Deprecated: As of release 10.0.21. Support for deploying RetailDeployablePackage in LCS will be removed in Oct 2022. |


## ModernPos.Sln and CloudPOs.sln in Retail SDK

POS extension development using the ModernPos.Sln and CloudPOs.sln and POS.Extension.csproj and POS folder is deprecated in 10.0.21, use the POS independent packaging SDK for POS extensions.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | In earlier versions of the Retail SDK, if there is POS extensions then code merge and repackaging is required to update to the latest version of the POS. The code merge was a time-consuming upgrade process and you had to maintain the full Retail SDK in the repository (repo), and you had to compile the core POS.App project. By using the independent packaging model, you must maintain only your extension. The process of updating to the latest version of the POS extensions is as easy as updating the version of the NuGet package that your project consumes and extensions can be independently deployed and services using the extension installers, base POS can be deployed and maintained separately, no more code merge or repackaging with base installer or code is required. |
| **Replaced by another feature?**   |  [POS independent packaging SDK]( https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/pos-extension/pos-extension-getting-started). |
| **Product areas affected**         | Dynamics 365 Commerce POS extension and deployment. |
| **Deployment option**              | All |
| **Status**                         | Deprecated: As of release 10.0.21. Support for combined POS packages and extension model using the ModernPos.Sln, CloudPOs.sln and POS.Extensons.csproj in Retail SDK will be removed in Oct 2022. |

## Features removed or deprecated in the Commerce 10.0.17 release

### Full dataset generation interval is deprecated

|  &nbsp; | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Beginning in this release, in the **Commerce scheduler parameters** form in Dynamics 365 headquarters, the **Full dataset generation interval in days** field will be deprecated. Also starting in this release, the field will be visually removed so that the value cannot be edited. This will stay as the value **0**. |
| **Replaced by another feature?**   | No |
| **Product areas affected**         | Dynamics 365 Commerce |
| **Deployment option**              | All|
| **Status**                         | Deprecated. Do not use this field or change the value in it.|

## Features removed or deprecated in the Commerce 10.0.15 release

### Internet Explorer 11 support for Dynamics 365 is deprecated

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Effective December 2020, Microsoft Internet Explorer 11 support for all Dynamics 365 products is deprecated, and Internet Explorer 11 won’t be supported after August 2021.<br><br>This will impact customers who use Dynamics 365 products that are designed to be used through an Internet Explorer 11 interface. After August 2021, Internet Explorer 11 won't be supported for such Dynamics 365 products. |
| **Replaced by another feature?**   | We recommend that customers transition to Microsoft Edge.|
| **Product areas affected**         | All Dynamics 365 products |
| **Deployment option**              | All|
| **Status**                         | Deprecated. Internet Explorer 11 won’t be supported after August 2021.|

## Features removed or deprecated in the Commerce 10.0.11 release
### Data action hooks
| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The data action hooks feature has been deprecated due to performance issues. |
| **Replaced by another feature?**   | We recommend using [data action overrides](../e-commerce-extensibility/data-action-overrides.md) to modify business logic in the data action layer.|
| **Product areas affected**         | e-Commerce extensibility data actions |
| **Deployment option**              | All |
| **Status**                         | Deprecated: As of release 10.0.11 |

### Retail SDK support for Visual Studio 2015, msbuild 14.0, and Retail SDK\Reference libraries and tools
| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Retail SDK support for Visual Studio 2015 has been deprecated and updated to support VS 2017, msbuild 15.0 and all the reference libraries and commerce proxy generator tools in the RetailSDK\References folder moved to NuGet packages to simplify the extension model and SDK upgrade process.|
| **Replaced by another feature?**   | We recommend that you follow the information in [Migrate the Retail SDK from Visual Studio 2015 to Visual Studio 2017](../dev-itpro/retail-sdk/migrate-sdk.md) to update your system. |
| **Product areas affected**         | Retail SDK extensions |
| **Deployment option**              | All |
| **Status**                         | Deprecated: As of release 10.0.11 |

### Retail Server Extension using IEdmModelExtender and CommerceController
| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Retail server extension using IEdmModelExtender and CommerceController has been deprecated to provide simplified extension model. The new implementation will have only the controller class without any additional IEdmModelExtender class implementation. This also avoids the dependency with a particular OData version (if the OData version is updated it may break extensions.) |
| **Replaced by another feature?**   |  We recommend that you use the IController class extension model by importing the NuGet (Microsoft.Dynamics.Commerce.Hosting.Contracts) package. |
| **Product areas affected**         | Retail server extensions |
| **Deployment option**              | All |
| **Status**                         | Deprecated: As of release 10.0.11 |

### Hardware station Extension using IHardwareStationController
| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Hardware station extension using IHardwareStationController has been deprecated to provide simplified extension model. The new implementation will have only the IController class without any additional class implementation and to avoid the dependency with core hardware station libraries, previously extension need to refer multiple libraries.) |
| **Replaced by another feature?**   | It is recommended to use the IController class extension model by importing the NuGet (Microsoft.Dynamics.Commerce.Hosting.Contracts) package. |
| **Product areas affected**         | Hardware station extensions |
| **Deployment option**              | All |
| **Status**                         | Deprecated: As of release 10.0.11 |

## Features removed or deprecated in the Commerce 10.0.10 release
### POS operation 803 - Picking and receiving
| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Picking and receiving operations is being deprecated due to new operation redesign. |
| **Replaced by another feature?**   | Yes. It is replaced by two new POS operations: inbound operation (804) and outbound operation (805).|
| **Product areas affected**         | Point of sale (POS) application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: As of release 10.0.10, the picking and receiving operation will no longer receive any new feature updates. Only critical bug fixes will be done for this operation in future releases. All customers are encouraged to move to the new [Inbound operations](../pos-inbound-inventory-operation.md) and [Outbound operations](../pos-outbound-inventory-operation.md), which will continue to be part of our long-term product roadmap. |


## Features removed or deprecated in the Commerce 10.0.7 release
### Commerce GetProductAvailabilities and GetAvailableInventoryNearby API's
| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | New optimized APIs have been created to replace the GetProductAvailabilities and GetAvailableInventoryNearby APIs. |
| **Replaced by another feature?**   | Yes: It is replaced by GetEstimatedAvailabilty and GetEstimatedProductWarehouseAvailability APIs. |
| **Product areas affected**         | e-Commerce application SDK |
| **Deployment option**              | All |
| **Status**                         | Deprecated: As of release 10.0.7, there will no longer be engineering investments made for GetProductAvailabilities and GetAvailableInventoryNearby. Organizations that use these APIs in their e-Commerce deployments should convert to the new GetEstimatedAvailabilty and GetEstimatedProductWarehouseAvailability APIs and enable the [Optimized product availability calculation feature](../calculated-inventory-retail-channels.md).  |

## Previous announcements about removed or deprecated features
To learn more about features that have been removed or deprecated in previous releases, see [Removed or deprecated features in previous releases](../../fin-ops-core/dev-itpro/migration-upgrade/deprecated-features.md?toc=/dynamics365/commerce/toc.json).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
