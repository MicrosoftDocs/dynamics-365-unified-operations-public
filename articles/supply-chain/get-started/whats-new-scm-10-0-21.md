---
title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.21 (October 2021) 
description: This topic describes features that are either new or changed in Dynamics 365 Supply Chain Management 10.0.21. 
author: kamaybac
ms.date: 08/09/2021
ms.topic: article
# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User, Developer, IT Pro
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: kamaybac
ms.search.validFrom: 2021-08-02
ms.dyn365.ops.version: 10.0.21
---

# What's new or changed in Dynamics 365 Supply Chain Management 10.0.21 (October 2021)

[!include [banner](../includes/banner.md)]

This topic lists features that are either new or changed in the Microsoft Dynamics 365 Supply Chain Management version 10.0.21. This version has a build number of 10.0.960 and is available as follows:

- **Preview of release:** August 2021
- **General availability of release (self-update):** September 2021
- **General availability of release (auto-update):** October 2021

## Features included in this release

The following table lists the features included in this release. The *Feature* column provides links to the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-supply-chain-management/planned-features), where you can see the official release dates for each feature. The *More information* column provides more details and/or links to related documentation.

Most of these features must be enabled using [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) before you can use them.

| Feature area | Feature | More information |
|---|---|---|
| Inventory&nbsp;and&nbsp;logistics | [Global Inventory Accounting Add-in for Dynamics 365 Supply Chain Management](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/global-inventory-accounting-add-in-dynamics-365-supply-chain-management) | [Global Inventory Accounting home page](../global-inventory-accounting/global-inventory-accounting-home.md) |
| Inventory&nbsp;and&nbsp;logistics | [Post on-hand adjustments using codes connected to offset accounts](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-supply-chain-management/post-on-hand-adjustments-using-configurable-reason-codes-connected-offset-accounts) | [Reason codes for inventory counting](../warehousing/reason-codes-for-counting-journals.md) |
| Inventory&nbsp;and&nbsp;logistics | [Sales quotation referenced data export policy](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-supply-chain-management/sales-quotation-referenced-data-export-policy) | Choose whether changes to data referenced by quotations will cause those quotations (or lines) to be included in the next incremental export. Your incremental exports will run more quickly if you choose not to include such quotations or lines.<br><br>This feature adds a setting called **Skip sales quotation referenced data during change tracking** to the **Accounts receivable parameters** page. |
| Inventory&nbsp;and&nbsp;logistics | [Sealed bidding](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-supply-chain-management/sealed-bidding) | [Sealed bidding for RFQs](../procurement/sealed-bidding.md) |
| Inventory&nbsp;and&nbsp;logistics | [Scan barcodes in the warehouse using GS1 format standards](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-supply-chain-management/scan-barcodes-warehouse-using-gs1-format-standards) | [GS1 bar codes and QR codes](../warehousing/gs1-barcodes.md) |
| Inventory&nbsp;and&nbsp;logistics | [Soft reservation for the Inventory Visibility Add-in](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-supply-chain-management/soft-reservation-inventory-visibility-add-in) | [Inventory Visibility reservations](../inventory/inventory-visibility-reservations.md) |
| Inventory&nbsp;and&nbsp;logistics | [Deduction and catch-weight enhancements for Rebate management](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-supply-chain-management/deduction-catch-weight-enhancements-rebate-management) | [Manage deductions using the deduction workbench](../rebate-management/deduction-workbench.md )<br><br>[Process, review, and post rebates](../rebate-management/process-review-post.md)<br><br>[Rebate management deals](../rebate-management/rebate-management-deals.md) |
| Inventory&nbsp;and&nbsp;logistics | [Warehouse app step instructions](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-supply-chain-management/warehouse-management-mobile-app-step-instructions) | [Customize step titles and instructions for the Warehouse Management mobile app](../warehousing/mobile-app-titles-instructions.md) |
| Inventory&nbsp;and&nbsp;logistics | [Work breaks and tracking updates for Landed cost](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-supply-chain-management/work-breaks-tracking-updates-landed-cost) | [Update tracking for put away](../landed-cost/update-tracking-putaway.md )<br><br>[Goods-in-transit processing](../landed-cost/in-transit-processing.md) |
| Master planning | [Negative days for Planning Optimization](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/negative-days-support-planning-optimization) | [Delay tolerance (negative days)](../master-planning/planning-optimization/delay-tolerance.md) |

## Feature enhancements included in this release

The following table lists the feature enhancements included in this release. Each of these provides an incremental improvement to an existing feature. Because they are only enhancements, they are not listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted). If you want to use any of these features, you must explicitly enable them in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Module | Feature&nbsp;name&nbsp;in feature&nbsp;management | More information |
|---|---|---|
| Cost management | Inventory closing progress details | This preview feature enables a detailed view of inventory closing progress. |
| Procurement and sourcing | Prevent overconsumption of general budget reservations when multiple purchase requisitions are in workflow | This preview feature improves error checking when users submit and approve purchase requisitions that exceed the remaining balance of a general budget reservation line. This helps prevent overconsumption of general budget reservations when multiple purchase requisitions are in workflow. |
| Production control | Show full serial, batch, and license plate numbers in the production floor execution interface | This feature provides an improved experience for viewing lists of serial, batch, and license plate numbers in the production floor execution interface. The display changes from a card view with a limited number of characters to a list view that provides enough space to show the full values. The list also provides the ability to search for specific numbers. |
| Sales and marketing | Limit the number of sales orders that can be selected for posting | This feature lets you define the maximum number of sales orders that can be selected when posting confirmations, picking lists, packing slips, and invoices from the sales orders list page. It is enabled automatically. The feature adds a setting called **Max. number of sales orders for posting** to the **Accounts receivable parameters** page. The new setting defaults to a value of *100*. The feature helps improve the performance of the sales orders list page when a substantial number of sales orders are selected. It has no impact on the number of sales orders that can be processed by a periodic task. |
| Warehouse management | Decouple putaway work from ASNs | This feature is required to send and receive advance shipping notices (ASNs) when you are running a warehouse management workload on a scale unit (as part of a distributed hybrid topology). It adds a new database table dedicated to storing information about putaway work. Previously, this information was stored in tables also used for the ASNs. |
| Warehouse management | Slot mixed units | Allows the system to slot items into locations that include mixed units (such as both boxes and cases). For each slotting template line, this feature allows you to choose whether the line should slot items into mixed-unit or single-unit locations. |
| Warehouse management | Use faster API for containers closing/reopening on packing station | When this preview feature is enabled, inventory transactions related to containers are created using a new light-weight process that improves performance of closing or reopening containers during manual packing-station processing. |

## New and updated documentation resources

We have recently added or significantly updated the following help topics. They aren't necessarily related to the new features added for this release, as listed in the previous section, but they may help you to get more out of existing features.

| Feature area | New or updated topics |
|---|---|
| Master planning | [Inventory forecasts](../master-planning/inventory-forecast.md) |
| Master planning | [Parameters not used by Planning Optimization](../master-planning/planning-optimization/not-used-parameters.md) |
| Master planning | [Replenishment methods and quantity modification](../master-planning/planning-optimization/replenishment-methods-quantity-modification.md) |
| Master planning | [Scheduling with infinite capacity](../master-planning/planning-optimization/infinite-capacity-planning.md) |
| Master planning | [View plan history and planning logs](../master-planning/planning-optimization/plan-history-logs.md) |
| Warehouse management | [Container packing strategies](../warehousing/container-packing-strategy-overview.md) |
| Warehouse management | [Cycle counting example scenarios](../warehousing/cycle-counting-scenarios.md) |
| Warehouse management | [Import inbound ASNs through data entity](../warehousing/import-asn-data-entity.md) |
| Warehouse management | [Over-picking for sales orders and transfer orders](../warehousing/over-picking-for-sales-and-transfer-orders.md) |
| Warehouse management | [Schedule wave label printing during wave](../warehousing/configure-task-based-wave-label-printing.md) |
| Warehouse management | [What's new or changed in the Warehouse Management mobile app](../warehousing/whats-new-wma.md) |

## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.21 includes platform updates. To learn more, see [Platform updates for version 10.0.21 of Finance and Operations apps (October 2021)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-21.md).

### Bug fixes

For information about the bug fixes included in each of the updates that are part of 10.0.21, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=605166&dbType=3&qc=4b9449bf0d947113983bd0697140bf4d8727bfafd5566aa682cb38db343374de).

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
