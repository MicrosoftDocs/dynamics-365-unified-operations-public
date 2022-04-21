---
title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.23 (January 2022)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.23. 
author: kamaybac
ms.date: 10/15/2021
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this topic to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: kamaybac
ms.search.validFrom: 2021-10-15
ms.dyn365.ops.version: 10.0.23
---

# What's new or changed in Dynamics 365 Supply Chain Management 10.0.23 (January 2022)

[!include [banner](../includes/banner.md)]

This topic lists features that are either new or changed in the Microsoft Dynamics 365 Supply Chain Management version 10.0.23. This version has a build number of 10.0.1037 and is available as follows:

- **Preview of release:** October 2021
- **General availability of release (self-update):** December 2021
- **General availability of release (auto-update):** January 2022

## Features included in this release

The following table lists the features that are included in this release. The *Feature* column provides links to the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-supply-chain-management/planned-features), where you can see the official release dates for each feature. The *More information* column provides more details and/or links to related documentation. To determine how to turn on a feature, see the *Enabled by* column. For more information about how to use feature management, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). We might update this topic to include features that made it into the build after this topic was initially published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Global address book | Define a default state/province for each country/region in address setup | You can now define a default state/province for each country/region in the address setup for the global address book. When a default state/province is set, it will be the default value entered in state/province fields when you create a new county or city record for that country/region. See also [Address setup](../../fin-ops-core/fin-ops/organization-administration/global-address-book-address-setup.md?toc=/dynamics365/supply-chain/toc.json) | Enabled by default. |
| Inventory&nbsp;and&nbsp;logistics | [Pause tasks in the Warehouse Management mobile app](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-supply-chain-management/park-tasks-warehouse-management-mobile-app) | [Configure detours for steps in mobile device menu items](../warehousing/warehouse-app-detours.md) | Feature management (*Warehouse management app detours*) |
| Inventory&nbsp;and&nbsp;logistics | [Warehouse app promoted fields](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-supply-chain-management/warehouse-management-mobile-app-step-instructions) | [Configure promoted fields for steps in the mobile device](../warehousing/warehouse-app-promoted-fields.md)| Feature management (*Warehouse app promoted fields*) |
| Manufacturing | [Manufacturing execution systems integration](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-supply-chain-management/manufacturing-execution-systems-integration) | [Integrate with third-party manufacturing execution systems](../production-control/mes-integration.md) | Feature management (*Manufacturing execution system integration*) |
| Manufacturing | [Report on co- and by-products from the production floor execution interface](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-supply-chain-management/enhanced-production-floor-execution-interface-process-manufacturing) | [How workers use the production floor execution interface](../production-control/production-floor-execution-use.md) | Feature management (*Report on co- and by-products from the production floor execution interface*) |
| Planning | [Planning Optimization support for priority-based planning](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-supply-chain-management/planning-optimization-support-priority-based-planning) | [Priority-based planning](../master-planning/planning-optimization/priority-based-planning.md) | Feature management (*Priority driven MRP support for Planning Optimization*) |

## Feature enhancements included in this release

The following table lists the feature enhancements that are new for this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

If you want to turn any of these features on or off, you must do so in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md), where they are listed using the names shown in the *Feature name in feature management* column of the following table.

| Module | Feature name in feature management | More information |
|---|---|---|
| Asset management | Offset accounts for expenses in work order journals | This feature lets you specify an offset account for each expense listed in a work order journal. You might typically associate a vendor account with each expense, but other account types are also supported. It adds two new columns (**Offset account type** and **Offset account**) to the **Expense** FastTab on the **Work order journal** page.|
| Cost management | Create related vouchers for standard cost rounding revaluations | <p>When an inventory financial posting (such as a sales order invoice or inventory transaction) is made, this feature causes the system to create a separate voucher for any related standard cost rounding revaluations and attach it to the financial posting voucher as a related voucher.</p><p>Without this feature, the system records standard cost rounding revaluations on the same voucher posting. That behavior can sometimes cause conflicting date information, because the revaluations use the session or system date, whereas financial postings use the posting date.</p> |
| Inventory and warehouse management | \[Russia\] Post storno financial inventory transactions according to the correction flag in the financial voucher for sales orders | This feature impacts the credit note corrections functionality for Russia. It enables posting of inventory transactions for sales invoices in accordance with the correction option in the general ledger. When this feature is enabled, there are no more discrepancies between **Correction** flag on financial voucher of inventory transaction and **Storno** flag on inventory transactions. |
| Inventory and warehouse management | (Russia) Run Inventory balance turnover report calculation in batch | For Russian localizations of Supply Chain Management, this feature provides the possibility to run the *Inventory balance turnover* report in batch, to store it, and to view the reports generated earlier. |
| Inventory and warehouse management | (Russia) Use translations to local language in country or region-specific primary forms in Inventory management | For Russian localizations of Supply Chain Management, this feature enables the use of Russian translations for product/item names and units of measure in the following Russian-specific inventory printouts: Counting list (INV-3), Counting list (INV-5), and Counting list (INV-6). |
| Master planning | Azure Machine Learning Service for demand forecasting | This feature enables the Azure Machine Learning Service to generate demand forecasts based on historical data. For more information, see [Demand forecasting setup](../master-planning/demand-forecasting-setup.md). |
| Procurement and sourcing | Clean up purchase-order update history | This feature lets you clean up temporary historical records related to purchase-order updates. It adds a new button called **Clean up purchase update history** to the Action Pane on the **All purchase orders** page. This feature is enabled by default. |
| Production control | (Preview) Auto-picking of warehouse enabled materials for auto-posted picking lists | This feature lets you auto-pick and resolve inventory dimensions for auto-posted, derived, and backflushed picking list journals. |
| Production control | Validate expiration of raw materials against planned consumption date | This feature changes how batch expiration dates are validated when reserving a batch of raw material to be used during production. When this feature is enabled, the batch expiration date is validated against the planned consumption date (the raw material date), as established on the production BOM line or batch order formula line. When this feature is disabled, the batch expiration date is validated against the planned delivery date of the production or batch order (as previously). |
| Sales and marketing | Clean up sales update history based on age | This feature lets you set the maximum age of records to keep when running the **Sales update history cleanup** periodic task. Older records will be deleted. This is useful for when you set the task to run periodically because the age is always calculated relative to the date the task is run. Without this feature, you can only set a specific date for the oldest records to keep. For more information, see [Schedule sales history data cleanup](../sales-marketing/sales-update-history-cleanup-performance-improvements.md). |
| Sales and marketing | Improve "Top 100" customers report performance | This feature improves the performance of the **Top 100** customers report by always running the report across all customers (which is its intended use) rather than by allowing custom queries. When this feature is enabled, all **Records to include** settings are disabled in the **Top 100** report dialog. |
| Warehouse management | Scale unit support for release to warehouse of outbound orders | When this feature is enabled, outbound orders can be released from the hub directly to the scale unit where the orders will be fulfilled. |

## New and updated documentation resources

We have recently added or significantly updated the following help topics. These topics aren't necessarily related to the new features that were added for this release, as listed in the previous section. However, they might help you to get more out of existing features.

| Feature area | New or updated topics |
|---|---|
| Engineering change management | [Engineering attributes and engineering attribute search](../engineering-change-management/engineering-attributes-and-search.md) now describes how engineering attribute inheritance works. |
| Master planning | [Master planning with demand forecasts](../master-planning/planning-optimization/demand-forecast.md) and [Forecast reduction keys](../master-planning/reduction-keys.md) now provide more information about how to work with reduction keys. |
| Master planning | [Safety stock fulfillment for items](../master-planning/safety-stock-replenishment.md) now provides more information about using minimum/maximum keys. |
| Master planning | [Inventory forecasts](../master-planning/inventory-forecast.md) now provides more information about allocating forecasts. |
| Master planning | [Supply schedule](../master-planning/supply-schedule.md) |
| Warehouse management | [Global mobile device parameters](../warehousing/mobile-device-parameters.md) |
| Warehouse management | [Anchoring](../warehousing/anchoring.md) |
| Sales and marketing | Intercompany trade is now described in detail, starting with [Set up intercompany trade](../sales-marketing/intercompany-trade-set-up.md) and its related topics. |
| Inventory management | Inventory Visibility documentation has been expanded and updated, starting with [Inventory Visibility Add-in overview](../inventory/inventory-visibility.md) and its related topics. |

## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.23 includes platform updates. To learn more, see [Platform updates for version 10.0.23 of Finance and Operations apps (November 2021)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-23.md).

### Bug fixes

For information about the bug fixes included in each of the updates that are part of 10.0.23, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=627874&dbType=3&qc=9b7e01944eb8b43f9c3aac4be26811c27be205847d6d2a240424f34f7e722910).

### Dynamics 365 and industry clouds: 2021 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2021 release wave 2 plan](/dynamics365-release-plan/2021wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) topic describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
