---
title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.24 (February 2022)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.24. 
author: kamaybac
ms.date: 12/03/2021
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this topic to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: kamaybac
ms.search.validFrom: 2021-12-03
ms.dyn365.ops.version: 10.0.24
---

# What's new or changed in Dynamics 365 Supply Chain Management 10.0.24 (February 2022)

[!include [banner](../includes/banner.md)]

This topic lists features that are either new or changed in the Microsoft Dynamics 365 Supply Chain Management version 10.0.24. This version has a build number of 10.0.1084 and is available as follows:

- **Preview of release:** December 2021
- **General availability of release (self-update):** January 2022
- **General availability of release (auto-update):** February 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this topic to include features that made it into the build after this topic was initially published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Distributed hybrid topology | [Enhanced warehouse execution workloads on scale units](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-supply-chain-management/enhanced-warehouse-execution-workloads-scale-units) | [Warehouse management workloads for cloud and edge scale units](../cloud-edge/cloud-edge-workload-warehousing.md) | Enabled by default. |
| Distributed hybrid topology | [Start production order on warehouse management workload for the cloud and edge scale unit](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-supply-chain-management/enhanced-manufacturing-execution-workloads-scale-units) | [Manufacturing execution workloads for cloud and edge scale units](../cloud-edge/cloud-edge-workload-manufacturing.md) | Feature management (*Start production order on warehouse management workload for the cloud and edge scale unit*)  |
| Planning | [Planning Optimization support for reorder margin and issue margin](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-supply-chain-management/planning-optimization-support-reorder-margin-issue-margin) | [Safety margins](../master-planning/planning-optimization/safety-margins.md) | Enabled by default. |

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

If you want to turn any of these features on or off, you must do that in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Module | Feature name in feature management | More information |
|---|---|---|
| Production control | On-demand material availability check for production orders | This feature makes it faster to open the **Production orders to release** page, which is available from the **Production floor management** workspace. Without this feature, the system automatically checks whether materials are available for all listed production orders as soon as you open the page, which can take significant time if you have a large number of orders. When this feature is enabled, the system instead provides a toolbar button, which you can use to initiate the materials check only for selected orders and when needed. |
| Production control | (Preview) Register material consumption on the production floor execution interface (non-WMS) | This feature enables workers to use the production floor execution interface to register material consumption, batch numbers, and serial numbers. This feature only supports items that are not enabled to use advanced warehouse processes (WMS). Support for WMS-enabled items is scheduled for a future release.<p>Some manufacturers, especially those within the process industries, need to explicitly register the amount of material consumed for each batch or production order. For example, workers might use a scale to weigh the amount of material consumed as they work. To ensure full material traceability, these organizations also need to register which batch numbers were consumed when producing each product. |
| Production control | Report as finished on warehouse management workload for the cloud and edge scale unit | This feature lets workers use the Warehouse Management mobile app to report a production or batch order as finished when the app is running against a warehouse management workload on a cloud or edge scale unit. For more information, see [Report as finished and putaway on a scale unit](../cloud-edge/cloud-edge-workload-manufacturing.md#RAF). |
| Warehouse management | New load planning workbench pages | Enables two new load planning workbench pages: **Inbound load planning workbench** and **Outbound load planning workbench**. |

## New and updated documentation resources

We have recently added or significantly updated the following help topics. These topics aren't necessarily related to the new features that were added for this release, as listed in the previous section. However, they might help you to get more out of existing features.

| Feature area | New or updated topics |
|---|---|
| Cost management | [Inventory value reports](../cost-management/inventory-value-report-storage.md) |
| Cost management | [Inventory value report examples and logic](../cost-management/inventory-value-report-examples.md) |
| Master planning | [Date and time parameters used by Planning Optimization](../master-planning/planning-optimization/date-time-used.md) |
| Master planning | [Demand forecasting setup](../master-planning/demand-forecasting-setup.md) |
| Master planning | [Use the safety stock journal to update minimum coverage for items](../master-planning/safety-stock-journal.md) |
| Production control | [Customize the production floor execution interface](../production-control/production-floor-execution-customize.md) |
| Production control | [Style the production floor execution interface](../production-control/production-floor-execution-styles.md) |
| Sales and marketing | [Schedule sales history data cleanup](../sales-marketing/sales-update-history-cleanup-performance-improvements.md) |
| Warehouse management | [Mobile device user accounts](../warehousing/mobile-device-work-users.md) |

## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.24 includes platform updates. To learn more, see [Platform updates for version 10.0.24 of Finance and Operations apps (February 2022)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-24.md).

### Bug fixes

For information about the bug fixes included in each of the updates that are part of 10.0.24, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=641306&dbType=3&qc=5b1d5e49c96b8a5cfb5601889a413e6f3773ba6500f9bc47310dcc5c54fff42f).

### Dynamics 365 and industry clouds: 2021 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2021 release wave 2 plan](/dynamics365-release-plan/2021wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) topic describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
