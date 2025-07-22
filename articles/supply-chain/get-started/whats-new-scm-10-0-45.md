---
title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.45 (September 2025)
description: Learn about features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.45 with a table outlining feature areas. 
author: kamaybac
ms.author: kamaybac
ms.topic: conceptual
ms.date: 07/28/2025
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# What's new or changed in Dynamics 365 Supply Chain Management 10.0.45 (September  2025)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management version 10.0.45. This version has a build number of 10.0.XXXX<!-- KFM: Update build number --> is available on the following schedule:

- **Preview of release:** July 2025
- **General availability of release (self-update):** September  2025
- **General availability of release (auto-update):** October 2025

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Inventory and warehouse management | [Enable quality control with acceptance sampling](/dynamics365/release-plan/2025wave1/finance-supply-chain/dynamics365-supply-chain-management/enable-quality-control-acceptance-sampling) | [Acceptance sampling (preview)](../inventory/quality-acceptance-sampling.md) | Feature management:<br>*(Preview) Acceptance sampling* |
| Master planning | [Implement lean manufacturing, catch weight, and step consumption](/dynamics365/release-plan/2025wave1/finance-supply-chain/dynamics365-supply-chain-management/implement-lean-manufacturing-catch-weight-step-consumption-planning-optimization) | [Master planning home page](../master-planning/master-planning-home-page.md) | Feature management:<br>*(Preview) Lean manufacturing for Planning Optimization* |
| Message processor | Clean up processed and canceled message processor messages | [Clean up processed and canceled message processor messages](../message-processor/message-processor-cleanup.md) | Enabled by default. |
| Production control | Generate license plates and print labels for MES integration | [Integrate with third-party manufacturing execution systems](../production-control/mes-integration.md) | Enabled by default you have [set up MES integration](../production-control/mes-integration.md). |
| Warehouse management | [Improve operations with Warehouse Management mobile app V4](/dynamics365/release-plan/2025wave1/finance-supply-chain/dynamics365-supply-chain-management/improve-operations-warehouse-management-mobile-app-v4) | [Migrate the Warehouse Management mobile app from V3 to V4 (preview)](../warehousing/warehouse-app-migrating-from-v3-v4.md) | Enabled by default in Supply Chain Management.<p>Must be [installed or upgraded locally]((../warehousing/warehouse-app-migrating-from-v3-v4.md)) on each device. |
| Warehouse management | Record and view container line packing details | [Packing containers with the Warehouse Management mobile app](../warehousing/warehouse-app-packing-containers.md) | Enabled by default. |

## <a name="enhancements"></a>Feature enhancements added in this release

The following table lists the feature enhancements that were added in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they're only enhancements, they aren't listed in the [release plan](/dynamics365/release-plan/2024wave2/finance-supply-chain/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

Some of these features aren't visible on your system until you turn them on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) using the name listed here for the *Feature management name* (additional configuration may also be needed). Features that don't show a feature management name are visible by default as of this version of Supply Chain Management, but typically add a new configuration option that you need to set to use the new functionality.

| Feature enhancement | Description |
|---|---|
| **Module:** Procurement and sourcing<br><br>**Feature management name:** *Enable calculation of earliest confirmed receipt date for vendor collaboration* | Displays the earliest confirmed receipt date for purchase order responses. The value is calculated based on the confirmed receipt dates for the purchase response lines. |
| **Module:** Procurement and sourcing<br><br>**Feature management name:** *Remove vendors from RFQ after bid is sent or received* | Lets you remove vendors from a request for quotation (RFQ) after a bid has been sent to or received from them. When removing a vendor, you can optionally send an email notification to inform them of the removal. Once removed, the vendor can no longer access the RFQ in the supplier portal. However, the purchase manager can re-add the vendor to the RFQ at any time, as long as the RFQ has not been accepted or rejected. This provides added control and flexibility during the RFQ evaluation process. |
| **Module:** Production control<br><br>**Feature management name:** *Enhanced numpad control for production floor execution interface* | Improves the control that represents the numpad in the production floor execution interface. It changes the control from being an element of type *String* to type *Real*, which makes the decimal separator consistent with regards to the regional settings. |
| **Module:** Sales and marketing<br><br>**Feature management name:** *Enable lookup based search for Sales External Item Identifier field* | Enables lookup-based search for the **External item identifier** field on sales order lines. |

## Preview features that are now generally available

<!-- KFM: Add details or remove this section -->

The following table lists the features that were introduced as public preview features in a previous version and became generally available in version 10.0.45. As with other new features, most of these features are turned off by default, so you must turn them on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) if you want to use them.

| Module | Feature name | More information |
|--|--|--|

## Features turned on by default in this release

<!-- KFM: Add details or remove this section -->

The following table lists the features that became turned on by default in version 10.0.43. You can still turn these features off in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) if necessary.

| Module | Feature name | More information |
|--|--|--|

## Features becoming mandatory in this release

<!-- KFM: Add details or remove this section -->

The following table lists the features that became mandatory in version 10.0.45. These features can still be seen in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) but can no longer be turned off.

| Module | Feature name | More information |
|---|---|---|

## Features removed from feature management

<!-- KFM: Add details or remove this section -->

The following table lists features that were removed from Feature management in version 10.0.45. These features are no longer listed in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) and are now a permanent part of Supply Chain Management.

| Module | Feature name | More information |
|---|---|---|

## Related information

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.45 includes platform updates. Learn more in [Platform updates for version 10.0.45 of Finance and Operations apps (September  2024)](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-45.md). <!-- KFM: Check link -->

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.45, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=XXXX). <!-- KFM: Get new link -->

### Dynamics 365: 2025 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Microsoft Dynamics 365: 2025 release wave 1 plan](/dynamics365/release-plan/2025wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
