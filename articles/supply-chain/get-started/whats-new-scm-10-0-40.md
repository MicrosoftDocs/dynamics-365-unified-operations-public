---
title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.40 (June 2024)
description: Learn about features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.40 with a table outlining feature areas. 
author: kamaybac
ms.author: kamaybac
ms.topic: conceptual
ms.date: 04/27/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# What's new or changed in Dynamics 365 Supply Chain Management 10.0.40 (June 2024)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management version 10.0.40. This version has a build number of 10.0.1935 and is available on the following schedule:

- **Preview of release:** April 2024
- **General availability of release (self-update):** May 2024
- **General availability of release (auto-update):** June 2024

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Copilot and AI innovation | [Enable efficient, accurate demand planning with Copilot](/dynamics365/release-plan/2024wave1/finance-supply-chain/dynamics365-supply-chain-management/enable-more-efficient-accurate-demand-planning-using-copilot) | [Analyze demand plans with Copilot](../demand-planning/demand-planning-copilot.md) | Enabled using the Power Apps maker portal.  |
| Copilot and AI innovation | [Generate context-aware insights for warehouse workers](/dynamics365/release-plan/2024wave1/finance-supply-chain/dynamics365-supply-chain-management/generate-context-aware-insights-warehouse-workers) | [Workload insights with Copilot in the Warehouse Management mobile app](../warehousing/warehouse-management-mobile-app-insights.md) | <p>Feature management:<br>*Context-aware worker summary screen in WMA*</p><p>Requires Warehouse Management mobile app version 2.3.2.0 or later.</p><p>Requires Supply Chain Management version 10.0.40 with proactive quality update 1 (PQU-1) or later.</p> |
| Copilot and AI innovation | AI summaries with Copilot | [AI summaries with Copilot](copilot-summaries-overview.md) | <p>Feature management:</p><ul><li>*Product summary when hovering on item*</li><li>*Product details summary*</li><li>*Purchase order summary*</li><li>*Sales order summary*</li><li>*Vendor summary*</li></ul><p>Requires Supply Chain Management version 10.0.40 with PQU-1 or later.</p> |
| Planning | Item substitution for bills of materials in Planning Optimization | [Item substitution for formulas and bills of materials](../master-planning/item-substitution.md) | Feature management:<br>*Item substitution for bill of materials in Planning optimization* |
| Inventory and logistics | [Reproduce business documents that include product bundles](/dynamics365/release-plan/2024wave1/finance-supply-chain/dynamics365-supply-chain-management/reproduce-business-documents-that-include-product-bundles) | [Sell and allocate product bundles](../sales-marketing/product-bundles-use.md#bundles-journals) | Feature management:<br>*(Preview) Product bundles in journals*  |
| Inventory and logistics | [Query and manage inventory without site or warehouse info](/dynamics365/release-plan/2024wave1/finance-supply-chain/dynamics365-supply-chain-management/query-post-reserve-inventory-without-specifying-site-or-warehouse) | [Data partition rule](../inventory/inventory-visibility-power-platform.md#data-partition) | Enabled by default |
| Manufacturing and asset management | [Track and trace serial and batch numbers for manufacturing](/dynamics365/release-plan/2024wave1/finance-supply-chain/dynamics365-supply-chain-management/track-trace-serial-batch-numbers-manufacturing) | [Register and track batch/serial numbers for finished products and their components (preview)](../production-control/tracked-components.md) | Feature management:<br>*Tracked components* |
| Planning | Rolling forecasts for demand planning | [Rolling forecasts](../demand-planning/rolling-forecasts.md) | Enabled by default |
| Warehouse Management | Complete mixed license plates from a mobile device | [Set up a mobile device menu item for completing mixed license plates](../warehousing/mobile-device-complete-mixed-lp-menu.md) | Enabled by default |
| Warehouse Management | [Inspect and process returned items more efficiently](/dynamics365/release-plan/2024wave1/finance-supply-chain/dynamics365-supply-chain-management/inspect-process-returned-items-more-efficiently) | [Receive unannounced sales returns](../warehousing/sales-returns-unannounced.md) | Enabled by default |
| Warehouse Management | Monitor the status of failed shipment lines | [Automatic rewaving of nonallocated shipment lines](../warehousing/auto-rewave-shipments.md) | Enabled by default |
| Warehouse Management | Operate external shared warehouse with Warehouse management only mode | [Warehouse management only mode with external shared warehouses](../warehousing/wms-only-mode-external-shared-warehouse.md) | Feature management:<br>*Warehouse management only mode*  |

## <a name="enhancements"></a>Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they're only enhancements, they aren't listed in the [release plan](/dynamics365/release-plan/2024wave1/finance-supply-chain/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

Some of these features aren't visible on your system until you turn them on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) using the name listed here for the *Feature management name* (additional configuration may also be needed). Features that don't show a feature management name are visible by default as of this version of Supply Chain Management, but typically add a new configuration option that you need to set to use the new functionality.

| Feature enhancement | Description |
|---|---|
| <p>**Module:** Cost management</p><p>**Feature management name:** *Clean up "Potential conflicts - inventory and general ledger" and "Potential conflicts - work in process and general ledger" report data*</p> | Provides a way to clean up the **Potential conflicts - inventory and general ledger** and **Potential conflicts - work in process and general ledger** report storage data. |
| <p>**Module:** Inventory and warehouse management</p><p>**Feature management name:** *Correct item that is not visible in released products form manually*</p> | Lets you manually correct items that aren't visible on the released products page. To use this feature, go to **Inventory management** \> **Periodic tasks** \> **Clean up** \> **Correct item that is not visible in released products form manually**. |
| <p>**Module:** Inventory and warehouse management</p><p>**Feature management name:** *Dimension history for documents report data clean up*</p> | Cleans up report data from the dimension history for documents, which includes purchase packing slips, purchase confirmations, sales packing slips, sales invoices, sales quotations, picking lists, and vendor invoices. |
| <p>**Module:** Master planning</p><p>**Feature management name:** *Exclude items without on-order quantity for Planning Optimization.*</p> | Adds an option to the master plan for excluding items without on-order quantity. This can be used for improving planning performance when there are many products defined and they rarely have demand but can't be excluded using the recommended product lifecycle state. |
| <p>**Module:** Master planning</p><p>**Feature management name:** *Freezing time fence for Planning optimization*</p> | Adds support for Freezing time fences for Planning optimization. |
| <p>**Module:** Master planning</p><p>**Feature management name:** *(Preview) Inherit inventory status for planned intercompany demand orders*</p> | Adds an option in master plans that allows intercompany orders to inherit inventory status from intercompany supply instead of applying a default value. To use this functionality, inventory statuses must exist on both companies and be identified by inventory status ID. |
| <p>**Module:** Master planning</p><p>**Feature management name:** *Item substitution for bill of materials in Planning optimization*</p> | Allows you to indicate substitute items that could be used in a bill of materials whenever there isn't enough on-hand of the main item. Indicate products that could substitute the main component by priority and planning will automatically pick the one with available on-hand inventory following the priorities indicated in the plan group. This functionality is available for Planning Optimization and not for the deprecated planning engine. |
| <p>**Module:** Master planning</p><p>**Feature management name:** *Transport days support for Planning Optimization*</p> | Enables transport days for Planning Optimization. Transport days are used to define the number of days between a given shipping warehouse and a destination address or other warehouse. |
| <p>**Module:** Master planning</p><p>**Feature management name:** *Use rounding for unit of measures in Planning Optimization*</p> | Ensures that the rounding rule provided by the unit of measure of an item is respected when replenishing through a purchase order. If the rounded quantity doesn't cover the replenishment requirements, the rounding rule is ignored and the quantity is rounded up instead. |
| <p>**Module:** Production control</p><p>**Feature management name:** *List view for reporting job progress from the production floor execution interface*</p> | Workers reporting job progress from the production floor execution interface can now choose to work from a list view that shows several jobs at once, or from a detail view that shows more information about one job at a time. Previously, only the detail view was available. |
| <p>**Module:** Sales and marketing</p><p>**Feature management name:** *Recalculate delivery dates upon creation of direct delivery*</p> | Adds a parameter called **Recalculate delivery dates** to the **Create direct delivery** dialog available from the **Sales Orders** page. When this parameter is set to *Yes*, the system recalculates the requested receipt date and requested ship date when creating a direct delivery order line if the confirmed receipt date isn't set on the sales order header and the delivery date control isn't set to *None*. Furthermore, for an intercompany order, the **Update requested receipt date with a confirmed date** parameter on the intercompany policy is respected. This means that even if a confirmed receipt is set on the sales order, the header recalculation still occurs for an intercompany order if this parameter is turned on and the direct delivery date control isn't set to *None*. |
| <p>**Module:** Warehouse management</p><p>**Enhancement:** *Hide mobile device menu items in the menus*</p><p>**Feature management name:** *(None)*</p> | <p>Lets you conceal selected mobile device menu items from the mobile device menu layout by right-clicking on them in the **Mobile device menu** page and choosing *Show* or *Hide*. This is useful for [detour](../warehousing/warehouse-app-detours.md) menu items, which must be in a menu structure that the workers that should use the detour have access to.</p><p>Learn more in [Mobile device menu](../warehousing/configure-mobile-devices-warehouse.md#mobile-device-menu). |
| <p>**Module:** Warehouse management</p><p>**Enhancement:** *Location blocking causes policy*</p><p>**Feature management name:** *(None)*</p> | <p>Adds a new blocking-causes policy that can apply to each location as a reason for being *Input blocked* and/or *Output blocked*. The new policy determines whether warehouse work location processing should also be blocked.</p><p>Learn more in [Define location blocking causes](../warehousing/tasks/configure-locations-wms-enabled-warehouse.md#define-location-blocking-causes). |
| <p>**Module:** Warehouse management</p><p>**Enhancement:** *Minimum amount of characters required for license plate numbers*</p><p>**Feature management name:** *(None)*</p> | <p></p><p>Lets you specify a minimum amount of characters required for license plate numbers, which prevents the system from creating license plate IDs that are too short. This can help prevent workers from making the mistake of scanning a location barcode instead of a license plate barcode.</p><p>To make this setting, go to the **Warehouse management parameters** page, open the **General** tab, expand the **License plates** FastTab, and set **Restrict license plate by** equal to *Minimum length*. Then specify a number in the **Minimum amount of characters required for license plate numbers** field.</p> |
| <p>**Module:** Warehouse management</p><p>**Enhancement:** *Work transaction date policy*</p><p>**Feature management name:** *(None)*</p> | <p>Allow warehouse work transaction dates to be adjusted to a time zone that's different from the one used by the system. You can configure the system to change the transaction dates according to the time zones of the company, the site, or each user's preferred time zone.</p><p>Learn more in [Define general warehouse work policies](../warehousing/warehouse-configuration.md#warehouse-management-parameters-work). |
| <p>**Module:** Warehouse management</p><p>**Feature management name:** *Advanced address maintenance*</p> | Lets you delete unused historical addresses on the **Manage addresses** page. The address type selection is shown in a tab-based format instead of a dropdown list. |
| <p>**Module:** Warehouse management</p><p>**Feature management name:** *(Preview) Context-aware worker summary screen in WMA*</p> | The AI-enhanced warehouse home screen in the Warehouse management mobile app uses advanced generative AI technology to provide warehouse workers with a personalized dashboard at the beginning of their shifts. |

## Preview features that are now generally available

The following table lists features that were introduced as public preview features in a previous version and became generally available in version 10.0.40. As with other new features, most of these features are turned off by default, so you must turn them on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) if you want to use them.

| Module | Feature name | More information |
|---|---|---|
| Warehouse management | *Warehouse management only mode* | [Warehouse management only mode overview](../warehousing/wms-only-mode-overview.md) |

## Related information

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.40 includes platform updates. Learn more in [Platform updates for version 10.0.40 of Finance and Operations apps (June 2024)](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-40.md).

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.40, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=932660).

### Dynamics 365: 2024 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2024 release wave 1 plan](/dynamics365/release-plan/2024wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
