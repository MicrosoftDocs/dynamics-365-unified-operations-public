---
title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.41 (September 2024)
description: Learn about features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.41 with a table outlining feature areas. 
author: kamaybac
ms.author: kamaybac
ms.topic: conceptual
ms.date: 08/07/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# What's new or changed in Dynamics 365 Supply Chain Management 10.0.41 (September 2024)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management version 10.0.41. This version has a build number of 10.0.2015 and is available on the following schedule:

- **Preview of release:** July 2024
- **General availability of release (self-update):** September 2024
- **General availability of release (auto-update):** October 2024

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Copilot and AI innovation | Follow-up questions in the Copilot sidecar | [Responsible AI FAQ for Follow-up questions in the Copilot sidecar (preview)](../../fin-ops-core/fin-ops/copilot/faq-copilot-suggested-questions.md) | Feature Management:<br>*(Preview) AI-generated follow-up questions for the Copilot sidecar in finance and operations apps*  |
| Inventory and logistics | [Enable quality control for goods-in-transit orders](/dynamics365/release-plan/2024wave1/finance-supply-chain/dynamics365-supply-chain-management/enable-quality-control-goods-in-transit-orders) | [Quality orders](../inventory/quality-orders.md) | Feature management:<br>*(Preview) Follow-up questions in the Copilot sidecar* |
| Inventory and logistics | Pair sales order with transfer order <!--KFM: Won't be on release plan --> | *Coming soon* | Feature management:<br>*(Preview) Pair transfer order lines with sales order lines* |
| Inventory and logistics | [Add transactions when recalculating weighted average](/dynamics365/release-plan/2024wave1/finance-supply-chain/dynamics365-supply-chain-management/recalculate-weighted-average-cost-including-physical-transaction) | [Options for including physical value in cost calculations](../cost-management/include-physical-value.md) | Feature management:<br>*(Preview) Recalculation for Weighted Average Cost including Physical Transaction* |
| Inventory and logistics | [Sync external changes through Inventory Visibility](/dynamics365/release-plan/2024wave1/finance-supply-chain/dynamics365-supply-chain-management/sync-external-inventory-changes-through-inventory-visibility) | *Coming soon* | Feature management:<br>*Inventory Visibility transaction integration* |
| Inventory and logistics | [Trace goods through the supply chain](/dynamics365/release-plan/2024wave1/finance-supply-chain/dynamics365-supply-chain-management/trace-goods-through-supply-chain) | [Traceability overview](../traceability/traceability-overview.md) | Feature management and Power Apps.<br><br>See [Install and update Traceability](../traceability/developer/traceability-install.md) |
| Inventory and logistics | [Track time-series inventory in Inventory Visibility](/dynamics365/release-plan/2024wave1/finance-supply-chain/dynamics365-supply-chain-management/track-time-series-inventory-inventory-visibility) | [Track time-series inventory in Inventory Visibility](../inventory/inventory-visibility-track-atp.md) | Feature management:<br>*Inventory Visibility integration with ATP* |
| Manufacturing and asset management | [Decouple production registration from time and attendance](/dynamics365/release-plan/2024wave1/finance-supply-chain/dynamics365-supply-chain-management/decouple-production-registration-time-attendance) | [Registration for manufacturing execution](../production-control/registration-manufacturing-execution.md) | Feature management:<br>*Skip time adjustments when calculating actual cost per production order* |
| Manufacturing and asset management | [Register time spent working on projects for production](/dynamics365/release-plan/2024wave1/finance-supply-chain/dynamics365-supply-chain-management/register-time-spent-working-projects-production) | [Registration for manufacturing execution](../production-control/registration-manufacturing-execution.md) | Feature management:<br>*Skip time adjustments when calculating actual cost per production order* |
| Procurement | [Approve POs and requisitions from mobile device](/dynamics365/release-plan/2024wave1/finance-supply-chain/dynamics365-supply-chain-management/approve-purchase-orders-requisitions-mobile-device) | [Approvals Management mobile app overview](../approval-management-mobile-app/approval-management-app-overview.md) | Feature management and Power Apps.<br><br>See [Onboard the Approvals Management mobile app](../approval-management-mobile-app/developer/onboard-approval-app.md) |
| Warehouse management | Outbound shipment processing policies <!--KFM: Won't be on release plan --> | [Outbound shipment processing policies](../warehousing/outbound-load-handling.md#outbound-shipment-policies) | Enabled by default |
| Warehouse management | Unannounced returns in Warehouse management only mode <!--KFM: Won't be on release plan --> | [Configure unannounced returns in Warehouse management only mode](../warehousing/wms-only-mode-unannounced-returns-setup.md) | Feature management:<br>*Warehouse management only mode* |

## <a name="enhancements"></a>Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they're only enhancements, they aren't listed in the [release plan](/dynamics365/release-plan/2024wave1/finance-supply-chain/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

Some of these features aren't visible on your system until you turn them on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) using the name listed here for the *Feature management name* (additional configuration may also be needed). Features that don't show a feature management name are visible by default as of this version of Supply Chain Management, but typically add a new configuration option that you need to set to use the new functionality.

| Feature enhancement | Description |
|---|---|
|<p>**Module:** Asset management</p><p>**Feature management name:** *(Preview) Print work order document attachments*</p> | Lets you print work order reports that include PDF documents attached to work order headers and lines. |
|<p>**Module:** Inventory and warehouse management</p><p>**Feature management name:** *(Preview) Inventory dimensions with license plate id cleanup*</p> | Adds the ability to clean up inventory dimensions with license plate IDs that are more than one year old, are financial updated, and have no on-hand inventory. |
|<p>**Module:** Master planning</p><p>**Feature management name:** *Enable the calculation of Batch CTP even when plan run ends with errors.*</p> | Allows for CTP-confirmed dates to be calculated for sales order lines, even when the Planning Optimization run ends with errors. Confirmed dates will be calculated for sales order lines that didn't have any errors. To enable or disable this behavior, use the **Calculate Batch CTP even with errors** setting in the plan settings for the dynamic plan. |
|<p>**Module:** Product information management</p><p>**Feature management name:** *(Preview) Enable foreign trade parameters for all countries*</p> | Enables foreign trade parameters for all countries. |
|<p>**Module:** Production control</p><p>**Feature management name:** *Add filter to hide completed jobs on the Kanban board*</p> | Adds a **Hide completed jobs** checkbox to the Kanban board. The option lets you choose to hide all completed jobs, which provides a cleaner and more focused view. |
|<p>**Module:** Procurement and sourcing</p><p>**Feature management name:** *Choose whether to consolidate sales orders for direct deliveries*</p> | Makes it possible to choose whether the *Create direct delivery orders* batch job should consolidate qualifying sales orders into a single purchase order when creating a direct delivery. You can control this behavior using the new **Consolidate sales orders for direct deliveries** setting on the **Delivery** tab of the **Procurement and sourcing parameters** page. When you enable this feature, the system defaults to not consolidating qualifying sales orders, which is different from the previous behavior. Previously, the batch job always consolidated qualifying sales orders. |
|<p>**Module:** Procurement and sourcing</p><p>**Feature management name:** *Enable purch parameters to control delivery information sync on sales and purchase orders*</p> | Controls the creating and updating of the **Delivery mode** and **Delivery terms** fields on purchase orders. The new parameters are added for stock and direct delivery scenarios. |
|<p>**Module:** Sales and marketing</p><p>**Feature management name:** *Price and discount search for derived line creation*</p> | Adds the ability to search for new prices in trade agreements for derived intercompany sales orders and sales order lines. |
| <p>**Module:** Warehouse management</p><p>**Enhancement:** *Container label printing improvement*</p><p>**Feature management name:** *(None)*</p> | <p>The system now allows printing of container labels when closing a container.</p><p>For more information, see [Container label layouts and printing](../warehousing/print-container-labels.md).</p> |
| <p>**Module:** Warehouse management</p><p>**Enhancement:** *Custom label layout data source parameters*</p><p>**Feature management name:** *(None)*</p> | <p>On a custom label layout data source, it is now possible to define parameters that the user can specify when printing labels. These parameters can be then used in label layouts in addition to values retrieved from table records, for example, to specify a quantity of labels to print.</p><p>For more information, see [Custom label layouts and printing](../warehousing/custom-label-layouts-and-printing.md)</p> |
| <p>**Module:** Warehouse management</p><p>**Enhancement:** *Dynamic printer selection improvements*</p><p>**Feature management name:** *(None)*</p> | <p>Lets you assign default printers to specific mobile devices.</p><p>For more information, see [Dynamic printer selection](../warehousing/dynamic-printing-selection.md).</p> |
| <p>**Module:** Warehouse management</p><p>**Enhancement:** *Load packing slip posting*</p><p>**Feature management name:** *(None)*</p> | <p>Introduces the capability to execute the sales order packing slip procedure as background batch tasks, which is triggered according to the data associated with warehouse loads.</p><p>For more information, see [Load packing slip posting](../warehousing/outbound-load-handling.md#load-packing-slip-posting).</p> |
| <p>**Module:** Warehouse management</p><p>**Enhancement:** *Location directives Locate by `ASN` for Transfer receipt*</p><p>**Feature management name:** *(None)*</p> | <p> Introduces the capability to put all the items on a license plate in one location and prevents the system from making you split the items into different locations for ASN (license plate receiving) of transfer orders. </p><p>For more information, see [Location directives using locate by ASN](../warehousing/create-location-directive.md#locate-by).</p> |

## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.41 includes platform updates. To learn more, see [Platform updates for version 10.0.41 of Finance and Operations apps (September 2024)](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-41.md).

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.41, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=948711).

### Dynamics 365: 2024 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2024 release wave 1 plan](/dynamics365/release-plan/2024wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
