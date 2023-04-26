---
# required metadata

title: Removed or deprecated features in Dynamics 365 Supply Chain Management
description: This article describes features that have been removed, or that are planned for removal in Dynamics 365 Supply Chain Management.
author: kamaybac
ms.date: 06/29/2022
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

This article will be updated as new removed or deprecated features are documented for Dynamics 365 Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

This list is intended to help you consider these removals and deprecations for your own planning.

> [!NOTE]
> Detailed information about objects in finance and operations apps can be found in the [Technical reference reports](/dynamics/s-e/). You can compare the different versions of these reports to learn about objects that have changed or been removed in each version of finance and operations apps.

## Features removed or deprecated in the Supply Chain Management 10.0.35 release

### Integration with Microsoft Outlook for contacts, appointments, and tasks

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | Exchange web service API is transitioning from SOAP to REST. |
| **Replaced by another feature?**   | No replacement is planned. We recommend that customers integrate with Dynamics 365 Sales. |
| **Product areas affected** | Supply Chain Management - sales and marketing |
| **Deployment option** | Cloud and on-premises |
| **Status** | <p> Deprecated. As of December 1, 2023, Microsoft will discontinue support for synchronizing contacts, appointments, and tasks between Supply Chain Management and Microsoft Outlook. Security updates will likewise not be provided for these features.</p><p>This functionality is being discontinued because the existing integration is based on SOAP, while Exchange Web Service (EWS) is transitioning from SOAP to REST and will only support REST going forward. There are no plans to add REST support for Outlook integration in Supply Chain Management.</p><p> As of May 1, 2024, it will no longer be possible to synchronize the following types of records between Supply Chain Management and Outlook:</p><ul><li>Contacts</li><li>Appointment activities</li><li>Task activities</li></ul><p>To prepare for this change, please redesign any extensions you may have made to any of these capabilities to remove the dependency.</p><p>To support customer relations management scenarios, consider integrating Dynamics 365 Sales with Outlook and/or using dual-write to synchronize contacts for customer accounts between Supply Chain Management and Dynamics 365 Sales (see also [Integrated customer master](../../fin-ops-core/dev-itpro/data-entities/dual-write/customer-mapping.md)).</p> |

## Features removed or deprecated in the Supply Chain Management 10.0.29 release

### Stock transfer orders that have tax on the transfer price

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | The [Stock transfer orders that have tax on the transfer price](../../finance/localizations/apac-ind-gst-stock-transfer-transactions.md) functionality is being replaced by the [Stock transfer orders for India](../../finance/localizations/apac-ind-stock-transfer.md) functionality. |
| **Replaced by another feature?**   | Yes, the [Stock transfer orders that have tax on the transfer price](../../finance/localizations/apac-ind-gst-stock-transfer-transactions.md) functionality is being replaced by the [Stock transfer orders for India](../../finance/localizations/apac-ind-stock-transfer.md) functionality. |
| **Product areas affected** | Supply Chain Management - inventory |
| **Deployment option** | Cloud and on-premises |
| **Status** | <p>Being deprecated. The *Stock transfer orders that have tax on the transfer price* functionality won't receive support with bug fixes and security fixes.</p><p>After April 2023, customers will be asked to use the improved functionality, *Stock transfer orders for India*, by default. After October 2023, the *Stock transfer orders that have tax on the transfer price* functionality will no longer be available, and customers will be asked to move to the improved *Stock transfer orders for India* functionality.</p><p>For more information, see [Stock transfer orders for India](../../finance/localizations/apac-ind-stock-transfer.md).</p> |

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

### <a name="wma"></a>Supply Chain Management- Warehousing (the warehouse app)

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Effective April 2021, *Supply Chain Management - Warehousing* (the warehouse app) is deprecated and won't be supported after April 2022. It is now replaced by the *Warehouse Management mobile app*, which was released with version 10.0.17 of Supply Chain Management. The new app is a complete replacement but uses same underlying framework, which makes migration easy. If needed, the two apps can be used side-by-side to help users gradually adjust as they learn to use the new app.<br><br>For more information about the new Warehouse Management mobile app, see [Warehouse Management mobile application](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/warehouse-management-mobile-application) and [Install and connect the Warehouse Management mobile app](../warehousing/install-configure-warehouse-management-app.md). |
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
| **Status**                         | Deprecated. On April 1, 2022, support for manufacturing scenarios was discontinued for the built-in master planning engine for Supply Chain Management. As of that date, Microsoft stopped all active development on manufacturing scenarios for the built-in planning engine, stopped releasing new features, and only released critical bug fixes.  Since that date, all companies that require support for manufacturing scenarios have been required to use Planning Optimization for their master planning calculations. For more information, see [Deprecated master planning overview](../master-planning/deprecated-master-planning-overview.md).<br><br>Since April 2022, only companies with on-premises deployments of Supply Chain Management have been able to continue using the built-in master planning engine for manufacturing scenarios. However, as of March 2023, Microsoft has now fully discontinued all support for the built-in master planning engine for all types of deployments. Hereafter, Microsoft will only provide support for critical blocking issues (which result in no planned orders being created or the continuous failure of built-in master planning). The built-in master planning engine is now referred to as the *deprecated master planning engine*. |

## Features removed or deprecated in the Supply Chain Management 10.0.11 release

### Use of built-in Supply Chain Management master planning engine for distribution scenarios

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | To enhance performance and minimize the SQL database load during master planning runs, the built-in Supply Chain Management master planning engine is being replaced by Planning Optimization. Planning Optimization allows for fast planning runs that can be performed even during office hours. This enables planners to react immediately to changes in demand or planning parameters. |
| **Replaced by another feature?**   | Yes, Planning Optimization will replace the existing built-in Supply Chain Management master planning engine. |
| **Product areas affected**         | Supply Chain Management - Master planning |
| **Deployment option**              | Cloud only. Planning Optimization is not supported with on-premises deployments. |
| **Status**                         | Deprecated. On April 1, 2021, support for distribution scenarios was discontinued for the built-in master planning engine for Supply Chain Management. Since then, customers running distribution scenarios have been required to use Planning Optimization for master planning calculations. For more information, see [Deprecated master planning overview](../master-planning/deprecated-master-planning-overview.md).<br><br>Since April 2021, only companies with on-premises deployments of Supply Chain Management have been able to continue using the built-in master planning engine for distribution scenarios. However, as of March 2023, Microsoft has now fully discontinued all support for the built-in master planning engine for all types of deployments. Hereafter, Microsoft will only provide support for critical blocking issues (which result in no planned orders being created or the continuous failure of built-in master planning). The built-in master planning engine is now referred to as the *deprecated master planning engine*. |

## Previous announcements about removed or deprecated features

To learn more about features that have been removed or deprecated in previous releases, see [Removed or deprecated features in previous releases](../../fin-ops-core/dev-itpro/migration-upgrade/deprecated-features.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]

