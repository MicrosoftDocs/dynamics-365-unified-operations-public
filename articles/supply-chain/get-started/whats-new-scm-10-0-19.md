---
title: Preview of Dynamics 365 Supply Chain Management 10.0.19 (July 2021) 
description: This topic describes features that are either new or changed in Dynamics 365 Supply Chain Management 10.0.19. 
author: kamaybac
ms.date: 04/23/2021
ms.topic: article
# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: kamaybac
ms.search.validFrom: 2021-04-23
ms.dyn365.ops.version: 10.0.19
---

# Preview of Dynamics 365 Supply Chain Management 10.0.19 (July 2021)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic lists features that are either new or changed in the Microsoft Dynamics 365 Supply Chain Management preview of version 10.0.19. This version has a build number of 10.0.837 and is available as follows:

- **Preview of release:** April 2021
- **General availability of release (self-update):** June 2021
- **General availability of release (auto-update):** July 2021

## Features included in this release

The following table lists the features included in this release. The *Feature* column provides links to the [release plan](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/planned-features), where you can see the official release dates for each feature. The *More information* column provides links to related documentation.

Most of these features must be enabled using [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) before you can use them. Some of the listed features are still in preview, while others may already be generally available.

| Feature area | Feature | More information |
|---|---|---|
| Inventory and logistics | [Contact person data entity export optimization](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/contact-person-data-entity-export-optimization)  | *Not available* |
| Inventory and logistics | [Incremental enhancements for warehouse execution capabilities with scale units](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/incremental-enhancements-warehouse-execution-capabilities-scale-units) |[Message processor messages](../cloud-edge/cloud-edge-message-processor-messages.md)<br><br>[Warehouse inventory adjustment](../cloud-edge/cloud-edge-warehouse-inventory-adjustment.md)<br><br>[Warehouse management workloads for cloud and edge scale units](../cloud-edge/cloud-edge-workload-warehousing.md) |
| Inventory and logistics | [Lookup functionality for Document introduction and Document conclusion fields on Sales quotation page](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/lookup-functionality-document-introduction-document-conclusion-fields-sales-quotation-page) | *Not available* |
| Inventory and logistics | [Warehouse execution with edge scale units on your custom hardware](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/warehouse-execution-edge-scale-units-custom-hardware) | [Deploy edge scale units on custom hardware using LBD](../cloud-edge/cloud-edge-edge-scale-units-lbd.md) |
| Manufacturing | [Manufacturing execution with edge scale units on your custom hardware](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/manufacturing-execution-edge-scale-units-custom-hardware) | [Deploy edge scale units on custom hardware using LBD](../cloud-edge/cloud-edge-edge-scale-units-lbd.md).
| Planning | Query-based planned order firming | [Firm planned orders](../master-planning/planning-optimization/planned-order-firming.md).
| Product information management | [Variant suggestions page improvements](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/variant-suggestions-page-improvements) | [Create predefined product variants](../pim/tasks/create-predefined-product-variants.md) |

## New and updated documentation resources

We have recently added or significantly updated the following help topics. They aren't necessarily related to the new features added for this release, as listed in the previous section, but they may help you to get more out of existing features.

| Feature area | New or updated topics |
|---|---|
| Engineering change management | [Engineering change management FAQs](../engineering-change-management/change-management-faq.md) |
| Procurement and sourcing | [Category requests from vendors](../procurement/category-requests-from-vendors.md) |
| Product information management | [Manage unit of measure](../pim/tasks/manage-unit-measure.md)<br><br>[Product configuration model calculations](../pim/config-model-calculations.md) |
| Production control | [Unified number sequence for job IDs](../production-control/unified-job-ids.md) |
| Transportation management | [LTL classes](../transportation/ltl-class.md)<br><br>[NMFC codes](../transportation/nmfc-codes.md) |
| Warehouse management | [Troubleshoot warehouse batch and serial reservation hierarchies](../warehousing/troubleshoot-warehouse-batch-and-serial-reservation-hierarchies.md) |
| Warehouse management, wave creation and processing | [Wave creation and processing](../warehousing/wave-processing.md)<br><br>[Warehouse parameters for wave processing](../warehousing/wave-warehouse-parameters.md)<br><br>[Wave templates](../warehousing/wave-templates.md)<br><br>[Wave allocation](../warehousing/wave-allocation-method.md)<br><br>[Schedule work creation during wave](../warehousing/configure-wave-schedule-work-creation.md)<br><br>[Containerization](../warehousing/wave-containerization.md)<br><br>[Wave execution notifications](../warehousing/wave-execution-notifications.md) |

## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.19 includes platform updates. To learn more, see [Platform updates for version 10.0.19 of Finance and Operations apps (July 2021)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-19.md).

### Bug fixes

For information about the bug fixes included in each of the updates that are part of 10.0.19, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=575415).

### Dynamics 365: 2021 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2021 release wave 1 plan](/dynamics365-release-plan/2021wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) topic describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
