---
title: Removed or deprecated features in Dynamics 365 Supply Chain Management
description: Learn about features that have been removed, deprecated, or that are planned for removal in Dynamics 365 Supply Chain Management.
author: kamaybac
ms.author: kamaybac
ms.topic: conceptual
ms.date: 06/14/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Removed or deprecated features in Dynamics 365 Supply Chain Management

[!include [banner](../includes/banner.md)]

This article will be updated as new removed or deprecated features are documented for Dynamics 365 Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

This list is intended to help you consider these removals and deprecations for your own planning.

> [!NOTE]
> Detailed information about objects in finance and operations apps can be found in the [Technical reference reports](/dynamics/s-e/). You can compare the different versions of these reports to learn about objects that have changed or been removed in each version of finance and operations apps.

## Features removed or deprecated in the Supply Chain Management 10.0.41 release

### Pricing management module

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | The Pricing management module is being replaced by the new [Unified pricing management module](../unified-pricing-management/upm-pricing-management-overview.md). |
| **Replaced by another feature?**  | Yes, the Pricing management module is being replaced by the new [Unified pricing management module](../unified-pricing-management/upm-pricing-management-overview.md). |
| **Product areas affected** | Supply Chain Management – Pricing management |
| **Deployment option** | Cloud and on-premises |
| **Status** | Deprecated. Approximately one year after the release of version 10.0.41, the Pricing management module will no longer be supported and may eventually be removed from the product. |

### Job card terminal

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | The job card terminal is being replaced by the new [production floor execution interface](../production-control/production-floor-execution-use.md). |
| **Replaced by another feature?**   | Yes, the job card terminal is to be replaced by the new [production floor execution interface](../production-control/production-floor-execution-use.md). |
| **Product areas affected** | Supply Chain Management – production control |
| **Deployment option** | Cloud and on-premises |
| **Status** | Deprecated. Approximately one year after the release of version 10.0.41, the job card terminal will no longer be supported and may eventually be removed from the product. |

### Inventory transactions support for internal warehouse operations

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | Using inventory transactions to track on-hand inventory for internal warehouse operations has well-known performance issues. |
| **Replaced by another feature?**   | Yes. [Warehouse-specific inventory transactions](../warehousing/warehouse-transactions.md), which have been available since version 10.0.32, replace the older inventory transactions for tracking internal warehouse operations.  |
| **Product areas affected** | Supply Chain Management – Warehouse management |
| **Deployment option** | Cloud and on-premises |
| **Status** | <p>Supported until version 10.0.40. As of version 10.0.41, inventory transactions will be deprecated for tracking on-hand inventory for internal warehouse operations. Existing customers will be able to continue using this scenario after that version, but new features and bug fixes for this scenario will only be implemented for [warehouse-specific inventory transactions](../warehousing/warehouse-transactions.md).</p><p>Approximately one year after the release of version 10.0.41, support for this scenario will be removed and all customers will be required to move to [warehouse-specific inventory transactions](../warehousing/warehouse-transactions.md) for tracking on-hand inventory for internal warehouse operations.</p> |

### Release to warehouse page

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | The **Release to warehouse** page has performance issues. |
| **Replaced by another feature?**   | Yes. The  **Release to warehouse** page has been split into two new release to warehouse pages, which together provide equivalent functionality with significantly improved performance. The new pages are **Release sales orders to warehouse** and **Release transfer orders to warehouse**. |
| **Product areas affected** | Supply Chain Management – Release to warehouse |
| **Deployment option** | Cloud and on-premises |
| **Status** | <p>Deprecated. The **Release to warehouse** page is now hidden in the app, but you can enable it if necessary by contacting Microsoft Support. We strongly recommend that you instead use the new pages (**Release sales orders to warehouse** and **Release transfer orders to warehouse**) because they provide equivalent functionality with significantly improved performance. The **Release to warehouse** page will be completely removed from the product one year after the release of Supply Chain Management version 10.0.41.</p> |

## Features removed or deprecated in the Supply Chain Management 10.0.40 release

### Scale unit capability for Supply Chain Management

| &nbsp;  | &nbsp;  |
|---|---|
| Reason for deprecation/removal | The scale unit capability for Microsoft Dynamics 365 Supply Chain Management has been paused for new customers since July 2022 and is now deprecated. |
| Replaced by another feature? | Yes. [Warehouse management only mode](../warehousing/wms-only-mode-overview.md) replaces some of the functionality planned for scale units and adds many new architectural and integration possibilities. |
| Product areas affected | Supply Chain Management – Warehouse management<br><br>Supply Chain Management – Production control |
| Deployment options | Cloud and on-premises |
| Status | The scale unit capability for Microsoft Dynamics 365 Supply Chain Management has been paused for new customers since July 2022. The capability is formally deprecated as of Supply Chain Management version 10.0.40 and will be completely removed for all customers one year after the release of that version. |

## Features removed or deprecated in the Supply Chain Management 10.0.39 release

### Load planning workbench

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | The **Load planning workbench** page has performance issues. |
| **Replaced by another feature?**   | Yes. The  **Load planning workbench** page has been split into two new workbench pages, which together provide equivalent functionality with significantly improved performance. The new pages are **Inbound load planning workbench** and **Outbound load planning workbench**. |
| **Product areas affected** | <p>Supply Chain Management – Warehouse management</p><p>Supply Chain Management – Transportation management</p> |
| **Deployment option** | Cloud and on-premises |
| **Status** | <p>Deprecated. The **Load planning workbench** page is now hidden in the app, but you can enable it if necessary by contacting Microsoft Support. We strongly recommend that you instead use the new pages (**Inbound load planning workbench** and **Outbound load planning workbench**) because they provide equivalent functionality with significantly improved performance. The **Load planning workbench** page will be completely removed from the product one year after the release of Supply Chain Management version 10.0.39.</p> |

## Features removed or deprecated in the Supply Chain Management 10.0.37 release

### Service-based authentication methods for the Warehouse Management mobile app

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | Support for service-based authentication methods (certificate and shared secret) is being removed to improve security. |
| **Replaced by another feature?**   | Yes. Service-based authentication is being replaced by user-based authentication (device code flow), which is more secure. |
| **Product areas affected** | Supply Chain Management – Warehouse management |
| **Deployment option** | Cloud and on-premises |
| **Status** | <p>Deprecated. As of July 15, 2024, Microsoft will discontinue support for using service-based authentication methods (certificate and shared secret) to connect the Warehouse Management mobile app to Supply Chain Management. Service-based authentication is being replaced by user-based authentication (device code flow). Administrators must update all devices to use user-based authentication before July 15, 2024. For more information about device code flow, see [User-based authentication FAQ](../warehousing/warehouse-app-user-based-auth-faq.md) and [User-based authentication](../warehousing/warehouse-app-authenticate-user-based.md).</p><p>Mass deployment with Microsoft Intune isn't yet supported for user-based authentication, but we expect to add support for it soon. For more information and the latest news about mass deploying to mobile devices for user-based authentication, see [Mass deploy the mobile app with user-based authentication](../warehousing/warehouse-app-intune-user-based.md).</p> |

## Features removed or deprecated in the Supply Chain Management 10.0.35 release

### Integration with Outlook for contacts, appointments, and tasks

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | Exchange web service API is transitioning from SOAP to REST. |
| **Replaced by another feature?**   | No replacement is planned. We recommend that customers integrate with Dynamics 365 Sales. |
| **Product areas affected** | Supply Chain Management – sales and marketing |
| **Deployment option** | Cloud and on-premises |
| **Status** | <p>Deprecated. As of December 1, 2023, Microsoft will discontinue support for synchronizing contacts, appointments, and tasks between Supply Chain Management and Outlook. In addition, security updates will no longer be provided for these features.</p><p>This functionality is being discontinued because the existing integration is based on SOAP. However, Exchange Web Service (EWS) is transitioning from SOAP to REST and will support only REST going forward. There are no plans to add REST support for Outlook integration in Supply Chain Management.</p><p>As of May 1, 2024, it will no longer be possible to synchronize the following types of records between Supply Chain Management and Outlook:</p><ul><li>Contacts</li><li>Appointment activities</li><li>Task activities</li></ul><p>To prepare for this change, redesign any extensions that you've made to any of these capabilities to remove the dependency.</p><p>To support customer relations management scenarios, consider integrating Dynamics 365 Sales with Outlook and/or using dual-write to synchronize contacts for customer accounts between Supply Chain Management and Dynamics 365 Sales. (Learn more in [Integrated customer master](../../fin-ops-core/dev-itpro/data-entities/dual-write/customer-mapping.md).)</p> |

## Features removed or deprecated in the Supply Chain Management 10.0.29 release

### Stock transfer orders that have tax on the transfer price

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | The [Stock transfer orders that have tax on the transfer price](../../finance/localizations/apac-ind-gst-stock-transfer-transactions.md) functionality is being replaced by the [Stock transfer orders for India](../../finance/localizations/apac-ind-stock-transfer.md) functionality. |
| **Replaced by another feature?**   | Yes, the [Stock transfer orders that have tax on the transfer price](../../finance/localizations/apac-ind-gst-stock-transfer-transactions.md) functionality is being replaced by the [Stock transfer orders for India](../../finance/localizations/apac-ind-stock-transfer.md) functionality. |
| **Product areas affected** | Supply Chain Management – inventory |
| **Deployment option** | Cloud and on-premises |
| **Status** | <p>Removed. The *Stock transfer orders that have tax on the transfer price* functionality has been removed as of October 2023. Customers must instead use the improved functionality, *Stock transfer orders for India*. Learn more in [Stock transfer orders for India](../../finance/localizations/apac-ind-stock-transfer.md).</p> |

## Features removed or deprecated in the Supply Chain Management 10.0.19 release

### Job card device

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | The job card device is replaced by the [production floor execution interface](../production-control/production-floor-execution-configure.md). |
| **Replaced by another feature?**   | Yes, the job card device is replaced by the [production floor execution interface](../production-control/production-floor-execution-configure.md). |
| **Product areas affected** | Supply Chain Management – production control |
| **Deployment option** | Cloud and on-premises |
| **Status** | Unsupported. As of April 2022, the job card device is no longer supported and customers must use the new production floor execution interface. |

## Features removed or deprecated in the Supply Chain Management 10.0.18 release

### <a name="wma"></a>Supply Chain Management- Warehousing (the warehouse app)

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Effective April 2021, *Supply Chain Management – Warehousing* (the warehouse app) is deprecated and won't be supported after April 2022. It's now replaced by the *Warehouse Management mobile app*, which was released with version 10.0.17 of Supply Chain Management. The new app is a complete replacement but uses same underlying framework, which makes migration easy.<br><br>For more information about the new Warehouse Management mobile app, see [Warehouse Management mobile application](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/warehouse-management-mobile-application) and [Install the Warehouse Management mobile app](../warehousing/install-configure-warehouse-management-app.md). |
| **Replaced by another feature?**   | Yes, replaced by the new Warehouse Management mobile app. |
| **Product areas affected**         | Supply Chain Management – warehouse app |
| **Deployment option**              | Cloud and on-premises |
| **Status**                         | Removed. As of April 2022, the old warehouse app is no longer supported and has been removed from the Microsoft Store and Google Play store. Customers must now use the new Warehouse Management mobile app instead. |

## Features removed or deprecated in the Supply Chain Management 10.0.15 release

### Internet Explorer 11 support for Dynamics 365 is deprecated

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Effective August 2021, Microsoft Internet Explorer 11 is no longer supported for use with Dynamics 365 products. |
| **Replaced by another feature?**   | We recommend that customers transition to Microsoft Edge.|
| **Product areas affected**         | All Dynamics 365 products |
| **Deployment option**              | All|
| **Status**                         | Removed. Support for Internet Explorer 11 was removed in August 2021.|

### Use of built-in Supply Chain Management master planning engine for manufacturing scenarios

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | To enhance performance and minimize the SQL database load during master planning runs, the built-in Supply Chain Management master planning engine is being replaced by Planning Optimization. Planning Optimization allows for fast planning runs that can be performed even during office hours. This enables planners to react immediately to changes in demand or planning parameters. |
| **Replaced by another feature?**   | Yes, Planning Optimization will replace the existing built-in Supply Chain Management master planning engine. |
| **Product areas affected**         | Supply Chain Management – Master planning |
| **Deployment option**              | Cloud only. Planning Optimization is not supported with on-premises deployments. |
| **Status**                         | Deprecated. On April 1, 2022, support for manufacturing scenarios was discontinued for the built-in master planning engine for Supply Chain Management. As of that date, Microsoft stopped all active development on manufacturing scenarios for the built-in planning engine, stopped releasing new features, and only released critical bug fixes.  Since that date, all companies that require support for manufacturing scenarios have been required to use Planning Optimization for their master planning calculations. Learn more in [Deprecated master planning overview](../master-planning/deprecated-master-planning-overview.md).<br><br>Since April 2022, only companies with on-premises deployments of Supply Chain Management have been able to continue using the built-in master planning engine for manufacturing scenarios. However, as of March 2023, Microsoft has now fully discontinued all support for the built-in master planning engine for all types of deployments. Hereafter, Microsoft will only provide support for critical blocking issues (which result in no planned orders being created or the continuous failure of built-in master planning). The built-in master planning engine is now referred to as the *deprecated master planning engine*. |

## Features removed or deprecated in the Supply Chain Management 10.0.11 release

### Use of built-in Supply Chain Management master planning engine for distribution scenarios

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | To enhance performance and minimize the SQL database load during master planning runs, the built-in Supply Chain Management master planning engine is being replaced by Planning Optimization. Planning Optimization allows for fast planning runs that can be performed even during office hours. This enables planners to react immediately to changes in demand or planning parameters. |
| **Replaced by another feature?**   | Yes, Planning Optimization will replace the existing built-in Supply Chain Management master planning engine. |
| **Product areas affected**         | Supply Chain Management – Master planning |
| **Deployment option**              | Cloud only. Planning Optimization isn't supported for on-premises deployments. |
| **Status**                         | Removed. On April 1, 2021, support for distribution scenarios was discontinued for the built-in master planning engine for Supply Chain Management. Since then, customers running distribution scenarios have been required to use Planning Optimization for master planning calculations. Learn more in [Deprecated master planning overview](../master-planning/deprecated-master-planning-overview.md).<br><br>Since April 2021, only companies with on-premises deployments of Supply Chain Management have been able to continue using the built-in master planning engine for distribution scenarios. However, as of March 2023, Microsoft has now fully discontinued all support for the built-in master planning engine for all types of deployments. Hereafter, Microsoft will only provide support for critical blocking issues (which result in no planned orders being created or the continuous failure of built-in master planning). The built-in master planning engine is now referred to as the *deprecated master planning engine*. |

## Previous announcements about removed or deprecated features

To learn more about features that have been removed or deprecated in previous releases, see [Removed or deprecated features in previous releases](../../fin-ops-core/dev-itpro/migration-upgrade/deprecated-features.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
