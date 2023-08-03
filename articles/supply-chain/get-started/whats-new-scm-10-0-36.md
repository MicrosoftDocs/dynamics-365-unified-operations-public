---
title: Preview of Dynamics 365 Supply Chain Management 10.0.36 (September 2023)
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

# Preview of Dynamics 365 Supply Chain Management 10.0.36 (September 2023)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management preview version 10.0.36. This version has a build number of 10.0.1695 and is available on the following schedule:

- **Preview of release:** July 2023
- **General availability of release (self-update):** September 2023
- **General availability of release (auto-update):** October 2023

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Inventory and logistics | [Archive inventory transactions](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-supply-chain-management/archive-inventory-transactions) | [Move inventory transactions history to long-term data retention](../../fin-ops-core/dev-itpro/sysadmin/archive-inventory-purge.md) | Feature management:<ul><li>*(Preview) Archive*</li><li>*(Preview) Archive data to Dataverse managed data lake and purge*</li><li>*(Preview) Purge archived inventory transactions*</li></ul> |
| Inventory and logistics | [Empower users with near real-time inventory insights](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-supply-chain-management/empower-users-near-real-time-inventory-insights) | *Coming soon* | Enabled by default |
| Inventory and logistics | [Integrate Inventory Visibility with Dynamics 365 Commerce](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/integrate-inventory-visibility-dynamics-365-commerce) | *Coming soon* | Enabled by default |
| Inventory and logistics | [Sell and price multiple items as a bundle](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/sell-price-multiple-items-as-bundle) | [Product bundles overview](../sales-marketing/product-bundles-overview.md) | Feature management:<br>*Product bundles*  |
| Manufacturing and asset management | [Detect spikes and deviations in sensor data](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/detect-spikes-deviations-sensor-data) | [Anomaly detection scenario](../sensor-data-intelligence/sdi-scenario-anomaly.md) | Enabled by default |
| Product information management | [Manage compliance with export control restrictions](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/manage-compliance-export-control-restrictions) | *Coming soon* | Feature management:<br>*(Preview) Advanced export control configuration*  |
| Warehouse management | Dynamic printer selection | [Dynamic printer selection](../warehousing/dynamic-printing-selection.md) | Enabled by default |
| Warehouse management | Operate warehouses connected to external order management systems | *Coming soon* | Feature management:<br>*(Preview) Warehouse management only mode* |

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they're only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

If you want to turn any of these features on or off, you must do so in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Module | Feature name in feature management | More information |
|---|---|---|
| Master planning | Allows to create Planned order setting Purchase quantity instead of Requirement quantity | Lets you create a planned order by setting the purchase quantity instead of the requirement quantity. |
| Master planning | Average daily usage for distribution scenarios | Ensures that average daily usage (ADU) is based on actual sales order dates and quantities. This can be especially useful in distribution scenarios or when transitioning from material requirements planning (MRP) to Demand Driven Material Requirements Planning (DDMRP). It calculates the ADU based on sales order dates and quantities and manufacturing consumption across the distribution network, disregarding transfer orders. |
| Master planning | (Preview) Exclude specific sales orders or sales order lines in Planning Optimization | Adds a parameter that lets you choose not to create supply for a sales order or a specific line when using Planning Optimization. This lets you keep an order unplanned, which can be useful for orders that require a review or approval process. |
| Master planning | Forecast demand plan import service | Adds support for using multiple threads when importing forecast demand plan lines. |
| Master planning | (Preview) Ignore specific transaction types using Planning Optimization | Lets you select which transaction types should be considered on the master plan when running Planning Optimization |
| Master planning | (Preview) Strict safety stock pegging for Planning Optimization | Gives you the option of directly pegging safety stock as demand against the planned order created for it. On the **Coverage groups** page, this feature adds a new parameter called **Strict safety stock pegging**, which lets you choose one of the following options for each coverage group:<ul><li>*No*: Safety stock is considered the least important of type of demand, so whenever a planned order is created for safety stock, all other demand will be prioritized, which lets you provide a higher service level for your customers. This is how the system always behaved in previous versions. </li><li>*Yes*: The system will apply strict safety stock pegging. When a planned order is created for fulfilling safety stock, it will always be pegged against safety stock, without allowing any other demand to be pegged against it (except when using a **Coverage code** of *Period*). This can provide better visibility in some scenarios, such as when you're using a high number of negative days.</li></ul> |
| Procurement and sourcing | Show only delivery addresses for workers when creating category-based purchase requisition lines | Improves privacy of workers by adding an option that will prevent users from seeing workers' home addresses when creating category- based requisition lines and purchase requisition lines. Instead, only addresses marked with a **Purpose** of *Delivery* will be shown. Addresses marked for both home and delivery purposes will be available, but users won't be able to see that the address is also a home address. The option is available on the **Procurement and sourcing** page, on the **Purchase requisition** tab. |
| Procurement and sourcing | (Preview) Supplier requested and confirmed shipment dates | Enables you to do the following:<ul><li>Determine the supplier's shipping calendar on the vendor and its subsequent default to the relevant document</li><li>Determine the delivery transport days from the supplier to the receiving point</li><li>Enhance the purchasing process through the incorporation of new requested and confirmed ship dates</li><li>Consider the supplier's shipping calendar and transport days for the automatic calculation of supplier ship dates.</li></ul> |
| Sales and marketing | (Preview) Archive sales order from history tables to Dataverse managed data lake and purge | Performs the last step in the archival process, which is archiving from history tables to Dataverse managed data lake. For more information, see [Archive sales orders](../../fin-ops-core/dev-itpro/sysadmin/archive-sales-orders.md). |
| Sales and marketing | Auto-create direct delivery intercompany orders originating from purchase order creation | Automates the creation of both an intercompany direct delivery sales order and an intercompany direct delivery purchase order when a purchase order in another legal entity is created. When this feature is disabled, the creation of the intercompany direct delivery purchase order is deferred until the intercompany direct delivery sales is opened in the sales order details page. When this feature is enabled, the intercompany direct delivery purchase order is created without having to open the intercompany direct delivery sales order from the sales order details form. This feature applies when both **Create Intercompany orders** and **Direct delivery** are set to *Yes* on an intercompany sales order. |
| Sales and marketing | Copy customer reference and requisition to purchase order line when created from sales order line | When a purchase order line is created from a sales order line, this feature copies the customer reference and requisition values from the sales order line to the purchase order line. If one or both values aren't specified for the sales order line, then the feature copies values from the sales order header instead. |
| Sales and marketing | Stop creation of source document header and line records related to sales packing slip posting | Stops unused source document header and source document line records from being created when posting sales order packing slips. |
| Transportation management | (Preview) Match vendor invoice journal with voyage cost in different currency. | Lets you specify any currency code on a vendor invoice journal and match it with the voyage cost in another currency. |
| Warehouse management | Consistent handling of license plate information for warehouse actions | Causes the system to be more consistent in the way it uses the columns of the `WHSWorkTrans` table, which stores information about user actions related to warehouse work. This change makes the system easier for developers to understand and may be required by future features related to inventory transactions. If your system includes customizations that affect or are affected by the `WHSWorkTrans` table, then you should enable this feature on a development system, test and modify your customizations as needed, and then deploy the updates to your production system. Then you can enable this feature on your production system to prepare it to take advantage of future updates. As a result of this feature, the system will store source and destination license plate information more consistently in the various columns of the table (no columns are removed or added). The first time you turn on this feature, it will process the `WHSWorkTrans` table by moving target license plate information for incomplete work to the `TargetLicensePlateId` column. It will also deduce the source license plate information for the pick work lines and update the `InventDimId` column accordingly. Records for already completed work won't be affected. Thereafter, the system will continue to work using the new convention. |

## New and updated documentation resources

We have recently added or significantly updated the following help articles. These articles aren't necessarily related to the new features that were added for this release, as listed in the previous sections. However, they might help you get more out of existing features.

| Feature area | New or updated articles |
|---|---|
| Procurement and sourcing | [Review and accept changes to confirmed purchase orders](../procurement/purchase-order-changes-after-confirmation.md) |
| Responsible AI | [Transparency notes for Dynamics 365 Supply Chain Management](../transparency-note.md) |
| Warehouse management | [Install and connect the Warehouse Management mobile app](../warehousing/install-configure-warehouse-management-app.md) now describes how to authenticate using device code flow |
| Warehouse management | [Optimize location directive queries](../warehousing/location-directives-optimize.md) |
| Warehouse management | [Warehouse Mobile app accessibility features](../warehousing/warehouse-app-accessibility.md) |

## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.36 includes platform updates. To learn more, see [Platform updates for version 10.0.36 of Finance and Operations apps (September 2023)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-36.md) <!--KFM: Confirm link -->.

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.36, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=831854&dbType=3&qc=bffd63612a8f998d04f4f14d6d456f17d1f6038819d1225f612e2fd0f5c59e17).

### Dynamics 365 and industry clouds: 2023 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2023 release wave 1 plan](/dynamics365/release-plan/2023wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
