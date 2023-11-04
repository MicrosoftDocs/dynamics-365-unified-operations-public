---
title: Preview of Dynamics 365 Supply Chain Management 10.0.38 (February 2024)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.38. 
author: kamaybac
ms.author: kamaybac
ms.reviewer: kamaybac
ms.search.form:
ms.topic: conceptual
ms.date: 10/27/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Preview of Dynamics 365 Supply Chain Management 10.0.38 (February 2024)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management preview version 10.0.38. This version has a build number of 10.0.1777 and is available on the following schedule:

- **Preview of release:** October 2023
- **General availability of release (self-update):** December 2023
- **General availability of release (auto-update):** February 2024

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Cost management | [Evaluate discrete manufacturing costs using standard cost](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/evaluate-costs-discrete-manufacturing-using-standard-cost) |  This enhancement for the Global Inventory Accounting enables discrete manufacturing companies to perform parallel inventory accounting practices for standard cost using multiple configurations. Though it's possible to enable this feature in Supply Chain Management 10.0.38, we recommend against doing so until further notice because additional service upgrades are still required (expected in early 2024). | Feature management:<br>*(Preview) Evaluate costs in discrete manufacturing using standard cost in Global Inventory Accounting*  |
| Inventory and logistics | [Apply compound charges to quotations and sales orders](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/apply-compound-charges-quotations-sales-orders) | *Coming soon* |  <p>Feature&nbsp;management:</p><ul><li>*Period charges*</li><li>*Sequence and compound for customer charges*</li><li>*Unit of measure for line level charges*</li></ul> |
| Inventory and logistics | [Enhanced order processing in Pricing management](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/enhanced-order-processing-pricing-management) | *Coming soon* | Enabled by default |
| Inventory and logistics | [Manage prices with the pricing management workspace](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/manage-prices-pricing-management-workspace) | Provides a pricing management workspace, which lets sales managers know about impending price rule status changes and supports their choice to modify pricing policies. Sales managers can perform light tasks to enable or disable the pricing rules without leaving the workspaces. | Feature management:<br>*(Preview) Pricing management workspace* |
| Inventory and logistics | [View and manage inventory with a new mobile app](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/view-manage-inventory-new-mobile-app) | *Coming soon* | Enabled by default |
| Manufacturing and asset management | Change the asset type of existing assets | [Change the asset type of existing assets](../asset-management/objects/change-asset-type.md) | Feature management:<br>*(Preview) Change types on assets and functional locations*  |
| Manufacturing and asset management | Change the functional location type of existing functional locations | [Change the type of existing functional locations](../asset-management/functional-locations/change-functional-location-type.md) | Feature management:<br>*(Preview) Change types on assets and functional locations*  |
| Manufacturing and asset management | [React to last-minute changes in production](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/react-last-minute-changes-production) | [Feature enhancements included in this release](#enhancements) | <p>Feature&nbsp;management:</p><ul><li>*Dynamic positive days for Planning Optimization*</li><li>*Prevent production orders to be released when full material is not available*</li><li>*Use of margins for scheduling orders*</li></ul> |
| Master planning | Demand planning app for Dynamics 365 Supply Chain Management | [Demand planning home page](../demand-planning/demand-planning-home-page.md) | Feature management:<br>*(Preview) Demand Planning* |
| Master planning | Prioritize existing supply over required BOM/route in Planning Optimization | [Demand-specified BOM or formula versions and/or routes](../master-planning/coverage-settings.md#specify-versions-routes) | Feature management:<br>*Prioritize existing supply over required BOM/route in Planning Optimization* |
| Procurement | [Inform vendors about when to ship items](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/inform-vendors-about-when-ship-items) | <p>Enables you to do the following:</p><ul><li>Determine the supplier's shipping calendar from the vendor and its subsequent default to the relevant document.</li><li>Determine the delivery transport days from the supplier to the receiving point.</li><li>Enhance the purchasing process through the incorporation of new requested and confirmed ship dates.</li><li>Consider the supplier's shipping calendar and transport days for the automatic calculation of supplier ship dates.</li></ul> | Feature management:<br>*Supplier requested and confirmed shipment dates* |
| Warehouse management | [Operate warehouses connected to external order management systems](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/operate-warehouses-connected-external-order-management-systems) | [Warehouse management only mode overview](../warehousing/wms-only-mode-overview.md) | Feature management:<br>*(Preview) Warehouse management only mode* |
| Warehouse management | [Optimize the inbound receiving process](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/optimize-inbound-receiving-process) | [Deferred receiving processing](../warehousing/mixed-license-plate-receiving.md#deferred-receiving-processing) | Enabled by default |

## <a name="enhancements"></a>Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they're only enhancements, they aren't listed in the [release plan](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

If you want to turn any of these features on or off, you must do so in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Module | Feature name in feature management | More information |
|---|---|---|
| Asset management | (Preview) Asset Management enhancements | Supervisors can now configure how work order start dates should be defaulted when changing the work order state. Choose between the scheduled/expected start date (current behavior) and actual start date (new option).<br><br>Supervisors can now configure how work order end dates should be defaulted when changing the work order state. Choose between the scheduled/expected end date (current behavior) and actual end date (new option).<br><br>Supervisors can now configure how the system should set the default value for the scheduled start date when dispatching a work order line. Choose between the expected start date from the work order header (current behavior) and scheduled start date from the work order line (new option).<br><br>Supervisors can now configure how the system should copy the description from a maintenance request to a work order. Choose between copying the description to the work order header (current behavior) or copying the description to the work order line. |
| Master planning | Dynamic positive days for Planning Optimization | Enables Planning Optimization to be set up with positive days at the coverage group or master plan level. The feature also adds support for dynamic positive days, which ensure that current on-hand inventory or other supply is used within the lead time while creating new supply to fulfill demand outside of the lead time. |
| Master planning | (Preview) Enable ATP calculations to consider user-modified delivery schedules applied to sales order lines | Enables available-to-promise (ATP) calculations to consider user-modified delivery schedules applied to sales order lines. Users working on the **Delivery schedule** page with ATP delivery date control enabled can adjust the delivery schedule for each line according to demand and expect the ATP calculation to reflect those adjustments. Without this feature, ATP calculations ignore user-modified schedules, which could produce less accurate results. |
| Master planning | Positive days for Planning Optimization | Enables the system to consider positive days settings when running Planning Optimization. |
| Master planning | Show batch job status as Error when applicable for Planning Optimization | Adds a new setting called **Show batch job status as Error when applicable** to the **Master planning parameters** page. When this parameter is set to *Yes*, master planning batch jobs are marked as an error if at least one error was found when calculating supply or processing the batch job. Set the parameter to *No* to show all completed master planning batch jobs as *Ended*, regardless of whether errors occurred during the run. |
| Master planning | Start dates of production orders of all components delayed when one of the components is delayed for Planning Optimization | When using Planning Optimization, this feature delays the production or purchase of components when needed to ensure they don't lie unused in the warehouse when they can't be used in the production of their parent item. |
| Master planning | (Preview) Support for splitting and grouping planned orders for Planning Optimization | Adds support for splitting and grouping planned orders for Planning Optimization. This is achieved by approving the planned orders to be either split or grouped and then rerunning planning for the item on the planned orders being split or grouped. |
| Master planning | Use of margins for scheduling orders | Adds the option to consider the use of receipt margin, issue margin, and reorder margin when scheduling a production order. |
| Procurement and sourcing | Synchronize updates of the Requested ship and receipt dates on intercompany sales and purchase order lines | Lets you control whether the requested ship and receipt dates are synchronized across intercompany sales and purchase order lines. It adds new settings to both the **Purchase order policies** and **Sales order policies** tabs of the **Intercompany** setup page for customers and vendors. |
| Product information management | (Preview) Enable product inquiry in-app Copilot chat functionality. | Enables product inquiry in-app Copilot chat functionality. |
| Production control | Change BOM item | Lets you change one BOM item to another in estimated or scheduled production orders. This includes the ability to use up the on-hand inventory of an existing item and substitute it for a new one once the on-hand has been used. |
| Production control | Production order route change | Lets you change a production order route of multiple scheduled production orders at the same time. |
| Production control | Standard cost financial posting of a production/batch order with a scrap account method. | Enables the system to financially update a fully scrapped production or batch order with a scrap account method. |
| Sales and marketing | Enable attribute-based pricing by company | Enables you to use attribute-based pricing by company. |
| Sales and marketing | (Preview) Pricing management for pricing rule cleanup | Pricing management for pricing rule cleanup. |
| Sales and marketing | Pricing management performance enhancement | Enables Pricing management to make some types of calculations more quickly. |
| Transportation management | Integrate Microsoft Sustainability Manager with transportation management | Enables companies to significantly reduce their carbon footprint. This is achieved through route optimization, reduced fuel consumption, and the increased use of lower-emission transportation options. This feature can help improve visibility, control, and automation for the transportation process. |
| Warehouse management | Prevent production orders to be released when full material is not available | Fixes an issue where the production control parameter **Requirement for material reservation** is set to *Require full reservation*. Previously, when a production order was released while this option was selected, its status was always changed from *Scheduled* to *Released*, even if all material couldn't be fully reserved. When this feature is enabled, when a production order is released with this option selected, the production order will only change status once all material is fully available for reservation. |

## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.38 includes platform updates. To learn more, see [Platform updates for version 10.0.38 of Finance and Operations apps (February 2024)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-38.md).<!--KFM: Confirm link -->

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.38, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=857683).

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
