---
title: Removed or deprecated features in Dynamics 365 Commerce
description: This article describes features that have been removed, or that are planned for removal from Dynamics 365 Commerce.
author: josaw1
ms.date: 03/10/2023
ms.topic: article
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2020-04-30
ms.dyn365.ops.version: Platform update 33
---

# Removed or deprecated features in Dynamics 365 Commerce

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article describes features that have been removed, or that are planned for removal from Dynamics 365 Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and may be removed in a future update.

This list is intended to help you consider these removals and deprecations for your own planning. 

> [!NOTE]
> Detailed information about objects in finance and operations apps can be found in the [Technical reference reports](/dynamics/s-e/). You can compare the different versions of these reports to learn about objects that have changed or been removed in each version of finance and operations apps.

## Features removed or deprecated in the Commerce 10.0.39 release

### (Italy) Customer information management for Retail POS

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The functionalities behind this feature flag are now available by default hence no need for a feature flag. |
| **Replaced by another feature?**   | No |
| **Product areas affected**         | HQ Italy Localization |
| **Deployment option**              | All |
| **Status**                         | Deprecated: This feature is turned on by default and no longer behind a feature flag since Commerce version 10.0.39 |

### (Poland) Customer information management for Retail POS

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The functionalities behind this feature flag are now available by default hence no need for a feature flag. |
| **Replaced by another feature?**   | No |
| **Product areas affected**         | HQ Poland Localization |
| **Deployment option**              | All |
| **Status**                         | Deprecated: This feature is turned on by default and no longer behind a feature flag since Commerce version 10.0.39 |

## Features removed or deprecated in the Commerce 10.0.33 release

### Accessibility Insights integration within site builder

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Similar results can be achieved with less latency by installing the Accessibility Insights browser plug-in from https://accessibilityinsights.io/. The reasons for deprecation are low feature usage, maintenance costs, and the availability of a more efficient browser plug-in. |
| **Replaced by another feature?**   | No |
| **Product areas affected**         | Site builder |
| **Deployment option**              | All |
| **Status**                         | Deprecated: Functionality was removed in spring 2023 and replaced with in-tool instructions to guide users to the Accessibility Insights browser plug-in. |

### You can no longer download packages from within HQ

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | We no longer support maintaining packages within HQ directly. Users are encouraged to use Lifecycle Services or other means to download these packages.
| **Replaced by another feature?**   | No |
| **Product areas affected**         | HQ |
| **Deployment option**              | All |
| **Status**                         | Deprecated: The UI may still be available but isn't supported |

## Features removed or deprecated in the Commerce 10.0.29 release

### Commerce parameters setting - Allow price adjustments to increase product price

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | We had this setting to control whether the price adjustment function allows increasing the product price. When this parameter is turned off, when using the price adjustment function organizations can only set a product's unit price lower than its base price and trade agreement sales price. We deprecate this setting because the price adjustment function was updated to support two-way adjustments (increase or decrease) out of the box. |
| **Replaced by another feature?**   | No |
| **Product areas affected**         | Pricing and discounts |
| **Deployment option**              | All |
| **Status**                         | Deprecated: This setting is turned on by default since Commerce version 10.0.29 and was removed in October 2023. |

### Commerce parameters setting - Enable price report for retail store

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | We had this setting to control whether the price report function is available for use on the store configuration form. We deprecate this setting because the store configuration form was updated to always provide the price report function as standard function. |
| **Replaced by another feature?**   | No |
| **Product areas affected**         | Pricing and discounts |
| **Deployment option**              | All |
| **Status**                         | Deprecated: This setting was removed in October 2023. |

### Commerce parameters setting - Use today’s date to calculate prices

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The supply chain management (SCM) pricing engine supports pricing calculation based on the requested ship date or requested receipt date, along with today's date. TheCommerce pricing engine only supports pricing calculation based on today's date. For customers who use both SCM and Commerce capabilities, we provided this setting and recommended that customers always set it to **Yes** so that the two pricing engines can work together. We deprecate this setting because it doesn't change the calculation behavior and is redundant. |
| **Replaced by another feature?**   | No |
| **Product areas affected**         | Pricing and discounts |
| **Deployment option**              | All |
| **Status**                         | Deprecated: This setting is turned on by default since Commerce version 10.0.29 and was removed in October 2023. |

## Feature deprecation effective July 2022

### Commerce analytics (Preview)

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The Dynamics 365 Commerce team has analyzed the usage and uptake of the Commerce analytics (Preview) feature, and a decision has been made to no longer move forward in bringing the feature to general availability.   |
| **Replaced by another feature?**   | At this time, Commerce analytics (Preview) won't be replaced by another feature or solution. The export of raw transactions and master data from finance and operations apps to Azure Data Lake continues to be available, as explained in [Export to Data Lake in finance and operations apps](../../fin-ops-core/dev-itpro/data-entities/finance-data-azure-data-lake.md). Partners and customers can leverage that data stream to author any intended analytics reports for their business needs.
| **Product areas affected**         | Commerce analytics (Preview) |
| **Deployment option**              | All |
| **Status**                         | We'll be looking at disabling this feature by August 30, 2022. From this date forward, no refreshing occurs in the current Power BI reports provided by Commerce analytics (Preview).     |

## Features removed or deprecated in the Commerce 10.0.21 release

[!include [banner](../includes/preview-banner.md)]

### Overlapping discounts handling setting in Commerce parameters

The **Overlapping discounts handling** setting on the **Commerce parameters** page is deprecated in the Commerce version 10.0.21 release. In the future, the Commerce pricing engine uses a single algorithm to determine the optimal combination of overlapping discounts.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | <p>The **Overlapping discounts handling** setting in Commerce parameters controls how the Commerce pricing engine searches and determines the optimal combination of overlapping discounts. It currently offers three options:<p><ul><li> **Best performance** – This option uses an advanced heuristics algorithm and a [marginal value ranking](../optimal-combination-overlapping-discounts.md) method to prioritize, evaluate, and determine the best discount combination in a timely manner.</li><li>**Balanced calculation** – In the current code base, this option works just like the **Best performance** option. Therefore, it's essentially a duplicated option.</li><li>**Exhaustive calculation** – This option uses an old algorithm that goes through all possible discount combinations during the price calculation. For orders that have large lines and quantities, this option might cause performance issues.</li></ul><p>To help simplify configuration, improve performance, and reduce incidents that are caused by the old algorithm, we'll completely remove the **Overlapping discounts handling** setting and update the internal logic of the Commerce pricing engine so that it now uses only the advanced algorithm (that is, the algorithm behind the **Best performance** option).</p> |
| **Replaced by another feature?**   | No. We recommend that organizations that use the **Balanced calculation** or **Exhaustive calculation** option switch to the **Best performance** option before this feature is removed. |
| **Product areas affected**         | Pricing and discounts |
| **Deployment option**              | All |
| **Status**                         | As of the 10.0.21 release, the **Overlapping discounts handling** setting was removed from Commerce parameters in October 2022. |

### Retail SDK distributed by using Lifecycle Services

The Retail SDK ships in Lifecycle Services. This mode of distribution is deprecated in release 10.0.21. In the future, Retail SDK reference packages, libraries, and samples are published in public repositories on GitHub.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The Retail SDK ships in Lifecycle Services. The Lifecycle Services process takes a few hours to finish, and the process has to be repeated for every update. In the future, Retail SDK reference packages, libraries, and samples are published in public repositories on GitHub. Extension samples and reference packages can be consumed easily, and the updates finish in a few minutes. |
| **Replaced by another feature?**   |  [Download Retail SDK samples and reference packages from GitHub and NuGet](../dev-itpro/retail-sdk/sdk-github.md) |
| **Product areas affected**         | Retail SDK |
| **Deployment option**              | All |
| **Status**                         | Deprecated: As of release 10.0.21, the SDK shipped via the Lifecycle Services VMs was removed in October 2023. |

### Retail deployable package and combined POS, Hardware station, and Cloud Scale unit installers

Retail deployable packages generated using the Retail SDK MSBuild is deprecated in 10.0.21. In the future, use the Cloud Scale Unit (CSU) package for Cloud Scale unit extensions (Commerce Runtime, channel database, Headless commerce APIs, Payments, and Cloud Point of Sale (POS)). Use extension-only installers for POS, Hardware station, and Cloud scale unit self-hosted.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | A Retail deployable package is a combined package that contains a complete set of extension packages and installers. This combined package makes the deployment complex, as CSU extensions go to Cloud scale unit and installers are deployed in stores. The installers include the extension and base product, which makes the updates difficult. With every upgrade, a code merge and package generation are required. To simplify this process, the extension packages are now separated into components for easy deployment and management. With the new approach, extensions and base product installers are separated and can be independently serviced and upgraded without a code merge or repackaging.|
| **Replaced by another feature?**   | CSU extensions, POS extension installers, Hardware station extension installers |
| **Product areas affected**         | Dynamics 365 Commerce extension and deployment |
| **Deployment option**              | All |
| **Status**                         | Deprecated: As of release 10.0.21, support for deploying RetailDeployablePackage in Lifecycle Services was removed in October 2022. |

For more information, see:

+ [Generate a separate package for Commerce Cloud Scale Unit (CSU)](../dev-itpro/retail-sdk/retail-sdk-packaging.md#generate-a-separate-package-for-commerce-cloud-scale-unit-csu)
+ [Create a Modern POS extension package](../dev-itpro/pos-extension/mpos-extension-packaging.md)
+ [Integrate the POS with a new hardware device](../dev-itpro/hardware-device-extension.md)
+ Code samples
    + [Cloud Scale Unit](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit)
    + [POS, CSU, and Hardware station](https://github.com/microsoft/Dynamics365Commerce.InStore)

### ModernPos.Sln and CloudPos.sln in the Retail SDK

POS extension development using ModernPos.sln, CloudPos.sln, POS.Extension.csproj, and the POS folder is deprecated in release 10.0.21. In the future, use the POS-independent packaging SDK for POS extensions.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | In earlier versions of the Retail SDK, if there are POS extensions, a code merge and repackaging is required to update to the latest version of the POS. The code merge was a time-consuming upgrade process and you had to maintain the full Retail SDK in the repository. You also had to compile the core POS.App project. By using the independent packaging model, you must maintain only your extension. The process of updating to the latest version of the POS extensions is as easy as updating the version of the NuGet package that your project consumes. Extensions can be deployed independently, and services use the extension installers. The base POS can be deployed and maintained separately, and no code merge or repackaging with the base installer or code is required. |
| **Replaced by another feature?**   | [POS-independent packaging SDK](../dev-itpro/pos-extension/pos-extension-getting-started.md) |
| **Product areas affected**         | Dynamics 365 Commerce POS extension and deployment |
| **Deployment option**              | All |
| **Status**                         | Deprecated: As of release 10.0.21, support for combined POS packages and extension model using the ModernPos.Sln, CloudPOs.sln, and POS.Extensons.csproj in Retail SDK was removed in October 2023. |

## Features removed or deprecated in the Commerce 10.0.17 release

### Full dataset generation interval is deprecated

|  &nbsp; | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Beginning in this release, in the **Commerce scheduler parameters** form in Dynamics 365 headquarters, the **Full dataset generation interval in days** field is deprecated. In this release, the field is visually removed so that the value can't be edited. This stays as the value **0**. |
| **Replaced by another feature?**   | No |
| **Product areas affected**         | Dynamics 365 Commerce |
| **Deployment option**              | All|
| **Status**                         | Deprecated. Don't use this field or change the value in it.|

## Features removed or deprecated in the Commerce 10.0.15 release

### Internet Explorer 11 support for Dynamics 365 is deprecated

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Effective December 2020, Microsoft Internet Explorer 11 support for all Dynamics 365 products is deprecated, and Internet Explorer 11 won't be supported after August 2021.<br><br>This impacts customers who use Dynamics 365 products that are designed to be used through an Internet Explorer 11 interface. After August 2021, Internet Explorer 11 won't be supported for such Dynamics 365 products. |
| **Replaced by another feature?**   | We recommend that customers transition to Microsoft Edge.|
| **Product areas affected**         | All Dynamics 365 products |
| **Deployment option**              | All|
| **Status**                         | Deprecated. Internet Explorer 11 won't be supported after August 2021.|

## Features removed or deprecated in the Commerce 10.0.11 release
### Data action hooks
| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The data action hooks feature was deprecated due to performance issues. |
| **Replaced by another feature?**   | We recommend using [data action overrides](../e-commerce-extensibility/data-action-overrides.md) to modify business logic in the data action layer.|
| **Product areas affected**         | e-Commerce extensibility data actions |
| **Deployment option**              | All |
| **Status**                         | Deprecated: As of release 10.0.11 |

### Retail SDK support for Visual Studio 2015, msbuild 14.0, and Retail SDK\Reference libraries and tools
| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Retail SDK support for Visual Studio 2015 was deprecated and updated to support VS 2017, msbuild 15.0 and all the reference libraries and commerce proxy generator tools in the RetailSDK\References folder moved to NuGet packages to simplify the extension model and SDK upgrade process.|
| **Replaced by another feature?**   | We recommend that you follow the information in [Migrate the Retail SDK from Visual Studio 2015 to Visual Studio 2017](../dev-itpro/retail-sdk/migrate-sdk.md) to update your system. |
| **Product areas affected**         | Retail SDK extensions |
| **Deployment option**              | All |
| **Status**                         | Deprecated: As of release 10.0.11 |

### Retail Server Extension using IEdmModelExtender and CommerceController
| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Retail server extension using IEdmModelExtender and CommerceController was deprecated to provide simplified extension model. The new implementation only has the controller class without any additional IEdmModelExtender class implementation. This also avoids the dependency with a particular OData version (if the OData version is updated it may break extensions.) |
| **Replaced by another feature?**   |  We recommend that you use the IController class extension model by importing the NuGet (Microsoft.Dynamics.Commerce.Hosting.Contracts) package. |
| **Product areas affected**         | Retail server extensions |
| **Deployment option**              | All |
| **Status**                         | Deprecated: As of release 10.0.11 |

### Hardware station Extension using IHardwareStationController
| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Hardware station extension using IHardwareStationController was deprecated to provide simplified extension model. The new implementation only has the IController class without any more class implementation and to avoid the dependency with core hardware station libraries, previously extension need to refer multiple libraries.) |
| **Replaced by another feature?**   | It's recommended to use the IController class extension model by importing the NuGet (Microsoft.Dynamics.Commerce.Hosting.Contracts) package. |
| **Product areas affected**         | Hardware station extensions |
| **Deployment option**              | All |
| **Status**                         | Deprecated: As of release 10.0.11 |

## Features removed or deprecated in the Commerce 10.0.10 release
### POS operation 803 - Picking and receiving
| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Picking and receiving operations is being deprecated due to new operation redesign. |
| **Replaced by another feature?**   | Yes. It's replaced by two new POS operations: inbound operation (804) and outbound operation (805).|
| **Product areas affected**         | Point of sale (POS) application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: As of release 10.0.10, the picking and receiving operation will no longer receive any new feature updates. Only critical bug fixes are done for this operation in future releases. All customers are encouraged to move to the new [Inbound operations](../pos-inbound-inventory-operation.md) and [Outbound operations](../pos-outbound-inventory-operation.md), which continues to be part of our long-term product roadmap. |


## Features removed or deprecated in the Commerce 10.0.7 release
### Commerce GetProductAvailabilities and GetAvailableInventoryNearby APIs
| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | New optimized APIs have been created to replace the GetProductAvailabilities and GetAvailableInventoryNearby APIs. |
| **Replaced by another feature?**   | Yes: It's replaced by GetEstimatedAvailabilty and GetEstimatedProductWarehouseAvailability APIs. |
| **Product areas affected**         | e-Commerce application SDK |
| **Deployment option**              | All |
| **Status**                         | Deprecated: As of release 10.0.7, no engineering investments are made for GetProductAvailabilities and GetAvailableInventoryNearby. Organizations that use these APIs in their e-Commerce deployments should convert to the new GetEstimatedAvailabilty and GetEstimatedProductWarehouseAvailability APIs and enable the [Optimized product availability calculation feature](../calculated-inventory-retail-channels.md).  |

## Previous announcements about removed or deprecated features
To learn more about features that are removed or deprecated in previous releases, see [Removed or deprecated features in previous releases](../../fin-ops-core/dev-itpro/migration-upgrade/deprecated-features.md?toc=/dynamics365/commerce/toc.json).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]

