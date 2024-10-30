---
title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.38 (February 2024)
description: Learn about features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.38 with a table outlining feature areas. 
author: kamaybac
ms.author: kamaybac
ms.topic: conceptual
ms.date: 04/19/2024
ms.custom:
  - bap-template
  - evergreen
ms.reviewer: kamaybac
ms.search.form:
---

# What's new or changed in Dynamics 365 Supply Chain Management 10.0.38 (February 2024)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management version 10.0.38. This version has a build number of 10.0.1777 and is available on the following schedule:

- **Preview of release:** October 2023
- **General availability of release (self-update):** December 2023
- **General availability of release (auto-update):** February 2024

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Copilot and AI innovation | [Add an AI inventory chatbot to your app or website](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/add-natural-language-inventory-chatbot-third-party-app-or-website) | [Inquire into inventory with Copilot](../inventory/inventory-visibility-copilot-api.md) | Enabled by default |
| Copilot and AI innovation | [Empower users with conversational product help and guidance](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/empower-users-conversational-product-help-guidance) | [Generative help and guidance with Copilot](../../fin-ops-core/fin-ops/copilot/copilot-generative-help.md) | [Enable Copilot capabilities in finance and operations apps](../../fin-ops-core/dev-itpro/copilot/enable-copilot-generative-help.md) |
| Copilot and AI innovation | [Use natural language to check inventory with Copilot](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/use-natural-language-check-inventory-copilot) | [Inquire into inventory with Copilot](../inventory/inventory-visibility-copilot-api.md) | Enabled by default |
| Cost management | [Evaluate discrete manufacturing costs using standard cost](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/evaluate-costs-discrete-manufacturing-using-standard-cost) |  This enhancement for the Global Inventory Accounting enables discrete manufacturing companies to perform parallel inventory accounting practices for standard cost using multiple configurations. Though it's possible to enable this feature in Supply Chain Management 10.0.38, we recommend against doing so until further notice because additional service upgrades are still required (expected in early 2024). | Feature management:<br>*(Preview) Evaluate costs in discrete manufacturing using standard cost in Global Inventory Accounting*  |
| Inventory and logistics | [Apply compound charges to quotations and sales orders](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/apply-compound-charges-quotations-sales-orders) | [Period charges](../sales-marketing/period-charges.md)<br><br> [Autocharge compounding and sequencing](../sales-marketing/auto-charge-sequence-compound.md)<br><br>[Units of measure for line-level charges](../sales-marketing/line-charges-specific-unit.md) |  <p>Feature&nbsp;management:</p><ul><li>*Period charges*</li><li>*Sequence and compound for customer charges*</li><li>*Unit of measure for line level charges*</li></ul> |
| Inventory and logistics | [Enhanced order processing in Pricing management](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/enhanced-order-processing-pricing-management) | *Coming soon* | Enabled by default |
| Inventory and logistics | [Find products and on-hand information by attribute](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/find-products-on-hand-information-attribute) | [Search for products using the Inventory Visibility app](../inventory/inventory-visibility-product-search-app.md)<br><br>[Query with product search](../inventory/inventory-visibility-api.md#product-search-query) (API) | Enabled by default |
| Inventory and logistics | [Integrate transportation management with Microsoft Cloud for Sustainability](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/integrate-transportation-management-cloud-sustainability) | [Integrate with Microsoft Sustainability Manager](../transportation/sustainability-manager-integration-setup.md) | Feature management:<br>*Integrate Microsoft Sustainability Manager with transportation management* |
| Inventory and logistics | Log and view successful API posts in Inventory Visibility | [Log and view successful API posts](../inventory/inventory-visibility-track-inventory-log-history.md) | Enabled by default |
| Inventory and logistics | [Manage prices with the pricing management workspace](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/manage-prices-pricing-management-workspace) | Provides a pricing management workspace, which lets sales managers know about impending price rule status changes and supports their choice to modify pricing policies. Sales managers can perform light tasks to enable or disable the pricing rules without leaving the workspaces. | Feature management:<br>*(Preview) Pricing management workspace* |
| Inventory and logistics | [View and manage inventory with a new mobile app](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/view-manage-inventory-new-mobile-app) | [Inventory On-hand mobile app](../inventory/inventory-onhand-mobile-app.md) | Enabled by default |
| Manufacturing and asset management | Change the asset type of existing assets | [Change the asset type of existing assets](../asset-management/objects/change-asset-type.md) | Feature management:<br>*(Preview) Change types on assets and functional locations*  |
| Manufacturing and asset management | Change the functional location type of existing functional locations | [Change the type of existing functional locations](../asset-management/functional-locations/change-functional-location-type.md) | Feature management:<br>*(Preview) Change types on assets and functional locations*  |
| Manufacturing and asset management | [React to last-minute changes in production](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/react-last-minute-changes-production) | [React to last-minute changes in production](../production-control/react-to-last-minute-changes.md)<br><br>[Dynamic positive days for last-minute orders](../master-planning/dynamic-positive-days.md)<br><br>See also the [Feature enhancements included in this release](#enhancements) section.</p> | <p>Feature&nbsp;management:</p><ul><li>*Production order route change*</li><li>*Change BOM item*</li><li>*Dynamic positive days for Planning Optimization*</li><li>*Prevent production orders to be released when full material is not available*</li><li>*Use of margins for scheduling orders*</li></ul> |
| Master planning | Demand planning in Microsoft Dynamics 365 Supply Chain Management | [Demand planning home page](../demand-planning/demand-planning-home-page.md) | Feature management:<br>*Demand Planning* |
| Master planning | Prioritize existing supply over required BOM/route in Planning Optimization | [Demand-specified BOM or formula versions and/or routes](../master-planning/coverage-settings.md#specify-versions-routes) | Feature management:<br>*Prioritize existing supply over required BOM/route in Planning Optimization* |
| Procurement | [Inform vendors about when to ship items](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/inform-vendors-about-when-ship-items) | [Calculate requested ship dates for purchase orders](../master-planning/supplier-requested-confirmed-dates.md) | Feature management:<br>*Supplier requested and confirmed shipment dates* |
| Warehouse management | [Operate warehouses connected to external order management systems](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/operate-warehouses-connected-external-order-management-systems) | [Warehouse management only mode overview](../warehousing/wms-only-mode-overview.md) | Feature management:<br>*Warehouse management only mode* |
| Warehouse management | [Optimize the inbound receiving process](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/optimize-inbound-receiving-process) | [Deferred receiving processing](../warehousing/mixed-license-plate-receiving.md#deferred-receiving-processing) | Enabled by default |

## <a name="enhancements"></a>Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they're only enhancements, they aren't listed in the [release plan](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

If you want to turn any of these features on or off, you must do so in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Module | Feature name in feature management | More information |
|---|---|---|
| Asset management | (Preview) Asset Management enhancements | Supervisors can now configure how work order start dates should be defaulted when changing the work order state. Choose between the scheduled/expected start date (current behavior) and actual start date (new option).<br><br>Supervisors can now configure how work order end dates should be defaulted when changing the work order state. Choose between the scheduled/expected end date (current behavior) and actual end date (new option).<br><br>Supervisors can now configure how the system should set the default value for the scheduled start date when dispatching a work order line. Choose between the expected start date from the work order header (current behavior) and scheduled start date from the work order line (new option).<br><br>Supervisors can now configure how the system should copy the description from a maintenance request to a work order. Choose between copying the description to the work order header (current behavior) or copying the description to the work order line. |
| Master planning | (Preview) Enable ATP calculations to consider user-modified delivery schedules applied to sales order lines | Enables available-to-promise (ATP) calculations to consider user-modified delivery schedules applied to sales order lines. Users working on the **Delivery schedule** page with ATP delivery date control enabled can adjust the delivery schedule for each line according to demand and expect the ATP calculation to reflect those adjustments. Without this feature, ATP calculations ignore user-modified schedules, which could produce less accurate results. |
| Master planning | Positive days for Planning Optimization | Enables the system to consider positive days settings when running Planning Optimization. |
| Master planning | Show batch job status as Error when applicable for Planning Optimization | Adds a new setting called **Show batch job status as Error when applicable** to the **Master planning parameters** page. When this parameter is set to *Yes*, master planning batch jobs are marked as an error if at least one error was found when calculating supply or processing the batch job. Set the parameter to *No* to show all completed master planning batch jobs as *Ended*, regardless of whether errors occurred during the run. |
| Master planning | Start dates of production orders of all components delayed when one of the components is delayed for Planning Optimization | When using Planning Optimization, this feature delays the production or purchase of components when needed to ensure they don't lie unused in the warehouse when they can't be used in the production of their parent item. |
| Master planning | (Preview) Support for splitting and grouping planned orders for Planning Optimization | Adds support for splitting and grouping planned orders for Planning Optimization. This is achieved by approving the planned orders to be either split or grouped and then rerunning planning for the item on the planned orders being split or grouped. |
| Master planning | Use of margins for scheduling orders | Adds the option to consider the use of receipt margin, issue margin, and reorder margin when scheduling a production order. |
| Procurement and sourcing | Synchronize updates of the Requested ship and receipt dates on intercompany sales and purchase order lines | Lets you control whether the requested ship and receipt dates are synchronized across intercompany sales and purchase order lines. It adds new settings to both the **Purchase order policies** and **Sales order policies** tabs of the **Intercompany** setup page for customers and vendors. |
| Product information management | (Preview) Enable product inquiry in-app Copilot chat functionality. | Enables product inquiry in-app Copilot chat functionality. |
| Production control | Standard cost financial posting of a production/batch order with a scrap account method. | Enables the system to financially update a fully scrapped production or batch order with a scrap account method. |
| Sales and marketing | Enable attribute-based pricing by company | Enables you to use attribute-based pricing by company. |
| Sales and marketing | (Preview) Pricing management for pricing rule cleanup | Pricing management for pricing rule cleanup. |
| Sales and marketing | (Preview) Pricing management performance enhancement | Improves performance of pricing calculations by using pricing rule hash strings to filter potential pricing rules and speed up matching logic. The first time you enable the feature, it generates a hash string for all existing rules. Thereafter, it automatically generates a hash string for each new pricing rule. The feature adds a new batch job, *Generate pricing rule hash value*, which you can manually schedule either to generate hash strings for rules that are missing them (delta), or to regenerate hash strings for all existing pricing rules. |
| Warehouse management | Prevent production orders to be released when full material is not available | Fixes an issue where the production control parameter **Requirement for material reservation** is set to *Require full reservation*. Previously, when a production order was released while this option was selected, its status was always changed from *Scheduled* to *Released*, even if all material couldn't be fully reserved. When this feature is enabled, when a production order is released with this option selected, the production order will only change status once all material is fully available for reservation. |

## Related information

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.38 includes platform updates. Learn more in [Platform updates for version 10.0.38 of Finance and Operations apps (February 2024)](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-38.md).

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
