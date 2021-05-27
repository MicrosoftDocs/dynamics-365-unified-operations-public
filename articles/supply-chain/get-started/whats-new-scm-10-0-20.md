---
title: Preview of Dynamics 365 Supply Chain Management 10.0.20 (July 2021) 
description: This topic describes features that are either new or changed in Dynamics 365 Supply Chain Management 10.0.20. 
author: kamaybac
ms.date: 05/28/2021
ms.topic: article
# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: kamaybac
ms.search.validFrom: 2021-05-28
ms.dyn365.ops.version: 10.0.20
---

# Preview of Dynamics 365 Supply Chain Management 10.0.20 (July 2021)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic lists features that are either new or changed in the Microsoft Dynamics 365 Supply Chain Management preview of version 10.0.20. This version has a build number of 10.0.889 and is available as follows:

- **Preview of release:** May 2021
- **General availability of release (self-update):** June 2021
- **General availability of release (auto-update):** July 2021

## Features included in this release

The following table lists the features included in this release. The *Feature* column provides links to the [release plan](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/planned-features), where you can see the official release dates for each feature. The *More information* column provides more details and/or links to related documentation.

Most of these features must be enabled using [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) before you can use them. Some of the listed features are still in preview, while others may already be generally available.

| Feature area | Feature | More information |
|---|---|---|
| Inventory and logistics | [Sales order details performance enhancement](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/sales-order-details-performance-enhancement) | This feature improves performance when opening sales order details. When this feature is enabled, It aligns the sales side to use the one-form pattern used on the purchase side by skipping the SalesTableListPage and open the SalesTable form in list view mode when a user accesses the menu All sales orders and similar list pages for sales. When this feature is disabled, then the SalesTableListPage is called. |
| Manufacturing | [Invoke process automation flows to create quality orders](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/invoke-process-automation-flows-create-quality-orders) | *Coming soon* <!-- KFM: Add link to new doc --> |
| Manufacturing | [Enhanced production floor execution interface for manufacturing](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/enhanced-production-floor-execution-interface-manufacturing) | [Configure the production floor execution interface](../production-control/production-floor-execution-configure.md) |
| Product information management | [Manage changes in formulas and their ingredients](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/engineering-change-management-support-process-manufacturing) | <!-- KFM: Add link to new doc --> |
| Product information management | [Product readiness checks](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/product-readiness-checks) | <!-- KFM: Add link to new doc -->  |

## Feature enhancements included in this release

The following table lists the feature enhancements included in this release. Each of these provides an incremental improvement to an existing feature. Because they are only enhancements, they are not listed on the [release plan](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted). If you want to use any of these features, you must explicitly enable them in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Feature area | Feature&nbsp;name&nbsp;in feature&nbsp;management | More information |
|---|---|---|
| Master planning | Negative days for Planning Optimization | This feature enables Planning Optimization to consider the **Negative days** parameter defined on coverage groups. |
| Master planning | Parallel authorizing of adjusted demand forecast | This feature allows parallel authorizing of adjusted demand forecast from the **Adjusted demand forecast** page. The intent of this feature is to increase performance when a high number of forecasts are being authorized. When authorizing, the user can specify the **Number of threads** in the authorizing dialog. |
| Master planning | (Preview) Batchable firming and consolidation for planned bulk and pack batch orders | This feature lets you use batch jobs to firm and consolidate planned bulk and pack orders. |
| Master planning | (Preview) Priority driven MRP support for Planning Optimization | This Planning Optimization preview feature enables master planning driven by planning priority with reorder point. Highlighted changes:<ul><li>**Planning priority** field on sales order line, purchase order line, demand forecast, and planned orders.</li><li>A new Coverage code option</li><li>**Item coverage** field for reorder point.</li><li>Master planning setup forms to control the planning priority setup.</li><li>Planning Optimization calculation logic to set and respect planning priority</li></ul> |
| Production control | Update related resource requirements when a route operation is changed | This feature enables the system to update the related resource requirements after a user changes the operation of an existing route step. |
| Production control | Copy generic routes | This feature enhances the copy route function to allow users to copy routes that aren't item specific. It enables the system to update all relevant information (such as site, route group, resource requirements, and various times) after the copy route function has been used to overwrite a route that is not yet assigned to an item. |





## New and updated documentation resources

We have recently added or significantly updated the following help topics. They aren't necessarily related to the new features added for this release, as listed in the previous section, but they may help you to get more out of existing features.

| Feature area | New or updated topics |
|---|---|
| Procurement and sourcing | [Maintain vendor certification](../../finance/public-sector/manage-vendor-certification.md) |
| Inventory management | [Quality and nonconformance management overview](../inventory/quality-management-processes.md) (plus all related quality-management topics) |
| Warehouse management | [Deferred processing of manual inventory movement](../warehousing/deferred-processing-manual-inventory-movement.md) |
|  | [User interface control styles for production floor execution](../production-control/production-floor-execution-styles.md) |

## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.20 includes platform updates. To learn more, see [Platform updates for version 10.0.20 of Finance and Operations apps (July 2021)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-20.md). <!-- KFM: Confirm link -->

### Bug fixes

For information about the bug fixes included in each of the updates that are part of 10.0.20, sign in to Lifecycle Services (LCS) and view the [KB article](#). <!-- KFM: Get new link -->

### Dynamics 365: 2021 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2021 release wave 1 plan](/dynamics365-release-plan/2021wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) topic describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
