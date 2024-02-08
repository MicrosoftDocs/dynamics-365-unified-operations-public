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

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management preview version 10.0.39. This version has a build number of 10.0.1860 and is available on the following schedule:

- **Preview of release:** January 2024
- **General availability of release (self-update):** March 2024
- **General availability of release (auto-update):** April 2024

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Inventory and logistics | [Offset Inventory Visibility adjustments](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/offset-inventory-visibility-adjustments) | *Coming soon* | Enabled by default |
| Warehouse management | Username/password and single-sign-on authentication for mobile devices | [User-based authentication](../warehousing/warehouse-app-authenticate-user-based.md) | Enabled by default |

## <a name="enhancements"></a>Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they're only enhancements, they aren't listed in the [release plan](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

Some of these features aren't visible on your system until you turn them on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) using the name listed for the *feature management name*. Features that don't show a feature management name are visible by default as of this version of Supply Chain Management, but typically need to be turned on using a setting on the relevant parameters page (see the *Description* column for details).

| Feature enhancement | Description |
|---|---|
|<p>**Module:** Inventory and warehouse management</p><p>**Enhancement name:** Consolidate including incoming work location directive action strategy</p><p>**Feature management name:** *(None)*</p> | A new [location directive action](../warehousing/create-location-directive#location-directive-actions-fasttab)  strategy working like the *Consolidate strategy*, but it also considers locations where items on incoming put-work lines aren't already available. This is beneficial when receiving multiple license plates with the same item and the items should be moved to the same location. A typical example could occur when receiving based on advance shipping notices (ASNs). |
|<p>**Module:** Inventory and warehouse management</p><p>**Enhancement name:** Full license plate movement policy</p><p>**Feature management name:** *(None)*</p> | This improvement helps workers to move license plates more quickly in the warehouse by speeding up the data capture process in the [Warehouse management mobile app movement process](../warehousing/mobile-device-movement-menu.md). |
|<p>**Module:** Inventory and warehouse management</p><p>**Enhancement name:** Split of transfer order registration and receiving when using the Warehouse management mobile app</p><p>**Feature management name:** *(None)*</p> | A new feature has been added to the Warehouse management parameter *Transfer order receiving process*. Previously, only license plate receiving processing could be used to separate the registration and cost update process. Now, you can also select *Split the registration and receiving for all flows*. This means, regardless of the receiving flows, the warehouse receiving clerks can update a transfer order receipt without waiting for any financial background processing. |
|<p>**Module:** Inventory and warehouse management</p><p>**Feature management name:** *Inventory transaction details page's performance improvement.*</p> | Improves the performance of the **Inventory transactions details** page. Users can now set default filters, so that the page shows only frequently checked inventory transactions. In addition, the page shows only inventory-related fields. To access the **Inventory transaction details** page, go to **Inventory management** \> **Inquiries and reports** \> **Transactions**. |
|<p>**Module:** Inventory and warehouse management</p><p>**Feature management name:** *Inventory Visibility integration with ATP*</p>| Enables the system to send the on-hand change schedule to Inventory Visibility to support available-to-promise (ATP) calculations. |
|<p>**Module:** Master planning</p><p>**Feature management name:** *Actions based on requested date for Planning Optimization*</p>| Introduces a parameter that lets you specify what date action messages are based on. When action messages are based on the required date, changes are suggested only if they're feasible. This behavior matches the previous behavior. When action messages are based on the requested date, they can give a better idea of how late orders are. However, the suggestions might not be possible. For example, there might be a suggestion to advance a number of days that's impossible according to lead times, or there might be a suggestion to create an order in the past. |
|<p>**Module:** Master planning</p><p>**Feature management name:** *Allows to create Planned order setting Purchase quantity instead of Requirement quantity*</p>| Makes it possible to create planned orders that set the purchase quantity instead of the requirement quantity. |
|<p>**Module:** Master planning</p><p>**Feature management name:** *Enable the calculation of CTP for Planning Optimization even when plan run ends with errors*</p>| Makes it possible to calculate capable-to-promise (CTP) confirmed dates for sales order lines even when the Planning Optimization run ended with errors. The confirmed dates are calculated for sales order lines that didn't have any errors. To enable or disable this behavior, use the **Calculate CTP for Planning Optimization even with errors** setting for the master plan. |
|<p>**Module:** Master planning</p><p>**Feature management name:** *Exclude demand forecasts for a certain time period for Planning Optimization*</p>| Makes it possible to ignore the forecasted demand for a specified period. This capability is useful if you don't want to supply for forecasts during the upcoming period. Any forecasted demand that occurs after the number of days that you specify is ignored and therefore isn't supplied for. |
|<p>**Module:** Master planning</p><p>**Feature management name:** *Min/Max coverage code rounding for Planning Optimization*</p>| Adds a setting that lets you control how values are rounded when you use multiples in a min/max coverage code. Round down to ensure that the quantities always stay within the maximum limit. This option is useful if the maximum represents the physical space of your warehouse. Round up to ensure that the maximum quantity is always fulfilled. This option is useful if the maximum represents a calculated value for your company to fulfill demand. |
|<p>**Module:** Master planning</p><p>**Feature management name:** *Recalculation of finite material date optionally for Planning Optimization*</p>| Adds a setting that lets you specify whether finite material availability dates should be recalculated when you reschedule production orders that have finite materials. We recommend that you **don't** recalculate for master plans that you've recently run, because the result will be faster rescheduling of multiple orders. Without this feature, the date is always recalculated. |
|<p>**Module:** Master planning</p><p>**Feature management name:** *Round down advance action days*</p>| Adds a new option for coverage groups that lets you round down advance action days. For example, the difference between the supply requirement date/time and the receipt requirement date/time is one day and four hours. If the new option is turned on, the result of the calculation is one advance action day. If the option is turned off, the result is two advance action days. This option is especially useful for preventing master planning from suggesting an advance of one day whenever the supply and the demand are on the same day. |
|<p>**Module:** Master planning</p><p>**Feature management name:** *Sort on requested date in Net requirements form*</p>| Adds an option that lets you sort by using the **Requested date** field instead of the **Requirement date** field on the **Net requirements** page. |
|<p>**Module:** Product information management</p><p>**Feature management name:** *Allow hazardous material divisions with same division codes in different material classes*</p>| Lets users create hazardous material divisions that have the same division code in different hazardous material classes. The feature creates a new data table to enable divisions that have the same code and moves data to this new table. |
|<p>**Module:** Production control</p><p>**Feature management name:** *Default order settings for Change production order BOM item*</p>| Updates the *Change BOM item* feature so that your default order settings are used to set the from-item and to-item. |
|<p>**Module:** Sales and marketing</p><p>**Feature management name:** *Enable prospects in Sales quotation lifecycle with Dynamics 365 Sales*</p>| Enables the integration of prospects between Dynamics 365 Sales and Supply Chain Management over dual-write. Prospects in Supply Chain Management integrate with account type *Prospect* in Dynamics 365 Sales. The lifecycle of a prospect from creation to converting into a customer is supported from both Dynamics 365 Sales and Supply Chain Management and is seamlessly integrated into the quotation winning process. With this feature, it's possible to use the prospect on a quotation in Supply Chain Management and as a potential customer in Dynamics 365 Sales. This feature adds a parameter to the **Accounts receivable parameters** page, which lets you turn the functionality on or off.<br><br>**Important**: This feature is a component of the upcoming [Enable prospects in prospect-to-cash with dual-write](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/enable-prospects-prospect-to-cash-dual-write) functionality. Some of the components required to fully support this functionality won't be available until a future release of dual-write becomes available. Until then, this feature will have no effect, so we recommend against enabling it for now. |
|<p>**Module:** Sales and marketing</p><p>**Feature management name:** *Faster vendor search*</p>| Improves the performance of the **Vendor search** dialog box by implementing an improved data model. |
|<p>**Module:** Sales and marketing</p><p>**Feature management name:** *Replace alternative item defaults on sales lines*</p>| Adds a new parameter, **Replace alternative item defaults on sales lines**, to the **General** tab of the **Accounts Receivable parameters** page. When this parameter is set to *Yes*, and alternative items must always be used, all item-dependent information (such as financial dimensions and units of measure) from the alternative item replace the original item information on the sales order line. When the parameter is set to *No*, all the information from the original item remains on the sales order line, and no replacements are made. When you first enable this feature, the parameter is set to *Yes* by default. Therefore, the system behaves just as it does without this feature. |
|<p>**Module:** Sales and marketing</p><p>**Feature management name:** *Sales referenced data export policy*</p>| Adds the following parameters to the **General** tab of the **Accounts receivable parameters** page: **Skip referenced data during change tracking** and **Skip sales quotation referenced data during change tracking**. When these two parameters are enabled, changes to referenced data doesn't cause sales orders, sales order lines, sales quotations, and/or sales quotation lines to be included in the next incremental export. By turning off these parameters, you can help incremental exports run more quickly. |

## New and updated documentation resources

We have recently added or significantly updated the following help articles. These articles aren't necessarily related to the new features that were added for this release, as listed in the previous sections. However, they might help you get more out of existing features.

| Feature area | New or updated articles |
|---|---|
| Inventory management | [Inventory Visibility diagnostic tool](../inventory/inventory-visibility-diagnostic-tool.md) |
| Master planning | [Safety stock pegging options](../master-planning/safety-stock-pegging.md) |
| Sales and marketing | [Calculate sales totals when prices include sales tax](../sales-marketing/sales-tax-calculation.md) |
| Warehouse management | [Set up a mobile device menu item for moving items in the warehouse](../warehousing/mobile-device-movement-menu.md) |
| Warehouse management | [Warehouse management only mode overview (preview)](../warehousing/wms-only-mode-overview.md) – The preview functionality that's described in this article and its related articles is frequently updated. The documentation is regularly updated to match the changes that are released with each version of Supply Chain Management. |

## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.39 includes platform updates. To learn more, see [Platform updates for version 10.0.39 of Finance and Operations apps (April 2024)](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-39.md).<!--KFM: Confirm link -->

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.39, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=886261).

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
