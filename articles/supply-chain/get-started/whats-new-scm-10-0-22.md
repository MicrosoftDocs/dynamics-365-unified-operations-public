---
title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.22 (November 2021) 
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.22. 
author: kamaybac
ms.date: 08/09/2021
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this topic to]
audience: Application User, Developer, IT Pro
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: kamaybac
ms.search.validFrom: 2021-08-02
ms.dyn365.ops.version: 10.0.22
---

# What's new or changed in Dynamics 365 Supply Chain Management 10.0.22 (November 2021)

[!include [banner](../includes/banner.md)]

This topic lists features that are either new or changed in the Microsoft Dynamics 365 Supply Chain Management version 10.0.22. This version has a build number of 10.0.995 and is available as follows:

- **Preview of release:** September 2021
- **General availability of release (self-update):** October 2021
- **General availability of release (auto-update):** November 2021

## Features included in this release

The following table lists the features that are included in this release. The *Feature* column provides links to the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-supply-chain-management/planned-features), where you can see the official release dates for each feature. The *More information* column provides more details and/or links to related documentation. To determine how to turn on a feature, see the *Enabled by* column. For more information about how to use feature management, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). We might update this topic to include features that made it into the build after this topic was initially published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Planning | [Planning Optimization support for capability-based resource allocation](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-supply-chain-management/planning-optimization-support-capability-based-resource-allocation) | [Scheduling with resource selection based on capability](../master-planning/planning-optimization/capability-based-scheduling.md) | Feature management (*Infinite capacity scheduling for Planning Optimization*) |

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted). If you want to use any of these features, you must explicitly enable them in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Module | Feature name in feature management | More information |
|---|---|---|
| Distributed hybrid topology | *(No feature management is required.)* | <p>This release expands the outbound load planning capabilities of the warehouse management workload for cloud and edge scale units.</p><p>For more information, see [Warehouse management workloads for cloud and edge scale units](../cloud-edge/cloud-edge-workload-warehousing.md).</p> |
| Engineering change management | Variant generation for engineering products | <p>This feature lets you generate several variants for an engineering product, based on its color, size, style, or configuration dimensions.</p><p>For more information, see [Generate variants for engineering products](../engineering-change-management/engineering-variants.md).</p> |
| Inventory and warehouse management | Inventory Visibility integration with reservation offset | <p>This feature can be enabled only after the *Inventory Visibility Integration* feature is enabled. It provides functionality to offset reservations that are made on Inventory Visibility.</p><p>For more information, see [Inventory Visibility reservations](../inventory/inventory-visibility-reservations.md).</p> |

## New and updated documentation resources

We have recently added or significantly updated the following help topics. These topics aren't necessarily related to the new features that were added for this release, as listed in the previous section. However, they might help you to get more out of existing features.

| Feature area | New or updated topics |
|---|---|
| Engineering change management | [Engineering change management overview](../engineering-change-management/product-engineering-overview.md) now lists all related, optional features available in feature management |
| Master planning | [Demand forecasting setup](../master-planning/demand-forecasting-setup.md) |
| Master planning | [Net requirements and pegging information with Planning Optimization](../master-planning/planning-optimization/net-requirements.md) |
| Warehouse management | [Release to warehouse](../warehousing/release-to-warehouse-process.md) provides a detailed overview of the full release to warehouse process |

## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.22 includes platform updates. To learn more, see [Platform updates for version 10.0.22 of Finance and Operations apps (November 2021)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-22.md).

### Bug fixes

For information about the bug fixes included in each of the updates that are part of 10.0.22, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=615299).

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
