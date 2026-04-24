---
title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.48 (June 2026)
description: Learn about features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.48 with a table outlining feature areas. 
author: kamaybac
ms.author: kamaybac
ms.reviewer: kamaybac
ms.search.form:
ms.topic: whats-new
ms.date: 04/24/2026
ms.update-cycle: 1095-days
ms.custom:
  - bap-template
  - evergreen
---

# What's new or changed in Dynamics 365 Supply Chain Management 10.0.48 (June 2026)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management version 10.0.48. This version has a build number of 10.0.x <!-- KFM: Get build number --> and is available on the following schedule:

- **Preview of release:** April 2026
- **General availability of release (self-update):** June 2026
- **General availability of release (auto-update):** July 2026

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature | More information | Enabled by |
| --- | --- | --- | --- |
| Procurement and sourcing | Manage the downstream impact of PO changes with Procurement Agent impact analysis | *Coming soon* | Feature management:<ul><li>*(Production ready preview) Agent management*</li><li>*(Production-ready preview) Procurement Agent - Impact analysis*</li></ul> |
| Procurement and sourcing | Try out the *updates from vendors* feature without a complete email setup |  |  Enabled by default |
| Warehouse management | Cluster picking strategy | [Cluster picking strategy](../warehousing/set-up-cluster-picking.md#cluster-picking-strategy) | Enabled by default |
| Warehouse management | Warehouse spatial location | [Warehouse spatial location overview (preview)](../warehousing/spatial-location-overview.md) | Feature management:<br>*Warehouse spatial location* |

## <a name="enhancements"></a>Feature enhancements added in this release

The following table lists the feature enhancements that were added in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they're only enhancements, they're not listed in the [release plan](/dynamics365/release-plan/2024wave2/finance-supply-chain/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements don't conflict with your existing customizations or preferences, each enhancement is turned off by default (unless otherwise noted).

Some of these features aren't visible on your system until you turn them on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) by using the name listed here for the *Feature management name* (additional configuration might also be needed). Features that don't show a feature management name are visible by default as of this version of Supply Chain Management, but typically add a new configuration option that you need to set to use the new functionality.

| Feature enhancement | Description |
| --- | --- |
| **Module:** Inventory and warehouse management<br><br>**Feature management name:** *Flexible sampling plan - Usability enhancements* | Improves the user experience for defining [flexible sampling plans](../inventory/quality-flexible-sampling-plans.md) by moving the **Last level** assignment from the header to a checkbox directly in the lines grid. This change makes the action more intuitive and provides contextual confirmation dialogs when users set, change, or clear the last level. |
| **Module:** Inventory and warehouse management<br><br>**Feature management name:** *Quality quick results entry enhancements* | Enhances the information display on the [quick results entry](../inventory/quality-quick-results-entry.md) page by adding information such as test descriptions and test plan notes. Now you can view test-related information and associated notes directly within the quick results entry workflow. |
| **Module:** Product information management<br><br>**Feature management name:** *Configure Product Lifecycle State business process policies without Engineering change management.* | Lets you configure product lifecycle state business process policies when [engineering change management](../engineering-change-management/product-engineering-overview.md) configuration keys aren't enabled. As a result, you can manage product behavior (such as purchasing, sales, and production) based on lifecycle states without relying on engineering change management. If you do use engineering change management, then you don't need this feature because engineering change management provides the required lifecycle-based business process rules. This setup offers flexibility to tailor operations according to a product's lifecycle stage. For example, you can choose to allow a new product to be purchased with a warning that indicates the item is still a prototype; or, for discontinued or end-of-life products, you can choose to allow sales of existing inventory while blocking new purchases or production. |
| **Module:** Production control<br><br>**Feature management name:** *Automatically stop and resume production jobs for indirect activities in production floor execution* | When a worker starts an indirect activity in the [production floor execution interface](../production-control/production-floor-execution-use.md), any production jobs currently in progress are automatically stopped and remembered. When the indirect activity ends, the previously active production jobs are automatically restarted, eliminating the need for workers to manually search for and restart their jobs. |
| **Module:** Sales and marketing<br><br>**Feature management name:** *Enable non-attribute based rebate management deals for Unified pricing scenario* | Allows rebate management deals that aren't based on attributes to be considered when using [Unified pricing management](../unified-pricing-management/upm-pricing-management-overview.md). |
| **Module:** Warehouse management<br><br>**Feature management name:** *(Production ready preview) Optimized 3D packing containerization algorithm* | Introduces a new optimized 3D packing algorithm to warehouse containerization processes. |

## Features turned on by default in this release

The following table lists the features that became turned on by default in version 10.0.48. You can still turn these features off in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) if necessary.

| Module | Feature name | More information |
| --- | --- | --- |
| Master planning | *Keep pegging between approved planned orders for Planning Optimization* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.47 (March 2026)](whats-new-scm-10-0-47.md) |

## Related information

### Platform updates for finance and operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.48 includes platform updates. Learn more in [Platform updates for version 10.0.48 of Finance and Operations apps (June 2026)](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-47.md).<!-- KFM: Confirm link -->

For information about the bug fixes included in each of the updates that are part of version 10.0.48, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](#). <!-- KFM: Get KB link -->

### What's new or changed in the Warehouse Management mobile app

The Warehouse Management mobile app is updated regularly following a different schedule than Supply Chain Management. For information about the latest versions and features, go to [What's new or changed in the Warehouse Management mobile app](../warehousing/warehouse-app-whats-new.md).

### What's new or changed in Demand planning

Demand planning in Dynamics 365 Supply Chain Management is updated regularly following a different schedule than Supply Chain Management. For information about the latest versions and features, go to [What's new or changed in Demand planning](../demand-planning/whats-new-demand-planning.md).

### What's new or changed in Planning Optimization

Microsoft updates Planning Optimization monthly. However, based on business requirements, the product team occasionally releases other updates between the scheduled releases. For information about the latest versions and features, go to [Planning Optimization release process and release history](../master-planning/planning-optimization/release-process.md)

### Dynamics 365 2026 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Microsoft Dynamics 365: 2026 release wave 1 plan](/dynamics365/release-plan/2026wave1/). It captures all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article describes features that are removed or scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

Before Microsoft removes any feature from the product, it announces the deprecation notice in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time is less than 12 months. Typically, these changes are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
