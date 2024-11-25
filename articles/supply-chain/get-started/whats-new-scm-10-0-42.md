---
title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.42 (December 2024)
description: Learn about features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.42 with a table outlining feature areas. 
author: kamaybac
ms.author: kamaybac
ms.topic: conceptual
ms.date: 08/07/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# What's new or changed in Dynamics 365 Supply Chain Management 10.0.42 (December 2024)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management version 10.0.42. This version has a build number of 10.0.2095 and is available on the following schedule:

- **Preview of release:** October 2024
- **General availability of release (self-update):** December 2024
- **General availability of release (auto-update):** February 2025

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Copilot and AI innovation | Customize the conversational help provided by Copilot | [Add knowledge to generative help and guidance with Copilot](../../fin-ops-core/dev-itpro/copilot/extend-copilot-generative-help.md) | Enabled using Copilot Studio. |
| Production control | Register material consumption as complete and edit dimensions on the production floor execution interface | [Configure the production floor execution interface](../production-control/production-floor-execution-configure.md)<br><br>[How workers use the production floor execution interface](../production-control/production-floor-execution-use.md) | Feature management:<br>*Register material consumption as complete and edit dimensions on the production floor execution interface* |
| Procurement and sourcing | Support contract lifecycle management in source to pay by flexible integration | [Contract lifecycle management overview (preview)](../procurement/contract-lifecycle-management/clm-overview.md) | Feature management:<br>*(Preview) Integrate with external contract lifecycle management systems* |
| Sales and marketing | Seamless sync with Dynamics 365 Sales | [Enable and configure seamless sync with Dynamics 365 Sales (preview)](../../fin-ops-core/fin-ops/data-entities/add-efficiency-in-quote-to-cash-seamless-sync.md) | Feature management:<br>*Automatically synchronize line data and totals with Dynamics 365 Sales* |
| Sales and marketing | [Roll out multifaceted pricing strategies](/dynamics365/release-plan/2024wave2/commerce/dynamics365-commerce/roll-out-multifaceted-pricing-strategies-unified-pricing-management-module) | [Unified pricing management overview (preview)](../unified-pricing-management/upm-pricing-management-overview.md) | Feature management:<br>*(Preview) Unified pricing management* |
| System administration | [Keep conversations going with Copilot follow-up questions](/dynamics365/release-plan/2024wave2/finance-supply-chain/dynamics365-supply-chain-management/keep-conversations-going-ai-generated-follow-ups) | [Responsible AI FAQ for Follow-up questions in the Copilot sidecar (preview)](../../fin-ops-core/fin-ops/copilot/faq-copilot-suggested-questions.md) | Feature management:<br>*(Preview) Follow-up questions in the Copilot sidecar* |

## <a name="enhancements"></a>Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they're only enhancements, they aren't listed in the [release plan](/dynamics365/release-plan/2024wave1/finance-supply-chain/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

Some of these features aren't visible on your system until you turn them on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) using the name listed here for the *Feature management name* (additional configuration may also be needed). Features that don't show a feature management name are visible by default as of this version of Supply Chain Management, but typically add a new configuration option that you need to set to use the new functionality.

| Feature enhancement | Description |
|---|---|
| <p>**Module:** Master planning</p><p>**Feature management name:** *Include invoiced and delivered orders during supply and demand forecast reduction for planning optimization*</p> | Include invoiced and delivered orders during supply and demand forecast reduction for Planning Optimization. Invoiced demand accounts for picked, packed, and invoiced issues. Delivered supplies accounts for registered, received, and delivered receipts. This only applies to products with a coverage group that has a reduction key specified, and the master plan must reduce forecast by transactions in period. |
| <p>**Module:** Product information management</p><p>**Feature management name:** *(Preview) Rename item number*</p> | Enables item number renaming. It finds all relevant records across the system that need to be updated with the new item number value. Additionally, the whole renaming process is thoroughly logged. The log is available at **Product information management** \> **Inquiries and reports** \> **Item number renaming logs**. |
| <p>**Module:** Production control</p><p>**Feature management name:** *New rule for validating the material batch expiration date*</p> | Adds a new option for validating batch expiration dates when reserving a batch of raw material to be used during production. It adds a new value, *Raw material date of production bill of material (BOM) or formula line*, to the **Validate batch expiration on** drop-down list on the **Item model groups** page. When this value is selected, the system validates the batch expiration date against the raw material date found on the production BOM or formula lines. |
| <p>**Module:** Production control</p><p>**Feature management name:** *Set the desired status on selected jobs in report progress list view in the production floor execution interface*</p> | Workers reporting job progress from the production floor execution interface can now select the desired status on multiple jobs in the report-progress list view. |
| <p>**Module:** Production control</p><p>**Feature management name:** *Streamlined registration process for indirect activities on the Production floor execution*</p> | Streamlines the process for workers to register for indirect activities through the production floor execution interface. Previously, when a worker registered for an indirect activity, a dialog box would open, asking them whether they wanted to stop the activity or log it at the end of their shift. This feature removes the dialog. Instead, the system automatically adds the indirect activity to the worker's active job list. The system stops the indirect activity when the worker begins a new task (such as a production job), another indirect activity, or a project job. |

## Preview features that are now generally available

The following table lists the features that were introduced as public preview features in a previous version and became generally available in version 10.0.42. As with other new features, most of these features are turned off by default, so you must turn them on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) if you want to use them.

| Module | Feature name | More information |
|---|---|---|
| Inventory and warehouse management | *Inventory Visibility integration with inventory adjustment posting* | [Enable Inventory Visibility for Commerce](../inventory/inventory-visibility-commerce-enable.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.34 (July 2023)](whats-new-scm-10-0-34.md) |
| Inventory and warehouse management | *Inventory Visibility integration with inventory adjustment offset* | [Inventory Visibility adjustment offset](../inventory/inventory-visibility-adjustment-offset.md)<br><br>[Enable Inventory Visibility for Commerce](../inventory/inventory-visibility-commerce-enable.md)<br><br>[Sync external inventory adjustments through Inventory Visibility](../inventory/inventory-visibility-sync-changes.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.34 (July 2023)](whats-new-scm-10-0-34.md) |

## New and updated documentation resources

We have recently added or significantly updated the following help articles. These articles aren't necessarily related to the new features that were added for this release, as listed in the previous sections. However, they might help you get more out of existing features.

| Feature area | New or updated articles |
|---|---|
| Master planning | [Calculate sales order delivery dates using CTP](../master-planning/planning-optimization/calculate-delivery-dates-using-ctp.md) now describes *(Preview) Near real-time CTP* and *(Preview) Improve Planning Optimization performance by merging and queueing plan regeneration jobs* functionality. |

## Related information

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.42 includes platform updates. Learn more in [Platform updates for version 10.0.42 of Finance and Operations apps (December 2024)](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-42.md).

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.42, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=968512).

### Dynamics 365: 2024 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Microsoft Dynamics 365 and Microsoft Copilot for business functions: 2024 release wave 2 plan](/dynamics365/release-plan/2024wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
