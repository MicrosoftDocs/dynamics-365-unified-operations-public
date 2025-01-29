---
title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.43 (March 2025)
description: Learn about features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.43 with a table outlining feature areas. 
author: kamaybac
ms.author: kamaybac
ms.topic: conceptual
ms.date: 01/27/2025
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# What's new or changed in Dynamics 365 Supply Chain Management 10.0.43 (March 2025)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management version 10.0.43. This version has a build number of 10.0.2177 and is available on the following schedule:

- **Preview of release:** January 2025
- **General availability of release (self-update):** March 2025
- **General availability of release (auto-update):** April 2025

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature | More information | Enabled by |
|---|---|---|---|
| System administration | Enhanced user feedback for Copilot and related experiences | [Enable enhanced user feedback for Copilot and related experiences (preview)](../../fin-ops-core/dev-itpro/copilot/enable-copilot-feedback.md) | Feature management:<br>*(Preview) Enable user feedback for Copilot and related experiences* |
| Inventory and logistics | [Enhance vendor rebate management](/dynamics365/release-plan/2024wave2/finance-supply-chain/dynamics365-supply-chain-management/enhance-vendor-rebate-management-reconciliation-resubmission-workflows) | [Process, review, and post rebates](../rebate-management/process-review-post.md)<br><br>[Rebate management posting setup](../rebate-management/rebate-management-posting.md)<br><br>[Rebate management deal workflows](../rebate-management/rebate-management-workflows.md) | Feature management:<ul><li>*Consolidate vendor invoices for the same vendor in vendor rebate deals*</li><li>*Enable posting of vendor rebate outputs to purchase order vendors*</li><li>*Enable resubmission of workflows for vendor rebate deals*</li></ul> |

## <a name="enhancements"></a>Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they're only enhancements, they aren't listed in the [release plan](/dynamics365/release-plan/2024wave2/finance-supply-chain/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

Some of these features aren't visible on your system until you turn them on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) using the name listed here for the *Feature management name* (additional configuration may also be needed). Features that don't show a feature management name are visible by default as of this version of Supply Chain Management, but typically add a new configuration option that you need to set to use the new functionality.

| Feature enhancement | Description |
|---|---|
| **Module:** Asset management<br><br>**Feature management name:** *Adjust forecast hours to match schedule hours when work orders are dispatched* | Lets you choose whether a forecast should be updated automatically when dispatching a work order after the hours have been manually changed.<br><br>Learn more in [Dispatch work orders](../asset-management/work-order-scheduling/dispatch-work-order.md). |
| **Module:** Asset management<br><br>**Feature management name:** *Role-based access control for work order lifecycle stages* | Lets admins assign security roles to each available work order lifecycle state. When a lifecycle state has a security role assigned to it, only users with that role will be able to change work orders to that lifecycle state.<br><br>Learn more in [Work order lifecycle states](../asset-management/setup-for-work-orders/work-order-lifecycle-states.md). |
| **Module:** Master planning<br><br>**Feature management name:** *Calculate catch weight quantities for catch weight enabled products in Planning Optimization* | Enhances Planning Optimization by enabling quantity calculations in catch weight units for products that are enabled as catch weight items. The feature ensures that master planning generates planned purchase orders with specified catch weight quantities. |
| **Module:** Master planning<br><br>**Feature management name:** *Dimension-based product configuration for Planning Optimization* | Dimension-based product configuration is one of the three built-in technologies that together help to simplify the creation of numerous product variants from a single product master and its bill of materials. This feature adds support for dimension-based product configuration to Planning Optimization, enabling the planning engine to generate planned orders both for final products and for their components based on the bill of materials for each item configuration.  |
| **Module:** Master planning<br><br>**Feature management name:** *Keep pegging between approved planned orders for Planning Optimization* | Lets you to choose whether pegging assignments should be kept for approved planned orders. To set this option, go to the **Master planning parameters** page, open the **Planned orders** tab, and set **Keep pegging between approved planned orders** to *Yes* or *No*. Enabling this option ensures that created supply is used for its initial purpose, following a first-come-first-served approach. We recommend that you enable this option in make-to-order scenarios or if you use grouping or splitting of planned orders. |
| **Module:** Master planning<br><br>**Feature management name:** *Support for material step consumption for Planning Optimization* | Adds support for step consumption in Planning Optimization. Step consumption is used to calculate fixed consumption based on the quantity of the end product. The quantity of consumed material is calculated based on the intervals (steps) defined for each BOM/formula line. |
| **Module:** Sales and marketing<br><br>**Feature management name:** *Introduce parameter to consider reserved on-hand quantity as unavailable for ATP* | Lets you choose whether reserved on-hand inventory should be considered available for use in promise (ATP) calculations. To set this options, go to the **Accounts receivable parameters** page, open the **Shipments** tab, expand the **Delivery control** FastTab, and set **ATP excl. reserved on-hand** to *Yes* or *No*. |
| **Module:** Master planning<br><br>**Feature management name:** *Clean up data from failed Demand planning import jobs* | Adds a scheduled task that cleans up staging table data related to failed import jobs from Demand planning in Microsoft Dynamics 365 Supply Chain Management. This feature is turned on by default. |
| **Module:** Procurement and sourcing<br><br>**Feature management name:** *Assign Auto Charge for Purchase Order* | Lets you choose whether to automatically add charges from a request for quotation (RFQ) to a purchase order. This feature adds a setting called **Assign Auto Charge for PO** to the **Request for quotation** tab of the **Procurement and sourcing parameters page**. When **Assign Auto Charge for PO** is set to *Yes*, charges from an RFQ are automatically copied to its related purchase order. This feature is mandatory and can't be turned off. |
| **Module:** Warehouse management<br><br>**Enhancement:** *Clean up work exception logs*<br><br>**Feature management name:** *(None)* | Adds a batch job that removes old or unneeded work-exception log entries based on specified criteria, which can help improve system performance for some operations (such as when searching for locations with open exceptions).<br><br>Learn more in [View and manage the work exceptions log](../warehousing/work-exceptions-log.md) |

## Preview features that are now generally available

The following table lists the features that were introduced as public preview features in a previous version and became generally available in version 10.0.43. As with other new features, most of these features are turned off by default, so you must turn them on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) if you want to use them.

| Module | Feature name | More information |
|--|--|--|
| Asset management | *Print work order document attachments* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.41 (September 2024)](whats-new-scm-10-0-41.md) |
| Cost management | *Inventory accounting in reporting currency* | N/A |
| Cost management | *Recalculation for Weighted Average Cost including Physical Transaction* | [Options for including physical value in cost calculations](../cost-management/include-physical-value.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.41 (September 2024)](whats-new-scm-10-0-41.md) |
| Inventory and warehouse management | *Dimension history for documents report data clean up* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.40 (June 2024)](whats-new-scm-10-0-40.md) |
| Inventory and warehouse management | *Inventory Visibility integration with ATP* | [Track time-series inventory in Inventory Visibility](../inventory/inventory-visibility-track-atp.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.41 (September 2024)](whats-new-scm-10-0-41.md) |
| Inventory and warehouse management | *Inventory Visibility transaction integration* | [Sync external inventory adjustments through Inventory Visibility](../inventory/inventory-visibility-sync-changes.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.41 (September 2024)](whats-new-scm-10-0-41.md) |
| Master planning | *Enable ATP calculations to consider user-modified delivery schedules applied to sales order lines* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.38 (February 2024)](whats-new-scm-10-0-38.md) |
| Master planning | *Improve Planning Optimization performance by merging and queueing plan regeneration jobs* | [Calculate sales order delivery dates using CTP](../master-planning/planning-optimization/calculate-delivery-dates-using-ctp.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.41 (September 2024)](whats-new-scm-10-0-41.md) |
| Master planning | *Inherit inventory status for planned intercompany demand orders* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.40 (June 2024)](whats-new-scm-10-0-40.md) |
| Master planning | *Near real-time CTP* | [Calculate sales order delivery dates using CTP](../master-planning/planning-optimization/calculate-delivery-dates-using-ctp.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.41 (September 2024)](whats-new-scm-10-0-41.md) |
| Procurement and sourcing | *Integrate with external contract lifecycle management systems* | [Enable and configure CLM integration](../procurement/contract-lifecycle-management/developer/clm-enable.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.42 (December 2024)](whats-new-scm-10-0-42.md) |
| Procurement and sourcing | *Enable purch parameters to control delivery information sync on sales and purchase orders* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.41 (September 2024)](whats-new-scm-10-0-41.md) |
| Production control | *Tracked components* | [Register and track batch/serial numbers for finished products and their components (preview)](../production-control/tracked-components.md)<br><br>[Configure the production floor execution interface](../production-control/production-floor-execution-configure.md)<br><br>[How workers use the production floor execution interface](../production-control/production-floor-execution-use.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.40 (June 2024)](whats-new-scm-10-0-40.md) |
| Sales and marketing | *Unified pricing management* | [Unified pricing management module overview](../unified-pricing-management/upm-pricing-management-overview.md) |

## Features turned on by default in this release

The following table lists the features that became turned on by default in version 10.0.43. You can still turn these features off in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) if necessary.

| Module | Feature name | More information |
|--|--|--|
| Asset management | *Asset Management enhancements* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.38 (February 2024)](whats-new-scm-10-0-38.md) |
| Asset management | *Change types on assets and functional locations* | [Change the type of existing functional locations](../asset-management/functional-locations/change-functional-location-type.md)<br><br>[Change the asset type of existing assets](../asset-management/objects/change-asset-type.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.38 (February 2024)](whats-new-scm-10-0-38.md) |
| Asset management | *Material availability check on maintenance work orders* | [Material availability check for work orders](../asset-management/work-orders/material-availability-check-work-orders.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.37 (November 2023)](whats-new-scm-10-0-37.md) |
| Inventory and warehouse management | *(India) Improvements in unit price and cost price handling in Stock transfer orders* | [Stock transfer orders for India](../../finance/localizations/india/apac-ind-stock-transfer.md) |
| Inventory and warehouse management | *Inventory transaction details page's performance improvement.* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.39 (April 2024)](whats-new-scm-10-0-39.md) |
| Master planning | *Actions based on requested date for Planning Optimization* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.39 (April 2024)](whats-new-scm-10-0-39.md) |
| Master planning | *Clean up data from failed Demand planning import jobs* | [Feature enhancements included in this release](#enhancements) |
| Master planning | *Dynamic positive days for Planning Optimization* | [Dynamic positive days for last-minute orders](../master-planning/dynamic-positive-days.md) |
| Master planning | *Enable the calculation of Batch CTP even when plan run ends with errors.* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.41 (September 2024)](whats-new-scm-10-0-41.md) |
| Master planning | *Exclude demand forecasts for a certain time period for Planning Optimization* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.39 (April 2024)](whats-new-scm-10-0-39.md) |
| Master planning | *Exclude items without on-order quantity for Planning Optimization.* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.40 (June 2024)](whats-new-scm-10-0-40.md) |
| Master planning | *Exclude specific sales orders or sales order lines in Planning Optimization* | [Exclude specific transactions or transaction types from master planning](../master-planning/ignore-transaction-types.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.36 (October 2023)](whats-new-scm-10-0-36.md) |
| Master planning | *Freezing time fence for Planning optimization* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.40 (June 2024)](whats-new-scm-10-0-40.md) |
| Master planning | *Item substitution (Plan group) support for Planning Optimization* | [Item substitution for formulas and bills of materials](../master-planning/item-substitution.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.39 (April 2024)](whats-new-scm-10-0-39.md) |
| Master planning | *Min/Max coverage code rounding for Planning Optimization* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.39 (April 2024)](whats-new-scm-10-0-39.md) |
| Master planning | *Positive days for Planning Optimization* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.38 (February 2024)](whats-new-scm-10-0-38.md) |
| Master planning | *Prioritize existing supply over required BOM/route in Planning Optimization* | [Coverage settings](../master-planning/coverage-settings.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.38 (February 2024)](whats-new-scm-10-0-38.md) |
| Master planning | *Recalculation of finite material date optionally for Planning Optimization* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.39 (April 2024)](whats-new-scm-10-0-39.md) |
| Master planning | *Round down advance action days* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.39 (April 2024)](whats-new-scm-10-0-39.md) |
| Master planning | *Sort on requested date in Net requirements form* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.39 (April 2024)](whats-new-scm-10-0-39.md) |
| Master planning | *Start dates of production orders of all components delayed when one of the components is delayed for Planning Optimization* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.38 (February 2024)](whats-new-scm-10-0-38.md) |
| Master planning | *Strict safety stock pegging for Planning Optimization* | [Safety stock pegging options](../master-planning/safety-stock-pegging.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.36 (October 2023)](whats-new-scm-10-0-36.md) |
| Master planning | *Support for splitting and grouping planned orders for Planning Optimization* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.38 (February 2024)](whats-new-scm-10-0-38.md) |
| Master planning | *Transport days support for Planning Optimization* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.40 (June 2024)](whats-new-scm-10-0-40.md) |
| Master planning | *Use of margins for scheduling orders* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.38 (February 2024)](whats-new-scm-10-0-38.md) |
| Procurement and sourcing | *Choose whether to consolidate sales orders for direct deliveries* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.41 (September 2024)](whats-new-scm-10-0-41.md) |
| Product information management | *Advanced export management configuration* | [Work with advanced export management for products, sales orders, and sales quotations](../pim/export-control-use.md)<br><br>[Enable and configure advanced export management](../pim/export-control-configure.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.36 (October 2023)](whats-new-scm-10-0-36.md) |
| Product information management | *Allow hazardous material divisions with same division codes in different material classes* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.39 (April 2024)](whats-new-scm-10-0-39.md) |
| Production control | *List view for reporting job progress from the production floor execution interface* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.40 (June 2024)](whats-new-scm-10-0-40.md) |
| Production control | *Material availability check for operations scheduled production orders* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.34 (July 2023)](whats-new-scm-10-0-34.md)<br><br>**Note:** This feature was mandatory in versions 10.0.41 and 10.0.42, but can now be turned off. |
| Production control | *Optimized report as finished process for serialized products* | N/A |
| Sales and marketing | *Recalculate delivery dates upon creation of direct delivery* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.40 (June 2024)](whats-new-scm-10-0-40.md) |
| Sales and marketing | *Unit of measure for line level charges* |  [Units of measure for line-level charges](../sales-marketing/line-charges-specific-unit.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.38 (February 2024)](whats-new-scm-10-0-38.md)<br><br>**Note:** This feature was mandatory in versions 10.0.41 and 10.0.42, but can now be turned off.|
| Transportation management | *Integrate Microsoft Sustainability Manager with transportation management* | [Integrate with Microsoft Sustainability Manager](../transportation/sustainability-manager-integration-setup.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.38 (February 2024)](whats-new-scm-10-0-38.md) |

## Features becoming mandatory in this release

The following table lists the features that became mandatory in version 10.0.43. These features can still be seen in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) but can no longer be turned off.

| Module | Feature name | More information |
|---|---|---|
| Cost management | *Clean up "Potential conflicts - inventory and general ledger" and "Potential conflicts - work in process and general ledger" report data* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.40 (June 2024)](whats-new-scm-10-0-40.md) |
| Cost management | *Cleanup redundant data from price calculation* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.37 (November 2023)](whats-new-scm-10-0-37.md) |
| Engineering change management | *Release multiple BOMs/formulas for Engineering Change Management* | [Release product structures](../engineering-change-management/release-product-structure.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.34 (July 2023)](whats-new-scm-10-0-34.md) |
| Inventory and warehouse management | *\[Russia\] Post storno financial inventory transactions according to the correction flag in the financial voucher for Sales orders* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.23 (January 2022)](whats-new-scm-10-0-23.md) |
| Inventory and warehouse management | *Cascade transfer order header date change to lines* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.35 (August 2023)](whats-new-scm-10-0-35.md) |
| Inventory and warehouse management | *Correct item that is not visible in released products form manually* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.40 (June 2024)](whats-new-scm-10-0-40.md) |
| Inventory and warehouse management | *Using unit of measure and unit quantity in inventory journals.* | N/A |
| Master planning | *Average daily usage for distribution scenarios* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.36 (October 2023)](whats-new-scm-10-0-36.md) |
| Master planning | *Show batch job status as Error when applicable for Planning Optimization* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.38 (February 2024)](whats-new-scm-10-0-38.md) |
| Master planning | *Use rounding for unit of measures in Planning Optimization* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.40 (June 2024)](whats-new-scm-10-0-40.md) |
| Procurement and sourcing | *Assign Auto Charge for Purchase Order* | [Feature enhancements included in this release](#enhancements) |
| Procurement and sourcing | *Check purchase order expenditure reviewers setup before enabling workflow.* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.35 (August 2023)](whats-new-scm-10-0-35.md) |
| Procurement and sourcing | *Synchronize updates of the Requested ship and receipt dates on intercompany sales and purchase order lines* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.38 (February 2024)](whats-new-scm-10-0-38.md) |
| Product information management | *Apply sales tax group for product variants in sales and procurement* | [Predefined product variants](../pim/tasks/create-predefined-product-variants.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.34 (July 2023)](whats-new-scm-10-0-34.md) |
| Production control | *Add filter to hide completed jobs on the Kanban board* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.41 (September 2024)](whats-new-scm-10-0-41.md) |
| Production control | *Change BOM item* | [React to last-minute changes in production](../production-control/react-to-last-minute-changes.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.38 (February 2024)] |
| Production control | *Default order settings for Change production order BOM item* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.39 (April 2024)](whats-new-scm-10-0-39.md) |
| Production control | *Enable partial receipt of subcontracted items and fix an issue with the calculation of scrap for BOM lines of type Vendor.* | N/A |
| Production control | *Leverage production order defaults in manufacturing execution system integration* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.37 (November 2023)](whats-new-scm-10-0-37.md) |
| Production control | *Production batch balancing enhanced onhand grid capability* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.32 (April 2023)](whats-new-scm-10-0-32.md) |
| Production control | *Production order route change* | [React to last-minute changes in production](../production-control/react-to-last-minute-changes.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.38 (February 2024)](whats-new-scm-10-0-38.md) |
| Production control | *Register material consumption on the production floor execution interface (non-WMS)* | [Configure the production floor execution interface](../production-control/production-floor-execution-configure.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.24 (February 2022)](whats-new-scm-10-0-24.md) |
| Production control | *Standard cost financial posting of a production/batch order with a scrap account method.* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.38 (February 2024)](whats-new-scm-10-0-38.md) |
| Sales and marketing | *Calculate and push prices, discounts and totals for selective sales orders and sales quotations when integrated with Dynamics 365 Sales*<br><br>*Copy Supply Chain Management sales quotation data to sales orders synced from Dynamics 365 Sales*<br><br>*Enable prospects in Sales quotation lifecycle with Dynamics 365 Sales*<br><br>*Integrate Sales Quotation lifecycle with Dynamics 365 Sales*<br><br>*Make Supply Chain Management price master when integrated with Dynamics 365 Sales*<br><br>*Process Dynamics 365 Sales integration related events*<br><br>*Set default ownership for sales quotations when integrated with Dynamics 365 Sales* | [Add efficiency in quote-to-cash with Dynamics 365 Sales](../../fin-ops-core/fin-ops/data-entities/add-efficiency-in-quote-to-cash-concept.md)<br><br>[Enable and configure extra efficiency in quote-to-cash with Dynamics 365 Sales](../../fin-ops-core/fin-ops/data-entities/add-efficiency-in-quote-to-cash-enable.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.34 (July 2023)](whats-new-scm-10-0-34.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.39 (April 2024)](whats-new-scm-10-0-39.md) |
| Sales and marketing | *Price and discount search for derived line creation* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.41 (September 2024)](whats-new-scm-10-0-41.md) |
| Sales and marketing | *Sales history cleanup performance improvements* | [Schedule sales history data cleanup](../sales-marketing/sales-update-history-cleanup-performance-improvements.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management version 10.0.19 (June 2021)](../supply-chain-dev/whats-new-scm-10-0-19.md) |
| Transportation management | *Match vendor invoice journal with voyage cost in different currency.* | [Turn on the Landed cost module and related features for your system](../landed-cost/landed-cost-enable.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.36 (October 2023)](whats-new-scm-10-0-36.md) |
| Transportation management | *Specify Goods In Transit Order when receiving via mobile device.* | [Turn on the Landed cost module and related features for your system](../landed-cost/landed-cost-enable.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.35 (August 2023)](whats-new-scm-10-0-35.md) |
| Warehouse management | *Over-pick materials for production orders and batch orders* | [Over-pick materials for production and batch orders](../warehousing/over-pick-materials-for-production-and-batch-orders.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.37 (November 2023)](whats-new-scm-10-0-37.md) |
| Warehouse management | *Prevent production orders to be released when full material is not available* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.38 (February 2024)](whats-new-scm-10-0-38.md) |

## Features removed from Feature management

The following table lists features that were removed from Feature management in version 10.0.43. These features are no longer listed in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) and are now a permanent part of Supply Chain Management.

| Module | Feature name | More information |
|---|---|---|
| Asset management | *Counter-based maintenance enhancements* | [Maintenance plans](../asset-management/preventive-and-reactive-maintenance/maintenance-plans.md) |
| Asset management | *Resource planning with maintenance* | N/A |
| Inventory and warehouse management | *(Poland) Allow to link several SAD invoices to one Purchase order line in one SAD* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.25 (April 2022)](whats-new-scm-10-0-25.md) |
| Inventory and warehouse management | *(Russia) Prevent discrepancies when issuing GTDs for purchase orders that include WMS-enabled items* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.26 (May 2022)](whats-new-scm-10-0-26.md) |
| Inventory and warehouse management | *Enable intercompany on-hand to only show nonzero on-hand quantity* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.28 (August 2022)](whats-new-scm-10-0-28.md) |
| Inventory and warehouse management | *Inventory journal approve workflow* | N/A |
| Inventory and warehouse management | *Inventory transaction consolidation* | [Consolidate inventory transactions](../inventory/archive-inventory-transactions.md)<br><br>[Archive Dynamics 365 Supply Chain Management Inventory transactions data](../../fin-ops-core/dev-itpro/sysadmin/archive-inventory.md)<br><br>[Consolidate inventory transactions FAQ](../inventory/inventory-transactions-consolidation-faq.md) |
| Inventory and warehouse management | *Reset the inventory journal workflow which status is unrecoverable.* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.37 (November 2023)](whats-new-scm-10-0-37.md) |
| Master planning | *(Stock transfer for India) Set up the default transfer type and price type for transfer orders created from Master planning* | [Stock transfer orders for India](../../finance/localizations/india/apac-ind-stock-transfer.md) |
| Master planning | *Priority driven MRP support for Planning Optimization* | [Priority-based planning](../master-planning/planning-optimization/priority-based-planning.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.23 (January 2022)](whats-new-scm-10-0-23.md) |
| Procurement and sourcing | *Assess supply risks to prevent supply chain disruptions* | [Supply risk assessment overview](../procurement/supply-risk-assessment-overview.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.31 (February 2023)](whats-new-scm-10-0-31.md) |
| Procurement and sourcing | *Purchase agreement matching policy* | N/A |
| Procurement and sourcing | *Purchase order delivery date* | N/A |
| Production control | *Enable to enter batch and serial numbers while reporting as finished from the Job Card Device.* | N/A |
| Production control | *Make finished goods physically available before posting to journals* | [Make finished goods physically available before posting to journals](../production-control/deferred-posting.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.29 (October 2022)](whats-new-scm-10-0-29.md) |
| Sales and marketing | *Copy customer reference and requisition to purchase order line when created from sales order line* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.36 (October 2023)](whats-new-scm-10-0-36.md) |
| Sales and marketing | *Sales order details performance enhancement* | [What's new or changed in Dynamics 365 Supply Chain Management 10.0.20 (August 2021)](../supply-chain-dev/whats-new-scm-10-0-20.md) |
| Sales and marketing | *Sales quotation details performance enhancement* | N/A |
| Transportation management | *Enable split vendor invoice journal line per cost type code and voyage id from multiple voyages*<br><br>*Performance improvements for post receipt function in Landed Cost* | [Landed cost module overview](../landed-cost/landed-cost-overview.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.33 (May 2023)](whats-new-scm-10-0-33.md) |
| Warehouse management | *Warehouse spatial awareness* | N/A |

## New and updated documentation resources

We have recently added or significantly updated the following help articles. These articles aren't necessarily related to the new features that were added for this release, as listed in the previous sections. However, they might help you get more out of existing features.

| Feature area | New or updated articles |
|---|---|
| Demand planning | [Demand forecasting algorithms](../demand-planning/forecast-algorithm-types.md) |
| Demand planning | [Forecast with signals (preview)](../demand-planning/forecasts-with-signals.md) |
| Demand planning | [Design forecast models](../demand-planning/design-forecast-models.md) |
| Demand planning | [Analyze demand plans with Copilot](../demand-planning/demand-planning-copilot.md) |
| Inventory management | [Inventory on-hand list](../inventory/inventory-on-hand-list.md) |
| Landed cost | [Landed cost module overview](../landed-cost/landed-cost-overview.md) |

## Related information

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.43 includes platform updates. Learn more in [Platform updates for version 10.0.43 of Finance and Operations apps (March 2024)](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-43.md). <!-- KFM: Confirm link -->

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.43, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=985753).

### Dynamics 365: 2024 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Microsoft Dynamics 365 and Microsoft Copilot for business functions: 2024 release wave 2 plan](/dynamics365/release-plan/2024wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
