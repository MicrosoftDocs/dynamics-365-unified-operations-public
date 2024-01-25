---
title: Preview of Dynamics 365 Supply Chain Management 10.0.39 (April 2024)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.39. 
author: kamaybac
ms.author: kamaybac
ms.reviewer: kamaybac
ms.search.form:
ms.topic: conceptual
ms.date: 01/29/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Preview of Dynamics 365 Supply Chain Management 10.0.39 (April 2024)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management preview version 10.0.39. This version has a build number of XXXX <!--KFM: Get build number --> and is available on the following schedule:

- **Preview of release:** January 2024
- **General availability of release (self-update):** March 2024
- **General availability of release (auto-update):** April 2024

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Inventory and logistics | [Offset Inventory Visibility adjustments](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/offset-inventory-visibility-adjustments) | *Coming soon*  | Enabled by default |
| Inventory and logistics | [Enable prospects in prospect-to-cash with dual-write](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/enable-prospects-prospect-to-cash-dual-write) | *Coming soon*  | Feature management:<br>*Enable prospects in Sales quotation lifecycle with Dynamics 365 Sales*  |

## <a name="enhancements"></a>Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they're only enhancements, they aren't listed in the [release plan](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

If you want to turn any of these features on or off, you must do so in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Module | Feature name in feature management | More information |
|---|---|---|
| Inventory and warehouse management | Inventory transaction details page's performance improvement. | Improves performance of the **Inventory transactions details** page. It allows users to set default filters to show only frequently checked inventory transactions. It also shows only inventory related fields. To access the **Inventory transaction details** page, go to **Inventory management** \> **Inquiries and reports** \> **Transactions**. |
| Inventory and warehouse management | Inventory Visibility integration with ATP | Makes it possible for the system to send the on-hand change schedule to Inventory Visibility to support available-to-promise (ATP) calculations. |
| Master planning | @MPS:IgnoreSpecificDemandTypesFeatureNameReleased. <!--KFM: What?! --> | Lets you select which transaction types should be considered on a master plan when running Planning Optimization. |
| Master planning | Actions based on requested date for Planning Optimization | Introduces a parameter that allows you to choose whether action messages should be based on the required date (as previously, which only suggests changes based on when is feasible) or on the requested date (action messages can give a better idea of how late orders are, but the suggestions may not be possible, such as advancing a number of days that isn't possible according to lead times, or suggesting to order in the past). |
| Master planning | Allows to create Planned order setting Purchase quantity instead of Requirement quantity | Makes it possible to create planned orders that set the purchase quantity rather than the requirement quantity. |
| Master planning | Enable the calculation of CTP for Planning Optimization even when plan run ends with errors | Allows capable-to-promise (CTP) confirmed dates to be calculated for sales order lines even when the Planning Optimization run ended with errors. The confirmed dates are calculated for sales order lines that didn't have any errors. Use the **Calculate CTP for Planning Optimization even with errors** setting for the master plan to enable or disable this behavior. |
| Master planning | Exclude demand forecasts for a certain time period for Planning Optimization | Makes it possible to ignore the forecasted demand for a certain time period. This is useful if you don't want to supply for forecasts during the upcoming period. Any forecasted demand occurring after the number of days you specify will be ignored and therefore not supplied for. |
| Master planning | Min/Max coverage code rounding for Planning Optimization | Adds a setting that lets you control how to round values when you using multiples in a min/max coverage code. Round down for the quantities to always stay within the maximum limit, which is useful if the maximum represents the physical space of your warehouse. Round up to make sure that the maximum quantity is always fulfilled, which is useful if the maximum represents a calculated value for your company to fulfill demand. |
| Master planning | Recalculation of finite material date optionally for Planning Optimization | Adds a setting that lets you to choose whether finite material availability dates should be recalculated when you are rescheduling production orders with finite materials. We recommend not recalculating for master plans that you have run recently because this will result in a faster rescheduling of multiple orders. Without this feature, the date is always recalculated. |
| Master planning | Round down advance action days | Adds a new option on coverage groups for rounding down advance action days. For example, if the difference between the supply requirement date/time and the receipt requirement date/time is one day and four hours, this will result in one advance action day when the option is on, and when the option is off it will result in two advance action days. This is especially useful for preventing master planning from suggesting to advance one day whenever the supply and the demand are on the same day. |
| Master planning | Sort on requested date in Net requirements form | Adds the option to sort using the **Requested date** instead of the **Requirement date** on the **Net requirements** page. |
| Product information management | Allow hazardous material divisions with same division codes in different material classes | Allows users to create hazardous material divisions with the same division code in different hazardous material classes. The feature creates a new data table to allow divisions with the same code and moves data to this new table. |
| Production control | Default order settings for Change production order BOM item | Updates the *Change BOM item* feature so that your default order settings will be used to set the from-item and to-item. |
| Sales and marketing | Faster vendor search | Improves the performance of the **Vendor search** dialog by implementing an improved data model. |
| Sales and marketing | Replace alternative item defaults on sales lines | Adds a parameter called **Replace alternative item defaults on sales lines** to the **General** tab of the **Accounts Receivable parameters** page. When this parameter is set to *Yes*, and alternative items must always be used, all item-dependent information (such as financial dimensions and units of measure) from the alternative item will replace the original item information on the sales order line. When set to *No*, all the information from the original item will remain on the sales order line and no replacements will be made. When you first enable this feature, the parameter defaults to *Yes*, which matches the way the system behaves without this feature. |
| Sales and marketing | Sales referenced data export policy | Adds following parameters to the **General** tab of the **Accounts receivable parameters** page: **Skip referenced data during change tracking** and **Skip sales quotation referenced data during change tracking**. When these two parameters are enabled, changes to referenced data won't cause sales orders, sales order lines, sales quotations, and/or sales quotation lines to be included in the next incremental export. Turning these options off can make incremental exports run quicker. |

## New and updated documentation resources

We have recently added or significantly updated the following help articles. These articles aren't necessarily related to the new features that were added for this release, as listed in the previous sections. However, they might help you get more out of existing features.

| Feature area | New or updated articles |
|---|---|
| Inventory management | [Inventory Visibility diagnostic tool](../inventory/inventory-visibility-diagnostic-tool.md) |
| Master planning | [Safety stock pegging options](../master-planning/safety-stock-pegging.md) |
| Sales and marketing | [Calculate sales totals when prices include sales tax](../sales-marketing/sales-tax-calculation.md) |
| Warehouse management | [Set up a mobile device menu item for moving items in the warehouse](../warehousing/mobile-device-movement-menu.md) |
| Warehouse management | [Warehouse management only mode overview (preview)](../warehousing/wms-only-mode-overview.md) – This preview functionality is receiving regular updates throughout the preview period, and this article and its related articles receive multiple updates to match the changes released with each version. |

## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.39 includes platform updates. To learn more, see [Platform updates for version 10.0.39 of Finance and Operations apps (April 2024)](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-39.md).<!--KFM: Confirm link -->

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.38, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=XXXX).<!--KFM: Get link -->

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