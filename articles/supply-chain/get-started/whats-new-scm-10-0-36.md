---
title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.36 (October 2023)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.36. 
author: kamaybac
ms.author: kamaybac
ms.reviewer: kamaybac
ms.search.form:
ms.topic: conceptual
ms.date: 07/31/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# What's new or changed in Dynamics 365 Supply Chain Management 10.0.36 (October 2023)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management version 10.0.36. This version has a build number of 10.0.1695 and is available on the following schedule:

- **Preview of release:** July 2023
- **General availability of release (self-update):** September 2023
- **General availability of release (auto-update):** September 2023

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Inventory and logistics | [Empower users with near real-time inventory insights](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-supply-chain-management/empower-users-near-real-time-inventory-insights) | [Inventory Visibility Power BI dashboard](../inventory/inventory-visibility-dashboard.md) | Enabled by default |
| Inventory and logistics | [Sell and price multiple items as a bundle](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/sell-price-multiple-items-as-bundle) | [Product bundles overview](../sales-marketing/product-bundles-overview.md) | Feature management:<br>*Product bundles*  |
| Product information management | [Manage compliance with export control restrictions](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/manage-compliance-export-control-restrictions) | [Advanced export control overview](../pim/export-control-overview.md) | Feature management:<br>*Advanced export control configuration*  |
| Warehouse management | Dynamic printer selection | [Dynamic printer selection](../warehousing/dynamic-printing-selection.md) | Enabled by default |
| Warehouse management | Operate warehouses connected to external order management systems | [Warehouse management only mode overview](../warehousing/wms-only-mode-overview.md) | Feature management:<br>*(Preview) Warehouse management only mode* |

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they're only enhancements, they aren't listed in the [release plan](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

If you want to turn any of these features on or off, you must do so in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Module | Feature name in feature management | More information |
|---|---|---|
| Master planning | Allows to create Planned order setting Purchase quantity instead of Requirement quantity | Lets you create a planned order by setting the purchase quantity instead of the requirement quantity. |
| Master planning | Average daily usage for distribution scenarios | Ensures that average daily usage (ADU) is based on actual sales order dates and quantities. This can be especially useful in distribution scenarios or when transitioning from material requirements planning (MRP) to Demand Driven Material Requirements Planning (DDMRP). It calculates the ADU based on sales order dates and quantities and manufacturing consumption across the distribution network, disregarding transfer orders. |
| Master planning | Exclude specific sales orders or sales order lines in Planning Optimization | Adds a parameter that lets you choose not to create supply for a sales order or a specific line when using Planning Optimization. This lets you keep an order unplanned, which can be useful for orders that require a review or approval process. |
| Master planning | Forecast demand plan import service | Adds support for using multiple threads when importing forecast demand plan lines. |
| Master planning | Ignore specific transaction types using Planning Optimization | Lets you select which transaction types should be considered on the master plan when running Planning Optimization |
| Master planning | Strict safety stock pegging for Planning Optimization | Gives you the option of directly pegging safety stock as demand against the planned order created for it. On the **Coverage groups** page, this feature adds a new parameter called **Strict safety stock pegging**, which lets you choose one of the following options for each coverage group:<ul><li>*No*: Safety stock is considered the least important type of demand, so whenever a planned order is created for safety stock, all other demand will be prioritized, which lets you provide a higher service level for your customers. This is how the system always behaved in previous versions. </li><li>*Yes*: The system will apply strict safety stock pegging. When a planned order is created for fulfilling safety stock, it will always be pegged against safety stock, without allowing any other demand to be pegged against it (except when using a **Coverage code** of *Period*). This can provide better visibility in some scenarios, such as when you're using a high number of negative days.</li></ul>See also [Safety stock pegging options](../master-planning/safety-stock-pegging.md). |
| Procurement and sourcing | Show only delivery addresses for workers when creating category-based purchase requisition lines | Improves privacy of workers by adding an option that will prevent users from seeing workers' home addresses when creating category- based requisition lines and purchase requisition lines. Instead, only addresses marked with a **Purpose** of *Delivery* will be shown. Addresses marked for both home and delivery purposes will be available, but users won't be able to see that the address is also a home address. The option is available on the **Procurement and sourcing** page, on the **Purchase requisition** tab. |
| Sales and marketing | Auto-create direct delivery intercompany orders originating from purchase order creation | Automates the creation of both an intercompany direct delivery sales order and an intercompany direct delivery purchase order when a purchase order in another legal entity is created. When this feature is disabled, the creation of the intercompany direct delivery purchase order is deferred until the intercompany direct delivery sales is opened in the sales order details page. When this feature is enabled, the intercompany direct delivery purchase order is created without having to open the intercompany direct delivery sales order from the sales order details form. This feature applies when both **Create Intercompany orders** and **Direct delivery** are set to *Yes* on an intercompany sales order. |
| Sales and marketing | Copy customer reference and requisition to purchase order line when created from sales order line | When a purchase order line is created from a sales order line, this feature copies the customer reference and requisition values from the sales order line to the purchase order line. If one or both values aren't specified for the sales order line, then the feature copies values from the sales order header instead. |
| Sales and marketing | Stop creation of source document header and line records related to sales packing slip posting | Stops unused source document header and source document line records from being created when posting sales order packing slips. This feature is turned on by default. |
| Transportation management | Match vendor invoice journal with voyage cost in different currency. | Lets you specify any currency code on a vendor invoice journal and match it with the voyage cost in another currency. |
| Warehouse management | Consistent handling of license plate information for warehouse actions | Causes the system to be more consistent in the way it uses the columns of the `WHSWorkTrans` table, which stores information about user actions related to warehouse work. This change makes the system easier for developers to understand and may be required by future features related to inventory transactions. If your system includes customizations that affect or are affected by the `WHSWorkTrans` table, then you should enable this feature on a development system, test and modify your customizations as needed, and then deploy the updates to your production system. Then you can enable this feature on your production system to prepare it to take advantage of future updates. As a result of this feature, the system will store source and destination license plate information more consistently in the various columns of the table (no columns are removed or added). The first time you turn on this feature, it will process the `WHSWorkTrans` table by moving target license plate information for incomplete work to the `TargetLicensePlateId` column. It will also deduce the source license plate information for the pick work lines and update the `InventDimId` column accordingly. Records for already completed work won't be affected. Thereafter, the system will continue to work using the new convention. |

> [!NOTE]
> Supply Chain Management version 10.0.36 introduces a label change for purchase orders and related functionality. All labels that use the term *Delivery date* have been changed to use the term *Receipt date*. The functionality remains unchanged. The terminology has been changed to allow for an upcoming feature that distinguishes between the date a delivery is sent (*Ship date*) and the date it is received (*Receipt date*). This label change applies automatically starting in version 10.0.36 and is not managed through feature management.

## Feature state changes in this release

The following table lists features that became mandatory or on by default in version 10.0.36. All these features will automatically be turned on for your system as soon as you update to version 10.0.36. Mandatory features can't be turned off, but features that are on by default can still be turned off by using [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). Features that are now listed as enabled by default are targeted to become mandatory with 2024 release wave 1.

The table also lists features that were previously in public preview but have changed to become generally available in version 10.0.36. This change indicates that the features are now recommended for use in production environments. These features are turned off by default unless otherwise noted. Therefore, you must use [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) to enable them if you want to use them. Features that are now listed as generally available are targeted to become enabled by default with 2024 release wave 1 and then to become mandatory with 2024 release wave 2.

| Module | Feature name | New feature state |
| --- | --- | --- |
| Cost management | [Cost calculation level](../cost-management/cost-calculation-level.md) | Mandatory |
| Cost management | [Enable user-defined batch number setup for inventory closing reverse](../../finance/get-started/whats-new-changed-10-0-20.md) | Mandatory |
| Cost management | [Inventory aging report storage](../cost-management/inventory-aging-report-storage.md) | Mandatory |
| Engineering Change Management | [Engineering Change Management](../engineering-change-management/product-engineering-overview.md) | Mandatory |
| Engineering Change Management | [Manage changes to formulas and their ingredients](../engineering-change-management/product-engineering-overview.md) | Mandatory |
| Inventory management | [Inventory on-hand report data clean up](whats-new-scm-10-0-28.md) | Mandatory |
| Inventory management | [(India) For transfer price rules, ignore location when "From warehouse code" is set to "All"](whats-new-scm-10-0-28.md) | Mandatory |
| Inventory management | Cascade transfer order header date change to lines | On by default |
| Inventory management | [Enable intercompany on-hand to only show nonzero on-hand quantity](whats-new-scm-10-0-28.md) | On by default |
| Master planning | [Azure Machine Learning Service for demand forecasting](../master-planning/demand-forecasting-setup.md) | Mandatory |
| Master planning | [Group transactions in Planning Optimization](whats-new-scm-10-0-29.md) | Mandatory |
| Master planning | [Infinite capacity scheduling for Planning Optimization](../master-planning/planning-optimization/infinite-capacity-planning.md) | Mandatory |
| Master planning | [Make-to-order supply automation](../master-planning/make-to-order-supply-automation.md) | Mandatory |
| Master planning | [Priority driven MRP support for Planning Optimization](../master-planning/planning-optimization/priority-based-planning.md) | Mandatory |
| Master planning | [CTP for Planning Optimization](../master-planning/planning-optimization/calculate-delivery-dates-using-ctp.md) | On by default |
| Master planning | [DDMRP for Planning Optimization](../master-planning/planning-optimization/ddmrp-overview.md) | On by default |
| Master planning | [Process manufacturing support for Planning Optimization](whats-new-scm-10-0-33.md) | On by default |
| Master planning | [Restart and resume logic for the forecast generation batch process](whats-new-scm-10-0-31.md) | On by default |
| Master planning | [Source products and materials from multiple vendors using Planning Optimization](../master-planning/source-from-multiple-vendors.md) | On by default |
| Procurement and sourcing | Add Quantity ordered field to the Posting product receipt page | Mandatory |
| Procurement and sourcing | Charges setup with site and warehouse | Mandatory |
| Procurement and sourcing | Check unit precision for not-stocked items | Mandatory |
| Procurement and sourcing | [Consolidate multiple purchase requisitions into a single purchase order by accounting date](whats-new-scm-10-0-25.md) | Mandatory |
| Procurement and sourcing | [Enable resetting procurement related workflows](../supply-chain-dev/whats-new-scm-10-0-20.md) | Mandatory |
| Procurement and sourcing | [Limit the number of purchase order lines per batch task](whats-new-scm-10-0-27.md) | Mandatory |
| Procurement and sourcing | [Post registered quantities of stocked products and remainders of not-stocked products for receipts and vendor invoices](whats-new-scm-10-0-26.md) | Mandatory |
| Procurement and sourcing | [Prevent overconsumption of general budget reservations when multiple purchase requisitions are in workflow](../supply-chain-dev/whats-new-scm-10-0-21.md) | Mandatory |
| Procurement and sourcing | RFQ reference link added to PO | Mandatory |
| Procurement and sourcing | [Sealed bidding for RFQs](../procurement/sealed-bidding.md) | Mandatory |
| Procurement and sourcing | [Synchronize tracking dimensions on intercompany sales and purchase order lines](whats-new-scm-10-0-26.md) | Mandatory |
| Procurement and sourcing | [Assess supply risks to prevent supply chain disruptions](../procurement/supply-risk-assessment-overview.md) | On by default |
| Procurement and sourcing | [Check purchase order expenditure reviewers setup before enabling workflow](whats-new-scm-10-0-35.md) | On by default |
| Procurement and sourcing | [Display legacy default RFQ reply field settings](whats-new-scm-10-0-25.md) | On by default |
| Procurement and sourcing | Purchase agreement matching policy | On by default |
| Procurement and sourcing | Purchase order delivery date | On by default |
| Procurement and sourcing | Request for quotation amendment and cancellation email framework options | On by default |
| Procurement and sourcing | [Review changes to confirmed purchase orders based on downstream impact](../procurement/purchase-order-changes-after-confirmation.md) | On by default |
| Procurement and sourcing | [Purchase order workflow submission and approval performance enhancement](whats-new-scm-10-0-32.md) | Generally available |
| Product information management | [Clean up product attribute values](whats-new-scm-10-0-26.md) | Mandatory |
| Product information management | [Populate product attribute values](whats-new-scm-10-0-27.md) | Mandatory |
| Product information management | [Product dimension version](../pim/product-dimensions.md#version-dim) | Mandatory |
| Production control | [Auto-picking of warehouse enabled materials for auto-posted picking lists](whats-new-scm-10-0-23.md) | Mandatory |
| Production control | [Copy generic routes](../supply-chain-dev/whats-new-scm-10-0-20.md) | Mandatory |
| Production control | [My jobs tab on the production floor execution interface](../production-control/production-floor-execution-use.md) | Mandatory |
| Production control | [Production teams in the production floor execution interface](../production-control/production-floor-execution-use.md) | Mandatory |
| Production control | [Update related resource requirements when a route operation is changed](../supply-chain-dev/whats-new-scm-10-0-20.md) | Mandatory |
| Production control | [Additional configuration on the production floor execution interface](../production-control/production-floor-execution-configure.md) | On by default |
| Production control | [Enable use of a numpad in the sign-in page](../production-control/production-floor-execution-configure.md) | On by default |
| Production control | [Improved user experience for the Report progress dialog in the Job Card Device](../production-control/report-finished-job-device.md) | On by default |
| Production control | [On-hand information in production orders to release page](whats-new-scm-10-0-30.md) | On by default |
| Production control | [Report on catch weight items from the production floor execution interface](../production-control/production-floor-execution-configure.md) | On by default |
| Production control | [Make finished goods physically available before posting to journals](../production-control/deferred-posting.md) | Generally available |
| Sales and marketing | [Calculate line net amount on import](../sales-marketing/calc-line-net-amounts-import.md) | Mandatory |
| Sales and marketing | [Calculate sales totals using multiple threads](whats-new-scm-10-0-29.md) | Mandatory |
| Sales and marketing | [Default broker contract tax information on vendor invoice lines](whats-new-scm-10-0-27.md) | Mandatory |
| Sales and marketing | [Prevent updates to intercompany sales order line requested dates in header to lines update scenario when derived](whats-new-scm-10-0-32.md) | Mandatory |
| Sales and marketing | [Update prices and discounts entered manually for intercompany](whats-new-scm-10-0-29.md) | Mandatory |
| Sales and marketing | [Adjusting reverse match for a settlement process](whats-new-scm-10-0-34.md) | On by default |
| Sales and marketing | [Keep existing sorting on intercompany sales lines when updating them](whats-new-scm-10-0-35.md) | On by default |
| Sales and marketing | [Settle customer payment deductions using the matching invoice](whats-new-scm-10-0-31.md) | On by default |
| Sales and marketing | [Sales history cleanup performance improvements](../sales-marketing/sales-update-history-cleanup-performance-improvements.md) | Generally available |
| Shared AP and AR | [Rebate management](../rebate-management/rebate-management-overview.md) | Mandatory |
| Shared AP and AR | Cancel posted rebate provision with a posting date | On by default |
| Shared AP and AR | Enable auto negative tier in Rebate management | On by default |
| Shared AP and AR | [Rebate management sold-to customers posting](whats-new-scm-10-0-34.md) | On by default |
| Transportation management | Allow unmatching of freight bills from freight invoice lines without a posted vendor invoice journal | Mandatory |
| Transportation management | Landed cost | On by default |
| Transportation management | [Assign shipments to related route segments](../transportation/assign-shipments-to-segments.md) | Generally available |
| Transportation management | [Enable shipping container creation and update in batch mode](../landed-cost/landed-cost-enable.md) | Generally available |
| Transportation management | [Enable split vendor invoice journal line per cost type code and voyage id from multiple voyages](../landed-cost/landed-cost-enable.md) | Generally available |
| Transportation management | [Generate data manually on voyage editor](../landed-cost/landed-cost-enable.md) | Generally available |
| Transportation management | [Performance improvements for post receipt function in Landed Cost](../landed-cost/landed-cost-enable.md) | Generally available |
| Warehouse management | [Catch weight product processing with warehouse management](../warehousing/catch-weight-processing.md) | Mandatory |
| Warehouse management | Change the error to a warning when releasing a load where sufficient quantity isn't available | Mandatory |
| Warehouse management | [Enhanced parser for GS1 barcodes](../warehousing/gs1-barcodes.md) | Mandatory |
| Warehouse management | Evaluate work header breaks before work header maximums during work creation | Mandatory |
| Warehouse management | Goods in Transit Receiving and Put away | Mandatory |
| Warehouse management | Hazardous materials enhancements | Mandatory |
| Warehouse management | Include Confirmed ship and Confirmed receipt dates into date filters on Load planning workbench | Mandatory |
| Warehouse management | [Inventory status changes for catch weight products](../warehousing/catch-weight-processing.md) | Mandatory |
| Warehouse management | [License plate receiving enhancements](../warehousing/warehousing-mobile-device-app-license-plate-receiving.md) | Mandatory |
| Warehouse management | License plate validation on source document lines | Mandatory |
| Warehouse management | Line reservation enhancements for the batch number reservation form feature | Mandatory |
| Warehouse management | [Location directive scopes](../warehousing/create-location-directive.md) | Mandatory |
| Warehouse management | [Multi-level detours for the Warehouse Management mobile app](../warehousing/warehouse-app-detours.md) | Mandatory |
| Warehouse management | [Multiple product receipt postings per load](../warehousing/inbound-load-handling.md) | Mandatory |
| Warehouse management | [Over receipt of load quantities](../warehousing/inbound-load-handling.md) | Mandatory |
| Warehouse management | [Packing work for packing stations](../warehousing/packing-work.md) | Mandatory |
| Warehouse management | Parent license plates cannot be target license plates | Mandatory |
| Warehouse management | [Pick line grouping](../warehousing/pick-line-grouping.md) | Mandatory |
| Warehouse management | [Post on-hand adjustments using configurable reason codes connected to offset accounts](../warehousing/reason-codes-for-counting-journals.md) | Mandatory |
| Warehouse management | Purchase order quantity left to load calculation using registered quantities | Mandatory |
| Warehouse management | Sales order packing slip corrections/cancellation transaction status change | Mandatory |
| Warehouse management | [Use existing catch weight tags when reporting production orders as finished](../warehousing/catch-weight-processing.md) | Mandatory |
| Warehouse management | [Warehouse-specific inventory transactions](../warehousing/warehouse-transactions.md) | Mandatory |
| Warehouse management | [Work policy enhancements for inbound work](../warehousing/warehouse-work-policies.md) | Mandatory |
| Warehouse management | [Auto-submit detour steps for the Warehouse Management mobile app](../warehousing/warehouse-app-detours.md) | On by default |
| Warehouse management | Options for validating ingredient batch expiration dates | On by default |
| Warehouse management | [Pack containers using the Warehouse Management mobile app](../warehousing/warehouse-app-packing-containers.md) | On by default |

## New and updated documentation resources

We have recently added or significantly updated the following help articles. These articles aren't necessarily related to the new features that were added for this release, as listed in the previous sections. However, they might help you get more out of existing features.

| Feature area | New or updated articles |
|---|---|
| Procurement and sourcing | [Review and accept changes to confirmed purchase orders](../procurement/purchase-order-changes-after-confirmation.md) |
| Responsible AI | [Responsible AI FAQs for Dynamics 365 Supply Chain Management](../responsible-ai-overview.md) |
| Warehouse management | [Install the Warehouse Management mobile app](../warehousing/install-configure-warehouse-management-app.md) now describes how to authenticate using device code flow |
| Warehouse management | [Optimize location directive queries](../warehousing/location-directives-optimize.md) |
| Warehouse management | [Warehouse Mobile app accessibility features](../warehousing/warehouse-app-accessibility.md) |

## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.36 includes platform updates. To learn more, see [Platform updates for version 10.0.36 of Finance and Operations apps (October 2023)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-36.md).

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.36, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=831854&dbType=3&qc=bffd63612a8f998d04f4f14d6d456f17d1f6038819d1225f612e2fd0f5c59e17).

### Dynamics 365, Viva Sales, and supply chain platform: 2023 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365, Viva Sales, and supply chain platform: 2023 release wave 2 plan](/dynamics365/release-plan/2023wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
