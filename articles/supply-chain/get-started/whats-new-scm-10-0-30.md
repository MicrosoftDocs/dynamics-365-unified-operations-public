---
title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.30 (November 2022)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.30. 
author: kamaybac
ms.date: 11/07/2022
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this article to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: kamaybac
ms.search.validFrom: 2022-09-08
ms.dyn365.ops.version: 10.0.30
---

# What's new or changed in Dynamics 365 Supply Chain Management 10.0.30 (November 2022)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management version 10.0.30. This version has a build number of 10.0.1362 and is available on the following schedule:

- **Preview of release:** September 2022
- **General availability of release (self-update):** October 2022
- **General availability of release (auto-update):** November 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Inventory and logistics | [Track soft reserved quantities within allocations](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-supply-chain-management/track-soft-reserved-quantities-within-allocations) | [Inventory Visibility inventory allocation](../inventory/inventory-visibility-allocation.md) |  Enabled by [service configuration](../inventory/inventory-visibility-configuration.md) |
| Manufacturing | [Monitor equipment with Sensor Data Intelligence](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-supply-chain-management/monitor-equipment-sensor-data-intelligence) | [Sensor Data Intelligence home page](../sensor-data-intelligence/sdi-home-page.md) | Feature management:<br>*(Preview) Sensor Data Intelligence* |
| Warehouse management | [Multilevel detours for the Warehouse Management mobile app](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-supply-chain-management/multi-level-detours-warehouse-management-mobile-app) | [Configure detours for steps in mobile device menu items](../warehousing/warehouse-app-detours.md) | Feature management:<br>*Multi-level detours for the Warehouse Management mobile app* |

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

If you want to turn any of these features on or off, you must do so in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Module | Feature name in feature management | More information |
|---|---|---|
| Production control | On-hand information in production orders to release page | Adds a column for the on-hand inventory quantity for the line item in the lines section on the **Production orders to release** page. |

## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.30 includes platform updates. To learn more, see [Platform updates for version 10.0.30 of Finance and Operations apps (November 2022)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-30.md).

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.30, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=745468).

### Dynamics 365 and industry clouds: 2022 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2022 release wave 2 plan](/dynamics365-release-plan/2022wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
