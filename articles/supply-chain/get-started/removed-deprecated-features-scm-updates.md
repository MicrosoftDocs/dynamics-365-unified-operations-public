---
title: Removed or deprecated features in Dynamics 365 Supply Chain Management
description: Learn about features that have been removed, deprecated, or that are planned for removal in Dynamics 365 Supply Chain Management.
author: kamaybac
ms.author: kamaybac
ms.topic: article
ms.date: 08/28/2025
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

## Features removed or deprecated in the Supply Chain Management 10.0.45 release

### Inventory On-hand mobile app (preview)

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | Microsoft has decided not to continue development and support for this preview feature. |
| **Replaced by another feature?** | Yes |
| **Product areas affected** | Supply Chain Management – Inventory management |
| **Deployment option** | Cloud and on-premises |
| **Status** | Removed. The *Inventory On-hand mobile app* preview (previously available on the Power Platform Admin Center) was never made generally available. It's now provided as a sample app that you can download from the [scmsamples-InventoryOnHand repository on GitHub](https://github.com/microsoft/scmsamples-InventoryOnHand) and customize as needed. Learn more in [Inventory On-hand mobile app](../inventory/inventory-onhand-mobile-app.md). |

## Features removed or deprecated in the Supply Chain Management 10.0.44 release

### Inquire into inventory with Copilot (preview)

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | Microsoft has decided not to continue development on this preview feature. |
| **Replaced by another feature?** | No |
| **Product areas affected** | Supply Chain Management – Inventory management |
| **Deployment option** | Cloud and on-premises |
| **Status** | Removed. This preview feature was never made generally available and is now completely removed from the [Inventory Visibility service](../inventory/inventory-visibility.md). |

### SHA1 hashing in the InventDim table

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | To ensure that data in the `InventDim` table is unique and easy to search for, the system hashes some of its data. The system previously used SHA1 hashing, which is now outdated, so we're replacing it with SpookyHash. |
| **Replaced by another feature?** | Yes. SHA1 hashing is being replaced by SpookyHash. |
| **Product areas affected** | Supply Chain Management – Inventory |
| **Deployment option** | Cloud and on-premises |
| **Status** | As of Supply Chain Management version 10.0.44, the system uses SpookyHash instead of SHA1 to hash data in the `InventDim` table. When you upgrade to version 10.0.44, the system automatically schedules a batch job that converts all `InventDim` data hashed using SHA1 to instead use SpookyHash. Version 10.0.44 can work with both SHA1 and SpookyHash data, but support for SHA1 will be removed in a future release. Extensibility was never supported for this part of the application, but if you have external code that uses SHA1 when creating, updating, or searching data in the `InventDim` table, you must stop using that code before upgrading to Supply Chain Management 10.0.44 because it will corrupt your data. |

### Rename item number (preview)

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | The item number field is a primary key that is used across multiple systems. The *(Preview) Rename item number* feature allowed users to edit the item number field, but we found that the feature could cause data inconsistencies in multi-system and apps-integration scenarios, leading to data integrity and data corruption issues. The feature was previously in preview and was never made generally available for use in production environments. |
| **Replaced by another feature?** | No |
| **Product areas affected** | Supply Chain Management – Product information management |
| **Deployment option** | Cloud and on-premises |
| **Status** | The *(Preview) Rename item number* feature was removed from the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace in Dynamics 365 Supply Chain Management version 10.0.44 and is no longer available. The capability is completely removed for all customers. If you need to rename an item number, we recommend that you use alternate methods, such as deleting and creating a new item, renaming attributes, or renaming search names, product names, and other item-related fields. |

## Features removed or deprecated in the Supply Chain Management 10.0.43 release

### The "Work creation number" number sequence has been removed

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | The *Work creation number* number sequence could sometimes create problems when the same prefixes were used for other number sequences. |
| **Replaced by another feature?** | Yes, the *Work creation number* number sequence and been replaced by the *Work creation ID* number sequence. The *Work creation ID* number sequence is designed to avoid conflicts with other number sequences. |
| **Product areas affected** | Supply Chain Management – Warehouse management |
| **Deployment option** | Cloud and on-premises |
| **Status** | Previously, there were two number sequences that were used to generate values for the **Work creation number** field for work records (*Work creation ID* and *Work creation number*). The newer *Work creation ID* number sequence has been available as a replacement for *Work creation number* for some time. For all currently available versions of Supply Chain Management (not just version 10.0.43 and later), you should always use the *Work creation ID* number sequence to generate work creation identification numbers. Although the *Work creation number* sequence is still present in the demo data, it's no longer used by the system and production data doesn't include the *Work creation number* number sequence. You can set up the *Work creation ID* number sequence on the **Warehouse management parameters** page. |

### "Adjustment out" mobile device menu items must now use process guide

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | The [process guide framework](../supply-chain-dev/process-guide-framework.md) offers enhanced extensibility support and allows for easier changes in the feature behavior. The framework will now be required for all mobile device menu items that use the *Adjustment out* work creation process. |
| **Replaced by another feature?**  | No. The process guide framework will be required for all mobile device menu items that use the *Adjustment out* work creation process. The ability to turn off this option is being removed from the product. |
| **Product areas affected** | Supply Chain Management – Warehouse management |
| **Deployment option** | Cloud and on-premises |
| **Status** | The **Use process guide** setting for mobile device menu items that use the *Adjustment out* work creation process will be made mandatory in Supply Chain Management version 10.0.45. Approximately one year after the release of version 10.0.45, the non-process guide implementation will no longer be supported and may eventually be removed from the product. Learn more in [Set up mobile device menu items for adjustment in and adjustment out](../warehousing/reason-codes-for-counting-journals.md#setup-adjustment-in-out). |

### "Spot cycle counting" mobile device menu items must now use process guide

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | The [process guide framework](../supply-chain-dev/process-guide-framework.md) offers enhanced extensibility support and allows for easier changes in the feature behavior. The framework will now be required for all mobile device menu items that use the *Spot cycle counting* work creation process. |
| **Replaced by another feature?**  | No. The process guide framework will be required for all mobile device menu items that use the *Spot cycle counting* work creation process. The ability to turn off this option is being removed from the product. |
| **Product areas affected** | Supply Chain Management – Warehouse management |
| **Deployment option** | Cloud and on-premises |
| **Status** | The **Use process guide** setting for mobile device menu items that use the *Spot cycle counting* work creation process will be enabled by default in Supply Chain Management version 10.0.45, and it will be made mandatory in version 10.0.47. Approximately one year after the release of version 10.0.47, the non-process guide implementation will no longer be supported and may eventually be removed from the product. Learn more in [Set up mobile devices for warehouse work](../warehousing/configure-mobile-devices-warehouse.md). |

## Features removed or deprecated in the Supply Chain Management 10.0.42 release

### Register material consumption on the production floor execution interface (WMS-enabled) (preview)

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | The *Register material consumption on the production floor execution interface (WMS-enabled)* feature (previously in preview) has been replaced by the *Register material consumption as complete and edit dimensions on the production floor execution interface* feature. |
| **Replaced by another feature?**  | Yes. The *Register material consumption on the production floor execution interface (WMS-enabled)* feature (previously in preview) has been replaced by the *[Register material consumption as complete and edit dimensions on the production floor execution interface](../production-control/production-floor-execution-configure.md#material-consumption)* feature, which also adds the ability to use the production floor execution interface to register material consumption for WMS-enabled items. |
| **Product areas affected** | Supply Chain Management – Production control |
| **Deployment option** | Cloud and on-premises |
| **Status** | Removed. As of Supply Chain Management version 10.0.41, if you never enabled the old *Register material consumption on the production floor execution interface (WMS-enabled)* feature, then you'll only see the newer *Register material consumption as complete and edit dimensions on the production floor execution interface* feature in feature management. If you previously enabled the old feature, you'll still be able to use it, but you'll soon be contacted by Microsoft Support with instructions on how to replace it with the newer feature. |

## Features removed or deprecated in the Supply Chain Management 10.0.41 release

### Pricing management module (preview)

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | The Pricing management module (previously in preview) is being replaced by the new [Unified pricing management module](../unified-pricing-management/upm-pricing-management-overview.md). |
| **Replaced by another feature?**  | Yes, the Pricing management module is being replaced by the new [Unified pricing management module](../unified-pricing-management/upm-pricing-management-overview.md). |
| **Product areas affected** | Supply Chain Management – Pricing management |
| **Deployment option** | Cloud and on-premises |
| **Status** | Deprecated and will be removed in a future release. It is replaced by the [Unified pricing management module](../unified-pricing-management/upm-pricing-management-overview.md), which offers nearly all of the same functionality as the deprecated Pricing management module, plus several important enhancements. Both the deprecated pricing management module and the Unified pricing management module use similar or identical navigation paths in the Supply Chain Management user interface, so only one of these modules can be active at a time. As of Supply Chain Management version 10.0.41, if you never enabled the deprecated pricing management module in your environment, only the Unified pricing management module will be available to you. If you have enabled the deprecated pricing management module, you can continue to use it until it is removed, but we recommend that you transition to the Unified pricing management module as soon as possible to take advantage of the new features and enhancements that it offers. For help transitioning from the deprecated pricing management module to the Unified pricing management module, please contact Microsoft Support. |

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
