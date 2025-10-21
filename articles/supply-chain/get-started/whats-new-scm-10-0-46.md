---
title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.46 (December 2025)
description: Learn about features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.46 with a table outlining feature areas. 
author: kamaybac
ms.author: kamaybac
ms.reviewer: kamaybac
ms.search.form:
ms.topic: whats-new
ms.date: 10/24/2025
ms.update-cycle: 1095-days
ms.custom:
  - bap-template
  - evergreen
---

# What's new or changed in Dynamics 365 Supply Chain Management 10.0.46 (December 2025)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management version 10.0.46. This version <!-- has a build number of 10.0.#### and --> is available on the following schedule:

- **Preview of release:** October 2025
- **General availability of release (self-update):** December 2025
- **General availability of release (auto-update):** February 2025

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Inventory and logistics | [Enhance supply chain traceability with tracking attributes](/dynamics365/release-plan/2025wave1/finance-supply-chain/dynamics365-supply-chain-management/track-tracking-attributes-data-collection-supply-chain-traceability) | [Configure data collection fields that are traced in Traceability](../traceability/developer/traceability-configure.md#configure-data-collection-fields-that-are-traced-in-traceability)<br><br> [Find items](../traceability/traceability-app-use.md#find-items) | Enabled by default. |
| Inventory and warehouse management | [Enable quality control with sample management](/dynamics365/release-plan/2025wave2/enterprise-resource-planning/dynamics365-supply-chain-management/enable-quality-control-sample-management) | *Coming soon* | Feature management:<ul><li>*Advanced quality management*</li><li>*(Preview) Sample management*</li></ul> | 
| Inventory and warehouse management | Manage test instrument calibration with Asset Management | *Coming soon* | Feature management:<ul><li>*Advanced quality management*</li><li>*(Preview) Optional linking of test instruments to maintainable assets*</li></ul> |
| Sales and marketing | [Calculate prices and discounts without creating sales orders](/dynamics365/release-plan/2025wave2/enterprise-resource-planning/dynamics365-supply-chain-management/calculate-prices-discounts-without-creating-sales-orders) | [Calculate prices and discounts without creating sales orders](../unified-pricing-management/upm-calculate-prices-without-sales-orders.md) | Enabled by default. |

## <a name="enhancements"></a>Feature enhancements added in this release

The following table lists the feature enhancements that were added in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they're only enhancements, they aren't listed in the [release plan](/dynamics365/release-plan/2024wave2/finance-supply-chain/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

Some of these features aren't visible on your system until you turn them on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) using the name listed here for the *Feature management name* (additional configuration may also be needed). Features that don't show a feature management name are visible by default as of this version of Supply Chain Management, but typically add a new configuration option that you need to set to use the new functionality.

| Feature enhancement | Description |
|---|---|
| **Module:** Warehouse management<br><br>**Enhancement:** *Outbound shipment processing policies better handle scenarios where shipped quantity differs from the ordered quantity*<br><br>**Feature management name:** *(None)* | The **Enforce shipment to order matching** option on the **Outbound shipment processing policies** page now works differently when set to *Yes*. In version 10.0.46 and later, when you confirm a shipment, the policy instructs the system to update the delivery remainder on the source order line to reflect the quantity that was actually shipped. If you later reverse the shipment, the delivery remainder is restored to the original ordered quantity. In version 10.0.45 and earlier, if the shipped quantity differs from the ordered quantity, you needed to manually update the delivery remainder to match the shipped quantity before you confirm the shipment.<br><br>Learn more in [Outbound shipment processing policies](../warehousing/outbound-load-handling.md#outbound-shipment-policies) and [Warehouse management only mode with external shared warehouses](../warehousing/wms-only-mode-external-shared-warehouse.md). |
| **Module:** Warehouse management<br><br>**Enhancement:** *Order-committed reservations are now fully supported as part of the "allow reservation on demand order" capability*<br><br>**Feature management name:** *(None)* | In Supply Chain Management version 10.0.46 and later, *order-committed reservations* are fully supported as part of the *allow reservation on demand order* capability. In Supply Chain Management version 10.0.45 and earlier, *outbound shipment order line* transaction reservations didn't support reservations on inventory dimensions below the location in the reservation hierarchy (however, these reservations were supported for *sales order line* transactions).<br><br>Learn more in [Flexible warehouse-level dimension reservation policy](../warehousing/flexible-warehouse-level-dimension-reservation.md). |

## Related information

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.46 includes platform updates. Learn more in [Platform updates for version 10.0.46 of Finance and Operations apps (September  2024)](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-46.md). <!-- KFM: Check link -->

<!-- 
### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.46, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=####).

-->

### Dynamics 365: 2025 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Microsoft Dynamics 365: 2025 release wave 2 plan](/dynamics365/release-plan/2025wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
