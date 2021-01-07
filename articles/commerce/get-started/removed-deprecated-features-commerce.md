---
# required metadata

title: Removed or deprecated features in Dynamics 365 Commerce 
description: This topic describes features that have been removed, or that are planned for removal from Dynamics 365 Commerce.
author: josaw
manager: AnnBe
ms.date: 01/07/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: josaw
#ms.search.scope: Operations
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
> Detailed information about objects in Finance and Operations apps can be found in the [Technical reference reports](https://mbs.microsoft.com/customersource/northamerica/AX/downloads/reports/axtechrefrep). You can compare the different versions of these reports to learn about objects that have changed or been removed in each version of Finance and Operations apps.
## Features removed or deprecated in the Commerce 10.0.17 release

### Full dataset generation interval is deprecated

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Beginning in this release, in the **Commerce scheduler parameters** form in Dynamics 365 headquarters, the **Full dataset generation interval in days** field will be deprecated. Also starting in this release, the field will be visually removed so that the value cannot be edited. This will stay as the value **0**. |
| **Replaced by another feature?**   | No |
| **Product areas affected**         | Dynamics 365 Commerce |
| **Deployment option**              | All|
| **Status**                         | Deprecated. Do not use this field or change the value in it.|


## Features removed or deprecated in the Commerce 10.0.15 release

### Internet Explorer 11 support for Dynamics 365 is deprecated

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Effective December 2020, Microsoft Internet Explorer 11 support for all Dynamics 365 products is deprecated, and Internet Explorer 11 won’t be supported after August 2021.<br><br>This will impact customers who use Dynamics 365 products that are designed to be used through an Internet Explorer 11 interface. After August 2021, Internet Explorer 11 won't be supported for such Dynamics 365 products. |
| **Replaced by another feature?**   | We recommend that customers transition to Microsoft Edge.|
| **Product areas affected**         | All Dynamics 365 products |
| **Deployment option**              | All|
| **Status**                         | Deprecated. Internet Explorer 11 won’t be supported after August 2021.|

## Features removed or deprecated in the Commerce 10.0.11 release
### Data action hooks
|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The data action hooks feature has been deprecated due to performance issues. |
| **Replaced by another feature?**   | We recommend using [data action overrides](../e-commerce-extensibility/data-action-overrides.md) to modify business logic in the data action layer.|
| **Product areas affected**         | e-Commerce extensibility data actions |
| **Deployment option**              | All |
| **Status**                         | Deprecated: As of release 10.0.11 |

### Retail SDK support for Visual Studio 2015, msbuild 14.0, and Retail SDK\Reference libraries and tools
|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Retail SDK support for Visual Studio 2015 has been deprecated and updated to support VS 2017, msbuild 15.0 and all the reference libraries and commerce proxy generator tools in the RetailSDK\References folder moved to NuGet packages to simplify the extension model and SDK upgrade process.|
| **Replaced by another feature?**   | We recommend that you follow the information in [Migrate the Retail SDK from Visual Studio 2015 to Visual Studio 2017](../dev-itpro/retail-sdk/migrate-sdk.md) to update your system. |
| **Product areas affected**         | Retail SDK extensions |
| **Deployment option**              | All |
| **Status**                         | Deprecated: As of release 10.0.11 |

### Retail Server Extension using IEdmModelExtender and CommerceController
|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Retail server extension using IEdmModelExtender and CommerceController has been deprecated to provide simplified extension model. The new implementation will have only the controller class without any additional IEdmModelExtender class implementation. This also avoids the dependency with a particular OData version (if the OData version is updated it may break extensions.) |
| **Replaced by another feature?**   |  We recommend that you use the IController class extension model by importing the NuGet (Microsoft.Dynamics.Commerce.Hosting.Contracts) package. |
| **Product areas affected**         | Retail server extensions |
| **Deployment option**              | All |
| **Status**                         | Deprecated: As of release 10.0.11 |

### Hardware station Extension using IHardwareStationController
|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Hardware station extension using IHardwareStationController has been deprecated to provide simplified extension model. The new implementation will have only the IController class without any additional class implementation and to avoid the dependency with core hardware station libraries, previously extension need to refer multiple libraries.) |
| **Replaced by another feature?**   | It is recommended to use the IController class extension model by importing the NuGet (Microsoft.Dynamics.Commerce.Hosting.Contracts) package. |
| **Product areas affected**         | Hardware station extensions |
| **Deployment option**              | All |
| **Status**                         | Deprecated: As of release 10.0.11 |

## Features removed or deprecated in the Commerce 10.0.10 release
### POS operation 803 - Picking and receiving
|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Picking and receiving operations is being deprecated due to new operation redesign. |
| **Replaced by another feature?**   | Yes. It is replaced by two new POS operations: inbound operation (804) and outbound operation (805).|
| **Product areas affected**         | Point of sale (POS) application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: As of release 10.0.10, the picking and receiving operation will no longer receive any new feature updates. Only critical bug fixes will be done for this operation in future releases. All customers are encouraged to move to the new [Inbound operations](https://docs.microsoft.com/dynamics365/commerce/pos-inbound-inventory-operation) and [Outbound operations](https://docs.microsoft.com/dynamics365/commerce/pos-outbound-inventory-operation), which will continue to be part of our long-term product roadmap. |


## Features removed or deprecated in the Commerce 10.0.7 release
### Commerce GetProductAvailabilities and GetAvailableInventoryNearby API's
|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | New optimized APIs have been created to replace the GetProductAvailabilities and GetAvailableInventoryNearby APIs. |
| **Replaced by another feature?**   | Yes: It is replaced by GetEstimatedAvailabilty and GetEstimatedProductWarehouseAvailability APIs. |
| **Product areas affected**         | e-Commerce application SDK |
| **Deployment option**              | All |
| **Status**                         | Deprecated: As of release 10.0.7, there will no longer be engineering investments made for GetProductAvailabilities and GetAvailableInventoryNearby. Organizations that use these APIs in their e-Commerce deployments should convert to the new GetEstimatedAvailabilty and GetEstimatedProductWarehouseAvailability APIs and enable the [Optimized product availability calculation feature](https://docs.microsoft.com/dynamics365/commerce/calculated-inventory-retail-channels).  |

## Previous announcements about removed or deprecated features
To learn more about features that have been removed or deprecated in previous releases, see [Removed or deprecated features in previous releases](../../fin-ops-core/dev-itpro/migration-upgrade/deprecated-features.md?toc=/dynamics365/commerce/toc.json).
