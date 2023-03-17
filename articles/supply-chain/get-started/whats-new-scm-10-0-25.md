---
title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.25 (April 2022)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.25. 
author: kamaybac
ms.date: 03/14/2022
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this article to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: kamaybac
ms.search.validFrom: 2021-02-01
ms.dyn365.ops.version: 10.0.25
---

# What's new or changed in Dynamics 365 Supply Chain Management 10.0.25 (April 2022)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in the Microsoft Dynamics 365 Supply Chain Management version 10.0.25. This version has a build number of 10.0.1149 and is available as follows:

- **Preview of release:** February 2022
- **General availability of release (self-update):** March 2022
- **General availability of release (auto-update):** April 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this article was initially published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Inventory&nbsp;and&nbsp;logistics | [Hazardous materials enhancements](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/hazardous-materials-enhancements) | Coming soon | Feature management:<br>*Hazardous materials enhancements* |
| Inventory&nbsp;and&nbsp;logistics | [Packing work for packing stations](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/packing-work-packing-stations) | [Packing work for packing outbound containers and processing shipments](../warehousing/packing-work.md) | Feature management:<br>*Packing work for packing stations* |
| Inventory&nbsp;and&nbsp;logistics | [Scan barcodes in the warehouse using GS1 format standards](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/scan-barcodes-warehouse-using-gs1-format-standards) | [GS1 bar codes and QR codes](../warehousing/gs1-barcodes.md) | Feature management:<br>*Scan GS1 barcodes* |
| Manufacturing | [Material consumption and reservations in the production floor execution interface](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/material-consumption-reservations-production-floor-execution-interface) | [How workers use the production floor execution interface](../production-control/production-floor-execution-use.md) | Feature management:<br>*Register material consumption on the production floor execution interface (non-WMS)*<br><br>And/or:<br><br>Feature management:<br>*(Preview) Register material consumption on the production floor execution interface (WMS-enabled)* |
| Planning | [Planning Optimization centralized calendar maintenance](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/planning-optimization-centralized-calendar-maintenance) | [Calendars and master planning](../master-planning/supply-chain-calendars-master-planning.md) | Enabled by default |
| Planning | [Planning Optimization suggestions to optimize existing supply](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/planning-optimization-suggestions-optimize-existing-supply) | [Action messages](../master-planning/action-messages.md) | Enabled by default |
| Planning | Planned orders simplified | [Planned orders simplified](../master-planning/planning-optimization/planned-orders-simplified.md ) | Feature management:<br>*Planned orders simplified* |

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

If you want to turn any of these features on or off, you must do that in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Module | Feature name in feature management | More information |
|---|---|---|
| Inventory and warehouse management | (Poland) Allow to link several SAD invoices to one Purchase order line in one SAD | This feature lets you split purchase order lines and link them to a single administrative document (SAD) when those purchase order lines were posted for several different invoices (such as for different shipments). |
| Procurement and sourcing | Consolidate multiple purchase requisitions into a single purchase order by accounting date | This feature allows multiple purchase requisitions to be consolidated into a single purchase order if the different purchase requisitions have different accounting dates. Purchase order creation and demand consolidation purchasing policy rules can be set up to automate the decision for grouping requisition lines by accounting date on the purchase order level. Purchase order consolidation by accounting date is not supported if budget control is enabled because the accounting date is used for budget reservations and encumbrance. Therefore, it should be retained during the transition from purchase requisition to purchase order. |
| Procurement and sourcing | Display legacy default RFQ reply field settings | This feature reintroduces the legacy default request for quotation (RFQ) reply field settings, which were previously removed from the user interface. These settings don't provide any functionality out of the box, but can be customized to provide it as required. Enable this feature if your organization has already added functionality for the default RFQ reply field settings or is planning to. When this feature is enabled, you can access the settings by going to the **Procurement and sourcing parameters** page, opening the **Request for quotation** tab, and selecting **Default request for quotation reply fields**. |
| Procurement and sourcing | Merge financial dimensions from the vendor with active dimension link financial dimension on the purchase order | This feature lets you merge financial dimensions from vendors with active dimension link financial dimensions after purchase requisition approval if you set up a link between a financial dimension and the site inventory dimension. Purchase order creation and demand consolidation purchasing policy rules can be set up to drive the decision for merging financial dimensions from vendors with active dimension link financial dimension on the purchase order header level. |
| Production control | (Russia) Enable default location setup for production formula/BOM and automatic GTD reservation/consumption in production | The feature enables additional options for production from imported raw materials (Russian localization only):<ul><li>Option to set the automatic default location for production formulas and bills of material on both resource groups and warehouses.</li><li>Automatic reservation of raw materials by the *GTD number* dimension at WMS-activated warehouses according to the non-WMS reservation algorithm. This applies in cases where a work policy for *Raw material picking* exists with **Work creation method** set to *Never* and the warehouse, location and item number setup matches the inventory transactions of the production (batch) order.</li><li>Automatic consumption of raw materials by *GTD number* dimension upon picking list posting, according to the acquired reservation described previously.</li></ul> |
| Warehouse management | Scale unit support for inbound and outbound warehouse orders | This feature causes the system to create outbound warehouse orders during the release-to-warehouse process, and to create inbound warehouse orders when transfer orders are posted as shipped. The system then synchronizes each inbound or outbound warehouse order to the scale unit responsible for shipping or receiving the order. Note that after enabling this feature, your warehouse execution workloads must be upgraded. For more information, see [Warehouse management workloads for cloud and edge scale units](../cloud-edge/cloud-edge-workload-warehousing.md).<br><br>This feature requires the *Decouple putaway work from ASNs* feature and will enable the capability of receiving transfer orders using the license plate receiving process on the Warehouse Management mobile app. |

## Feature state changes in this release

The following table lists features that became mandatory or on by default starting in 10.0.25. All of these features will automatically be turned on for your system as soon as you update to 10.0.25. Mandatory features can't be turned off, but features that are on by default can still be turned off using [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

The table also lists features that were previously in public preview, but have changed to become generally available in 10.0.25, which means they are now recommended for use on production environments. These features are turned off by default unless otherwise noted, so you must use [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) to enable them if you want to use them.

| Module | Feature name | Feature state |
| --- | --- | --- |
| Asset management | [Apply rules for grouping work orders while running a maintenance plan](../asset-management/preventive-and-reactive-maintenance/creating-work-orders.md) | Generally available |
| Asset management | [Counter-based maintenance enhancements](../asset-management/preventive-and-reactive-maintenance/maintenance-plans.md) | Generally available |
| Cost management | [Cost calculation level](../cost-management/cost-calculation-level.md) | Generally available |
| Cost management | Enable user-defined batch number setup for inventory closing reverse | Generally available |
| Cost management | [Inventory closing progress details](whats-new-scm-10-0-21.md) | Generally available |
| Cost management | [Options of defaulting financial dimensions for inventory standard cost revaluation](../cost-management/manage-standard-cost-updates.md) | Generally available |
| Cost management | Inventory value report data clean up | On by default |
| Cost management | [Inventory value report storage](../cost-management/inventory-value-report-storage.md) | On by default |
| Cost management | Show inventory closing log in grid | On by default |
| Engineering change management | [Enable change management on existing products](../engineering-change-management/change-management-existing-products.md) | On by default |
| Engineering change management | [Engineering Change Management](../engineering-change-management/product-engineering-overview.md) | On by default |
| Engineering change management | [Engineering notifications for production](../engineering-change-management/engineering-change-management.md) | On by default |
| Engineering change management | [Improved attribute inheritance for Engineering Change Management](../engineering-change-management/engineering-attributes-and-search.md) | On by default |
| Engineering change management | [Manage changes to formulas and their ingredients](../engineering-change-management/manage-formula-changes.md) | On by default |
| Engineering change management | [Product readiness checks](../engineering-change-management/product-readiness.md) | On by default |
| Engineering change management | [Variant generation for engineering products](../engineering-change-management/engineering-variants.md) | On by default |
| Inventory and warehouse management | Navigation to BOM version from BOM lines | Mandatory |
| Master planning | [Batchable firming and consolidation for planned bulk and pack batch orders](whats-new-scm-10-0-20.md) | Generally available |
| Master planning | Resource planning with maintenance | Generally available |
| Master planning | Enable master plan setup wizard features | Mandatory |
| Master planning | [Forecast model selection on Demand forecast details](../master-planning/manual-adjustments-baseline-forecast.md) | Mandatory |
| Master planning | [Master planning progress visualization](../master-planning/tasks/monitor-master-planning-run.md) | Mandatory |
| Master planning | [Parallel firming of planned orders](../master-planning/planning-optimization/planned-order-firming.md) | Mandatory |
| Master planning | [Planned order firming with filtering](../master-planning/planning-optimization/planned-order-firming.md) | On by default |
| Master planning | [Saved views for planned orders](saved-views-scm.md) | On by default |
| Procurement and sourcing | Disable Purchase Requisition Distribution Reset Button | Generally available |
| Procurement and sourcing | [Enable resetting procurement related workflows](whats-new-scm-10-0-20.md) | Generally available |
| Procurement and sourcing | Ability to confirm accepted purchase orders from vendor collaboration in batch | Mandatory |
| Procurement and sourcing | Purchase agreement Closed status | Mandatory |
| Procurement and sourcing | Add lines to PO invoices associated with a purchase agreement | On by default |
| Procurement and sourcing | Add Quantity ordered field to the Posting product receipt page | On by default |
| Procurement and sourcing | [Allow vendors to apply for procurement categories through vendor collaboration](../procurement/category-requests-from-vendors.md) | On by default |
| Procurement and sourcing | Charges from and to amounts on Purchase orders | On by default |
| Procurement and sourcing | Charges setup with site and warehouse | On by default |
| Procurement and sourcing | Enable purchase duty calculation based on annual tariff | On by default |
| Procurement and sourcing | [Purchase agreement responsible party](../procurement/purchase-agreements.md) | On by default |
| Procurement and sourcing | [Saved views for purchase orders](saved-views-scm.md) | On by default |
| Product information management | [Strict validation on default order quantities](../production-control/default-order-settings.md) | Mandatory |
| Product information management | Bill of materials report pre-processing to avoid timeout | On by default |
| Product information management | Default financial dimensions separately when using item templates | On by default |
| Product information management | Enable product dimension groups for item templates | On by default |
| Product information management | Regenerate product variant names based on nomenclature | On by default |
| Product information management | [Variant suggestions page improvements](../pim/tasks/create-predefined-product-variants.md) | On by default |
| Production control | Improved production catch weight quantity picking | Generally available |
| Production control | A new button to Stop break has been added to the Job Card Terminal page | Mandatory |
| Production control | [Enable automatic generation of license plate number when reporting as finished in the job card device](../production-control/production-floor-execution-configure.md) | Mandatory |
| Production control | Enable partial receipt of subcontracted items and fix an issue with the calculation of scrap for BOM lines of type Vendor | Mandatory |
| Production control | [Feature for locking job card device and job card terminal so that they can be sanitized](../production-control/production-floor-execution-configure.md) | Mandatory |
| Production control | Improvements to the Approve and Transfer jobs dialogs | Mandatory |
| Production control | [License plate for reporting as finished added to the Job Card Device](../production-control/production-floor-execution-configure.md) | Mandatory |
| Production control | [Print label from Job Card Device](../production-control/production-floor-execution-configure.md) | Mandatory |
| Production control | [Production floor execution](../production-control/production-floor-execution-configure.md) | Mandatory |
| Production control | [Asset management functionality for the production floor execution interface](../production-control/production-floor-execution-configure.md) | On by default |
| Production control | [Job search for the production floor execution interface](../production-control/production-floor-execution-configure.md) | On by default |
| Production control | [Override default production reservation](../production-control/override-default-reservation-principle.md) | On by default |
| Production control | [Show full serial, batch, and license plate numbers in the production floor execution interface](whats-new-scm-10-0-21.md) | On by default |
| Sales and marketing | [Sales order details performance enhancement](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/sales-order-details-performance-enhancement) | Generally available |
| Sales and marketing | Sales quotation details performance enhancement | Generally available |
| Sales and marketing | Sales order referenced data export policy | Mandatory |
| Sales and marketing | [Sales order to purchase order line deletion policy](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/sales-order-purchase-order-line-deletion-policy) | Mandatory |
| Sales and marketing | [Sales quotation referenced data export policy](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-supply-chain-management/sales-quotation-referenced-data-export-policy)| Mandatory |
| Sales and marketing | [Contact person data entity export optimization](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/contact-person-data-entity-export-optimization) | On by default |
| Sales and marketing | Enable lookup for sales quotation document introduction and document conclusion fields | On by default |
| Sales and marketing | [Improve "Top 100" customers report performance](whats-new-scm-10-0-23.md) | On by default |
| Sales and marketing | Recalculate estimated customer balance | On by default |
| Sales and marketing | [Sales return order line registration with decimal precision with and without catch weight](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/sales-return-order-line-registration-decimal-precision-without-catch-weight) | On by default |
| Sales and marketing | [Saved Views for Sales and Marketing](saved-views-scm.md) | On by default |
| Sales and marketing | Single click sales order confirmation | On by default |
| Warehouse management | [Cross docking templates with location directives](../warehousing/planned-cross-docking.md) | Generally available |
| Warehouse management | [Disable expected receipts from quality orders that sample blocked inventory](../inventory/inventory-blocking.md) | Generally available |
| Warehouse management | License plate receiving history | Generally available |
| Warehouse management | [Material handling equipment interface](../warehousing/mhax.md) | Generally available |
| Warehouse management | [Round quantities down to nearest sales unit on release to warehouse](whats-new-scm-10-0-19.md) | Generally available |
| Warehouse management | Scale unit support for warehouse app work lists | Generally available |
| Warehouse management | Shipment wave label details | Generally available |
| Warehouse management | [Use faster API for containers closing/reopening on packing station](whats-new-scm-10-0-21.md) | Generally available |
| Warehouse management | [Validate templates selected for replenishment jobs](whats-new-scm-10-0-20.md) | Generally available |
| Warehouse management | Allow replenishment template to use existing immediate replenishment work (across units) | Mandatory |
| Warehouse management | Automatic assigning of the GUIDs on WHS user creation | Mandatory |
| Warehouse management | Capture product variants and tracking dimensions in the warehousing app during load item receiving | Mandatory |
| Warehouse management | [Change the inventory status of items controlled by tracking dimensions](../inventory/inventory-statuses.md) | Mandatory |
| Warehouse management | [Change work pool on work](../warehousing/change-work-pool-on-work.md) | Mandatory |
| Warehouse management | [Cluster position full](../warehousing/cluster-position-full.md) | Mandatory |
| Warehouse management | [Cluster Putaway Feature](../warehousing/putaway-clusters.md) | Mandatory |
| Warehouse management | [Confirm and transfer](../warehousing/confirm-and-transfer.md) | Mandatory |
| Warehouse management | [Confirm outbound shipments from batch jobs](../warehousing/confirm-outbound-shipments-from-batch-jobs.md) | Mandatory |
| Warehouse management | [Control whether to display a receiving summary page on mobile devices](../warehousing/warehousing-mobile-device-app-license-plate-receiving.md) | Mandatory |
| Warehouse management | [Deferred processing of manual inventory movement operation](../warehousing/deferred-processing-manual-inventory-movement.md) | Mandatory |
| Warehouse management | Do not allow to create loads, that do not meet wave load building template requirements | Mandatory |
| Warehouse management | [Enhanced license plate label layouts](../warehousing/document-routing-layout-for-license-plates.md) | Mandatory |
| Warehouse management | [Evaluate all actions for Multi SKU location directives](/troubleshoot/dynamics-365/supply-chain/warehousing/evaluate-multiple-location-directive-actions) | Mandatory |
| Warehouse management | Hide the Total Value field on the "All Loads" and "Load Details" pages | Mandatory |
| Warehouse management | License plate label build configuration | Mandatory |
| Warehouse management | Load line manual correction for admin or similar trusted users | Mandatory |
| Warehouse management | [Location license plate positioning](../warehousing/location-license-plate-positioning.md) | Mandatory |
| Warehouse management | [Location product dimension mixing](../warehousing/location-product-dimension-mixing.md) | Mandatory |
| Warehouse management | Make mobile device inventory movement inventory status field editable | Mandatory |
| Warehouse management | [Manual sales line picking service for admin or similar trusted users](../warehousing/manual-order-line-picking-exception-handling.md) | Mandatory |
| Warehouse management | [Prevent transfer order shipped license plates from being used on other warehouses than the destination warehouse](../warehousing/warehousing-mobile-device-app-license-plate-receiving.md) | Mandatory |
| Warehouse management | Prompt to resolve ambiguous 'Loc / LP' names | Mandatory |
| Warehouse management | [Quality check](../warehousing/quality-check.md) | Mandatory |
| Warehouse management | [User settings, icons, and step titles for the new warehouse app](../warehousing/install-configure-warehouse-management-app.md) | Mandatory |
| Warehouse management | [Additional location zone](../warehousing/additional-location-zones.md) | On by default |
| Warehouse management | [Create and process transfer orders from the warehouse app](../warehousing/create-transfer-order-from-warehouse-app.md) | On by default |
| Warehouse management | Enable fast validation for warehouse mobile devices | On by default |
| Warehouse management | [Maximum execution time for the warehouse management on-hand entries cleanup job](../warehousing/onhand-cleanup.md) | On by default |
| Warehouse management | [Outbound workload visualization](../warehousing/outbound-workload-visualization.md) | On by default |
| Warehouse management | [Process warehouse app events](../warehousing/warehouse-app-events.md) | On by default |
| Warehouse management | [Saved view for the load planning workbench](saved-views-scm.md) | On by default |
| Warehouse management | [Saved view for the work details page](saved-views-scm.md) | On by default |
| Warehouse management | [Saved view for wave processing](saved-views-scm.md) | On by default |
| Warehouse management | [Saved views for load processing](saved-views-scm.md) | On by default |
| Warehouse management | [Saved views for shipment processing](saved-views-scm.md) | On by default |
| Warehouse management | [Wave batch job details](../warehousing/wave-processing.md) | On by default |
| Warehouse management | [Wave execution notifications](../warehousing/wave-execution-notifications.md) | On by default |

## Additional resources

### Platform updates for finance and operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.25 includes platform updates. To learn more, see [Platform updates for version 10.0.25 of finance and operations apps (April 2022)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-25.md).

### Bug fixes

For information about the bug fixes included in each of the updates that are part of 10.0.25, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=654580&dbType=3&qc=3799fa965b008dd980d27cf740e4582e6384ec6601ae8a35b7eaec6f1287a868).

### Dynamics 365 and industry clouds: 2022 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2022 release wave 1 plan](/dynamics365-release-plan/2022wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]

