---
title: Preview of Dynamics 365 Supply Chain Management 10.0.27 (July 2022)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.27. 
author: kamaybac
ms.date: 04/22/2022
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this topic to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: kamaybac
ms.search.validFrom: 2021-04-22
ms.dyn365.ops.version: 10.0.27
---

# Preview of Dynamics 365 Supply Chain Management 10.0.27 (July 2022)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management preview version 10.0.27. This version has a build number of 10.0.1227 and is available on the following schedule:

- **Preview of release:** April 2022
- **General availability of release (self-update):** June 2022
- **General availability of release (auto-update):** July 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this topic to include features that were added to the build after this topic was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Inventory and logistics | [Inventory allocation for the Inventory Visibility Add-in](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/inventory-allocation-inventory-visibility-add-in) | Coming soon | Enabled by default |
| Manufacturing | "My day" view for the production floor execution interface | [How workers use the production floor execution interface](../production-control/production-floor-execution-use.md) and [Show vacation balances in the production floor execution interface](../production-control/production-floor-execution-payroll-stats.md) | Feature management:<br>*"My day" view for the production floor execution interface* |
| Planning | [Planning Optimization support for subcontracting](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/planning-optimization-support-subcontracting) | [Manage subcontracting work in production](../production-control/manage-subcontract-work-production.md) | Enabled by default |

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

If you want to turn any of these features on or off, you must do so in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Module | Feature name in feature management | More information |
|---|---|---|
| Master planning | Consider inventory lead time when creating a planned transfer order | When a planned transfer order is created, this feature causes the system to consider the inventory lead time that is specified in the item's default order settings when it calculates the receipt date of the planned transfer order for the delivery date control setup as lead time of the *None* or *Sales* type. When transfer lead time is specified, its value will be used for the receipt date calculation, and transport days will be disregarded. |
| Procurement and sourcing | Default broker contract tax information on vendor invoice lines | This feature introduces logic to set default values for the **Sales tax** and **Item sales tax** fields on broker contract vendor invoice lines. This logic is applied only when the charge type on the broker contract line is ledger/ledger. The item sales tax group will take its default value either from the brokerage procurement category (if it's set up) or from the charge type. The sales tax group will take its default value from the vendor account. |
| Procurement and sourcing | Limit the number of purchase order lines per batch task | This feature helps you to optimize system performance when confirmations and product receipts are posted. It adds a new setting that is named **Lines per task** to the **Delivery** tab of the **Procurement and sourcing parameters** page. This new setting lets you limit the number of purchase order lines that each batch task processes. Therefore, it can help prevent large batch tasks from slowing down the system. |
| Product information management | Populate product attribute values | This feature adds a periodic task that is named *Populate product attribute values*. This new periodic task creates missing product attribute value records for attributes that are associated with products via a product category. |
| Production control | Additional configuration on the production floor execution interface | <p>This feature adds the following options to the **Configure production floor execution** page:</p><ul><li>**Auto-open start dialog when completing search** – When this option is enabled, the **Start job** dialog box is automatically opened when workers use the search bar to find the job.</li><li>**Auto-open report progress dialog when completing search** – When this option is enabled, the **Report progress** dialog box for the job is automatically opened when workers use the search bar to find the job.</li><li>**Default remaining quantity in the report progress dialog** – When this option is enabled, the **Report progress** dialog box shows the remaining quantity to report on a production job.</li></ul><p>For more information, see [Configure the production floor execution interface](../production-control/production-floor-execution-configure.md).</p> |
| Production control | Production teams in the production floor execution interface | <p>When multiple workers are assigned to the same production job, they can now nominate one worker as a pilot. The remaining workers automatically become assistants to that pilot. For the resulting team, only the pilot must register job status, whereas time records apply to all team members. This feature also supports a scenario that is named *assist resource*. In this scenario, a worker can register as an assistant to another worker, who then becomes the pilot for the newly formed group.</p><p>For more information, see [How workers use the production floor execution interface](../production-control/production-floor-execution-use.md).</p> |
| Production control | Report on planning items in the production floor execution interface | This feature simplifies the process of reporting on batch orders for planning items in the production floor execution interface. When a batch order is created for a product that has a production type of *Planning item*, reporting as finished can be done only on the co-products and by-products for that batch order. Batch orders for planning items are typically used to support disassembly processes, where a raw material product is disassembled into multiple distinct products. When a worker reports a batch order for a planning item as finished, the **Report progress** dialog box will now show only the co-products and by-products. Previously, it also showed the planning item, and this behavior could confuse workers. |

## New and updated documentation resources

We have recently added or significantly updated the following Help topics. These topics aren't necessarily related to the new features that were added for this release, as listed in the previous sections. However, they might help you get more out of existing features.

| Feature area | New or updated topics |
|---|---|
| Cost management | [Weighted average date with Include physical value and marking](../cost-management/weighted-average-date.md) |
| Distributed hybrid topology | [Try out scale units in a distributed hybrid topology](../cloud-edge/cloud-edge-try-out.md) |
| Dual-write | [Sync on-demand with the Supply Chain Management pricing engine](../../fin-ops-core/dev-itpro/data-entities/dual-write/pricing-engine.md) |
| Warehouse management | [Release to warehouse](../warehousing/release-to-warehouse-process.md) |

## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.27 includes platform updates. To learn more, see [Platform updates for version 10.0.27 of Finance and Operations apps (June 2022)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-27.md).<!-- KFM Confirm link -->

### Bug fixes

For information about the bug fixes included in each of the updates that are part of 10.0.27, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=673271).

### Dynamics 365 and industry clouds: 2022 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2022 release wave 1 plan](/dynamics365-release-plan/2022wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) topic describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
