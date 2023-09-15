---
title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.29 (October 2022)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.29. 
author: kamaybac
ms.date: 08/12/2022
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this article to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: kamaybac
ms.search.validFrom: 2022-08-01
ms.dyn365.ops.version: 10.0.29
---

# What's new or changed in Dynamics 365 Supply Chain Management 10.0.29 (October 2022)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management version 10.0.29. This version has a build number of 10.0.1326 and is available on the following schedule:

- **Preview of release:** August 2022
- **General availability of release (self-update):** September 2022
- **General availability of release (auto-update):** September 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Inventory and logistics | [Allocate and reserve WMS items in Inventory Visibility](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-supply-chain-management/allocate-reserve-whs-items-inventory-visibility) | [Inventory Visibility support for WMS items](../inventory/inventory-visibility-whs-support.md) | Enabled by default |
| Inventory and logistics | [Preload streamlined on-hand inventory lists](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-supply-chain-management/query-inventory-visibility-summary-entity) | [Use the Inventory Visibility app](../inventory/inventory-visibility-power-platform.md) | Enabled by service configuration |
| Make-to-order supply automation | [Make-to-order supply automation](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-supply-chain-management/make-to-order-supply-automation) | [Make-to-order supply automation](../master-planning/make-to-order-supply-automation.md) | Feature management:<br>*Make-to-order supply automation* |
| Planning | [View and apply detailed insights for DDMRP](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-supply-chain-management/view-apply-detailed-insights-ddmrp) | [Demand Driven Material Requirements Planning overview](../master-planning/planning-optimization/ddmrp-overview.md) | Feature management:<br>*DDMRP for Planning Optimization* |
| Production control | [Make finished goods physically available before posting to journals](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-supply-chain-management/make-finished-goods-physically-before-posting) | [Make finished goods physically available before posting to journals](../production-control/deferred-posting.md) | Feature management:<br>*(Preview) Make finished goods physically available before posting to journals* |
| Warehouse management | [Look up relevant data within the warehouse mobile app](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-supply-chain-management/look-up-relevant-data-within-warehouse-mobile-app) | [Query data using Warehouse Management mobile app detours](../warehousing/warehouse-app-data-inquiry.md) | Feature management:<br>*Warehouse management app data inquiry flow* |

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

If you want to turn any of these features on or off, you must do so in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Module | Feature name in feature management | More information |
|---|---|---|
| Cost management | Optimization of co-product pending price calculation | This feature fixes a conflict that can sometimes occur when co-product prices are calculated by using multiple threads. It causes the system to make sure that each co-product price is calculated just once. The result of that calculation is then used as the input for all other calculations. If a pending price already exists, that price is used. |
| Master planning | Group transactions in Planning Optimization | This feature can help reduce the number of planned orders that are generated to supply a single sales order line when you're using Planning Optimization. When this feature is turned on, Planning Optimization will group all inventory transactions for an order line into a single requirement for the full quantity. (This behavior matches the built-in planning engine behavior.) Supply and demand are grouped separately. Therefore, the feature helps reduce the transaction volume when you have split transactions and when you use dimensions (such as batch numbers or serial numbers) that aren't coverage dimensions. |
| Procurement and sourcing | Put vendor on hold for purchase orders | This feature lets you put a vendor on hold for purchase orders. It adds a new *Purchase order* hold type that marks a vendor as on hold for purchase orders. You won't be able to create new purchase orders for vendors that are on hold for purchase orders, but you will still be able to proceed with any open invoices or payments for those vendors. |
| Sales and marketing | Calculate line net amount on import | This feature lets you control whether the system should recalculate line totals when you import data through the *Sales order lines*, *Sales quotation lines*, or *Return order lines* entity using OData or dual-write. It only has an effect when you also have trade agreement evaluation policies in place that restrict changes to the **Net amount** field for sales order lines, sales quotation lines, and/or return order lines. It adds a setting called **Calculate line net amount** to the **Accounts receivable > Setup > Accounts receivable parameters** page. When this setting is set to *Yes*, the system will always recalculate line amounts when needed (thereby ignoring any trade agreement evaluation policy for the line net amount). When the setting is set to *No*, the system will never automatically calculate the line net amount, even when incoming changes to the line price, quantity, and/or discount would imply that the line net amount should be recalculated. This feature is enabled by default and initially sets **Calculate line net amount** to *Yes*. The *No* setting matches the system behavior prior to version 10.0.23 and is provided chiefly to support legacy integration scenarios.<br><br>For more information, see [Recalculate line net amounts when importing sales orders, quotations, and returns](../sales-marketing/calc-line-net-amounts-import.md). |
| Sales and marketing | Calculate sales totals using multiple threads | This feature helps improve performance by enabling the system to use parallel processing when it calculates sales totals in a batch. The feature adds a new **Number of threads** field to the **Calculate sales totals** dialog box. If you choose to run the calculation in a batch, you can use this field to set the maximum number of threads. If you set the value to *0* (zero) or *1*, a single thread will be used. Values above 1 enable multithreading. |
| Sales and marketing | Update prices and discounts entered manually for intercompany | This feature adds support for manual change policies for intercompany orders. It includes support for transferring manual change policies between intercompany sales and purchase orders. Previously, manual change policies were supported only for non-intercompany orders. When this feature is enabled, the system will give you the option to update prices and discounts after you save changes to an intercompany order. This option lets you choose whether you want to apply the new prices and discounts details to the intercompany order or leave the order unchanged. |

## New and updated documentation resources

We have recently added or significantly updated the following Help articles. These articles aren't necessarily related to the new features that were added for this release, as listed in the previous sections. However, they might help you get more out of existing features.

| Feature area | New or updated articles |
|---|---|
| Master planning, CTP | [Calculate sales order delivery dates using CTP](../master-planning/planning-optimization/calculate-delivery-dates-using-ctp.md) |
| Master planning, DDMRP | [Demand Driven Material Requirements Planning overview](../master-planning/planning-optimization/ddmrp-overview.md)<br>[Turn on the DDMRP feature for your system](../master-planning/planning-optimization/ddmrp-enable.md)<br>[Inventory positioning](../master-planning/planning-optimization/ddmrp-inventory-positioning.md)<br>[Buffer profile and levels](../master-planning/planning-optimization/ddmrp-buffer-profile-and-levels.md)<br>[Demand-driven planning](../master-planning/planning-optimization/ddmrp-planning.md)<br>[Visual and collaborative execution](../master-planning/planning-optimization/ddmrp-visual-and-collaborative-execution.md) |
| Warehouse management | [Pack containers for shipment](../warehousing/packing-containers.md)<br>[Packing work for packing outbound containers and processing shipments](../warehousing/packing-work.md) |

## Feature state changes in this release

The following table lists features that became mandatory or on by default in version 10.0.29. All these features will automatically be turned on for your system as soon as you update to version 10.0.29. Mandatory features can't be turned off, but features that are on by default can still be turned off by using [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

The table also lists features that were previously in public preview but have changed to become generally available in version 10.0.29. This change indicates that the features are now recommended for use in production environments. These features are turned off by default unless otherwise noted. Therefore, you must use [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) to enable them if you want to use them.

| Module | Feature name | New feature state |
| --- | --- | --- |
| Asset management | [Asset management functionality for the production floor execution interface](../production-control/production-floor-execution-configure.md) | Mandatory |
| Cost management | [Change the label of Cancellation in Closing and adjustment to Reverse](/dynamics365-release-plan/2020wave1/dynamics365-supply-chain-management/change-terminology-inventory-closing-cancellation-inventory-closing-reverse) | Mandatory |
| Cost management | Clean up BOM calculation details cross costing versions | Mandatory |
| Cost management | [Compare item prices storage](../cost-management/compare-item-price.md) | Mandatory |
| Cost management | [Cost calculation level](../cost-management/cost-calculation-level.md) | On by default |
| Cost management | Enable user-defined batch number setup for inventory closing reverse | On by default |
| Cost management | [Inventory closing progress details](whats-new-scm-10-0-21.md) | On by default |
| Cost management | [Inventory value report storage](../cost-management/inventory-value-report-storage.md) | Mandatory |
| Cost management | Inventory value report data clean up | Mandatory |
| Cost management | Moving average, fallback cost sequence | Mandatory |
| Cost management | Show inventory closing log in grid | Mandatory |
| Cost management | Show the items with not fully settled transactions in summary format | Mandatory |
| Inventory and warehouse management | Allow empty batch attributes values | Mandatory |
| Inventory and warehouse management | Auto increment line numbers of inventory transfer order lines | Mandatory |
| Inventory and warehouse management | Create transfer order from sales line | Mandatory |
| Inventory and warehouse management | Disable inventory journal line field in workflow | Mandatory |
| Inventory and warehouse management | Enable inventory quality management parameters warning feature | Mandatory |
| Inventory and warehouse management | (China) Exclude physical receipt and issue costs from monthly average cost | On by default |
| Inventory and warehouse management | [Inventory journal approve workflow](../inventory/inventory-journal-workflow.md) | Mandatory |
| Inventory and warehouse management | [Inventory on-hand report storage](/dynamics365-release-plan/2020wave1/dynamics365-supply-chain-management/inventory-on-hand-report-storage) | Mandatory |
| Inventory and warehouse management | [Saved views for inventory management](saved-views-scm.md) | Mandatory |
| Inventory and warehouse management | Transfer order cancellation | Mandatory |
| Inventory and warehouse management | Using unit of measure and unit quantity in inventory journals | Mandatory |
| Inventory and warehouse management | Unlock inventory journal | Mandatory |
| Manufacturing | [Auto-picking of warehouse enabled materials for auto-posted picking lists](whats-new-scm-10-0-23.md) | Generally available |
| Manufacturing | Enable display of inventory dimensions in the materials list for production route operations | Mandatory |
| Manufacturing | [Enable to enter batch and serial numbers while reporting as finished from the Job Card Device](../production-control/report-finished-job-device.md) | On by default |
| Manufacturing | Improved production catch weight quantity picking | On by default |
| Manufacturing | [Job search for the production floor execution interface](../production-control/production-floor-execution-configure.md) | Mandatory |
| Manufacturing | [Manufacturing execution system integration](../production-control/mes-integration.md) | On by default |
| Manufacturing | ["My day" view for the production floor execution interface](../production-control/production-floor-execution-configure.md) | On by default |
| Manufacturing | [On-demand material availability check for production orders](whats-new-scm-10-0-24.md) | On by default |
| Manufacturing | [Override default production reservation](../production-control/override-default-reservation-principle.md) | Mandatory |
| Manufacturing | [Register material consumption on the production floor execution interface (non-WMS)](../production-control/production-floor-execution-configure.md) | Generally available |
| Manufacturing | [Report on catch weight items from the production floor execution interface](../production-control/production-floor-execution-configure.md) | Generally available |
| Manufacturing | [Report on co- and by-products from the production floor execution interface](../production-control/production-floor-execution-configure.md) | On by default |
| Manufacturing | [Report on planning items in the production floor execution interface](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-supply-chain-management/enhanced-production-floor-execution-interface-process-manufacturing) | On by default |
| Manufacturing | [Saved views for production control](saved-views-scm.md) | Mandatory |
| Manufacturing | [Show full serial, batch, and license plate numbers in the production floor execution interface](../production-control/production-floor-execution-configure.md) | Mandatory |
| Manufacturing | [Validate expiration of raw materials against planned consumption date](whats-new-scm-10-0-23.md) | On by default |
| Master planning | [Auto-firming for Planning Optimization](../master-planning/planning-optimization/planned-order-firming.md) | Mandatory |
| Master planning | [Batchable firming and consolidation for planned bulk and pack batch orders](whats-new-scm-10-0-20.md) | On by default |
| Master planning | [Include items with on-hand when pre-processing filters are enabled](/dynamics365-release-plan/2020wave1/dynamics365-supply-chain-management/master-planning-include-items-on-hand-when-pre-processing-filters-are-enabled) | On by default |
| Master planning | [Infinite capacity scheduling for Planning Optimization](../master-planning/planning-optimization/infinite-capacity-planning.md) | On by default |
| Master planning | [Margins for Planning Optimization](../master-planning/planning-optimization/safety-margins.md) | Mandatory |
| Master planning | [Negative days for Planning Optimization](../master-planning/planning-optimization/delay-tolerance.md) | Mandatory |
| Master planning | [Parallel authorizing of adjusted demand forecast](whats-new-scm-10-0-20.md) | Mandatory |
| Master planning | [Planned order firming with filtering](../master-planning/planning-optimization/planned-order-firming.md) | Mandatory |
| Master planning | [Planned production orders for Planning Optimization](../master-planning/planning-optimization/production-planning.md) | Mandatory |
| Master planning | [Purchase trade agreements for Planning Optimization](../master-planning/planning-optimization/purchase-trade-agreement.md) | Mandatory |
| Master planning | [Saved views for planned orders](saved-views-scm.md) | Mandatory |
| Procurement and sourcing | Charges from and to amounts on purchase orders | Mandatory |
| Procurement and sourcing | Disable purchase requisition distribution Reset button | On by default |
| Procurement and sourcing | [Enable resetting procurement related workflows](whats-new-scm-10-0-20.md) | On by default |
| Procurement and sourcing | [Limit the number of purchase order lines per batch task](whats-new-scm-10-0-27.md) | On by default |
| Procurement and sourcing | [Merge financial dimensions from the vendor with active dimension link financial dimension on the purchase order](whats-new-scm-10-0-25.md) | Mandatory |
| Procurement and sourcing | [Post registered quantities of stocked products and remainders of not-stocked products for receipts and vendor invoices](whats-new-scm-10-0-26.md) | Generally available |
| Procurement and sourcing | [Prevent overconsumption of general budget reservations when multiple purchase requisitions are in workflow](whats-new-scm-10-0-21.md) | On by default |
| Procurement and sourcing | [Purchase agreement responsible party](../procurement/purchase-agreements.md) | Mandatory |
| Procurement and sourcing | [Saved views for purchase orders](saved-views-scm.md) | Mandatory |
| Product information management | Bill of materials report pre-processing to avoid timeout | Mandatory |
| Product information management | Default financial dimensions separately when using item templates | Mandatory |
| Product information management | Enable product dimension groups for item templates | Mandatory |
| Product information management | Item - barcode entity improvements | Mandatory |
| Product information management | Regenerate product variant names based on nomenclature | Mandatory |
| Product information management | [Saved views for released products](saved-views-scm.md) | Mandatory |
| Product information management | [Variant suggestions page improvements](../pim/tasks/create-predefined-product-variants.md) | Mandatory |
| Sales and marketing | [Charges allocation on a sales order](/dynamics365-release-plan/2020wave1/dynamics365-supply-chain-management/miscellaneous-charges-enhancements) | Mandatory |
| Sales and marketing | Clean up sales-order update history | Mandatory |
| Sales and marketing | [Clean up sales update history based on age](../sales-marketing/sales-update-history-cleanup-performance-improvements.md) | Mandatory |
| Sales and marketing | [Contact person data entity export optimization](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/contact-person-data-entity-export-optimization) | Mandatory |
| Sales and marketing | Copy total discount group for sales credit note | Mandatory |
| Sales and marketing | [Enable lookup for sales quotation document introduction and document conclusion fields](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/lookup-functionality-document-introduction-document-conclusion-fields-sales-quotation-page) | Mandatory |
| Sales and marketing | [Improve "Top 100" customers report performance](whats-new-scm-10-0-23.md) | Mandatory |
| Sales and marketing | Include waiting records in history cleanup tasks | Mandatory |
| Sales and marketing | Limit the number of sales order lines per batch task | On by default |
| Sales and marketing | [Limit the number of sales orders that can be selected for posting](whats-new-scm-10-0-21.md) | Mandatory |
| Sales and marketing | Recalculate estimated customer balance | Mandatory |
| Sales and marketing | [Sales return order line registration with decimal precision with and without catch weight](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/sales-return-order-line-registration-decimal-precision-without-catch-weight) | Mandatory |
| Sales and marketing | [Saved views for sales and marketing](saved-views-scm.md) | Mandatory |
| Sales and marketing | [Single click sales order confirmation](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/single-click-sales-order-confirmation) | Mandatory |
| Transportation management | Allow unmatching of freight bills from freight invoice lines without a posted vendor invoice journal | On by default |
| Transportation management | [Enable creation of a vendor invoice journal when discarding a freight bill](whats-new-scm-10-0-20.md) | On by default |
| Transportation management | [Small Parcel Shipping](../warehousing/small-parcel-shipping.md) | Mandatory |
| Transportation management | [USMCA certification of origin document](../transportation/usmca-certification-of-origin.md) | On by default |
| Warehouse management | [Additional location zone](../warehousing/additional-location-zones.md) | Mandatory |
| Warehouse management | [Cancel work](../warehousing/cancel-warehouse-work.md) | Mandatory |
| Warehouse management | [Consolidate shipment](../warehousing/configure-shipment-consolidation-policies.md) | Mandatory |
| Warehouse management | [Create and process transfer orders from the warehouse app](../warehousing/create-transfer-order-from-warehouse-app.md) | Mandatory |
| Warehouse management | Cross docking templates with location directives | On by default |
| Warehouse management | [Decouple putaway work from ASNs](whats-new-scm-10-0-21.md) | Mandatory |
| Warehouse management | [Deferred put operations](../warehousing/deferred-processing-manual-inventory-movement.md) | Mandatory |
| Warehouse management | Deferred put - container | On by default |
| Warehouse management | Deferred put processing – enable for audit template feature with trigger event set to Prior | Mandatory |
| Warehouse management | [Disable expected receipts from quality orders that sample blocked inventory](../inventory/inventory-blocking.md) | On by default |
| Warehouse management | Enable fast validation for warehouse mobile devices | Mandatory |
| Warehouse management | [Enhanced parser for GS1 barcodes](../warehousing/gs1-barcodes.md) | Generally available |
| Warehouse management | [Flexible order-committed license plate reservation](../warehousing/flexible-warehouse-level-dimension-reservation.md) | Mandatory |
| Warehouse management | [Flexible warehouse-level dimension reservation](../warehousing/flexible-warehouse-level-dimension-reservation.md) | Mandatory |
| Warehouse management | [Item consolidation location utilization](../warehousing/item-consolidation-location-utilization.md) | On by default |
| Warehouse management | License plate receiving history | On by default |
| Warehouse management | [Manual shipment consolidation](../warehousing/consolidate-shipments-manual-workbench.md) | On by default |
| Warehouse management | [Manual transfer line picking service for admin or similar trusted users](whats-new-scm-10-0-28.md) | Generally available |
| Warehouse management | [Material handling equipment interface](../warehousing/mhax.md) | Mandatory |
| Warehouse management | [New load planning workbench pages](whats-new-scm-10-0-24.md) | Generally available |
| Warehouse management | [Outbound workload visualization](../warehousing/outbound-workload-visualization.md) | Mandatory |
| Warehouse management | [Planned cross docking](../warehousing/planned-cross-docking.md) | Mandatory |
| Warehouse management | [Process warehouse app events](../warehousing/warehouse-app-events.md) | Mandatory |
| Warehouse management | Query enhancement for the co-product and by-product put away work template | Mandatory |
| Warehouse management | [Round quantities down to nearest sales unit on release to warehouse](whats-new-scm-10-0-19.md) | Mandatory |
| Warehouse management | [Saved view for the load planning workbench](saved-views-scm.md) | Mandatory |
| Warehouse management | [Saved view for the work details page](saved-views-scm.md) | Mandatory |
| Warehouse management | [Saved view for wave processing](saved-views-scm.md) | Mandatory |
| Warehouse management | [Saved views for load processing](saved-views-scm.md) | Mandatory |
| Warehouse management | [Saved views for shipment processing](saved-views-scm.md) | Mandatory |
| Warehouse management | [Scan GS1 barcodes](../warehousing/gs1-barcodes.md) | Generally available |
| Warehouse management | Shipment wave label details | Mandatory |
| Warehouse management | [Slot mixed units](whats-new-scm-10-0-21.md) | Mandatory |
| Warehouse management | [Use faster API for containers closing/reopening on packing station](whats-new-scm-10-0-21.md) | On by default |
| Warehouse management | [Validate templates selected for replenishment jobs](whats-new-scm-10-0-20.md) | On by default |
| Warehouse management | [Warehouse app promoted fields](../warehousing/warehouse-app-promoted-fields.md) | Mandatory |
| Warehouse management | [Warehouse app step instructions](../warehousing/mobile-app-titles-instructions.md) | Mandatory |
| Warehouse management | [Warehouse location status](../warehousing/warehouse-location-status.md) | Mandatory |
| Warehouse management | [Warehouse management app detours](../warehousing/warehouse-app-detours.md) | On by default |
| Warehouse management | [Wave batch job details](../warehousing/wave-processing.md) | Mandatory |
| Warehouse management | [Wave execution notifications](../warehousing/wave-execution-notifications.md) | Mandatory |

## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.29 includes platform updates. To learn more, see [Platform updates for version 10.0.29 of Finance and Operations apps (October 2022)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-29.md).

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.29, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=726559).

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
