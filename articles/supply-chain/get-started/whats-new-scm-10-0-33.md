---
title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.33 (April 2023)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.33. 
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

# What's new or changed in Dynamics 365 Supply Chain Management 10.0.33 (April 2023)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management version 10.0.33. This version has a build number of 10.0.1549 and is available on the following schedule:

- **Preview of release:** March 2023
- **General availability of release (self-update):** April 2023
- **General availability of release (auto-update):** May 2023

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Inventory and logistics | [Assign shipments to related route segments](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-supply-chain-management/assign-shipments-related-route-segments) | [Assign shipments to related route segments](../transportation/assign-shipments-to-segments.md) | Feature management:<br>*(Preview)Assign shipments to related route segments* |
| Inventory and logistics | [Create and update containers in batch processing mode](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-supply-chain-management/create-update-containers-batch-processing-mode) | [Manage shipping containers](../landed-cost/manage-shipping-containers.md) | Feature management:<br>*(Preview) Enable shipping container creation and update in batch mode* |
| Inventory and logistics | [Split cost type codes for multiple voyages in the vendor invoice journal](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-supply-chain-management/split-cost-type-codes-multiple-voyages-vendor-invoice-journal) | This feature for the Landed cost module empowers businesses to more effectively distribute transportation expenses linked to various voyages. By using this feature, users creating a vendor invoice journal for multiple voyages can assign a distinct journal line for each cost type code, with the voyage name incorporated in its description. This streamlines the reconciliation process. Previously, the system would consolidate all costs from voyages with the same cost type code into a single line in the vendor invoice journal. With this update, vendor invoice journals will be split according to the cost type code. | Feature management:<br>*(Preview) Enable split vendor invoice journal line per cost type code and voyage id from multiple voyages* |
| Inventory and logistics | [Make soft reservations from sales orders](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-supply-chain-management/make-soft-reservations-sales-orders) | [Inventory Visibility reservations](../inventory/inventory-visibility-reservations.md) | Feature management:<br>*Inventory Visibility integration with soft reservation on sales order lines* |
| Inventory and logistics | [Manage attribute-based omnichannel sales pricing](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-supply-chain-management/manage-attribute-based-omnichannel-sales-pricing) | [Pricing management overview](../pricing-management/pricing-management-overview.md) | Feature management:<br>*(Preview) Pricing management* |
| Manufacturing and asset management | [Empower maintenance workers with new mobile experience](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-supply-chain-management/empower-maintenance-workers-new-mobile-experience) | [Asset Management mobile app overview](../asset-management/asset-management-mobile-app/asset-management-mobile-app-overview.md) | Enabled by default in Supply Chain Management. Dataverse setup and configuration required. |
| Warehouse management | Create and print custom label layouts | [Custom label layouts and printing](../warehousing/custom-label-layouts-and-printing.md) | Enabled by default |

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they're only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

If you want to turn any of these features on or off, you must do so in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Module | Feature name in feature management | More information |
|---|---|---|
| Master planning | Process manufacturing support for Planning Optimization | Enables the creation of planned orders for formulas, co-products, and by-products when Planning Optimization is used, thereby supporting process manufacturing industries and the sequencing of production jobs. |
| Product information management | Setup company specific number sequences | Lets you set up both cross-company and company-specific number sequences on the  **Product information management parameters** page. Company-specific number sequences are on the **Number sequences** tab while cross-company sequences are now available on the **Shared number sequences** tab. |
| Sales and marketing | Integrate Sales Quotation lifecycle with Dynamics 365 Sales | This feature applies when Supply Chain Management is integrated with Dynamics 365 Sales. It changes the way sales quotations in Dynamics 365 Sales integrate with sales quotations in Supply Chain management. Once enabled, state and status transitions throughout the lifecycle of sales quotations are mapped between the two applications. A policy of ownership is applied to control the actions available for a sales quotation when in either Dynamics 365 Sales or in Supply Chain Management.<br><br>**Note:** This feature is a component of the upcoming [Add efficiency in prospect-to-cash integration with Sales](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-supply-chain-management/gain-added-efficiency-prospect-to-cash-integration-dynamics-365-sales) functionality. Some of the components required to fully support this functionality won't be available until a future release of the Dual-write Supply Chain solution. Until then, this feature will have no effect, so we recommend against enabling it for now. |
| Sales and marketing | Process Dynamics 365 Sales integration related events | This feature requires the *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* feature. It enables events related to the integration to be processed asynchronously using the message processor framework. This can improve performance of integrated sales orders and quotations in some scenarios, such as when transitioning the status of a sales quotation when creating a quotation journal or quotation confirmation journal.<br><br>**Note:** This feature is a component of the upcoming [Add efficiency in prospect-to-cash integration with Sales](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-supply-chain-management/gain-added-efficiency-prospect-to-cash-integration-dynamics-365-sales) functionality. Some of the components required to fully support this functionality won't be available until a future release of the Dual-write Supply Chain solution. Until then, this feature will have no effect, so we recommend against enabling it for now. |
| Transportation management | (Preview) Performance improvements for post receipt function in Landed Cost | Improves performance of the Landed cost module by reducing the amount of information queried and update when posting product receipts for large purchase orders. |
| Transportation management | (Preview) Post landed cost with the specified posting type and account value on cost type code when credit type is 'Ledger Account'. | Posts landed costs with the specified posting type and account value on cost type code when the credit type is *Ledger Account*. As a result, landed costs won't be posted to clearing account consistently. |

## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.33 includes platform updates. To learn more, see [Platform updates for version 10.0.33 of Finance and Operations apps (April 2023)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-33.md).

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.33, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=795940).

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
