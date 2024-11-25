---
title: What's new or changed in Dynamics 365 Supply Chain Management version 10.0.19 (June 2021) 
description: Learn about features that are either new or changed in Dynamics 365 Supply Chain Management 10.0.19 with an outline on included features. 
author: kamaybac
ms.author: kamaybac
ms.topic: conceptual
ms.date: 05/28/2024
ms.custom:
  - bap-template
  - evergreen
ms.reviewer: kamaybac
ms.search.form:
---

# What's new or changed in Dynamics 365 Supply Chain Management version 10.0.19 (June 2021)

[!include [banner](../../finance/includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management version 10.0.19. This version has a build number of 10.0.837 and is available as follows:

- **Preview of release:** April 2021
- **General availability of release (self-update):** June 2021
- **General availability of release (auto-update):** June 2021

## Features included in this release

The following table lists the features included in this release. The *Feature* column provides links to the [release plan](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/planned-features), where you can see the official release dates for each feature. The *More information* column provides more details and/or links to related documentation.

Most of these features must be enabled using [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) before you can use them.

| Feature area | Feature | More information |
|---|---|---|
| Inventory&nbsp;and&nbsp;logistics | [Approve and save vendor-submitted bank details](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/approve-save-vendor-submitted-bank-details) | [Maintain vendor bank account information](../../finance/accounts-payable/maintain-vendor-bank-info.md) |
| Inventory and logistics | [Contact person data entity export optimization](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/contact-person-data-entity-export-optimization)  | When this feature is enabled, changes to referenced data will not cause related contacts to be included in the next incremental export. When this feature is disabled, changes to referenced data will cause related contacts to be included in the next incremental export. |
| Inventory and logistics | [Incremental enhancements for warehouse execution capabilities with scale units](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/incremental-enhancements-warehouse-execution-capabilities-scale-units) |[Message processor messages](../cloud-edge/cloud-edge-message-processor-messages.md)<br><br>[Warehouse inventory adjustment](../cloud-edge/cloud-edge-warehouse-inventory-adjustment.md)<br><br>[Warehouse management workloads for cloud and edge scale units](../cloud-edge/cloud-edge-workload-warehousing.md) |
| Inventory and logistics | [Lookup functionality for Document introduction and Document conclusion fields on Sales quotation page](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/lookup-functionality-document-introduction-document-conclusion-fields-sales-quotation-page) | This feature adds lookup functionality for the **Document introduction** and **Document conclusion** fields on the **Sales quotation** page.<br><br>This feature is enabled by default. |
| Inventory and logistics | [Warehouse execution with edge scale units on your custom hardware](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/warehouse-execution-edge-scale-units-custom-hardware) | [Deploy edge scale units on custom hardware using LBD](../cloud-edge/cloud-edge-edge-scale-units-lbd.md) |
| Manufacturing | [Manufacturing execution with edge scale units on your custom hardware](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/manufacturing-execution-edge-scale-units-custom-hardware) | [Deploy edge scale units on custom hardware using LBD](../cloud-edge/cloud-edge-edge-scale-units-lbd.md) |
| Planning | Query-based planned order firming | [Firm planned orders](../master-planning/planning-optimization/planned-order-firming.md) |
| Product information management | [Variant suggestions page improvements](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/variant-suggestions-page-improvements) | [Create predefined product variants](../pim/tasks/create-predefined-product-variants.md) |

## Feature enhancements included in this release

The following table lists the feature enhancements included in this release. Each of these provides an incremental improvement to an existing feature. Because they are only enhancements, they are not listed in the [release plan](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted). If you want to use any of these features, you must explicitly enable them in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Module | Feature&nbsp;name&nbsp;in feature&nbsp;management | More information |
|---|---|---|
| Sales and marketing | Sales history cleanup performance improvements | Sales history cleanup can take a long time if run infrequently on environments with a high volume of sales updates. To reduce duration and improve reliability, this feature splits clean-up into batches that run for a limited duration. Where possible, database capabilities will be leveraged to minimize locking and avoid joining transactional tables during cleanup. Learn more in [Schedule sales history data cleanup](../sales-marketing/sales-update-history-cleanup-performance-improvements.md). |
| Sales and marketing | Update Requested receipt date with Confirmed date for intercompany orders | This feature lets you control what will happen to sales and purchase date field values when using intercompany direct delivery. You can choose whether the system will update requested dates or skip updating them. If you skip the update, the requested dates will represent what the customer has requested. If you enable updating, the requested dates (when using delivery date control) only initially represent what the customer requested. Delivery date control, when different from *None*, will overrule what has initially been requested. You can set this option using the new **Update Requested receipt date with Confirmed date** setting on the intercompany vendor or customer settings.<br><br>If the feature is disabled, the system will overwrite the requested receipt date on original sales orders based on the delivery date control rule, but the requested shipping date will remain as is. |
| Warehouse management | Round quantities down to nearest sales unit on release to warehouse | This feature adds an option that can restrict order quantities on release to warehouse. When enabled, order quantities will be rounded down to the nearest whole sales unit, and orders that include quantities for less than one sales unit will be rejected for release. |
| Warehouse management | Organization-wide "Schedule work creation" wave method | On enabling this feature, the *Schedule work creation* wave method will be configured to run in parallel across all legal entities. Several additional settings will also be affected. For complete details, see [Schedule work creation during wave](../warehousing/configure-wave-schedule-work-creation.md). |

## New and updated documentation resources

We have recently added or significantly updated the following help articles. They aren't necessarily related to the new features added for this release, as listed in the previous section, but they may help you to get more out of existing features.

| Feature area | New or updated articles |
|---|---|
| Engineering change management | [Engineering change management FAQs](../engineering-change-management/change-management-faq.md) |
| Procurement and sourcing | [Category requests from vendors](../procurement/category-requests-from-vendors.md) |
| Product information management | [Manage unit of measure](../pim/tasks/manage-unit-measure.md)<br><br>[Product configuration model calculations](../pim/config-model-calculations.md) |
| Production control | [Unified number sequence for job IDs](../production-control/unified-job-ids.md) |
| Transportation management | [LTL classes](../transportation/ltl-class.md)<br><br>[Work with NMFC codes in Dynamics 365 Supply Chain Management](../transportation/nmfc-codes.md) |
| Warehouse management, wave creation and processing | [Wave creation and processing](../warehousing/wave-processing.md)<br><br>[Warehouse parameters for wave processing](../warehousing/wave-warehouse-parameters.md)<br><br>[Wave templates](../warehousing/wave-templates.md)<br><br>[Wave allocation](../warehousing/wave-allocation-method.md)<br><br>[Schedule work creation during wave](../warehousing/configure-wave-schedule-work-creation.md)<br><br>[Containerization](../warehousing/wave-containerization.md)<br><br>[Wave execution notifications](../warehousing/wave-execution-notifications.md) |

## Related information

### Platform updates for finance and operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.19 includes platform updates. Learn more in [Platform updates for version 10.0.19 of finance and operations apps (June 2021)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-19.md).

### Bug fixes

For information about the bug fixes included in each of the updates that are part of 10.0.19, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=575415).

### Dynamics 365: 2021 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2021 release wave 1 plan](/dynamics365-release-plan/2021wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](../get-started/removed-deprecated-features-scm-updates.md) article describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](../get-started/removed-deprecated-features-scm-updates.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]

