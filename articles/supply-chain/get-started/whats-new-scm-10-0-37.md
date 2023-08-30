---
title: Preview of Dynamics 365 Supply Chain Management 10.0.37 (November 2023)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.37. 
author: kamaybac
ms.author: kamaybac
ms.reviewer: kamaybac
ms.search.form:
ms.topic: conceptual
ms.date: 09/01/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Preview of Dynamics 365 Supply Chain Management 10.0.37 (November 2023)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management preview version 10.0.37. This version has a build number of 10.0.1695 <!-- KFM: Get new build number --> and is available on the following schedule:

- **Preview of release:** September 2023
- **General availability of release (self-update):** October 2023
- **General availability of release (auto-update):** November 2023

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Asset management | Material availability check on maintenance work orders | *Coming soon* |  Feature management:<br>*(Preview) Material availability check on maintenance work orders* |
| Inventory and logistics | [Integrate Inventory Visibility with Dynamics 365 Commerce](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/integrate-inventory-visibility-dynamics-365-commerce) | *Coming soon* | Enabled by default |
| Manufacturing and asset management | [Over-pick materials for production orders and batch orders](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/over-pick-materials-production-orders-batch-orders) | *Coming soon* | Feature management:<br>*Over-pick materials for production orders and batch orders* |
| Warehouse management | [Automatically update documents when receiving purchase orders](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/automatically-update-documents-when-receiving-purchase-orders) | [Warehouse handling of inbound loads for purchase and inbound shipment orders](../warehousing/inbound-load-handling.md) | Enabled by default |
| Warehouse management | Confirm serial numbers during picking | [Batch, serial, and license plate confirmation](../warehousing/batch-and-license-plate-confirmation.md) | Enabled by default |
| Warehouse management | Warehouse mobile devices workspace | [Warehouse mobile devices workspace](../warehousing/mobile-device-workspace.md) | Enabled by default |
| Warehouse management | Work user session query range utility tool | [Query data using Warehouse Management mobile app detours](../warehousing/warehouse-app-data-inquiry.md) | Enabled by default |

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they're only enhancements, they aren't listed in the [release plan](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

If you want to turn any of these features on or off, you must do so in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Module | Feature name in feature management | More information |
|---|---|---|
| Cost management | Cleanup redundant data from price calculation | Lets you remove redundant data from price calculation procedures. This includes data that may have been generated from incomplete, terminated, or cancelled jobs when running calculations from costing versions. |
| Inventory and warehouse management | Reset the inventory journal workflow which status is unrecoverable | Lets you change the status of an inventory journal workflow from *Unrecoverable* to *Cancelled*, which then allows you to edit the workflow as needed. | <!--KFM: Listed twice in FM. New, but already on by default? -->
| Production control | Leverage production order defaults in manufacturing execution system integration | Enables the configuration set up on the **Production order defaults** page to apply when [integrating with external manufacturing execution systems (MES)](../production-control/mes-integration.md). |
| Sales and marketing | (Preview) Pricing management - Allow applying adjustments to standard trade agreements | Allows sales managers to choose whether or not to apply adjustments to standard trade agreements. |
| Sales and marketing | (Preview) Sequence and compound for customer charges | Enables the new charge concepts of sequence, compound, and specific unit of measurement for customer charges. The feature supports setting up and working with these concepts on auto charges. They provide the capability of defining the order in which header-level charges are calculated and which invoice amounts are taken into account when calculating the value upon which a header level charge is calculated. |
| Sales and marketing | (Preview) Skip Completion for pricing management enhanced orders | When this feature is enabled, you no longer need to select **Complete** to proceed with a a sales order that uses Pricing management features. However, you still need to select **Recalculate** to update outdated sales line prices. Funds aren't supported for sales orders where the user opted to skip order completion. |  <!--KFM: Pricing management features should be described and added to [Turn on the Pricing management module for your system](../pricing-management/pricing-management-enable.md) -->

## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.37 includes platform updates. To learn more, see [Platform updates for version 10.0.37 of Finance and Operations apps (November 2023)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-37.md). <!-- KFM: Confirm link -->

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.37, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](#)<!-- KFM: Get new link -->.

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
