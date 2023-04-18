---
title: Preview of Dynamics 365 Supply Chain Management 10.0.34 (June 2023)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.34. 
author: kamaybac
ms.author: kamaybac
ms.reviewer: kamaybac
ms.search.form:
ms.topic: conceptual
ms.date: 03/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Preview of Dynamics 365 Supply Chain Management 10.0.34 (June 2023)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management preview version 10.0.34. This version has a build number of 10.0.1549 and is available on the following schedule:

- **Preview of release:** April 2023
- **General availability of release (self-update):** June 2023
- **General availability of release (auto-update):** July 2023

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Inventory and logistics | [Add efficiency in prospect-to-cash integration with Sales](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-supply-chain-management/gain-added-efficiency-prospect-to-cash-integration-dynamics-365-sales) | *Coming soon* | Feature management:<ul><li>*Integrate Sales Quotation lifecycle with Dynamics 365 Sales*</li><li>*Set default ownership for sales quotations when integrated with Dynamics 365 Sales*</li><li>*Make Supply Chain Management price master when integrated with Dynamics 365 Sales*</li><li>*Calculate and push prices, discounts and totals for selective sales orders and sales quotations when integrated to Dynamics 365 Sales*</li><li>*Copy Supply Chain Management sales quotation data to sales orders synced from Dynamics 365 Sales*</li><li>*Process Dynamics 365 Sales integration related events*</li></ul> |
| Inventory and logistics | [Apply right tax with minimal effort in order entry for product variants](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-supply-chain-management/apply-right-taxation-minimal-effort-order-entry-product-variants) | [Predefined product variants](../pim/tasks/create-predefined-product-variants.md) | Feature management:<br>*Apply sales tax group for product variants in sales and procurement* |
| Inventory and logistics | [Archive sales orders](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-supply-chain-management/archive-sales-orders) |  | Feature management:<ul><li>*(Preview) Archive sales orders to history tables using archive service*</li><li>*(Preview) Archive sales orders to history tables*</li></ul><!--KFM: Please confirm. --> |
| Inventory and logistics | [Calculate available-to-promise for up to three months](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-supply-chain-management/calculate-promise-up-three-months) |  |  |
| Inventory and logistics | [Empower users with near real-time inventory insights](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-supply-chain-management/empower-users-near-real-time-inventory-insights) |  |  |
| Inventory and logistics | [Provide a better configuration experience for Inventory Visibility users](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-supply-chain-management/provide-better-configuration-experience-inventory-visibility-users) |  |  |
| Manufacturing and asset management | [Check material availability for scheduled operations](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-supply-chain-management/check-material-availability-scheduled-operations) | This feature makes it possible for organizations that use the scheduling type *Schedule operations* to check for material availability. Previously, it was only possible to check for material availability when using the *Schedule jobs* scheduling type. Before releasing a production order to the shop floor, production supervisors can check the material availability of each order by going to the **Production floor management** workspace and selecting the **Production orders to release** tile. The **Production orders to release** page now lists and indicates material availability both for orders that use the *Schedule operations* scheduling type and for orders that use the *Schedule jobs* scheduling type. | Feature management:<br>*Material availability check for operations scheduled production orders* |

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they're only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

If you want to turn any of these features on or off, you must do so in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Module | Feature name in feature management | More information |
|---|---|---|
| Product information management | User specific product name and description | Lets workers select the language in which product names and descriptions are shown for them in the user interface. <!--KFM: Should probably be documented in [Show translated product names and descriptions in the UI](../pim/show-translated-product-info.md) --> |
| Product information management | Product bundles | Lets you to group related items together by using a parent item that includes or more component items. Bundles are defined using bills of material. <!--KFM: does this really belong here? Seems like a major feature. Doc probably required. (Preview) required. --> |
| Master planning | Forecast demand plan import service. | Allows multiple threads for importing forecast demand plan lines <!--KFM: does this really belong here? Seems like a major feature. Doc probably required. (Preview) required. Period in name. --> |
| Production control | Faster Gantt charts | Enables Gantt charts to load more quickly throughout the system, making it faster for you to review orders, material availability, calendars, and more. |
| Inventory and warehouse management | Inventory Visibility integration with inventory adjustment offset | Makes it possible to offset an inventory adjustment that was previously posted in Inventory Visibility. <!--KFM: (Preview) required. --> |
| Inventory and warehouse management | Inventory Visibility integration with inventory adjustment posting | Makes it possible to post inventory adjustments to inventory visibility by batch. <!--KFM: (Preview) required. --> |
| Sales and marketing | Adjusting reverse match for a settlement process | Adjusting reverse match for a settlement process <!--KFM: Name and description are the same. Description needed. --> |
| Sales and marketing | (Preview) Sequence and compound for customer charges | Enables the new charge concepts of sequence, compound, and specific unit of measure for customer charges. The feature supports setting up and working with these concepts on auto charges. They lets you define the order in which header-level charges are calculated and which invoice amounts are taken into account when calculating the value upon which a header-level charge is calculated. |
| Sales and marketing | (Preview) Unit of measure for line level charges | Makes it possible to specify a unit of measure (UoM) for which a line-level auto charge applies. You can set up auto charges that only apply to lines that use the exact UoM configured for the charge, or you could choose to allow the charge to apply proportionally based on an applicable UoM conversion factor (if available). This feature supports customer and vendor line-level charges and applies for sales quotation and sales order lines, request for quotation, purchase requisition, and purchase order lines. |
| Sales and marketing | Operational reporting of Sales invoice and packing slip | Operational reporting of Sales invoice and packing slip <!--KFM: Name and description are the same. Description needed. (Preview) required. --> |
| Shared AP and AR | Rebate management sold-to customers posting | Enable users to select sold-to customers as an option for the Rebate management posting account source. With the introduction of this new account source type, you can use *sold-to customers* as an extension type of a deal line account, and use this posting profile on any number of rebate lines. Once sold-to customers is set, date transactions will be split and grouped together per account when Rebate management is processed. Those transactions will also be posted to the same account accordingly. |
| Transportation management | (Preview) Source document and accounting distribution support for Landed Cost | Lets you include landed costs in the accounting distribution of purchased product receipts, which makes it east to identify and track these costs. This feature lets you associate freight cost from landed cost with their corresponding source documents, which provides a more accurate and comprehensive view of the total cost of goods received. With this functionality, you can gain greater visibility into the expenses associated with your purchases and transportation, allowing for better cost analysis and management. |

## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.34 includes platform updates. To learn more, see [Platform updates for version 10.0.34 of Finance and Operations apps (June 2023)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-34.md)<!--KFM: confirm link -->.

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.34, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](#)<!--KFM: get link -->.

### Dynamics 365 and industry clouds: 2023 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2023 release wave 1 plan](/dynamics365/release-plan/2023wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
