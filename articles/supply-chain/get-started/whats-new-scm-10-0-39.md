---
title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.39 (April 2024)
description: Learn about features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.39 with a table outlining feature areas. 
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

# What's new or changed in Dynamics 365 Supply Chain Management 10.0.39 (April 2024)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management version 10.0.39. This version has a build number of 10.0.1860 and is available on the following schedule:

- **Preview of release:** January 2024
- **General availability of release (self-update):** March 2024
- **General availability of release (auto-update):** April 2024

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Copilot and AI innovation | [Enable efficient, accurate demand planning with Copilot](/dynamics365/release-plan/2024wave1/finance-supply-chain/dynamics365-supply-chain-management/enable-more-efficient-accurate-demand-planning-using-copilot) | [Analyze demand plans with Copilot (preview)](../demand-planning/demand-planning-copilot.md) | Enabled by default |
| Copilot and AI innovation | [Generate context-aware insights for warehouse workers](/dynamics365/release-plan/2024wave1/finance-supply-chain/dynamics365-supply-chain-management/generate-context-aware-insights-warehouse-workers) | [Workload insights with Copilot in the Warehouse Management mobile app](../warehousing/warehouse-management-mobile-app-insights.md) | <p>Feature management:<br>*Context-aware worker summary screen in WMA*</p><p>Requires Warehouse Management mobile app version 2.3.2.0 or later.</p><p>Requires Supply Chain Management version 10.0.39 with proactive quality update 3 (PQU-3) or later.</p> |
| Copilot and AI innovation | AI summaries with Copilot | [AI summaries with Copilot](copilot-summaries-overview.md) | <p>Feature management:</p><ul><li>*Product summary when hovering on item*</li><li>*Product details summary*</li><li>*Purchase order summary*</li><li>*Sales order summary*</li><li>*Vendor summary*</li></ul><p>Requires Supply Chain Management version 10.0.39 with PQU-3 or later.</p> |
| Inventory and logistics | [Enable prospects in prospect-to-cash with dual-write](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/enable-prospects-prospect-to-cash-dual-write) | [Work with prospects in prospect-to-cash with Dynamics 365 Sales](../../fin-ops-core/fin-ops/data-entities/prospects-in-prospect-to-cash-use.md) | Feature management:<br>*Enable prospects in Sales quotation lifecycle with Dynamics 365 Sales* |
| Inventory and logistics | [Offset Inventory Visibility adjustments](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/offset-inventory-visibility-adjustments) | [Inventory Visibility adjustment offset](../inventory/inventory-visibility-adjustment-offset.md) | Enabled by default |
| Planning | Item substitution for formulas in Planning Optimization | [Item substitution for formulas and bills of materials](../master-planning/item-substitution.md) | Feature management:<br>*Item substitution (Plan group) support for Planning Optimization* |
| Warehouse management | [Optimize the customer returns process](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/optimize-customer-returns-process) | [Receive unannounced sales returns](../warehousing/sales-returns-unannounced.md) | Enabled by default |
| Warehouse management | Username/password and single-sign-on authentication for mobile devices | [User-based authentication](../warehousing/warehouse-app-authenticate-user-based.md) | Enabled by default |

## <a name="enhancements"></a>Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they're only enhancements, they aren't listed in the [release plan](/dynamics365/release-plan/2024wave1/finance-supply-chain/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

Some of these features aren't visible on your system until you turn them on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) using the name listed here for the *Feature management name* (additional configuration may also be needed). Features that don't show a feature management name are visible by default as of this version of Supply Chain Management, but typically add a new configuration option that you need to set to use the new functionality.

| Feature enhancement | Description |
|---|---|
|<p>**Module:** Warehouse management</p><p>**Enhancement:** *Consolidate including incoming work* location directive action strategy</p><p>**Feature management name:** *(None)*</p> | <p>Adds a new [location directive action](../warehousing/create-location-directive.md#location-directive-actions-fasttab) strategy called *Consolidate including incoming work*. It works like the existing *Consolidate* strategy, except it also considers locations where items on incoming put-work lines aren't already available. This is beneficial when receiving multiple license plates with the same item and the items should be moved to the same location. This can be useful, for example, when receiving based on advance shipping notices (ASNs).</p><p>Learn more in [Work with location directives](../warehousing/create-location-directive.md). |
|<p>**Module:** Warehouse management</p><p>**Enhancement:** Full license plate movement policy</p><p>**Feature management name:** *(None)*</p> | <p>Lets workers move license plates more quickly in the warehouse by reducing the number of scans needed when using a *Movement* or *Movement by template* mobile device menu item.</p><p>Learn more in [Set up a mobile device menu item for moving items in the warehouse](../warehousing/mobile-device-movement-menu.md) and [Set up a mobile device menu item for moving items by template](../warehousing/mobile-device-move-by-template-menu.md). |
|<p>**Module:** Warehouse management</p><p>**Enhancement:** Split transfer order registration and receiving when using the Warehouse Management mobile app</p><p>**Feature management name:** *(None)*</p> | <p>Makes it possible to split the registration and cost-update processes for transfer orders, which lets receiving clerks use the Warehouse Management mobile app to update a transfer order receipt without waiting for any financial background processing, regardless of the receiving flow.  Previously, it was only possible to split registrations and cost updates during license plate receiving.</p><p>To enable this capability, go to the **Warehouse management parameters** page, open the **General** tab, expand the **Receiving** FastTab and set **Transfer order receiving process** to *Split the registration and receiving for all flows*.</p> |
|<p>**Module:** Warehouse management</p><p>**Feature management name:** *Inventory transaction details page's performance improvement.*</p> | <p>Improves the performance of the **Inventory transactions details** page. Users can now set default filters, so that the page shows only frequently checked inventory transactions. In addition, the page shows only inventory-related fields.</p><p>To access the **Inventory transaction details** page, go to **Inventory management** \> **Inquiries and reports** \> **Transactions**.</p> |
|<p>**Module:** Inventory and warehouse management</p><p>**Feature management name:** *Inventory Visibility integration with ATP*</p>| Enables the system to send the on-hand change schedule to Inventory Visibility to support available-to-promise (ATP) calculations. |
|<p>**Module:** Master planning</p><p>**Feature management name:** *Actions based on requested date for Planning Optimization*</p>| Introduces a parameter that lets you specify what date action messages are based on. When action messages are based on the required date, changes are suggested only if they're feasible. This behavior matches the previous behavior. When action messages are based on the requested date, they can give a better idea of how late orders are. However, the suggestions might not be possible. For example, there might be a suggestion to advance a number of days that's impossible according to lead times, or there might be a suggestion to create an order in the past. |
|<p>**Module:** Master planning</p><p>**Feature management name:** *Allows to create Planned order setting Purchase quantity instead of Requirement quantity*</p>| Makes it possible to create planned orders that set the purchase quantity instead of the requirement quantity. |
|<p>**Module:** Master planning</p><p>**Feature management name:** *Enable the calculation of CTP for Planning Optimization even when plan run ends with errors*</p>| Makes it possible to calculate capable-to-promise (CTP) confirmed dates for sales order lines even when the Planning Optimization run ended with errors. The confirmed dates are calculated for sales order lines that didn't have any errors. To enable or disable this behavior, use the **Calculate CTP for Planning Optimization even with errors** setting for the master plan. |
|<p>**Module:** Master planning</p><p>**Feature management name:** *Exclude demand forecasts for a certain time period for Planning Optimization*</p>| Makes it possible to ignore the forecasted demand for a specified period. This capability is useful if you don't want to supply for forecasts during the upcoming period. Any forecasted demand that occurs after the number of days that you specify is ignored and therefore isn't supplied for. |
|<p>**Module:** Master planning</p><p>**Feature management name:** *Min/Max coverage code rounding for Planning Optimization*</p>| Adds a setting that lets you control how values are rounded when you use multiples in a min/max coverage code. Round down to ensure that the quantities always stay within the maximum limit. This option is useful if the maximum represents the physical space of your warehouse. Round up to ensure that the maximum quantity is always fulfilled. This option is useful if the maximum represents a calculated value for your company to fulfill demand. |
|<p>**Module:** Master planning</p><p>**Feature management name:** *Recalculation of finite material date optionally for Planning Optimization*</p>| Adds a setting that lets you specify whether finite material availability dates should be recalculated when you reschedule production orders that have finite materials. We recommend that you *don't* recalculate for master plans that you've recently run, because the result will be faster rescheduling of multiple orders. Without this feature, the date is always recalculated. |
|<p>**Module:** Master planning</p><p>**Feature management name:** *Round down advance action days*</p>| Adds a new option for coverage groups that lets you round down advance action days. For example, the difference between the supply requirement date/time and the receipt requirement date/time is one day and four hours. If the new option is turned on, the result of the calculation is one advance action day. If the option is turned off, the result is two advance action days. This option is especially useful for preventing master planning from suggesting an advance of one day whenever the supply and the demand are on the same day. |
|<p>**Module:** Master planning</p><p>**Feature management name:** *Sort on requested date in Net requirements form*</p>| Adds an option that lets you sort by using the **Requested date** field instead of the **Requirement date** field on the **Net requirements** page. |
|<p>**Module:** Product information management</p><p>**Feature management name:** *Allow hazardous material divisions with same division codes in different material classes*</p>| Lets users create hazardous material divisions that have the same division code in different hazardous material classes. The feature creates a new data table to enable divisions that have the same code and moves data to this new table. |
|<p>**Module:** Production control</p><p>**Feature management name:** *Default order settings for Change production order BOM item*</p>| Updates the *Change BOM item* feature so that your default order settings are used to set the from-item and to-item. |
|<p>**Module:** Sales and marketing</p><p>**Feature management name:** *Faster vendor search*</p>| Improves the performance of the **Vendor search** dialog box by implementing an improved data model. |
|<p>**Module:** Sales and marketing</p><p>**Feature management name:** *Replace alternative item defaults on sales lines*</p>| Adds a new parameter, **Replace alternative item defaults on sales lines**, to the **General** tab of the **Accounts Receivable parameters** page. When this parameter is set to *Yes*, and alternative items must always be used, all item-dependent information (such as financial dimensions and units of measure) from the alternative item replace the original item information on the sales order line. When the parameter is set to *No*, all the information from the original item remains on the sales order line, and no replacements are made. When you first enable this feature, the parameter is set to *Yes* by default. Therefore, the system behaves just as it does without this feature. |
|<p>**Module:** Sales and marketing</p><p>**Feature management name:** *Sales referenced data export policy*</p>| Adds the following parameters to the **General** tab of the **Accounts receivable parameters** page: **Skip referenced data during change tracking** and **Skip sales quotation referenced data during change tracking**. When these two parameters are enabled, changes to referenced data doesn't cause sales orders, sales order lines, sales quotations, and/or sales quotation lines to be included in the next incremental export. By turning off these parameters, you can help incremental exports run more quickly. |

## New and updated documentation resources

We have recently added or significantly updated the following help articles. These articles aren't necessarily related to the new features that were added for this release, as listed in the previous sections. However, they might help you get more out of existing features.

| Feature area | New or updated articles |
|---|---|
| Inventory management | [Inventory Visibility diagnostic tool](../inventory/inventory-visibility-diagnostic-tool.md) |
| Inventory management | [Use the Inventory Visibility app UI version 2](../inventory/inventory-visibility-power-platform.md) – Many other articles about the Inventory Visibility Add-in have also been updated to reflect the new UI for the Inventory Visibility app in Power Apps. |
| Master planning | [Safety stock pegging options](../master-planning/safety-stock-pegging.md) |
| Sales and marketing | [Calculate sales totals when prices include sales tax](../sales-marketing/sales-tax-calculation.md) |
| Warehouse management | [Automatic rewaving of nonallocated shipment lines](../warehousing/auto-rewave-shipments.md) |
| Warehouse management | [Set up a mobile device menu item for moving items in the warehouse](../warehousing/mobile-device-movement-menu.md) |
| Warehouse management | [Set up a mobile device menu item for moving items by template](../warehousing/mobile-device-move-by-template-menu.md) |
| Warehouse management | [Warehouse management only mode overview (preview)](../warehousing/wms-only-mode-overview.md) – The preview functionality that's described in this article and its related articles is frequently updated. The documentation is regularly updated to match the changes that are released with each version of Supply Chain Management. |

## Related information

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.39 includes platform updates. Learn more in [Platform updates for version 10.0.39 of Finance and Operations apps (April 2024)](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-39.md).

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.39, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=886261).

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
