---
# required metadata

title: Removed or deprecated features in Dynamics 365 Supply Chain Management
description: This topic describes features that have been removed, or that are planned for removal in Dynamics 365 Supply Chain Management.
author: kamaybac
ms.date: 04/27/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: kamaybac
ms.search.validFrom: 2020-03-03 
ms.dyn365.ops.version: Platform update 33

---

# Removed or deprecated features in Dynamics 365 Supply Chain Management

[!include [banner](../includes/banner.md)]

This topic will be updated as new removed or deprecated features are documented for Dynamics 365 Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

This list is intended to help you consider these removals and deprecations for your own planning.

> [!NOTE]
> Detailed information about objects in Finance and Operations apps can be found in the [Technical reference reports](/dynamics/s-e/). You can compare the different versions of these reports to learn about objects that have changed or been removed in each version of Finance and Operations apps.


## Features removed or deprecated in the Supply Chain Management 10.0.19 release

### Job card device

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | The [job card device](../production-control/config-job-card-device.md) is being replaced by the new [production floor execution interface](../production-control/production-floor-execution-configure.md). |
| **Replaced by another feature?**   | Yes, the [job card device](../production-control/config-job-card-device.md) is to be replaced by the new [production floor execution interface](../production-control/production-floor-execution-configure.md). |
| **Product areas affected** | Supply Chain Management - production control |
| **Deployment option** | Cloud and on-premises |
| **Status** | Deprecated. The job card device will receive support with bug and security fixes, but feature enhancements will no longer be provided. After April 2022, the job card device will no longer be supported and customers will be asked to move to the new production floor execution interface. |

## Features removed or deprecated in the Supply Chain Management 10.0.18 release

### Dynamics 365 for Finance and Operations - Warehousing (the warehouse app)

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Effective April 2021, *Dynamics  365 for Finance and Operations - Warehousing* (the warehouse app) is deprecated and won't be supported after April 2022. It is now replaced by the *Warehouse Management mobile app*, which was released with version 10.0.17 of Supply Chain Management. The new app is a complete replacement but uses same underlying framework, which makes migration easy. If needed, the two apps can be used side-by-side to help users gradually adjust as they learn to use the new app.<br><br>For more information about the new Warehouse Management mobile app, see [Warehouse Management mobile application](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/warehouse-management-mobile-application) and [Install and connect the Warehouse Management mobile app](../warehousing/install-configure-warehouse-management-app.md). |
| **Replaced by another feature?**   | Yes, replaced by the new Warehouse Management mobile app. |
| **Product areas affected**         | Supply Chain Management - warehouse app |
| **Deployment option**              | Cloud and on-premises |
| **Status**                         | Deprecated. The warehouse app will receive support with bug and security fixes, but feature enhancements will no longer be provided. After April 2022, the old warehouse app will no longer be supported and customers will be asked to move to the new Warehouse Management mobile app. The old warehouse app will then be removed from the Microsoft Store and Google Play store.  |

## Features removed or deprecated in the Supply Chain Management 10.0.15 release

### Internet Explorer 11 support for Dynamics 365 is deprecated

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Effective December 2020, Microsoft Internet Explorer 11 support for all Dynamics 365 products is deprecated, and Internet Explorer 11 won’t be supported after August 2021.<br><br>This will impact customers who use Dynamics 365 products that are designed to be used through an Internet Explorer 11 interface. After August 2021, Internet Explorer 11 won't be supported for such Dynamics 365 products. |
| **Replaced by another feature?**   | We recommend that customers transition to Microsoft Edge.|
| **Product areas affected**         | All Dynamics 365 products |
| **Deployment option**              | All|
| **Status**                         | Deprecated. Internet Explorer 11 won’t be supported after August 2021.|

### Use of built-in Supply Chain Management master planning engine for manufacturing scenarios

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | To enhance performance and minimize the SQL database load during master planning runs, the built-in Supply Chain Management master planning engine is being replaced by Planning Optimization. Planning Optimization allows for fast planning runs that can be performed even during office hours. This enables planners to react immediately to changes in demand or planning parameters. |
| **Replaced by another feature?**   | Yes, Planning Optimization will replace the existing built-in Supply Chain Management master planning engine. |
| **Product areas affected**         | Supply Chain Management - Master planning |
| **Deployment option**              | Cloud only. Planning Optimization is not supported with on-premises deployments. |
| **Status**                         | Deprecated. By April 1, 2022, manufacturing scenarios will no longer be supported for the built-in Supply Chain Management master planning engine. As of that date, Microsoft will stop all active development on manufacturing scenarios for the built-in planning engine, will not release any new features, and will only release critical bug fixes. After that date, all companies that require support for manufacturing scenarios must use Planning Optimization for their master planning calculations. Planning Optimization is expected to fully support manufacturing scenarios by October 2022. For more information, see the [Planning Optimization documentation](../master-planning/planning-optimization/planning-optimization-overview.md).<br><br>Companies with on-premises deployments of Supply Chain Management may continue to use the built-in master planning engine for manufacturing scenarios after April 2022. However, no more feature enhancements will be provided. |

## Features removed or deprecated in the Supply Chain Management 10.0.11 release

### Use of built-in Supply Chain Management master planning engine for distribution scenarios

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | To enhance performance and minimize the SQL database load during master planning runs, the built-in Supply Chain Management master planning engine is being replaced by Planning Optimization. Planning Optimization allows for fast planning runs that can be performed even during office hours. This enables planners to react immediately to changes in demand or planning parameters. |
| **Replaced by another feature?**   | Yes, Planning Optimization will replace the existing built-in Supply Chain Management master planning engine. |
| **Product areas affected**         | Supply Chain Management - Master planning |
| **Deployment option**              | Cloud only. Planning Optimization is not supported with on-premises deployments. |
| **Status**                         | Deprecated. By April 1, 2021, distribution scenarios will no longer be supported with the built-in Dynamics 365 Supply Chain Management master planning engine. For distribution scenarios, customers must use Planning Optimization for master planning calculations. For more information, see [Planning Optimization documentation](../master-planning/planning-optimization/planning-optimization-overview.md). Customers with on-premises deployments of Dynamics 365 Supply Chain Management may continue to use the Supply Chain Management master planning engine for distribution scenarios after April 2021. However, no more feature enhancements will be provided. |

## Previous announcements about removed or deprecated features

To learn more about features that have been removed or deprecated in previous releases, see [Removed or deprecated features in previous releases](../../fin-ops-core/dev-itpro/migration-upgrade/deprecated-features.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
