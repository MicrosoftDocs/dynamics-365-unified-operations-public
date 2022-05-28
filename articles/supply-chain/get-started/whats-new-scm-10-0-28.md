---
title: Preview of Dynamics 365 Supply Chain Management 10.0.28 (August 2022)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.28. 
author: kamaybac
ms.date: 05/27/2022
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this topic to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: kamaybac
ms.search.validFrom: 2022-05-27
ms.dyn365.ops.version: 10.0.28
---

# Preview of Dynamics 365 Supply Chain Management 10.0.28 (August 2022)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management preview version 10.0.28. This version has a build number of 10.0.1264 and is available on the following schedule:

- **Preview of release:** May 2022
- **General availability of release (self-update):** July 2022
- **General availability of release (auto-update):** July 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this topic to include features that were added to the build after this topic was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Inventory and logistics | [Landed cost integration entities for third-party freight forwarders](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/landed-cost-integration-third-party-freight-forwarders) | [Landed cost entities overview](../landed-cost/landed-cost-entities-overview.md) | Enabled by default |
| Planning | [Planning Optimization support for shelf life](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/planning-optimization-support-shelf-life) | Coming soon <!-- KFM: Vendor is preparing this. Expected May 20. --> | Enabled by default |

<!-- KFM: Confirm status of this feature:
| Planning | [Demand Driven Material Requirements Planning (DDMRP)](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/demand-driven-material-requirements-planning-ddmrp) | Coming soon | Feature management:<br>*(Preview) DDMRP for Planning Optimization* | -->

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

If you want to turn any of these features on or off, you must do so in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Module | Feature name in feature management | More information |
|---|---|---|
| Inventory and warehouse management | Enable intercompany on-hand to only show nonzero onhand quantity | This feature lets you choose whether items that have zero on-hand quantity should be included in the intercompany on-hand list. You can control this option by using the **Enable intercompany on-hand to only show nonzero onhand quantity** setting that this feature adds to the **Inventory and warehouse management parameters** page. |
| Inventory and warehouse management | (India) For transfer price rules, ignore location when "From warehouse code" is set to "All" | <p>This feature applies only to India localizations. It makes the process of setting up transfer prices for items in stock transfers more intuitive.</p><p>You set up transfer prices by configuring each item with transfer pricing rules. One way to do this configuration is to include a rule line where the **From warehouse code** field is set to *All*. This setting indicates that the transfer price that is defined by the line should apply regardless of the warehouse that the item is picked from. When this feature is enabled, transfer price rules where the **From warehouse code** field is set to *All* will ignore the **Location** setting. Therefore, the rule will apply regardless of the location that is specified on the transfer order. This behavior is probably what is expected, because location is below warehouse in the storage dimension hierarchy.</p><p>Without this feature, the system will apply rules of this type only when the location on the transfer order exactly matches the location that is set for the rule. (If a blank location is set for the rule, the system will apply the rule only to transfer orders that also have a blank value for the location.)</p> |
| Inventory and warehouse management | Inventory on-hand report data clean up | This feature provides a way to clean up the data that is used to create *Inventory on-hand report storage* reports. |
| Production control | Assign project activities for service agreement and service order lines | This feature adds a field that is named **Project activity** to service agreement and service order lines, so that you can set a project activity for them. The feature will help prevent blocking errors when you post service management project journals that require that a project activity be set.  |
| Warehouse management | Manual transfer line picking service for admin or similar trusted users | This feature lets administrators manually pick inventory transactions that are related to transfer lines. These lines include lines that have already been released to the warehouse. Administrators should do this picking only in exceptional cases, such as when the system is in a corrupted state. |

## New and updated documentation resources

We have recently added or significantly updated the following Help topics. These topics aren't necessarily related to the new features that were added for this release, as listed in the previous sections. However, they might help you get more out of existing features.

| Feature area | New or updated topics |
|---|---|
| Cost management | [Fixed receipt price](../cost-management/fixed-receipt-price.md) |
| Cost management | [Inventory costing frequently asked questions](../cost-management/inventory-costing-faq.md) |
| Cost management | [Post to charge account accounting principle](../cost-management/post-to-charge-account-accounting-principle.md) |
| Inventory management | [Inventory transaction details](../inventory/inventory-transactions-details.md) |

## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.28 includes platform updates. To learn more, see [Platform updates for version 10.0.28 of Finance and Operations apps (June 2022)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-28.md).<!-- KFM Confirm link -->

### Bug fixes

For information about the bug fixes included in each of the updates that are part of 10.0.28, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=694438).

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
