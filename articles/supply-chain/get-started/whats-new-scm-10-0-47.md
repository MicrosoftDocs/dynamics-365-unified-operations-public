---
title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.47 (March 2026)
description: Learn about features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.47 with a table outlining feature areas. 
author: kamaybac
ms.author: kamaybac
ms.reviewer: kamaybac
ms.search.form:
ms.topic: whats-new
ms.date: 01/26/2026
ms.update-cycle: 1095-days
ms.custom:
  - bap-template
  - evergreen
---

# What's new or changed in Dynamics 365 Supply Chain Management 10.0.47 (March 2026)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management version 10.0.47. This version  has a build number of 10.0.2428 and is available on the following schedule:

- **Preview of release:** January 2026
- **General availability of release (self-update):** March 2026
- **General availability of release (auto-update):** April 2026

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature | More information | Enabled by |
| --- | --- | --- | --- |
| Sales and marketing | [Manage pricing rules using a generic base currency](/dynamics365/release-plan/2025wave2/enterprise-resource-planning/dynamics365-supply-chain-management/manage-pricing-rules-using-generic-base-currency) | *Coming soon* | Enabled by default |
| Sales and marketing | [Optimize pricing data import and export workflows](/dynamics365/release-plan/2025wave2/enterprise-resource-planning/dynamics365-supply-chain-management/optimize-pricing-data-import-export-workflows) | *Coming soon* | Enabled by default |
| Sales and marketing | [Simulate prices based on sales order line attributes](/dynamics365/release-plan/2025wave2/enterprise-resource-planning/dynamics365-supply-chain-management/simulate-prices-based-sales-order-line-attributes) | *Coming soon* | Enabled by default |

## <a name="enhancements"></a>Feature enhancements added in this release

The following table lists the feature enhancements that were added in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they're only enhancements, they aren't listed in the [release plan](/dynamics365/release-plan/2024wave2/finance-supply-chain/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

Some of these features aren't visible on your system until you turn them on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) using the name listed here for the *Feature management name* (additional configuration may also be needed). Features that don't show a feature management name are visible by default as of this version of Supply Chain Management, but typically add a new configuration option that you need to set to use the new functionality.

| Feature enhancement | Description |
| --- | --- |
| **Module:** Asset Management<br><br>**Feature management name:** *Add maintenance checklist template lines to work order lines* | Add maintenance checklist lines from a predefined template directly to work order lines. |
| **Module:** Inventory and warehouse management<br><br>**Feature management name:** *Configure quality associations by product dimensions* | Allows administrators to configure quality associations by product dimensions such as configuration, color, and size. It ensures that quality checks can be applied at a more granular level for specific product variants. |
| **Module:** Master Planning<br><br>**Feature management name:** *(Preview) Exclude blocked transactions from planning if inventory status isn't a coverage plan dimension* | Excludes blocked transactions from planning when inventory status isn't set as a coverage plan dimension. When this feature is turned on, the **Net requirements** page no longer shows blocked transactions as *On-hand* and *Inventory journal* entries that offset each other by inventory blocking. This new behavior is more consistent with that of other planning scenarios. This feature only affects Planning Optimization, not the deprecated planning engine. |
| **Module:** Master Planning<br><br>**Feature management name:** *Consider receipt margins when applying action* | Causes the system to consider receipt margins when applying actions and to adjust receipt and delivery dates accordingly. For a purchase or a production order, receipt and delivery date can be set in the past. However for a transfer order, the receipt date must always be after the ship date. In situations where scheduling backwards from the requirement date results in a transfer order with a ship date that's in the past, the system applies the receipt margin only partially or not at all because transfer orders can't have ship dates in the past. |
| **Module:** Production Control<br><br>**Feature management name:** *(Preview) Sensor Data Intelligence - Auto report progress* | Uses sensors to capture production output in real time and automatically post progress at configurable intervals based on unit conversion factors, eliminating manual entry for reporting progress. Workers get live visibility into produced units directly in the production floor execution interface, with support for up to two levels of unit tracking (such as boxes per pallet). |
| **Module:** Warehouse management<br><br>**Feature management name:** *Remove Show Closed Button* | Removes the **Show closed** button from warehouse related forms. Instead, you can now use filters and saved views directly on the form. This feature is enabled by default. |

## Preview features that are now generally available

The following table lists the features that were introduced as public preview features in a previous version and became generally available in version 10.0.47. As with other new features, most of these features are turned off by default, so you must turn them on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) if you want to use them.

| Module | Feature name | More information |
| --- | --- | --- |
| Inventory and warehouse management | *Sample management* | [Sample management overview](../inventory/quality-sample-management-overview.md)<br><br>[Enable and configure sample management](../inventory/quality-sample-management-admin.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.46 (December 2025)](whats-new-scm-10-0-46.md) |

## Features turned on by default in this release

The following table lists the features that became turned on by default in version 10.0.47. You can still turn these features off in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) if necessary.

| Module | Feature name | More information |
| --- | --- | --- |
| Accounts receivable | *Approved customer list* | [Advanced quality management overview](../inventory/advanced-quality-management-overview.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.44 (June 2025)](whats-new-scm-10-0-44.md) |
| Asset Management | *Aggregated material availability check* | [Material availability check for work orders](../asset-management/work-orders/material-availability-check-work-orders.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.44 (June 2025)](whats-new-scm-10-0-44.md) |
| Asset Management | *Credit limit check on work order dispatch* | [Bill for maintenance on customer-owned assets](../asset-management/integration-to-project-management-and-accounting/customer-billing.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.44 (June 2025)](whats-new-scm-10-0-44.md) |
| Inventory and warehouse management | *Advanced quality management* | [Advanced quality management overview](../inventory/advanced-quality-management-overview.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.44 (June 2025)](whats-new-scm-10-0-44.md) |
| Organization administration | *Electronic signature improvements* | [Advanced quality management overview](../inventory/advanced-quality-management-overview.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.44 (June 2025)](whats-new-scm-10-0-44.md) |
| Production control | *Dispense management* | [Advanced quality management overview](../inventory/advanced-quality-management-overview.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.44 (June 2025)](whats-new-scm-10-0-44.md) |
| Shared AP and AR | *Rebate processing use multiple batch tasks* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.45 (September 2025)](whats-new-scm-10-0-45.md) |

## Features becoming mandatory in this release

The following table lists the features that became mandatory in version 10.0.47. These features can still be seen in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) but can no longer be turned off.

| Module | Feature name | More information |
| --- | --- | --- |
| Asset Management | *Adjust forecast hours to match schedule hours when work orders are dispatched* | [Dispatch work orders](../asset-management/work-order-scheduling/dispatch-work-order.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.43 (March 2025)](whats-new-scm-10-0-43.md) |
| Asset Management | *Print work order document attachments* |  [What's new or changed in Dynamics 365 Supply Chain Management 10.0.41 (September 2024)](whats-new-scm-10-0-41.md) |
| Asset Management | *Role-based access control for work order lifecycle stages* | [Work order lifecycle states](../asset-management/setup-for-work-orders/work-order-lifecycle-states.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.43 (March 2025)](whats-new-scm-10-0-43.md) |
| Inventory and warehouse management | *Dimension history for documents report data clean up* |  [What's new or changed in Dynamics 365 Supply Chain Management 10.0.40 (June 2024)](whats-new-scm-10-0-40.md) |
| Warehouse management | *Warehouse management only mode* | [Warehouse management only mode overview](../warehousing/wms-only-mode-overview.md) |

## Related information

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.47 includes platform updates. Learn more in [Platform updates for version 10.0.47 of Finance and Operations apps (September  2024)](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-47.md). <!-- KFM: Check link -->

For information about the bug fixes included in each of the updates that are part of version 10.0.47, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=xx). <!-- KFM: Get new link -->

### Dynamics 365: 2025 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Microsoft Dynamics 365: 2025 release wave 2 plan](/dynamics365/release-plan/2025wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
