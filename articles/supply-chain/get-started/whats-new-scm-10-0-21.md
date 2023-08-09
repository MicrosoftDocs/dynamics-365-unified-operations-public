---
title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.21 (October 2021) 
description: This article describes features that are either new or changed in Dynamics 365 Supply Chain Management 10.0.21. 
author: kamaybac
ms.date: 10/28/2021
ms.topic: article
# ms.search.form:  [Operations AOT form name to tie this article to]
audience: Application User, Developer, IT Pro
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: kamaybac
ms.search.validFrom: 2021-08-02
ms.dyn365.ops.version: 10.0.21
---

# What's new or changed in Dynamics 365 Supply Chain Management 10.0.21 (October 2021)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in the Microsoft Dynamics 365 Supply Chain Management version 10.0.21. This version has a build number of 10.0.960 and is available as follows:

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

## Features turned on by default in this release

The following table lists the features that are turned on by default in 10.0.21. Most features that have been turned on atomically can be turned off in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Feature name | Enable date | Feature added | Feature state | Module |
| :--- | :--- | :--- | :--- | :--- |
| Inventory on-hand report storage | 9/1/2021 | 4/1/2020 | On by default | Inventory and warehouse management |
| Transfer Order Cancellation | 9/1/2021 | 7/13/2020 | On by default | Inventory and warehouse management |
| Unlock Inventory Journal | 9/1/2021 | 8/17/2020 | On by default | Inventory and warehouse management |
| Saved views for Inventory management | 9/1/2021 | 9/30/2020 | On by default | Inventory and warehouse management |
| Navigation to BOM version from BOM lines | 9/1/2021 | 11/11/2019 | On by default | Inventory and warehouse management |
| Using unit of measure and unit quantity in inventory journals | 9/1/2021 | 11/11/2019 | On by default | Inventory and warehouse management |
| Allow empty batch attributes values | 9/1/2021 | 11/11/2019 | On by default | Inventory and warehouse management |
| Auto increment line numbers of inventory transfer order lines | 9/1/2021 | 10/11/2019 | On by default | Inventory and warehouse management |
| Inventory journal approve workflow | 9/1/2021 | 1/6/2020 | On by default | Inventory and warehouse management |
| Enable inventory quality management parameters warning feature | 9/1/2021 | 10/7/2019 | On by default | Inventory and warehouse management |
| Create transfer order from sales line | 9/1/2021 | 8/31/2019 | On by default | Inventory and warehouse management |
| Forecast model selection on Demand forecast details | 9/1/2021 | 10/11/2019 | On by default | Master planning |
| Master planning progress visualization | 9/1/2021 | 10/7/2019 | On by default | Master planning |
| Auto-firming for Planning Optimization | 9/1/2021 | 10/11/2019 | On by default | Master planning |
| Parallel firming of planned orders | 9/1/2021 | 8/31/2019 | On by default | Master planning |
| Bid submission success message | 9/1/2021 | 5/15/2019 | On by default | Procurement and sourcing |
| RFQ reference link added to PO | 9/1/2021 | 8/31/2019 | On by default | Procurement and sourcing |
| Ability to confirm accepted purchase orders from vendor collaboration in batch | 9/1/2021 | 9/10/2019 | On by default | Procurement and sourcing |
| Purchasing cXML enhancements | 9/1/2021 | 11/11/2019 | On by default | Procurement and sourcing |
| Display the &quot;Open published requests for quotation&quot; link as a tile | 9/1/2021 | 9/30/2020 | On by default | Procurement and sourcing |
| RFQ questions and answers | 9/1/2021 | 2/19/2020 | On by default | Procurement and sourcing |
| Hazardous materials product information and shipping documentation | 9/1/2021 | 6/14/2020 | On by default | Product information management |
| Strict validation on default order quantities | 9/1/2021 | 6/24/2020 | On by default | Product information management |
| Country of origin management feature | 9/1/2021 | 7/13/2020 | On by default | Product information management |
| Saved views for released products | 9/1/2021 | 9/30/2020 | On by default | Product information management |
| Improvements to the Approve and Transfer jobs dialogs | 9/1/2021 | 10/11/2019 | On by default | Production control |
| License plate for reporting as finished added to the Job Card Device | 9/1/2021 | 8/31/2019 | On by default | Production control |
| A new button to Stop break has been added to the Job Card Terminal page | 9/1/2021 | 2/19/2020 | On by default | Production control |
| Enable partial receipt of subcontracted items and fix an issue with the  calculation of scrap for BOM lines of type Vendor. | 9/1/2021 | 11/11/2019 | On by default | Production control |
| Saved views for production control | 9/1/2021 | 8/17/2020 | On by default | Production control |
| Dynamics 365 Guides for Manufacturing | 9/1/2021 | 7/13/2020 | On by default | Production control |
| Production floor execution | 9/1/2021 | 9/30/2020 | On by default | Production control |
| Feature for locking job card device and job card terminal so that they can be sanitized | 9/1/2021 | 5/10/2020 | On by default | Production control |
| Charges allocation on a sales order | 9/1/2021 | 9/30/2020 | On by default | Sales and marketing |
| Limit the number of sales orders that can be selected for posting | 9/1/2021 | 9/1/2021 | On by default | Sales and marketing |
| Clean up sales-order update history | 9/1/2021 | 9/1/2021 | On by default | Sales and marketing |
| Change the number sequence for cycle counting work | 9/1/2021 | 10/7/2019 | On by default | Warehouse management |
| Task based wave demand replenishment | 9/1/2021 | 10/7/2019 | Mandatory | Warehouse management |
| Hide the Total Value field on the &quot;All Loads&quot; and &quot;Load Details&quot; pages | 9/1/2021 | 10/7/2019 | On by default | Warehouse management |
| Wave label printing | 9/1/2021 | 2/19/2020 | Mandatory | Warehouse management |
| Associate purchase order inventory transactions with load | 9/1/2021 | 1/6/2020 | Mandatory | Warehouse management |
| Enhanced license plate label layouts | 9/1/2021 | 2/19/2020 | On by default | Warehouse management |
| Organization-wide work blocking | 9/1/2021 | 2/19/2020 | Mandatory | Warehouse management |
| Work line details | 9/1/2021 | 10/11/2019 | On by default | Warehouse management |
| Make mobile device inventory movement inventory status field editable | 9/1/2021 | 10/16/2019 | On by default | Warehouse management |
| Confirm outbound shipments from batch jobs | 9/1/2021 | 7/13/2020 | On by default | Warehouse management |
| Control whether to display a receiving summary page on mobile devices | 9/1/2021 | 4/1/2020 | On by default | Warehouse management |
| Prompt to resolve ambiguous &#39;Loc / LP&#39; names | 9/1/2021 | 4/1/2020 | On by default | Warehouse management |
| Capture product variants and tracking dimensions in the warehousing app during load item receiving | 9/1/2021 | 5/10/2020 | On by default | Warehouse management |
| Do not allow to create loads, that do not meet wave load building template requirements. | 9/1/2021 | 8/17/2020 | On by default | Warehouse management |
| Evaluate all actions for Multi SKU location directives | 9/1/2021 | 9/30/2020 | On by default | Warehouse management |

## New and updated documentation resources

We have recently added or significantly updated the following help articles. They aren't necessarily related to the new features added for this release, as listed in the previous section, but they may help you to get more out of existing features.

| Feature area | New or updated articles |
|---|---|
| Master planning | [Inventory forecasts](../master-planning/inventory-forecast.md) |
| Master planning | [Parameters not used by Planning Optimization](../master-planning/planning-optimization/not-used-parameters.md) |
| Master planning | [Replenishment methods and quantity modification](../master-planning/planning-optimization/replenishment-methods-quantity-modification.md) |
| Master planning | [Scheduling with infinite capacity](../master-planning/planning-optimization/infinite-capacity-planning.md) |
| Master planning | [View plan history and planning logs](../master-planning/planning-optimization/plan-history-logs.md) |
| Warehouse management | [Container packing strategies](../warehousing/container-packing-strategy-overview.md) |
| Warehouse management | [Cycle counting example scenarios](../warehousing/cycle-counting-scenarios.md) |
| Warehouse management | [Import inbound ASNs through the V3 data entity](../warehousing/import-asn-data-entity.md) |
| Warehouse management | [Over-picking for sales orders and transfer orders](../warehousing/over-picking-for-sales-and-transfer-orders.md) |
| Warehouse management | [Schedule wave label printing during wave](../warehousing/configure-task-based-wave-label-printing.md) |
| Warehouse management | [What's new or changed in the Warehouse Management mobile app](../warehousing/whats-new-wma.md) |

## Additional resources

### Platform updates for finance and operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.21 includes platform updates. To learn more, see [Platform updates for version 10.0.21 of finance and operations apps (October 2021)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-21.md).

### Bug fixes

For information about the bug fixes included in each of the updates that are part of 10.0.21, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=605166&dbType=3&qc=4b9449bf0d947113983bd0697140bf4d8727bfafd5566aa682cb38db343374de).

### Dynamics 365 and industry clouds: 2021 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2021 release wave 2 plan](/dynamics365-release-plan/2021wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]

