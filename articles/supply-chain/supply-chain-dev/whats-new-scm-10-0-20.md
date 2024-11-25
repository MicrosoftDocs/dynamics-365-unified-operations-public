---
title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.20 (August 2021) 
description: Learn about features that are either new or changed in Dynamics 365 Supply Chain Management 10.0.20 with an outline on included features. 
author: kamaybac
ms.author: kamaybac
ms.topic: conceptual
ms.date: 05/28/2024
ms.custom:
  - bap-template
  - evergreen
ms.reviewer: kamaybac
ms.search.form:
---

# What's new or changed in Dynamics 365 Supply Chain Management 10.0.20 (August 2021)

[!include [banner](../../finance/includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management version 10.0.20. This version has a build number of 10.0.886 and is available as follows:

- **Preview of release:** May 2021
- **General availability of release (self-update):** July 2021
- **General availability of release (auto-update):** August 2021

## Features included in this release

The following table lists the features included in this release. The *Feature* column provides links to the [release plan](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/planned-features), where you can see the official release dates for each feature. The *More information* column provides more details and/or links to related documentation.

Most of these features must be enabled using [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) before you can use them.

| Feature area | Feature | More information |
|---|---|---|
| Inventory&nbsp;and&nbsp;logistics | [Sales order details performance enhancement](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/sales-order-details-performance-enhancement) | This feature makes the user interface more responsive when opening sales orders, especially orders that include many lines. |
| Manufacturing | [Invoke process automation flows to create quality orders](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/invoke-process-automation-flows-create-quality-orders) | [Invoke process automation flows to create quality orders](../production-control/process-automation-quality-orders.md ) |
| Manufacturing | [Enhanced production floor execution interface for manufacturing](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/enhanced-production-floor-execution-interface-manufacturing) | [Configure the production floor execution interface](../production-control/production-floor-execution-configure.md) |
| Planning | [Infinite capacity scheduling for Planning Optimization](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/schedule-infinite-capacity-support-planning-optimization) | [Scheduling with infinite capacity](../master-planning/planning-optimization/infinite-capacity-planning.md) |
| Product information management | [Manage changes in formulas and their ingredients](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/engineering-change-management-support-process-manufacturing) | [Manage changes in formulas and their ingredients](../engineering-change-management/manage-formula-changes.md) |
| Product information management | [Product readiness checks](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/product-readiness-checks) | [Product readiness](../engineering-change-management/product-readiness.md) |

## Feature enhancements included in this release

The following table lists the feature enhancements included in this release. Each of these provides an incremental improvement to an existing feature. Because they are only enhancements, they are not listed in the [release plan](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted). If you want to use any of these features, you must explicitly enable them in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Module | Feature&nbsp;name&nbsp;in feature&nbsp;management | More information |
|---|---|---|
| Master planning | Parallel authorizing of adjusted demand forecast | This feature allows parallel authorizing of adjusted demand forecast from the **Adjusted demand forecast** page. The intent of this feature is to increase performance when a high number of forecasts are being authorized. When authorizing, the user can specify the **Number of threads** in the authorizing dialog. |
| Master planning | Batchable firming and consolidation for planned bulk and pack batch orders | This feature lets you use batch jobs to firm and consolidate planned bulk and pack orders. |
| Production control | Copy generic routes | This feature enhances the copy route function to allow users to copy routes that aren't item specific. It enables the system to update all relevant information (such as site, route group, resource requirements, and various times) after the copy route function has been used to overwrite a route that is not yet assigned to an item. |
| Production control | Update related resource requirements when a route operation is changed | This feature enables the system to update the related resource requirements after a user changes the operation of an existing route step. |
| Product information management | Bill of materials report pre-processing to prevent timeout | This feature causes the bill of materials report to be pre-processed. This will avoid timeout issues when having a large data load for the report. |
| Procurement and sourcing | Enable resetting procurement related workflows | This preview feature allows you to reset the following workflows to draft status: Purchase Order, Vendor Change, and Purchase Requisitions. |
| Transportation management | Enable creation of a vendor invoice journal when discarding a freight bill | When this feature is enabled, a corresponding vendor invoice journal will only be created for reconciliation reasons when you are using the pay-vendor option. Otherwise, the invoice journal will always be created. |
| Warehouse management | Validate templates selected for replenishment jobs | This feature helps ensure that users select valid replenishment templates when setting up a replenishment job. It prevents users from creating a replenishment job without a template and from selecting templates of type *Wave demand*, which won't create any replenishment work and may take a long time to process. |

## New and updated documentation resources

We have recently added or significantly updated the following help articles. They aren't necessarily related to the new features added for this release, as listed in the previous section, but they may help you to get more out of existing features.

| Feature area | New or updated articles |
|---|---|
| Engineering change management | [Product lifecycle states and transactions](../engineering-change-management/product-lifecycle-state-transactions.md) |
| Inventory management | [Inventory Visibility Add-in](../inventory/inventory-visibility.md)<br><br>[Quality and nonconformance management overview](../inventory/quality-management-processes.md) (plus all related quality-management articles) |
| Procurement and sourcing | [Maintain vendor certification](../../finance/public-sector/manage-vendor-certification.md) |
| Production control | [Style the production floor execution interface](../production-control/production-floor-execution-styles.md) |
| Warehouse management | [Assign step icons and titles for the Warehouse Management mobile app](../warehousing/step-icons-titles.md)<br><br>[Deferred processing of manual inventory movement](../warehousing/deferred-processing-manual-inventory-movement.md) |

## Related information

### Platform updates for finance and operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.20 includes platform updates. Learn more in [Platform updates for version 10.0.20 of finance and operations apps (July 2021)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-20.md).

### Bug fixes

For information about the bug fixes included in each of the updates that are part of 10.0.20, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=586707&dbType=3&qc=d0dad8eee2af234e8c288e2a7df14c579004518673d014be511f900cfed008f8). 

### Dynamics 365: 2021 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2021 release wave 1 plan](/dynamics365-release-plan/2021wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](../get-started/removed-deprecated-features-scm-updates.md) article describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](../get-started/removed-deprecated-features-scm-updates.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]

