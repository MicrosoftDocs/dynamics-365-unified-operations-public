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

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management version 10.0.43. This version has a build number of 10.0.X <!-- KFM: get build number --> and is available on the following schedule:

- **Preview of release:** January 2025
- **General availability of release (self-update):** March 2025
- **General availability of release (auto-update):** April 2025

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Copilot and AI innovation | Enhanced user feedback for Copilot and related experiences | [Enable enhanced user feedback for Copilot and related experiences (preview)](../../fin-ops-core/dev-itpro/copilot/enable-copilot-feedback.md) | Feature management:<br>*(Preview) Enable user feedback for Copilot and related experiences* |
| Inventory and logistics | [Enhance vendor rebate management](/dynamics365/release-plan/2024wave2/finance-supply-chain/dynamics365-supply-chain-management/enhance-vendor-rebate-management-reconciliation-resubmission-workflows) | [Rebate management deal workflows](../rebate-management/rebate-management-workflows.md) | Feature management:<ul><li>*Consolidate vendor invoices for the same vendor in vendor rebate deals*</li><li>*Enable posting of vendor rebate outputs to purchase order vendors*</li><li>*Enable resubmission of workflows for vendor rebate deals*</li></ul> |

## <a name="enhancements"></a>Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they're only enhancements, they aren't listed in the [release plan](/dynamics365/release-plan/2024wave2/finance-supply-chain/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

Some of these features aren't visible on your system until you turn them on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) using the name listed here for the *Feature management name* (additional configuration may also be needed). Features that don't show a feature management name are visible by default as of this version of Supply Chain Management, but typically add a new configuration option that you need to set to use the new functionality.

| Feature enhancement | Description |
|---|---|
| **Module:** Asset management<br><br>**Feature management name:** *Role-based access control for work order lifecycle stages* | Lets admins assign security roles to each available work order lifecycle state. When a lifecycle state has a security role assigned to it, only users with that role will be able to change work orders to that lifecycle state.<br><br>Learn more in [Work order lifecycle states](../asset-management/setup-for-work-orders/work-order-lifecycle-states.md). |
| **Module:** Asset management<br><br>**Feature management name:** *Adjust forecast hours to match schedule hours when work orders are dispatched* | Lets you choose whether a forecast should be updated automatically when dispatching a work order after the hours have been manually changed.<br><br>Learn more in [Dispatch work order](../asset-management/work-order-scheduling/dispatch-work-order.md). |
| **Module:** Master planning<br><br>**Feature management name:** *Keep pegging between approved planned orders for Planning Optimization* | Lets you to choose whether pegging assignments should be kept for approved planned orders. To set this option, go to the **Master planning parameters** page, open the **Planned orders** tab, and set **Keep pegging between approved planned orders** to *Yes* or *No*. Enabling this option ensures that created supply is used for its initial purpose, following a first-come-first-served approach. We recommend that you enable this option in make-to-order scenarios or if you use grouping or splitting of planned orders. |
| **Module:** Master planning<br><br>**Feature management name:** *Calculate catch weight quantities for catch weight enabled products in Planning Optimization* | Enhances Planning Optimization by enabling quantity calculations in catch weight units for products that are enabled as catch weight items. The feature ensures that master planning generates planned purchase orders with specified catch weight quantities. |
| **Module:** Master planning<br><br>**Feature management name:** *Support for material step consumption for Planning Optimization* | Adds support for step consumption in Planning Optimization. Step consumption is used to calculate fixed consumption based on the quantity of the end product. The quantity of consumed material is calculated based on the intervals (steps) defined for each BOM/formula line. |
| **Module:** Master planning<br><br>**Feature management name:** *Dimension-based product configuration for Planning Optimization* | Lets you create many product variants from a single product master and its bill of materials. |
| **Module:** Master planning<br><br>**Feature management name:** *Clean up data from failed Demand planning import jobs* | Adds a scheduled task that cleans up staging table data related to failed import jobs from Demand planning in Microsoft Dynamics 365 Supply Chain Management. |
| **Module:** Procurement and sourcing<br><br>**Feature management name:** *(Preview) Follow-up with vendors on purchase orders* | Follow-up with vendors on purchase orders. |
| **Module:** Product information management<br><br>**Feature management name:** *(Preview) Enable foreign trade parameters for all countries* | Enables foreign trade parameters for all countries. |
| **Module:** Sales and marketing<br><br>**Feature management name:** *Introduce parameter to consider reserved on-hand quantity as unavailable for ATP* | Lets you choose whether reserved on-hand inventory should be considered available for use in promise (ATP) calculations. To set this options, go to the **Accounts receivable parameters** page, open the **Shipments** tab, expand the **Delivery control** FastTab, and set **ATP excl. reserved on-hand** to *Yes* or *No*. |
| **Module:** Warehouse management<br><br>**Enhancement:** *Clean up work exception logs*<br><br>**Feature management name:** *(None)* | Adds a batch job that removes old or unneeded work-exception log entries based on specified criteria, which can help improve system performance for some operations (such as when searching for locations with open exceptions).<br><br>Learn more in [View and manage the work exceptions log](../warehousing/work-exceptions-log.md) |

## Preview features that are now generally available

The following table lists the features that were introduced as public preview features in a previous version and became generally available in version 10.0.43. As with other new features, most of these features are turned off by default, so you must turn them on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) if you want to use them.

| Module | Feature name | More information |
|---|---|---|
| Sales and marketing | *Unified pricing management* | [Unified pricing management module overview (preview)](../unified-pricing-management/upm-pricing-management-overview.md) <!-- KFM: This is still named with "(Preview)" in FM --> |

## Features becoming mandatory in this release

The following table lists the features that became mandatory in version 10.0.41. These features can still be seen in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) but can no longer be turned off.

| Module | Feature name | More information |
|---|---|---|
| Procurement and sourcing | *Assign Auto Charge for Purchase Order* | Lets you choose whether to automatically add charges from a request for quotation (RFQ) to a purchase order. This feature adds a setting called **Assign Auto Charge for PO** to the **Request for quotation** tab of the **Procurement and sourcing parameters page**. When **Assign Auto Charge for PO** is set to *Yes*, charges from an RFQ are automatically copied to its related purchase order. |
| Master planning | *Batch CTP*| Adds a new delivery date control type called *Batch CTP*, which provides confirmed delivery dates for sales order lines when the current dynamic master plan is run. This delivery control makes capable to promise (CTP) functionality available when you are using Planning Optimization. In some previous versions of Supply Chain Management, this feature was called *CTP for Planning Optimization*<br><br>Learn more in [Calculate sales order delivery dates using CTP](../master-planning/planning-optimization/calculate-delivery-dates-using-ctp.md) |

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

For information about the bug fixes included in each of the updates that are part of version 10.0.43, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](#). <!-- KFM: get link -->

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
