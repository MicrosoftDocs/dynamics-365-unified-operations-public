---
title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.45 (September 2025)
description: Learn about features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.45 with a table outlining feature areas. 
author: kamaybac
ms.author: kamaybac
ms.reviewer: kamaybac
ms.search.form:
ms.topic: whats-new
ms.date: 08/05/2025
ms.update-cycle: 1095-days
ms.custom:
  - bap-template
  - evergreen
---

# What's new or changed in Dynamics 365 Supply Chain Management 10.0.45 (September  2025)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management version 10.0.45. This version has a build number of 10.0.2345 and is available on the following schedule:

- **Preview of release:** July 2025
- **General availability of release (self-update):** September  2025
- **General availability of release (auto-update):** October 2025

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Inventory and warehouse management | [Enable quality control with acceptance sampling](/dynamics365/release-plan/2025wave1/finance-supply-chain/dynamics365-supply-chain-management/enable-quality-control-acceptance-sampling) | [Acceptance sampling (preview)](../inventory/quality-acceptance-sampling.md) | Feature management:<br>*(Preview) Acceptance sampling* |
| Master planning | [Support lean manufacturing with Planning Optimization](/dynamics365/release-plan/2025wave1/finance-supply-chain/dynamics365-supply-chain-management/implement-lean-manufacturing-catch-weight-step-consumption-planning-optimization) | [Master planning home page](../master-planning/master-planning-home-page.md) | Feature management:<br>*(Preview) Lean manufacturing for Planning Optimization* |
| Message processor | Clean up processed and canceled message processor messages | [Clean up processed and canceled message processor messages](../message-processor/message-processor-cleanup.md) | Enabled by default. |
| Production control | Generate license plates and print labels for MES integration | [Integrate with third-party manufacturing execution systems](../production-control/mes-integration.md) | Enabled by default you have [set up MES integration](../production-control/mes-integration.md). |
| Sales and marketing | Use external item identifiers to add products to orders | [Use external item identifiers to add products to orders](../sales-marketing/external-item-product-search-lookup.md) | Feature management:<br>*Enable lookup based search for Sales External Item Identifier field* |
| Warehouse management | [Improve operations with Warehouse Management mobile app V4](/dynamics365/release-plan/2025wave1/finance-supply-chain/dynamics365-supply-chain-management/improve-operations-warehouse-management-mobile-app-v4) | [Migrate the Warehouse Management mobile app from V3 to V4 (preview)](../warehousing/warehouse-app-migrating-from-v3-v4.md) | Enabled by default in Supply Chain Management.<p>Must be [installed or upgraded locally](../warehousing/warehouse-app-migrating-from-v3-v4.md) on each device. |
| Warehouse management | Record and view container line packing details | [Packing containers with the Warehouse Management mobile app](../warehousing/warehouse-app-packing-containers.md) | Enabled by default. |

## <a name="enhancements"></a>Feature enhancements added in this release

The following table lists the feature enhancements that were added in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they're only enhancements, they aren't listed in the [release plan](/dynamics365/release-plan/2024wave2/finance-supply-chain/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

Some of these features aren't visible on your system until you turn them on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) using the name listed here for the *Feature management name* (additional configuration may also be needed). Features that don't show a feature management name are visible by default as of this version of Supply Chain Management, but typically add a new configuration option that you need to set to use the new functionality.

| Feature enhancement | Description |
|---|---|
| **Module:** Procurement and sourcing<br><br>**Feature management name:** *Enable calculation of earliest confirmed receipt date for vendor collaboration* | Displays the earliest confirmed receipt date for purchase order responses. The value is calculated based on the confirmed receipt dates for the purchase response lines. |
| **Module:** Procurement and sourcing<br><br>**Feature management name:** *Remove vendors from RFQ after bid is sent or received* | Lets you remove vendors from a request for quotation (RFQ) after a bid has been sent to or received from them. When removing a vendor, you can optionally send an email notification to inform them of the removal. Once removed, the vendor can no longer access the RFQ in the supplier portal. However, the purchase manager can re-add the vendor to the RFQ at any time, as long as the RFQ has not been accepted or rejected. This provides added control and flexibility during the RFQ evaluation process. |
| **Module:** Production control<br><br>**Feature management name:** *Enhanced numpad control for production floor execution interface* | Improves the control that represents the numpad in the production floor execution interface. It changes the control from being an element of type *String* to type *Real*, which makes the decimal separator consistent with regards to the regional settings. |
| **Module:** Shared AP and AR<br><br>**Feature management name:** *Rebate processing use multiple batch tasks* | Enables rebates to be processed in batch with multiple batch tasks running at the same time. |

## Preview features that are now generally available

The following table lists the features that were introduced as public preview features in a previous version and became generally available in version 10.0.45. As with other new features, most of these features are turned off by default, so you must turn them on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) if you want to use them.

| Module | Feature name | More information |
|--|--|--|
| Accounts receivable | *Approved customer list* | [Advanced quality management overview](../inventory/advanced-quality-management-overview.md)<br><br>[Approved customer lists](../sales-marketing/approved-customer-lists.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.44 (June 2025)](whats-new-scm-10-0-44.md) |
| Inventory and warehouse management | *Advanced quality management* | [Advanced quality management overview](../inventory/advanced-quality-management-overview.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.44 (June 2025)](whats-new-scm-10-0-44.md) |
| Inventory and warehouse management | *Pair transfer order lines with sales order lines* | [Link transfer order lines with sales order lines](../inventory/pair-transfer-and-sales-lines.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.41 (September 2024)](whats-new-scm-10-0-41.md) |
| Organization administration | *Electronic signature improvements* | [Advanced quality management overview](../inventory/advanced-quality-management-overview.md)<br><br>[CAPA management administration](../inventory/capa-admin.md)<br><br>[Electronic batch records (EBRs)](../production-control/quality-electronic-batch-record.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.44 (June 2025)](whats-new-scm-10-0-44.md) |
| Product information management | *Enable foreign trade parameters for all countries* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.44 (June 2025)](whats-new-scm-10-0-44.md) |
| Production control | *Dispense management* | [Advanced quality management overview](../inventory/advanced-quality-management-overview.md)<br><br>[Production dispensing (preview)](../production-control/quality-production-dispensing.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.44 (June 2025)](whats-new-scm-10-0-44.md) |

## Features turned on by default in this release

The following table lists the features that became turned on by default in version 10.0.43. You can still turn these features off in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) if necessary.

| Module | Feature name | More information |
|--|--|--|
| Asset management | *Print work order document attachments* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.41 (September 2024)](whats-new-scm-10-0-41.md) |
| Asset management | *Adjust forecast hours to match schedule hours when work orders are dispatched* | [Dispatch work orders](../asset-management/work-order-scheduling/dispatch-work-order.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.43 (March 2025)](whats-new-scm-10-0-43.md) |
| Asset management | *Role-based access control for work order lifecycle stages* | [Work order lifecycle states](../asset-management/setup-for-work-orders/work-order-lifecycle-states.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.43 (March 2025)](whats-new-scm-10-0-43.md) |
| Inventory and warehouse management | *Dimension history for documents report data clean up* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.40 (June 2024)](whats-new-scm-10-0-40.md) |
| Inventory and warehouse management | *Enable warehouse items in Inventory Visibility* | [Enable Inventory Visibility for Commerce](../inventory/inventory-visibility-commerce-enable.md)<br><br>[Inventory Visibility support for WMS items](../inventory/inventory-visibility-whs-support.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.26 (May 2022)](whats-new-scm-10-0-26.md) |
| Inventory and warehouse management | *Inventory Visibility integration with ATP* | [Track time-series inventory in Inventory Visibility](../inventory/inventory-visibility-track-atp.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.41 (September 2024)](whats-new-scm-10-0-41.md) |
| Inventory and warehouse management | *Inventory Visibility integration with reservation offset* | [Inventory Visibility reservations](../inventory/inventory-visibility-reservations.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.22 (November 2021)](../supply-chain-dev/whats-new-scm-10-0-22.md) |
| Inventory and warehouse management | *Inventory Visibility integration with soft reservation on sales order lines* | [Inventory Visibility reservations](../inventory/inventory-visibility-reservations.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.33 (May 2023)](whats-new-scm-10-0-33.md) |
| Inventory and warehouse management | *Inventory Visibility transaction integration* | [Sync external inventory adjustments through Inventory Visibility](../inventory/inventory-visibility-sync-changes.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.41 (September 2024)](whats-new-scm-10-0-41.md) |
| Production control | *Allow to select validation logic for expiration of raw materials: either against planned consumption date or production order delivery date* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.42 (December 2024)](whats-new-scm-10-0-42.md) |
| Production control | *Register material consumption as complete and edit dimensions on the production floor execution interface* | [Configure the production floor execution interface](../production-control/production-floor-execution-configure.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.42 (December 2024)](whats-new-scm-10-0-42.md) |
| Production control | *Set the desired status on selected jobs in report progress list view in the production floor execution interface* | [Configure the production floor execution interface](../production-control/production-floor-execution-configure.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.42 (December 2024)](whats-new-scm-10-0-42.md) |
| Production control | *Streamlined registration process for indirect activities on the Production floor execution* | [Configure the production floor execution interface](../production-control/production-floor-execution-configure.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.42 (December 2024)](whats-new-scm-10-0-42.md) |
| Production control | *Tracked components* | [Register and track batch/serial numbers for finished products and their components](../production-control/tracked-components.md)<br><br>[Integrate Traceability with tracked components in Supply Chain Management (preview)](../traceability/traceability-integration-scm.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.40 (June 2024)](whats-new-scm-10-0-40.md) |
| Sales and marketing | *Product bundles in journals* | [Enable and set up product bundles](../sales-marketing/product-bundles-setup.md)<br><br>[Sell and allocate product bundles](../sales-marketing/product-bundles-use.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.40 (June 2024)](whats-new-scm-10-0-40.md) |
| Shared AP and AR | *Allow match rebate by order account* | Rebates are matched not only by invoice account but also the order account when setting the field **Matched by order account** for rebate tables. |
| Shared AP and AR | *Consolidate vendor invoices for the same vendor in vendor rebate deals* | [Process, review, and post rebates](../rebate-management/process-review-post.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.43 (March 2025)](whats-new-scm-10-0-43.md) |
| Shared AP and AR | *Credit note calculation enhancement in Rebate management* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.32 (April 2023)](whats-new-scm-10-0-32.md) |
| Shared AP and AR | *Enable posting of vendor rebate outputs to purchase order vendors* | [Rebate management posting setup](../rebate-management/rebate-management-posting.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.43 (March 2025)](whats-new-scm-10-0-43.md) |
| Shared AP and AR | *Enable resubmission of workflows for vendor rebate deals* | [Rebate management deal workflows](../rebate-management/rebate-management-workflows.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.43 (March 2025)](whats-new-scm-10-0-43.md) |
| Shared AP and AR | *Export channels for electronic invoicing integration* | Lets you set up channels for exporting to an electronic invoicing service. |
| Shared AP and AR | *Write-off before rebate claim* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.32 (April 2023)](whats-new-scm-10-0-32.md) |

## Features becoming mandatory in this release

The following table lists the features that became mandatory in version 10.0.45. These features can still be seen in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) but can no longer be turned off.

| Module | Feature name | More information |
|---|---|---|
| Asset management | *Asset Management enhancements* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.38 (February 2024)](whats-new-scm-10-0-38.md) |
| Asset management | *Change types on assets and functional locations* | [Change the type of existing functional locations](../asset-management/functional-locations/change-functional-location-type.md)<br><br>[Change the asset type of existing assets](../asset-management/objects/change-asset-type.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.38 (February 2024)](whats-new-scm-10-0-38.md) |
| Asset management | *Material availability check on maintenance work orders* | [Material availability check for work orders](../asset-management/work-orders/material-availability-check-work-orders.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.37 (November 2023)](whats-new-scm-10-0-37.md) |
| Inventory and warehouse management | *(India) Improvements in unit price and cost price handling in Stock transfer orders* | [Stock transfer orders for India](../../finance/localizations/india/apac-ind-stock-transfer.md) |
| Inventory and warehouse management | *Correct item that is not visible in released products form manually* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.40 (June 2024)](whats-new-scm-10-0-40.md) |
| Inventory and warehouse management | *Inventory transaction details page's performance improvement.* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.39 (April 2024)](whats-new-scm-10-0-39.md) |
| Inventory and warehouse management | *Inventory Visibility integration* | [Inventory Visibility Add-in overview](../inventory/inventory-visibility.md)<br><br>[Install and set up Inventory Visibility](../inventory/inventory-visibility-setup.md) |
| Inventory and warehouse management | *Inventory Visibility integration with inventory adjustment offset* | [Inventory Visibility adjustment offset](../inventory/inventory-visibility-adjustment-offset.md)<br><br>[Enable Inventory Visibility for Commerce](../inventory/inventory-visibility-commerce-enable.md)<br><br>[Sync external inventory adjustments through Inventory Visibility](../inventory/inventory-visibility-sync-changes.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.34 (July 2023)](whats-new-scm-10-0-34.md) |
| Inventory and warehouse management | *Inventory Visibility integration with inventory adjustment posting* | [Enable Inventory Visibility for Commerce](../inventory/inventory-visibility-commerce-enable.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.34 (July 2023)](whats-new-scm-10-0-34.md) |
| Product information management | *Advanced export management configuration* | [Work with advanced export management for products, sales orders, and sales quotations](../pim/export-control-use.md)<br><br>[Enable and configure advanced export management](../pim/export-control-configure.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.36 (October 2023)](whats-new-scm-10-0-36.md) |
| Product information management | *Product service type* | N/A |
| Production control | *List view for reporting job progress from the production floor execution interface* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.40 (June 2024)](whats-new-scm-10-0-40.md) |
| Production control | *Optimized report as finished process for serialized products* | N/A |
| Sales and marketing | *Period charges* | [Period charges](../sales-marketing/period-charges.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.38 (February 2024)](whats-new-scm-10-0-38.md) |
| Sales and marketing | *Sales order creation performance enhancement* | N/A |
| Sales and marketing | *Stop creation of source document header and line records related to sales packing slip posting* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.36 (October 2023)](whats-new-scm-10-0-36.md) |
| Sales and marketing | *Unit of measure for line level charges* | [Units of measure for line-level charges](../sales-marketing/line-charges-specific-unit.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.38 (February 2024)](whats-new-scm-10-0-38.md) |
| Shared AP and AR | Cancel posted rebate provision with a posting date | Lets you posted rebate provision with a specified posting date and reverse the original transactions and documents. |
| Shared AP and AR | Delete rebate transactions with posting amount equals to zero while posting | Rebate date transactions with posting amount equals to zero are automatically deleted during posting. This only applies to rebate deals with an output type of *Financial*. |
| Transportation management | *Integrate Microsoft Sustainability Manager with transportation management* | [Integrate with Microsoft Sustainability Manager](../transportation/sustainability-manager-integration-setup.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.38 (February 2024)](whats-new-scm-10-0-38.md) |

## Features removed from feature management

The following table lists features that were removed from Feature management in version 10.0.45. These features are no longer listed in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) and are now a permanent part of Supply Chain Management.

| Module | Feature name | More information |
|---|---|---|
| Cost management | *Cost calculation level* | [Cost calculation level](../cost-management/cost-calculation-level.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.12 (August 2020)](../supply-chain-dev/whats-new-scm-10-0-12.md) |
| Inventory and warehouse management | *\[Russia\] Post storno financial inventory transactions according to the correction flag in the financial voucher for Sales orders* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.23 (January 2022)](whats-new-scm-10-0-23.md) |
| Procurement and sourcing | *Filter by date when assessing supply risks* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.35 (August 2023)](whats-new-scm-10-0-35.md) |
| Procurement and sourcing | *Purchase order workflow submission and approval performance enhancement* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.32 (April 2023)](whats-new-scm-10-0-32.md) |
| Procurement and sourcing | *Request for quotation amendment and cancellation email framework options* | N/A |
| Procurement and sourcing | *Select RFQ fields to include in vendor RFQ reply forms* | [Requests for quotation (RFQs) overview](../procurement/request-quotations.md) |
| Procurement and sourcing | *Show only delivery addresses for workers when creating category-based purchase requisition lines* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.36 (October 2023)](whats-new-scm-10-0-36.md) |
| Product information management | *Apply sales tax group for product variants in sales and procurement* | [Predefined product variants](../pim/tasks/create-predefined-product-variants.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.34 (July 2023)](whats-new-scm-10-0-34.md) |
| Production control | *Add filter to hide completed jobs on the Kanban board* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.41 (September 2024)](whats-new-scm-10-0-41.md) |
| Production control | *Change BOM item* | [React to last-minute changes in production](../production-control/react-to-last-minute-changes.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.38 (February 2024)](whats-new-scm-10-0-38.md) |
| Production control | *Default order settings for Change production order BOM item* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.39 (April 2024)](whats-new-scm-10-0-39.md) |
| Production control | *Leverage production order defaults in manufacturing execution system integration* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.37 (November 2023)](whats-new-scm-10-0-37.md) |
| Production control | *Production order route change* | [React to last-minute changes in production](../production-control/react-to-last-minute-changes.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.38 (February 2024)](whats-new-scm-10-0-38.md) |
| Production control | *Register material consumption on the production floor execution interface (non-WMS)* | [Configure the production floor execution interface](../production-control/production-floor-execution-configure.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.24 (February 2022)](whats-new-scm-10-0-24.md) |
| Production control | *Standard cost financial posting of a production/batch order with a scrap account method.* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.38 (February 2024)](whats-new-scm-10-0-38.md) |
| Sales and marketing | *Auto-create direct delivery intercompany orders originating from purchase order creation* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.36 (October 2023)](whats-new-scm-10-0-36.md) |
| Sales and marketing | *Price and discount search for derived line creation* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.41 (September 2024)](whats-new-scm-10-0-41.md) |
| Warehouse management | *Over-pick materials for production orders and batch orders* | [Over-pick materials for production and batch orders](../warehousing/over-pick-materials-for-production-and-batch-orders.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.37 (November 2023)](whats-new-scm-10-0-37.md) |

## Related information

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.45 includes platform updates. Learn more in [Platform updates for version 10.0.45 of Finance and Operations apps (September  2024)](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-45.md). <!-- KFM: Check link -->

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.45, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=1043223).

### Dynamics 365: 2025 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Microsoft Dynamics 365: 2025 release wave 1 plan](/dynamics365/release-plan/2025wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
