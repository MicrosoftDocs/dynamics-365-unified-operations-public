---
# required metadata

title: Removed or deprecated features in Dynamics 365 Commerce 
description: This topic describes features that have been removed, or that are planned for removal from Dynamics 365 Commerce.
author: josaw
manager: AnnBe
ms.date: 05/04/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2020-04-30
ms.dyn365.ops.version: Platform update 33

---

# Removed or deprecated features in Dynamics 365 Commerce

[!include [banner](../includes/banner.md)]

This topic describes features that have been removed, or that are planned for removal from Dynamics 365 Finance.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

This list is intended to help you consider these removals and deprecations for your own planning. 

> [!NOTE]
> Detailed information about objects in Finance and Operations apps can be found in the [Technical reference reports](https://mbs.microsoft.com/customersource/northamerica/AX/downloads/reports/axtechrefrep). You can compare the different versions of these reports to learn about objects that have changed or been removed in each version of Finance and Operations apps.

## Features removed or deprecated in the Commerce 10.0.10 release
### POS operation 803 - Picking and receiving
|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Picking and receiving operations is being deprecated due to new operation redesign |
| **Replaced by another feature?**   | Yes  - replaced by two new POS operations, Inbound operation (804) and Outbound operation (805)|
| **Product areas affected**         | Point of Sale Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: As of version 10.0.10 the Picking and receiving operation will no longer receive any new feature updates and only critical bug fixes will be done for this operation in future releases.  All customers are encouraged to move to the new [Inbound operations](https://docs.microsoft.com/en-us/dynamics365/commerce/pos-inbound-inventory-operation) and [Outbound operations](https://docs.microsoft.com/en-us/dynamics365/commerce/pos-outbound-inventory-operation) which will continue to have investment in our long term product roadmap. |


## Features removed or deprecated in the Commerce 10.0.7 release
### Commerce GetProductAvailabilities and GetAvailableInventoryNearby API's
|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | New optimized API's have been created to replace the old|
| **Replaced by another feature?**   | Yes  - replaced by GetEstimatedAvailabilty and GetEstimatedProductWarehouseAvailability API's |
| **Product areas affected**         | e-Commerce application SDK |
| **Deployment option**              | All |
| **Status**                         | Deprecated: As of version 10.0.7, there will no longer be engineering investments made for the GetProductAvailabilities and GetAvailableInventoryNearby.  Organizations that use these API's in their e-Commerce deployments should conver to the new GetEstimatedAvailabilty and GetEstimatedProductWarehouseAvailability API's and enable the [Optimized product availability calculation feature](https://docs.microsoft.com/en-us/dynamics365/commerce/calculated-inventory-retail-channels)  |

## Previous announcements about removed or deprecated features
To learn more about features that have been removed or deprecated in previous releases, see [Removed or deprecated features in previous releases](../../fin-ops-core/dev-itpro/migration-upgrade/deprecated-features.md?toc=/dynamics365/commerce/toc.json).
