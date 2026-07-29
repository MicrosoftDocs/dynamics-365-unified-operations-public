---
title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.49 (September 2026)
description: Learn about features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.49 with a table outlining feature areas. 
author: kamaybac
ms.author: kamaybac
ms.reviewer: kamaybac
ms.search.form:
ms.topic: whats-new
ms.date: 07/29/2026
ms.update-cycle: 1095-days
ms.custom:
  - bap-template
  - evergreen
---

# What's new or changed in Dynamics 365 Supply Chain Management 10.0.49 (September 2026)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management version 10.0.49. This version has a build number of 10.0.2790 and is available on the following schedule:

- **Preview of release:** July 2026
- **General availability of release (self-update):** September 2026
- **General availability of release (auto-update):** October 2026

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature | More information | Enabled by |
| --- | --- | --- | --- |
| Accounts payable | Use financial tags in procurement documents | [Use financial tags in procurement documents](../procurement/financial-tags-procurement.md) | Feature management:<br>*Enable financial tags for purchase order invoicing* |
| Master planning | Closed for pickup policy on the transport calendar | [Calendars and master planning](../master-planning/supply-chain-calendars-master-planning.md) | Feature management:<br>*Consider open for pickup on transport calendar for planned transfer orders with Planning Optimization* |
| Master planning | Consider sub-BOM and sub-route in supply forecast reduction | [Master planning with supply forecasts](../master-planning/planning-optimization/supply-forecast.md) | Feature management:<br>*Consider BOM and route in supply- and demand forecast reduction with Planning Optimization* |
| Master planning | Filter derived requirements by coverage time fence with Planning Optimization | [Coverage time fences](../master-planning/planning-optimization/coverage-time-fence.md) | Feature management:<br>*Filter derived requirements by coverage time fence with Planning Optimization* |
| Procurement and sourcing | [Manage supplier relationships with Supplier Engagement](/dynamics365/release-plan/2026wave1/enterprise-resource-planning/dynamics365-supply-chain-management/manage-supplier-relationships-improve-collaboration) | *Coming soon* | Feature management:<br>*(Preview) Supplier Engagement* |
| Procurement and sourcing | RFQ bid–driven fixed asset field updates | [Purchase requisition overview](../procurement/purchase-requisitions-overview.md) | Enabled by default |
| Production control | [Enforce same-batch selection for raw materials in production and batch orders](/dynamics365/release-plan/2026wave1/enterprise-resource-planning/dynamics365-supply-chain-management/enforce-same-batch-selection-raw-materials-production-batch-orders) | [Reserve the same batch for a production order (preview)](../production-control/reserve-same-batch-production-order.md) | Feature management:<br>*(Preview) Use same batch selection for raw materials in production* |
| Warehouse management | Import inbound ASNs as despatch advice messages | [Import inbound ASNs as despatch advice messages](../warehousing/despatch-advice-notice.md) | Enabled by default |
| Warehouse management | Prevent multiple owners in warehouse locations | [Prevent multiple owners in warehouse locations](../warehousing/prevent-multiple-owners-locations.md) | Enabled by default |
| Warehouse management | Source system inventory status mapping | [Source system inventory status mapping](../warehousing/wms-only-mode-exchange-data.md#inventory-status-mapping) | Enabled by default |

## <a name="enhancements"></a>Feature enhancements added in this release

The following table lists the feature enhancements that were added in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they're only enhancements, they're not listed in the [release plan](/dynamics365/release-plan/2026wave1/enterprise-resource-planning/dynamics365-supply-chain-management/planned-features) and might not be mentioned elsewhere in the documentation. To ensure that these enhancements don't conflict with your existing customizations or preferences, most of these features are turned off by default, so you must turn them on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) if you want to use them (unless otherwise noted).

| Module | Feature name | More information |
| --- | --- | --- |
| Inventory and warehouse management | *CAPA case HTML note editor* | Enables the rich HTML note editor on the **CAPA Case Detail** page, replacing the read-only viewer. This feature lets you create and edit formatted notes directly on the CAPA case log. |
| Inventory and warehouse management | *(Preview) Optimized inventory transaction consolidation* | Consolidate financially updated inventory transactions from closed periods into summary records to reduce table size and improve system performance. Consolidation is also a prerequisite for archiving inventory transactions with Dataverse long term retention. |
| Procurement and sourcing | *Synchronize establishment across the direct delivery chain* | Enables a purchase parameter and an origin prompt to control whether the system synchronizes establishments across the direct delivery chain between sales orders and purchase orders. |
| Production control | *Prevent shop floor activity after daily registrations are calculated* | Blocks workers from making additional shop floor registrations (such as clock-in, clock-out, job start, or job stop) after the system calculates time registrations for the day. The system displays the following error message: "You can't register any activities now because your registrations are already processed for today. Please contact your supervisor for assistance." When a worker receives this message, their supervisor should go to the **Approve** page and select **Undo calculation** for today for the affected worker. |
| Production control | *The feature enables batch auto-scale and priority based scheduling for message processor queues.* | Previously, the message queue setup for *Number of processor tasks* was limited to the maximum batch threads for a single batch server. When batch auto-scale is enabled, this feature makes it possible to utilize available capacity beyond a single batch. With priority based scheduling, you can also link message processor queues and batch server groups, use scheduling priority, and use maximum concurrency. |
| Sales and marketing | *Unified pricing management change tracking* | Enables automatic price change tracking for global Unified pricing management rules, discounts, and trade agreements. This feature writes change tracking rows to `RetailPriceChangeTracking` to notify Azure Product Search of price changes. |

## Preview features that are now generally available

The following table lists the features that were introduced as public preview features in a previous version and became generally available in version 10.0.49. As with other new features, most of these features are turned off by default, so you must turn them on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) if you want to use them.

| Module | Feature name | More information |
| --- | --- | --- |
| Inventory and warehouse management | *Optional linking of test instruments to maintainable assets* | [Manage test instrument calibration with Asset Management](../asset-management/preventive-and-reactive-maintenance/asset-management-test-instrument-calibration.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.46 (December 2025)](whats-new-scm-10-0-46.md) |
| Master Planning | *Keep supply for confirmed demand in Planning Optimization* | [Keep supply for confirmed demand in Planning Optimization](../master-planning/planning-optimization/keep-supply-for-confirmed-demand.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.48 (June 2026)](whats-new-scm-10-0-48.md) |
| Master Planning | *Optimize confirmed dates for CTP line changes* | [Optimize confirmed dates for CTP line changes](../master-planning/planning-optimization/optimize-confirmed-dates-for-ctp-line-changes.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.48 (June 2026)](whats-new-scm-10-0-48.md) |
| Master Planning | *Soft issue margins with Planning Optimization* | [Soft issue margin](../master-planning/planning-optimization/safety-margins.md#soft-issue-margin)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.48 (June 2026)](whats-new-scm-10-0-48.md) |
| Product information management | *Configure Product Lifecycle State business process policies without Engineering change management.* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.48 (June 2026)](whats-new-scm-10-0-48.md) |
| Sales and marketing | *Enable lookup based search for Sales External Item Identifier field* | [Use external item identifiers to add products to orders](../sales-marketing/external-item-product-search-lookup.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.45 (September 2025)](whats-new-scm-10-0-45.md)<br><br>This feature went directly from preview to mandatory in version 10.0.49. |
| Warehouse management | *(Production Ready Preview) Dynamic work classification* | [Dynamic work classification](../warehousing/dynamic-work-classification.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.48 (June 2026)](whats-new-scm-10-0-48.md)<br><br>This feature went directly from preview to on by default in version 10.0.49. |

## Features turned on by default in this release

The following table lists the features that became turned on by default in version 10.0.49. You can still turn these features off in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) if necessary.

| Module | Feature name | More information |
| --- | --- | --- |
| Asset Management | *Add maintenance checklist template lines to work order lines* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.47 (March 2026)](whats-new-scm-10-0-47.md) |
| Asset Management | *Remarks can be associated with each change in lifecycle states* | [Introduction to assets](../asset-management/objects/introduction-to-objects.md)<br><br>[Introduction to work orders](../asset-management/work-orders/introduction-to-work-orders.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.46 (December 2025)](whats-new-scm-10-0-46.md) |
| Inventory and warehouse management | *Acceptance sampling* | [Acceptance sampling](../inventory/quality-acceptance-sampling.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.45 (September 2025)](whats-new-scm-10-0-45.md) |
| Inventory and warehouse management | *Configure quality associations by product dimensions* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.47 (March 2026)](whats-new-scm-10-0-47.md) |
| Inventory and warehouse management | *Sample management* | [Sample management overview](../inventory/quality-sample-management-overview.md)<br><br>[Enable and configure sample management](../inventory/quality-sample-management-admin.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.46 (December 2025)](whats-new-scm-10-0-46.md) |
| Inventory and warehouse management | *View calibration tools for test instruments* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.46 (December 2025)](whats-new-scm-10-0-46.md) |
| Warehouse management | *(Production Ready Preview) Dynamic work classification* | [Dynamic work classification](../warehousing/dynamic-work-classification.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.48 (June 2026)](whats-new-scm-10-0-48.md)<br><br>This feature went directly from preview to on by default in version 10.0.49. |

## Features becoming mandatory in this release

The following table lists the features that became mandatory in version 10.0.49. These features still appear in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) but you can no longer turn them off.

| Module | Feature name | More information |
| --- | --- | --- |
| Asset Management | *Aggregated material availability check* | [Material availability check for work orders](../asset-management/work-orders/material-availability-check-work-orders.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.44 (June 2025)](whats-new-scm-10-0-44.md) |
| Asset Management | *Credit limit check on work order dispatch* | [Bill for maintenance on customer-owned assets](../asset-management/integration-to-project-management-and-accounting/customer-billing.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.44 (June 2025)](whats-new-scm-10-0-44.md) |
| Inventory and warehouse management | *Advanced quality management* | [Advanced quality management overview](../inventory/advanced-quality-management-overview.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.44 (June 2025)](whats-new-scm-10-0-44.md) |
| Inventory and warehouse management | *Inventory Visibility integration with ATP* | [Track time-series inventory in Inventory Visibility](../inventory/inventory-visibility-track-atp.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.41 (September 2024)](whats-new-scm-10-0-41.md) |
| Inventory and warehouse management | *Inventory Visibility integration with reservation offset* | [Inventory Visibility reservations](../inventory/inventory-visibility-reservations.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.22 (November 2021)](../supply-chain-dev/whats-new-scm-10-0-22.md) |
| Inventory and warehouse management | *Inventory Visibility transaction integration* | [Sync external inventory adjustments through Inventory Visibility](../inventory/inventory-visibility-sync-changes.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.41 (September 2024)](whats-new-scm-10-0-41.md) |
| Inventory and warehouse management | *Enable warehouse items in Inventory Visibility* | [Enable Inventory Visibility for Commerce](../inventory/inventory-visibility-commerce-enable.md)<br><br>[Inventory Visibility support for WMS items](../inventory/inventory-visibility-whs-support.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.26 (May 2022)](whats-new-scm-10-0-26.md) |
| Production control | *Dispense management* | [Advanced quality management overview](../inventory/advanced-quality-management-overview.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.44 (June 2025)](whats-new-scm-10-0-44.md) |
| Sales and marketing | *Recalculate delivery dates upon creation of direct delivery* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.40 (June 2024)](whats-new-scm-10-0-40.md) |
| Sales and marketing | *Enable lookup based search for Sales External Item Identifier field* | [Use external item identifiers to add products to orders](../sales-marketing/external-item-product-search-lookup.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.45 (September 2025)](whats-new-scm-10-0-45.md)<br><br>This feature went directly from preview to mandatory in version 10.0.49. |
| Shared AP and AR | *Consolidate vendor invoices for the same vendor in vendor rebate deals* | [Process, review, and post rebates](../rebate-management/process-review-post.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.43 (March 2025)](whats-new-scm-10-0-43.md) |
| Shared AP and AR | *Enable posting of vendor rebate outputs to purchase order vendors* | [Rebate management posting setup](../rebate-management/rebate-management-posting.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.43 (March 2025)](whats-new-scm-10-0-43.md) |

## Features removed from feature management

The following table lists features that were removed from Feature management in version 10.0.49. These features are no longer listed in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) and are now a permanent part of Supply Chain Management.

| Module | Feature name | More information |
|---|---|---|
| Asset Management | *Print work order document attachments* |  [What's new or changed in Dynamics 365 Supply Chain Management 10.0.41 (September 2024)](whats-new-scm-10-0-41.md) |
| Asset Management | *Adjust forecast hours to match schedule hours when work orders are dispatched* | [Dispatch work orders](../asset-management/work-order-scheduling/dispatch-work-order.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.43 (March 2025)](whats-new-scm-10-0-43.md) |
| Asset Management | *Role-based access control for work order lifecycle stages* | [Work order lifecycle states](../asset-management/setup-for-work-orders/work-order-lifecycle-states.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.43 (March 2025)](whats-new-scm-10-0-43.md) |
| Inventory and warehouse management | *Correct item that is not visible in released products form manually* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.40 (June 2024)](whats-new-scm-10-0-40.md) |
| Inventory and warehouse management | *Using unit of measure and unit quantity in inventory journals.* | N/A |
| Inventory and warehouse management | *Cascade transfer order header date change to lines* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.35 (August 2023)](whats-new-scm-10-0-35.md) |
| Procurement and sourcing | *Synchronize updates of the Requested ship and receipt dates on intercompany sales and purchase order lines* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.38 (February 2024)](whats-new-scm-10-0-38.md) |
| Procurement and sourcing | *Choose whether to consolidate sales orders for direct deliveries* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.41 (September 2024)](whats-new-scm-10-0-41.md) |
| Production control | *Production batch balancing enhanced onhand grid capability* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.32 (April 2023)](whats-new-scm-10-0-32.md) |
| Sales and marketing | *Calculate and push prices, discounts and totals for selective sales orders and sales quotations when integrated with Dynamics 365 Sales* | [Calculate and push prices, discounts, and totals from Supply Chain Management to Sales](../../fin-ops-core/fin-ops/data-entities/add-efficiency-in-quote-to-cash-use.md#push-to-sales)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.34 (July 2023)](whats-new-scm-10-0-34.md) |
| Sales and marketing | *Copy Supply Chain Management sales quotation data to sales orders synced from Dynamics 365 Sales* | [Copy Supply Chain Management sales quotation data to sales orders synced from Sales](../../fin-ops-core/fin-ops/data-entities/add-efficiency-in-quote-to-cash-use.md#copy-quotation-data)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.34 (July 2023)](whats-new-scm-10-0-34.md). |
| Sales and marketing | *Replace alternative item defaults on sales lines* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.39 (April 2024)](whats-new-scm-10-0-39.md) |

## Related information

### Platform updates for finance and operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.49 includes platform updates. Learn more in [Platform updates for version 10.0.49 of Finance and Operations apps (September 2026)](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-49.md). <!-- KFM: Confirm link -->

For information about the bug fixes included in each of the updates that are part of version 10.0.49, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=1156136).

### What's new or changed in the Warehouse Management mobile app

The Warehouse Management mobile app is updated regularly following a different schedule than Supply Chain Management. For information about the latest versions and features, go to [What's new or changed in the Warehouse Management mobile app](../warehousing/warehouse-app-whats-new.md).

### What's new or changed in Demand planning

Demand planning in Dynamics 365 Supply Chain Management is updated regularly following a different schedule than Supply Chain Management. For information about the latest versions and features, go to [What's new or changed in Demand planning](../demand-planning/whats-new-demand-planning.md).

### What's new or changed in Planning Optimization

Microsoft updates Planning Optimization monthly. However, based on business requirements, the product team occasionally releases other updates between the scheduled releases. For information about the latest versions and features, go to [Planning Optimization release process and release history](../master-planning/planning-optimization/release-process.md).

### Dynamics 365 2026 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Microsoft Dynamics 365: 2026 release wave 1 plan](/dynamics365/release-plan/2026wave1/). It captures all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article describes features that are removed or scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

Before Microsoft removes any feature from the product, it announces the deprecation notice in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time but are binary compatible with sandbox and production environments, the deprecation time is less than 12 months. Typically, these changes are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
