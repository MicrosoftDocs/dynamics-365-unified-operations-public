---
title: Preview of Dynamics 365 Supply Chain Management 10.0.25 (April 2022)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.25. 
author: kamaybac
ms.date: 02/01/2022
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this topic to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: kamaybac
ms.search.validFrom: 2021-02-01
ms.dyn365.ops.version: 10.0.25
---

# Preview of Dynamics 365 Supply Chain Management 10.0.25 (April 2022)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic lists features that are either new or changed in the Microsoft Dynamics 365 Supply Chain Management preview of version 10.0.25. This version has a build number of <!--KFM: Get build # --> and is available as follows:

- **Preview of release:** February 2021
- **General availability of release (self-update):** March 2022
- **General availability of release (auto-update):** April 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this topic to include features that made it into the build after this topic was initially published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Inventory&nbsp;and&nbsp;logistics | [Scan barcodes in the warehouse using GS1 format standards](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-supply-chain-management/scan-barcodes-warehouse-using-gs1-format-standards) <!-- Update to 2022w1 link when published --> | [GS1 bar codes and QR codes](../warehousing/gs1-barcodes.md) | Feature management:<br>*Scan GS1 barcodes* |
| Inventory&nbsp;and&nbsp;logistics | Hazardous materials enhancements | These enhancements build on existing hazardous materials functionality to better help companies stay in compliance with local regulations when transporting hazardous materials across different geographies. | Feature management:<br>*Hazardous materials enhancements* |
| Inventory&nbsp;and&nbsp;logistics | Packing work for packing stations | This feature greatly improves the flexibility and agility of your packing and shipping operations. During the packing process, warehouse workers can now pack and ship individual parcels that are related to same shipment and load. Order lines that are part of the same shipment don't necessarily need to be shipped together if some items are ready for shipment right away. A single order can be packed and shipped in multiple parcels at different shipping times, thereby reducing wait times and adding agility.| Feature management:<br>*Packing work for packing stations* |
| Manufacturing | [Material consumption and reservations in the production floor execution interface](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/material-consumption-reservations-production-floor-execution-interface) | [How workers use the production floor execution interface](../production-control/production-floor-execution-use.md) | Feature management:<br>*(Preview) Register material consumption on the production floor execution interface (WMS-enabled)* |
| Manufacturing | [Register material consumption on scale units](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/register-material-consumption-scale-units) | [Manufacturing execution workloads for cloud and edge scale units](../cloud-edge/cloud-edge-workload-manufacturing.md) | Feature management:<br>*Register material consumption on the mobile app on a scale unit* |
| Planning | [Planning Optimization suggestions to optimize existing supply](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/planning-optimization-suggestions-optimize-existing-supply) | [Action messages](../master-planning/action-messages.md) | Enabled by default |
| Planning | Planned orders simplified | [Planned orders simplified](../master-planning/planning-optimization/planned-orders-simplified.md ). | Feature management:<br>*Planned orders simplified*  |


## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

If you want to turn any of these features on or off, you must do that in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Module | Feature name in feature management | More information |
|---|---|---|
| Procurement and sourcing | Display legacy default RFQ reply field settings | This feature reintroduces the legacy default request for quotation (RFQ) reply field settings, which were previously removed from the user interface. These settings don't provide any functionality out of the box, but can be customized to provide it as required. Enable this feature if your organization has already added functionality for the default RFQ reply field settings or is planning to. When this feature is enabled, you can access the settings by going to the **Procurement and sourcing parameters** page, opening the **Request for quotation** tab, and selecting **Default request for quotation reply fields**. |
| Procurement and sourcing | Merge financial dimensions from the vendor with active dimension link financial dimension on the purchase order | This feature lets you merge financial dimensions from vendors with active dimension link financial dimensions after purchase requisition approval if you set up a link between a financial dimension and the site inventory dimension. Purchase order creation and demand consolidation purchasing policy rules can be set up to drive the decision for merging financial dimensions from vendors with active dimension link financial dimension on the purchase order header level. |
| Procurement and sourcing | Disable Purchase Requisition Distribution Reset Button | This feature disables the **Reset** button on the **Accounting distribution** page  for purchase requisitions that are in review. |
| Procurement and sourcing | Consolidate multiple purchase requisitions into a single purchase order by accounting date | This feature allows multiple purchase requisitions to be consolidated into a single purchase order if the different purchase requisitions have different accounting dates. Purchase order creation and demand consolidation purchasing policy rules can be set up to automate the decision for grouping requisition lines by accounting date on the purchase order level. Purchase order consolidation by accounting date is not supported if budget control is enabled because the accounting date is used for budget reservations and encumbrance. Therefore, it should be retained during the transition from purchase requisition to purchase order. |
| Production control | Enable default location setup for production formula/BOM and automatic GTD reservation/consumption in production | The feature enables additional options for production from imported raw materials (Russian localization only):<ul><li>Option to set the automatic default location for production formulas and bills of material on both resource groups and warehouses.</li><li>Automatic reservation of raw materials by the *GTD number* dimension at WMS-activated warehouses according to the non-WMS reservation algorithm. This applies in cases where a work policy for *Raw material picking* exists with **Work creation method** set to *Never* and the warehouse, location and item number setup matches the inventory transactions of the production (batch) order.</li><li>Automatic consumption of raw materials by *GTD number* dimension upon picking list posting, according to the acquired reservation described previously.</li></ul> |
| Inventory and warehouse management | (Poland) Allow to link several SAD invoices to one Purchase order line in one SAD | This feature provides the possibility to link more than one SAD invoice to the purchase order line in one SAD. |
| Warehouse management | Disable expected receipts from quality orders that sample blocked inventory | This feature prevents the system from creating expected receipt transactions for quality orders that sample inventory with a blocking status. Because the blocked inventory isn't available, this feature removes the expected receipts. This helps make sure that inventory doesn't end with multiple blocking statuses, which can result in data integrity issues. |
| Warehouse management <!-- KFM: Check module name ion FM --> | (Preview) Scale unit support for inbound and outbound warehouse orders | This feature causes the system to create outbound warehouse orders during the release-to-warehouse process, and to create inbound warehouse orders when transfer orders are posted as shipped. The system then synchronizes each inbound or outbound warehouse order to the scale unit responsible for shipping or receiving the order. Note that after enabling this feature, your warehouse execution workloads must be upgraded. For more information, see [Warehouse management workloads for cloud and edge scale units](../cloud-edge/cloud-edge-workload-warehousing.md).<br><br>This feature requires the *Decouple putaway work from ASNs* feature and will enable the capability of receiving transfer orders using the license plate receiving process on the Warehouse Management mobile app.  |

## Features turned on by default in this release

The following table lists features that became either mandatory or turned on by default starting in 10.0.25. All of these features will automatically be turned on for your system as soon as you update to 10.0.25 (if they aren't already). Mandatory features can't be turned off, but default-on features can still be turned off using [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Feature name | Enable date | Feature added | Feature state | Module |
| --- | --- | --- | --- | --- |

## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.25 includes platform updates. To learn more, see [Platform updates for version 10.0.25 of Finance and Operations apps (November 2021)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-25.md). <!--KFM: Confirm link -->

### Bug fixes

For information about the bug fixes included in each of the updates that are part of 10.0.25, sign in to Lifecycle Services (LCS) and view the [KB article](#). <!--KFM: Get new link -->

### Dynamics 365 and industry clouds: 2022 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2022 release wave 1 plan](/dynamics365-release-plan/2021wave/). <!--KFM: Confirm link -->
We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) topic describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]