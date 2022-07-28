---
title: Preview of Dynamics 365 Supply Chain Management 10.0.29 (October 2022)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.29. 
author: kamaybac
ms.date: 08/01/2022
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this article to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: kamaybac
ms.search.validFrom: 2022-08-01
ms.dyn365.ops.version: 10.0.29
---

# Preview of Dynamics 365 Supply Chain Management 10.0.29 (October 2022)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management preview version 10.0.29. This version has a build number of 10.0.1264 <!-- KFM: Get new build number --> and is available on the following schedule:

- **Preview of release:** August 2022
- **General availability of release (self-update):** September 2022
- **General availability of release (auto-update):** October 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|




## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

If you want to turn any of these features on or off, you must do so in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Module | Feature name in feature management | More information |
|---|---|---|





## New and updated documentation resources

We have recently added or significantly updated the following Help articles. These articles aren't necessarily related to the new features that were added for this release, as listed in the previous sections. However, they might help you get more out of existing features.

| Feature area | New or updated articles |
|---|---|




## Feature state changes in this release

The following table lists features that became mandatory or on by default starting in 10.0.29. All of these features will automatically be turned on for your system as soon as you update to 10.0.29. Mandatory features can't be turned off, but features that are on by default can still be turned off using [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

The table also lists features that were previously in public preview, but have changed to become generally available in 10.0.29, which means they are now recommended for use on production environments. These features are turned off by default unless otherwise noted, so you must use [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) to enable them if you want to use them.

| Module | Feature name | New feature state |
| --- | --- | --- |
| Cost management | [Change the label of Cancellation in Closing and adjustment to Reverse](/dynamics365-release-plan/2020wave1/dynamics365-supply-chain-management/change-terminology-inventory-closing-cancellation-inventory-closing-reverse) | Mandatory |
| Cost management | Clean up BOM calculation details cross costing versions | Mandatory |
| Cost management | [Compare item prices storage](../cost-management/compare-item-price.md) | Mandatory |
| Cost management | Show inventory closing log in grid | Mandatory |
| Cost management | [Inventory value report storage](../cost-management/inventory-value-report-storage.md) | Mandatory |
| Cost management | Inventory value report data clean up | Mandatory |
| Cost management | Moving average, fallback cost sequence | Mandatory |
| Cost management | Show the items with not fully settled transactions in summary format <!-- KFM: continue here --> | Mandatory |
| Inventory and warehouse management | Allow empty batch attributes values | Mandatory |
| Inventory and warehouse management | Auto increment line numbers of inventory transfer order lines | Mandatory |
| Inventory and warehouse management | Create transfer order from sales line | Mandatory |
| Inventory and warehouse management | Disable inventory journal line field in workflow | Mandatory |
| Inventory and warehouse management | Enable inventory quality management parameters warning feature | Mandatory |
| Inventory and warehouse management | Inventory journal approve workflow | Mandatory |
| Inventory and warehouse management | Inventory on-hand report storage | Mandatory |
| Inventory and warehouse management | Saved views for inventory management | Mandatory |
| Inventory and warehouse management | Using unit of measure and unit quantity in inventory journals | Mandatory |
| Inventory and warehouse management | Unlock inventory journal | Mandatory |
| Inventory and warehouse management | Transfer order cancellation | Mandatory |
| Sales and marketing | Charges allocation on a sales order | Mandatory |
| Sales and marketing | Clean up sales-order update history | Mandatory |
| Sales and marketing | Clean up sales update history based on age | Mandatory |
| Sales and marketing | Contact person data entity export optimization | Mandatory |
| Sales and marketing | Copy total discount group for sales credit note | Mandatory |
| Sales and marketing | Enable lookup for sales quotation document introduction and document conclusion fields | Mandatory |
| Sales and marketing | Improve "Top 100" customers report performance | Mandatory |
| Sales and marketing | Include waiting records in history cleanup tasks | Mandatory |
| Sales and marketing | Limit the number of sales orders that can be selected for posting | Mandatory |
| Sales and marketing | Recalculate estimated customer balance | Mandatory |
| Sales and marketing | Sales return order line registration with decimal precision with and without catch weight | Mandatory |
| Sales and marketing | Saved views for sales and marketing | Mandatory |
| Sales and marketing | Single click sales order confirmation | Mandatory |
| Cost management | Cost calculation level | On by default |
| Cost management | Enable user-defined batch number setup for inventory closing reverse | On by default |
| Cost management | Inventory closing progress details | On by default |
| Sales and marketing | Limit the number of sales order lines per batch task | On by default |
| Transportation management | Allow unmatching of freight bills from freight invoice lines without a posted vendor invoice journal | On by default |
| Transportation management | Enable creation of a vendor invoice journal when discarding a freight bill | On by default |
| Transportation management | Small Parcel Shipping | On by default |
| Transportation management | USMCA certification of origin document | On by default |
| Sales and marketing | Calculate sales totals using multiple threads | Generally available |





## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.29 includes platform updates. To learn more, see [Platform updates for version 10.0.29 of Finance and Operations apps (June 2022)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-29.md). <!--KFM: Confirm link -->

### Bug fixes

For information about the bug fixes included in each of the updates that are part of 10.0.29, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=694438). <!-- KFM: Get new KB link -->

### Dynamics 365 and industry clouds: 2022 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2022 release wave 1 plan](/dynamics365-release-plan/2022wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]