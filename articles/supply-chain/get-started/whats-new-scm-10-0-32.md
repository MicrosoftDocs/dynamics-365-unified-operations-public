---
title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.32 (March 2023)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.32. 
author: kamaybac
ms.author: kamaybac
ms.reviewer: kamaybac
ms.search.form:
ms.topic: conceptual
ms.date: 01/30/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# What's new or changed in Dynamics 365 Supply Chain Management 10.0.32 (March 2023)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management version 10.0.32. This version has a build number of 10.0.1515 and is available on the following schedule:

- **Preview of release:** January 2023
- **General availability of release (self-update):** March 2023
- **General availability of release (auto-update):** April 2023

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Planning | New exception process for migrating to Planning Optimization | [Migration to Planning Optimization for master planning](../master-planning/new-master-planning-engine.md) | Enabled by default |
| Planning | [Transition to Planning Optimization one company at a time](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-supply-chain-management/transition-planning-optimization-one-company-at-time) | [Continue to use deprecated master planning for some companies](../master-planning/planning-optimization/get-started.md#exclude-po) | Enabled by default |
| Procurement | [Improve security for vendor bank account information updates](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-supply-chain-management/improve-security-vendor-bank-account-information-updates) |  [Vendor bank account workflow](../../finance/accounts-payable/vendor-bank-account-workflow.md) | Feature management:<br>*Vendor bank account change proposal workflow* |
| Product information management | [Share product information across legal entity boundaries](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-supply-chain-management/share-product-information-across-legal-entity-boundaries) | [Cross-company product sharing](../pim/share-products-across-companies.md) | Feature management:<br>*(Preview) Cross-company data sharing for products* |
| Warehouse management | License plate layouts | [License plate label layouts and printing](../warehousing/print-license-plate-labels-using-label-layouts.md) | Enabled by default |
| Warehouse management | [Optimize performance of internal movements in warehouse](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-supply-chain-management/optimize-performance-internal-movements-warehouse) | [Warehouse-specific inventory transactions](../warehousing/warehouse-transactions.md) | Feature management:<br>*(Preview) Warehouse-specific inventory transactions* |
| Warehouse management | [Pack shipments with speed and resilience](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-supply-chain-management/pack-shipments-speed-resilience) | [Packing containers with the Warehouse Management mobile app](../warehousing/warehouse-app-packing-containers.md)<br><br>[Example scenario – Pack containers with the Warehouse Management mobile app](../warehousing/warehouse-app-pack-containers-scenario.md)<br><br>[Container label layouts and printing](../warehousing/print-container-labels.md)<br><br>[Mobile device container packing policies](../warehousing/warehouse-app-pack-containers-policies.md) | Feature management:<br>*Pack containers using the Warehouse Management mobile app* |
| Warehouse management | Warehouse groups | [Warehouse groups](../warehousing/warehouse-groups.md) | Enabled by default |

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

If you want to turn any of these features on or off, you must do so in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Module | Feature name in feature management | More information |
|---|---|---|
| Procurement and sourcing | (Preview) Purchase order workflow submission and approval performance enhancement | This feature improves the performance of the purchase order workflow submission dialog and approval dialog which is most noticeable on purchase orders with larger number of lines. When this feature is enabled, purchase order totals and accounting distributions are calculated and validated by a workflow execution. Validation errors surface in the workflow history. This feature is not supported when budget control is enabled. |
| Production control | Production batch balancing enhanced onhand grid capability | Provides an enhanced on-hand grid capability for the batch balancing process. |
| Sales and marketing | Prevent updates to intercompany sales order line requested dates in header to lines update scenario when derived. | This feature prevents updating intercompany sales order line requested dates in a header to lines scenario when the intercompany sales order line is created from the purchase order and therefore is derived. Previously, when updating either confirmed or requested dates on the intercompany sales order header, both requested and confirmed sales order line dates would be updated when Transfer settings from the header to the lines ship and receipt dates, update ship and receipt dates, is *Yes*. When this feature is enabled, only the sales order line confirmed dates are updated in such a header to lines update scenario. |
| Warehouse management | (Preview) Warehouse-specific inventory transactions | Helps optimize the performance of warehouse management processes, especially when processing a large number of SKUs. It also prepares the Supply Chain Management database to support future improvements. The feature adds a new database table that stores inventory transactions specifically for warehouse management processes, which then use this table to drive on-hand inventory changes rather than using the common inventory transaction table (InventTrans). As a result, this feature significantly reduces the load on the InventTrans table, thereby also improving the performance of many other system processes. |

## Feature state changes in this release

The following table lists features that became mandatory or on by default in version 10.0.32. All these features will automatically be turned on for your system as soon as you update to version 10.0.32. Mandatory features can't be turned off, but features that are on by default can still be turned off by using [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). Features that are now listed as enabled by default are targeted to become mandatory with 2023 release wave 2.

The table also lists features that were previously in public preview but have changed to become generally available in version 10.0.32. This change indicates that the features are now recommended for use in production environments. These features are turned off by default unless otherwise noted. Therefore, you must use [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) to enable them if you want to use them. Features that are now listed as generally available are targeted to become enabled by default with 2023 release wave 2 and then to become mandatory with 2024 release wave 1.

| Module | Feature name | New feature state |
| --- | --- | --- |
| Accounts payable | Add lines to PO invoices associated with a purchase agreement | Mandatory |
| Accounts payable | [Enable vendor collaboration certification management](../../finance/public-sector/manage-vendor-certification.md) | On by default |
| Accounts payable | [Maintain vendor bank information using vendor collaboration workspace](../../finance/accounts-payable/maintain-vendor-bank-info.md) | Mandatory |
| Accounts payable | Purchasing card processing | On by default |
| Asset management | [Apply rules for grouping work orders while running a maintenance plan](../asset-management/preventive-and-reactive-maintenance/creating-work-orders.md) | Mandatory |
| Asset management | [Counter-based maintenance enhancements](../asset-management/preventive-and-reactive-maintenance/maintenance-plans.md) | On by default |
| Asset management | [Offset accounts for expenses in work order journals](whats-new-scm-10-0-23.md) | On by default |
| Asset management | [Work order billing](../asset-management/integration-to-project-management-and-accounting/customer-billing.md) | Mandatory|
| Cost management | Enable error execution log for cost accounting overhead calculation | Generally available |
| Cost management | [Inventory aging report storage](../cost-management/inventory-aging-report-storage.md) | On by default |
| Cost management | [Post on-hand adjustments using configurable reason codes connected to offset accounts](../warehousing/reason-codes-for-counting-journals.md) | On by default |
| Engineering change management | [Enable change management on existing products](../engineering-change-management/change-management-existing-products.md) | Mandatory |
| Engineering change management | [Engineering notifications for production](../engineering-change-management/engineering-change-management.md) | Mandatory |
| Engineering change management | [Improved attribute inheritance for Engineering Change Management](../engineering-change-management/engineering-attributes-and-search.md) | Mandatory |
| Engineering change management | [Product readiness checks](../engineering-change-management/product-readiness.md) | Mandatory |
| Engineering change management | [Variant generation for engineering products](../engineering-change-management/engineering-variants.md) | Mandatory |
| Inventory management | [Inventory on-hand report data clean up](whats-new-scm-10-0-28.md) | On by default |
| Master planning | [Azure Machine Learning Service for demand forecasting](../master-planning/demand-forecasting-setup.md) | On by default |
| Master planning | [Batchable firming and consolidation for planned bulk and pack batch orders](whats-new-scm-10-0-20.md) | Mandatory |
| Master planning | [Consider inventory lead time when creating a planned transfer order](whats-new-scm-10-0-27.md) | Generally available |
| Master planning | [CTP for Planning Optimization](../master-planning/planning-optimization/calculate-delivery-dates-using-ctp.md) | Generally available |
| Master planning | [Group transactions in Planning Optimization](whats-new-scm-10-0-29.md) | On by default |
| Master planning | [Include items with on-hand when pre-processing filters are enabled](/dynamics365-release-plan/2020wave1/dynamics365-supply-chain-management/master-planning-include-items-on-hand-when-pre-processing-filters-are-enabled) | Mandatory |
| Master planning | [Make-to-order supply automation](../master-planning/make-to-order-supply-automation.md) | On by default |
| Master planning | [Planned orders simplified](../master-planning/planning-optimization/planned-orders-simplified.md) | Mandatory |
| Master planning | [Priority driven MRP support for Planning Optimization](../master-planning/planning-optimization/priority-based-planning.md) | On by default |
| Master planning | [Source products and materials from multiple vendors using Planning Optimization](../master-planning/source-from-multiple-vendors.md) | Generally available |
| Procurement and sourcing | [Allow vendors to apply for procurement categories through vendor collaboration](../procurement/category-requests-from-vendors.md) | Mandatory |
| Procurement and sourcing | Bid submission success message | Mandatory |
| Procurement and sourcing | Check unit precision for not-stocked items | On by default |
| Procurement and sourcing | [Clean up purchase-order update history](whats-new-scm-10-0-23.md)  | Mandatory |
| Procurement and sourcing | [Default broker contract tax information on vendor invoice lines](whats-new-scm-10-0-27.md) | On by default |
| Procurement and sourcing | Disable Purchase Requisition Distribution Reset Button | Mandatory |
| Procurement and sourcing | [Limit the number of purchase order lines per batch task](whats-new-scm-10-0-27.md) | On by default |
| Procurement and sourcing | [Post registered quantities of stocked products and remainders of not-stocked products for receipts and vendor invoices](whats-new-scm-10-0-26.md) | On by default |
| Procurement and sourcing | [Purchasing cXML enhancements](../procurement/purchasing-cxml-enhancements.md) | Mandatory |
| Procurement and sourcing | [Put vendor on hold for purchase orders](../procurement/set-up-vendor-accounts.md) | Mandatory |
| Procurement and sourcing | Request for quotation amendment and cancellation email framework options | Generally available |
| Procurement and sourcing | [RFQ questions and answers](../procurement/rfq-question.md) | Mandatory |
| Procurement and sourcing | [Sealed bidding for RFQs](../procurement/sealed-bidding.md) | On by default |
| Procurement and sourcing | [Synchronize tracking dimensions on intercompany sales and purchase order lines](whats-new-scm-10-0-26.md) | On by default |
| Product information management | [Clean up product attribute values](whats-new-scm-10-0-26.md) | On by default |
| Product information management | [Country of origin management feature](../pim/country-of-origin.md) | Mandatory |
| Product information management | [Populate product attribute values](whats-new-scm-10-0-27.md) | On by default |
| Production control | [Auto-picking of warehouse enabled materials for auto-posted picking lists](whats-new-scm-10-0-23.md)  | On by default |
| Production control | [Copy generic routes](whats-new-scm-10-0-20.md) | On by default |
| Production control | [Enable to enter batch and serial numbers while reporting as finished from the Job Card Device](../production-control/report-finished-job-device.md) | Mandatory |
| Production control | Improved production catch weight quantity picking | Mandatory |
| Production control | [Manufacturing execution system integration](../production-control/mes-integration.md) | Mandatory |
| Production control | ["My day" view for the production floor execution interface](../production-control/production-floor-execution-use.md) | Mandatory |
| Production control | [My jobs tab on the production floor execution interface](../production-control/production-floor-execution-use.md) | On by default |
| Production control | [On-demand material availability check for production orders](whats-new-scm-10-0-24.md) | Mandatory |
| Production control | Options for validating ingredient batch expiration dates | Generally available |
| Production control | [Production teams in the production floor execution interface](../production-control/production-floor-execution-use.md) | On by default |
| Production control | [Register material consumption on the production floor execution interface (non-WMS)](../production-control/production-floor-execution-use.md) | On by default |
| Production control | [Report on co- and by-products from the production floor execution interface](../production-control/production-floor-execution-use.md) | Mandatory |
| Production control | [Report on planning items in the production floor execution interface](whats-new-scm-10-0-27.md) | Mandatory |
| Production control | [Update related resource requirements when a route operation is changed](whats-new-scm-10-0-20.md) | On by default |
| Production control | [Validate expiration of raw materials against planned consumption date](whats-new-scm-10-0-23.md) | Mandatory |
| Sales and marketing | [Calculate sales totals using multiple threads](whats-new-scm-10-0-29.md) | On by default |
| Sales and marketing | Limit the number of sales order lines per batch task | Mandatory |
| Sales and marketing | [Update prices and discounts entered manually for intercompany](whats-new-scm-10-0-29.md)  | On by default |
| Sales and marketing | [Update Requested receipt date with Confirmed date for intercompany orders](whats-new-scm-10-0-19.md) | Mandatory |
| Shared AP and AR | Cancel posted rebate provision with a posting date | Generally available |
| Shared AP and AR | Credit note calculation enhancement in Rebate management | Generally available |
| Shared AP and AR | Enable auto negative tier in Rebate management | Generally available |
| Shared AP and AR | [Rebate Management](../rebate-management/rebate-management-overview.md) | On by default |
| Shared AP and AR | Write-off before rebate claim | Generally available |
| Transportation management | Goods in Transit Receiving and Put away | On by default |
| Transportation management | Options for updating the mode of delivery for sales order lines when creating loads | Generally available |
| Warehouse management | Allow editing of physical dimension for a released product and its handling unit. | Mandatory |
| Warehouse management | Auto update shipment | Mandatory |
| Warehouse management | Change the error to a warning when releasing a load where sufficient quantity isn't available | On by default |
| Warehouse management | [Cross docking templates with location directives](../warehousing/planned-cross-docking.md) | Mandatory |
| Warehouse management | Deferred put - container | Mandatory |
| Warehouse management | [Disable expected receipts from quality orders that sample blocked inventory](../inventory/inventory-blocking.md) | Mandatory |
| Warehouse management | [Enhanced parser for GS1 barcodes](../warehousing/gs1-barcodes.md) | On by default |
| Warehouse management | Evaluate work header breaks before work header maximums during work creation | On by default |
| Warehouse management | Include Confirmed ship and Confirmed receipt dates into date filters on Load planning workbench | On by default |
| Warehouse management | [Item consolidation location utilization](../warehousing/item-consolidation-location-utilization.md) | Mandatory |
| Warehouse management | [License plate receiving enhancements](../warehousing/warehousing-mobile-device-app-license-plate-receiving.md) | On by default |
| Warehouse management | License plate receiving history | Mandatory |
| Warehouse management | License plate validation on source document lines | On by default |
| Warehouse management | Line reservation enhancements for the batch number reservation form feature | On by default |
| Warehouse management | [Location directive inventory picking aging](../warehousing/location-directive-inventory-picking-aging.md) | Mandatory |
| Warehouse management | [Manual shipment consolidation](../warehousing/consolidate-shipments-manual-workbench.md) | Mandatory |
| Warehouse management | [Manual transfer line picking service for admin or similar trusted users](whats-new-scm-10-0-28.md) | Mandatory |
| Warehouse management | [Maximum execution time for the warehouse management on-hand entries cleanup job](../warehousing/onhand-cleanup.md)  | Mandatory |
| Warehouse management | [New load planning workbench pages](whats-new-scm-10-0-24.md) | Mandatory |
| Warehouse management | [Organization-wide "Schedule work creation" wave method](../warehousing/configure-wave-schedule-work-creation.md) | Mandatory |
| Warehouse management | [Organization-wide system directed work sequencing](../warehousing/system-directed-work-sequencing.md) | Mandatory |
| Warehouse management | [Organization wide wave step code](../warehousing/advanced-load-building-during-wave.md) | Mandatory |
| Warehouse management | [Outbound sorting](../warehousing/outbound-sorting.md) | Mandatory |
| Warehouse management | [Over receipt of load quantities](../warehousing/inbound-load-handling.md) | On by default |
| Warehouse management | [Packaging product dimensions](../warehousing/packing-vs-storage-dimensions.md) | Mandatory |
| Warehouse management | [Packing work for packing stations](../warehousing/packing-work.md) | On by default |
| Warehouse management | Parent license plates cannot be target license plates | On by default |
| Warehouse management | [Pick line grouping](../warehousing/pick-line-grouping.md) | On by default |
| Warehouse management | Purchase order quantity left to load calculation using registered quantities | On by default |
| Warehouse management | [Quality Management For Warehouse Processes](../inventory/quality-management-for-warehouses-processes.md) | Mandatory |
| Warehouse management | [Replenishment over location capacity](../warehousing/replenishment-over-location-capacity.md) | Mandatory |
| Warehouse management | Sales order packing slip corrections/cancellation transaction status change | On by default |
| Warehouse management | Scale unit support for warehouse app work lists | Mandatory |
| Warehouse management | [Scan GS1 barcodes](../warehousing/gs1-barcodes.md) | Mandatory |
| Warehouse management | [Schedule work creation](../warehousing/configure-wave-schedule-work-creation.md) | Mandatory |
| Warehouse management | [System directed cluster picking](../warehousing/system-directed-cluster-pick.md) | Mandatory |
| Warehouse management | System directed work sequencing | Mandatory |
| Warehouse management | [Use faster API for containers closing/reopening on packing station](whats-new-scm-10-0-21.md) | Mandatory |
| Warehouse management | [Validate templates selected for replenishment jobs](whats-new-scm-10-0-20.md) | Mandatory |
| Warehouse management | [Warehouse management app data inquiry flow](../warehousing/warehouse-app-data-inquiry.md) | Mandatory |
| Warehouse management | [Warehouse management application - blank GTD](whats-new-scm-10-0-26.md) | Mandatory |
| Warehouse management | [Warehouse release rule](../warehousing/release-to-warehouse-rule.md) | Mandatory |
| Warehouse management | [Wave Load building feature](../warehousing/advanced-load-building-during-wave.md) | Mandatory |
| Warehouse management | [Wave step code](../warehousing/wave-step-codes.md) | Mandatory |
| Warehouse management | [Work policy enhancements for inbound work](../warehousing/warehouse-work-policies.md) | On by default |
| Warehouse management | [Work split](../warehousing/work-split.md) | Mandatory |

## New and updated documentation resources

We have recently added or significantly updated the following help articles. These articles aren't necessarily related to the new features that were added for this release, as listed in the previous sections. However, they might help you get more out of existing features.

| Feature area | New or updated articles |
|---|---|
| Master planning | [DDMRP FAQ](../master-planning/planning-optimization/ddmrp-faqs.md) |
| Master planning | [Set up scrap to calculate raw material requirements](../master-planning/scrap-calculations.md) |
| Supply Chain Management development | [Create and process custom message queues and message types](../supply-chain-dev/message-processor.md) |
| Support | [Use Customer Lockbox to manage secure access to customer data](../../fin-ops-core/dev-itpro/sysadmin/customer-lockbox.md) |
| Warehouse management | [Manage inbound putaway based on container types](../warehousing/inbound-putaway-by-container-type.md) |
| Warehouse management | [Monitor Warehouse Management usage and performance](../warehousing/application-insights-monitor-usage-performance.md)

## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.32 includes platform updates. To learn more, see [Platform updates for version 10.0.32 of Finance and Operations apps (March 2023)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-32.md).

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.32, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=787268).

### Dynamics 365 and industry clouds: 2023 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2023 release wave 1 plan](/dynamics365/release-plan/2023wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
