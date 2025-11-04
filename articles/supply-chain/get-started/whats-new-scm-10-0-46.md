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

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management version 10.0.46. This version  has a build number of 10.0.2428 and is available on the following schedule:

- **Preview of release:** October 2025
- **General availability of release (self-update):** December 2025
- **General availability of release (auto-update):** February 2026

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Inventory and logistics | [Enhance supply chain traceability with tracking attributes](/dynamics365/release-plan/2025wave1/finance-supply-chain/dynamics365-supply-chain-management/track-tracking-attributes-data-collection-supply-chain-traceability) | [Configure data collection fields that are traced in Traceability](../traceability/developer/traceability-configure.md#configure-data-collection-fields-that-are-traced-in-traceability)<br><br>[Find items](../traceability/traceability-app-use.md#find-items) | Enabled by default. |
| Inventory and warehouse management | [Enable quality control with sample management](/dynamics365/release-plan/2025wave2/enterprise-resource-planning/dynamics365-supply-chain-management/enable-quality-control-sample-management) | [Sample management overview](../inventory/quality-sample-management-overview.md) | Feature management:<ul><li>*Advanced quality management*</li><li>*(Preview) Sample management*</li></ul> |
| Inventory and warehouse management | Manage test instrument calibration with Asset Management | [Manage test instrument calibration with Asset Management](../asset-management/preventive-and-reactive-maintenance/asset-management-test-instrument-calibration.md) | Feature management:<ul><li>*Advanced quality management*</li><li>*(Preview) Optional linking of test instruments to maintainable assets*</li></ul> |
| Omnichannel commerce | [Enable custom price attributes for POS and e-commerce](/dynamics365/release-plan/2025wave2/enterprise-resource-planning/dynamics365-commerce/enable-custom-price-attributes-pos-e-commerce) | [Add custom pricing attributes for Dynamics 365 Commerce Point of Sale](../unified-pricing-management/upm-support-custom-attributes.md)<br><br>[Example custom request handler code](../unified-pricing-management/upm-custom-request-handler-example.md) | Enabled by default. |
| Sales and marketing | [Calculate prices and discounts without creating sales orders](/dynamics365/release-plan/2025wave2/enterprise-resource-planning/dynamics365-supply-chain-management/calculate-prices-discounts-without-creating-sales-orders) | [Calculate prices and discounts without creating sales orders](../unified-pricing-management/upm-calculate-prices-without-sales-orders.md) | Enabled by default. |

## <a name="enhancements"></a>Feature enhancements added in this release

The following table lists the feature enhancements that were added in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they're only enhancements, they aren't listed in the [release plan](/dynamics365/release-plan/2024wave2/finance-supply-chain/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

Some of these features aren't visible on your system until you turn them on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) using the name listed here for the *Feature management name* (additional configuration may also be needed). Features that don't show a feature management name are visible by default as of this version of Supply Chain Management, but typically add a new configuration option that you need to set to use the new functionality.

| Feature enhancement | Description |
|---|---|
| **Module:** Asset management<br><br>**Feature management name:** *Remarks can be associated with each change in lifecycle states* | Allows for remarks to be captured on changes in lifecycle states.<br><br>Learn more in [Introduction to assets](../asset-management/objects/introduction-to-objects.md) and [Introduction to work orders](../asset-management/work-orders/introduction-to-work-orders.md). |
| **Module:** Inventory and warehouse management<br><br>**Feature management name:** *View calibration tools for test instruments* | On the **Test instrument calibration** record details page, this feature renames the **Assign calibration tools** menu item to **Calibration tools**. The menu item is also enabled regardless of calibration state. If selected for a closed calibration record, the menu item opens a view showing which tools are assigned to the selected test instrument. Otherwise, the menu item keeps its previous behavior. This change makes it easier to understand and verify the equipment used during calibration, supporting greater accuracy and traceability in your quality processes. |
| **Module:** Master planning<br><br>**Feature management name:** *Consider only released demand and supply as qualified for DDMRP net flow calculation* | Net flow calculations, which are used to determine which buffer zone an item belongs to, are performed with released demand as a qualified demand and released supply as an order quantity. |
| **Module:** Production control<br><br>**Feature management name:** *Auto-complete secondary operation with primary* | Allows for the automatic completion of secondary operations once their corresponding primary operation is completed on the production floor execution interface. The time recorded for the secondary operation matches the time registered for the primary operation. Supervisors can activate this functionality by enabling the **Complete secondary operation with primary** parameter on the route group associated the secondary operation.<br><br>Learn more in [Configure the production floor execution interface](../production-control/production-floor-execution-configure.md). |
| **Module:** Production control<br><br>**Feature management name:** *Material list on the production floor execution interface* | Enables administrators to configure options that allow production floor workers to view the list of materials required for a job directly within the production floor execution interface. It enhances visibility into material requirements, helping workers ensure that all necessary components are available before starting or continuing a production task.<br><br>Learn more in [Configure the production floor execution interface](../production-control/production-floor-execution-configure.md). |
| **Module:** Production control<br><br>**Feature management name:** *Serial number reporting beyond single unit* | Allows workers to use the production floor execution interface to report a quantity greater than one for items that are tracked by serial number but not strictly controlled by it. To enable this functionality, the item must be linked to a tracking dimension group where the **Serial number control setting** is set to *No* for the serial number dimension.<br><br>Learn more in [Configure the production floor execution interface](../production-control/production-floor-execution-configure.md). |
| **Module:** Production control<br><br>**Feature management name:** *(Preview) Record test results from the production floor execution interface* | Allows workers to record test results on quality orders directly from the production floor execution interface.<br><br>Learn more in [Configure the production floor execution interface](../production-control/production-floor-execution-configure.md). |
| **Module:** Sales and marketing<br><br>**Feature management name:** *Unified pricing management pricing rule performance enhancement* | Improves unified pricing management pricing rule performance. |
| **Module:** Sales and marketing<br><br>**Enhancement:** *Create sales orders directly from the navigation pane*<br><br>**Feature management name:** *(None)* | You can now create a new sales order directly from the navigation pane without having to open the **All sales orders** page. To do so, select **Modules** \> **Sales and marketing** \> **Sales orders** \> **Create sales order** from the navigation pane.<br><br>Learn more in [Create sales orders](../sales-marketing/tasks/create-sales-orders.md). |
| **Module:** Warehouse management<br><br>**Feature management name:** *(Preview) Dynamic work classification* | Enables dynamic classification of created warehouse work by writing Power Fx expressions that return the work pool, work priority, work line class overrides, and work line location directive overrides. |
| **Module:** Warehouse management<br><br>**Enhancement:** *Order-committed reservations are now fully supported as part of the "allow reservation on demand order" capability*<br><br>**Feature management name:** *(None)* | In Supply Chain Management version 10.0.46 and later, *order-committed reservations* are fully supported as part of the *allow reservation on demand order* capability. In Supply Chain Management version 10.0.45 and earlier, *outbound shipment order line* transaction reservations didn't support reservations on inventory dimensions below the location in the reservation hierarchy (however, these reservations were supported for *sales order line* transactions).<br><br>Learn more in [Flexible warehouse-level dimension reservation policy](../warehousing/flexible-warehouse-level-dimension-reservation.md). |
| **Module:** Warehouse management<br><br>**Enhancement:** *Outbound shipment processing policies better handle scenarios where shipped quantity differs from the ordered quantity*<br><br>**Feature management name:** *(None)* | The **Enforce shipment to order matching** option on the **Outbound shipment processing policies** page now works differently when set to *Yes*. In version 10.0.46 and later, when you confirm a shipment, the policy instructs the system to update the delivery remainder on the source order line to reflect the quantity that was actually shipped. If you later reverse the shipment, the delivery remainder is restored to the original ordered quantity. In version 10.0.45 and earlier, if the shipped quantity differs from the ordered quantity, you needed to manually update the delivery remainder to match the shipped quantity before you confirm the shipment.<br><br>Learn more in [Outbound shipment processing policies](../warehousing/outbound-load-handling.md#outbound-shipment-policies) and [Warehouse management only mode with external shared warehouses](../warehousing/wms-only-mode-external-shared-warehouse.md). |

## Preview features that are now generally available

The following table lists the features that were introduced as public preview features in a previous version and became generally available in version 10.0.46. As with other new features, most of these features are turned off by default, so you must turn them on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) if you want to use them.

| Module | Feature name | More information |
|--|--|--|
| Inventory and warehouse management | Acceptance sampling | [Acceptance sampling](../inventory/quality-acceptance-sampling.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.45 (September 2025)](whats-new-scm-10-0-45.md) |
| Master planning | Lean manufacturing for Planning Optimization | [Lean manufacturing for Planning Optimization](../master-planning/lean-for-planning-optimization.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.45 (September 2025)](whats-new-scm-10-0-45.md) |
| Product information management | Cross-company data sharing for products | [Cross-company product sharing](../pim/share-products-across-companies.md)<br><br>[What's new or changed in Dynamics 365 Supply Chain Management 10.0.32 (April 2023)](whats-new-scm-10-0-32.md) |

## Related information

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.46 includes platform updates. Learn more in [Platform updates for version 10.0.46 of Finance and Operations apps (September  2024)](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-46.md). <!-- KFM: Check link -->

For information about the bug fixes included in each of the updates that are part of version 10.0.46, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=1070810).

### Dynamics 365: 2025 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Microsoft Dynamics 365: 2025 release wave 2 plan](/dynamics365/release-plan/2025wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
