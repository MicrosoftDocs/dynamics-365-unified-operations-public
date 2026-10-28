---
title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.50 (December 2026)
description: Learn about features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.50 with a table outlining feature areas. 
author: kamaybac
ms.author: kamaybac
ms.reviewer: kamaybac
ms.search.form:
ms.topic: whats-new
ms.date: 10/12/2026
ms.update-cycle: 1095-days
ms.custom:
  - bap-template
  - evergreen
---

# What's new or changed in Dynamics 365 Supply Chain Management 10.0.50 (December 2026)

[!INCLUDE [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management version 10.0.50. This version has a build number of 10.0.2919 and is available on the following schedule:

- **Preview of release:** October 2026
- **General availability of release (self-update):** December 2026
- **General availability of release (auto-update):** January 2027

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature | More information | Enabled by |
| --- | --- | --- | --- |
| Inventory and warehouse management | Approval workflow for CAPA cases | [CAPA case approval workflows](../inventory/capa-approval-workflow.md) | Feature management:<br>*CAPA case approval workflow* |
| Inventory and warehouse management | Approval workflow for quality orders | [Quality order approval workflows](../inventory/quality-order-approval-workflow.md) | Feature management:<br>*Quality order approval workflow* |
| Inventory and warehouse management | Batch stability testing | [Batch stability testing](../inventory/quality-batch-stability-testing.md) | Feature management:<br>*(Preview) Batch stability testing* |
| Production control | Create report-as-finished journal lines from a proposal | [Create report-as-finished journal lines from a proposal](../production-control/create-report-finished-journal-lines.md) | Feature management:<br>*(Preview) Create report as finished journal lines from a proposal* |
| Production control | Production scrap reason codes | [Flexible production scrap reason codes](../production-control/production-scrap-reason-codes.md) | Feature management:<br>*(Preview) Flexible production scrap reason codes* |
| Rental management | Rental management | [Rental management overview](../rental-management/rental-management-overview.md) | Feature management:<br>*(Preview) Rental management* |
| Sales and marketing | Automatically assign the sales responsible worker for a sales order based on the customer | [Default the sales responsible worker from the customer](../sales-marketing/default-sales-responsible-from-customer.md) | Enabled by default |
| Sales and marketing | Exclude purchase, production, and inbound transfer supply from ATP calculations | [Exclude purchase, production, or inbound transfer supply from ATP calculations](../sales-marketing/available-to-promise-supply-exclusions.md) | Feature management:<br>*Configurable ATP with Receipt Control* |
| Warehouse management | Capture photos and videos in the Warehouse Management mobile app | [Capture photos and videos by using Warehouse Management mobile app detours](../warehousing/warehouse-app-media-capture.md) | Feature management:<br>*(Preview) Media capture in the warehouse mobile app* |
| Warehouse management | Despatch advice for transfer orders to external shared warehouses | [Despatch advice messages for transfer orders to external shared warehouses](../warehousing/wms-only-mode-transfer-order-despatch-advice.md) | Enabled by default |

<a name="enhancements"></a>

## Feature enhancements added in this release

The following table lists the feature enhancements that were added in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they're only enhancements, they're not listed in the [AI at Work Roadmap](https://www.microsoft.com/microsoft-365/roadmap) and might not be mentioned elsewhere in the documentation. To ensure that these enhancements don't conflict with your existing customizations or preferences, most of these features are turned off by default. To use them, turn them on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) unless otherwise noted.

| Module | Feature name | More information |
|---|---|---|
| Asset Management | *Financial tags for Asset management forecasts* | Adds support for financial tags on Asset management job type and work order forecasts.<br><br>This feature is new and turned on by default in version 10.0.50. |
| Asset Management | *Maintenance plan scheduling API* | Adds an API that queues maintenance plan scheduling as a batch job for the maintenance plans, assets, or functional locations that you select. |
| Inventory and warehouse management | *Financial tags for inventory to deliver* | Enables financial tag propagation for inventory-to-deliver quality and quarantine orders. |
| Inventory and warehouse management | *Inventory Visibility integration with Commerce Scale unit managed identity* | Allows Inventory Visibility integration to be turned on using the Commerce Scale unit managed identity, without requiring the Microsoft Entra application ID, secret, or tenant ID.<br><br>This feature is new and turned on by default in version 10.0.50. |
| Inventory and warehouse management | *Optimize transaction scope for Inventory management reports* | When this feature is enabled, Inventory management SQL Server Reporting Services (SSRS) preprocessing reports generate data outside the default report transaction scope. This approach prevents long-running transactions and reduces transaction log growth when reports process large volumes of data. Temporary report tables remain on the default connection, so extensions to report data providers can continue to read and update them.<br><br>This feature is new and turned on by default in version 10.0.50. |
| Master Planning | *Support of production pool and production group in planned orders* | Adds the production pool and production group to planned orders. The values are copied from the released product when planned production orders, planned kanbans, planned transfer orders, planned purchase orders, and planned batch orders are created. |
| Master Planning | *Support tracking dimension inheritance for BOM lines* | Lets you define tracking dimension inheritance policies and assign them to BOM lines. The values of the tracking dimensions that a policy specifies are then propagated across planned orders, according to the inheritance setup on the BOM lines. Tracking dimension inheritance policies apply only to Planning Optimization. |
| Master Planning | *Use warehouse calendar for planned purchase order receipt date calculations with Planning Optimization* | When this feature and the **Supplier requested and confirmed shipment dates** parameter in Procurement and sourcing are both turned on, Planning Optimization schedules the receipt of planned purchase orders by using the warehouse calendar instead of the vendor purchase calendar. Receipt dates therefore align with the open days on the warehouse calendar. If no warehouse calendar is set up, the coverage group calendar is used as the receipt calendar instead. This change also affects action calculations, because they use the receipt calendar to determine closed days. |
| Production Control | *Configure license plate label printing for co-products and by-products* | Adds an option to production floor execution configurations that prevents license plate labels from being printed for co-products and by-products when production is reported as finished. |
| Production Control | *Financial tags for plan to produce* | Enables financial tag propagation for plan-to-produce production orders, routes, journals, and manufacturing execution.<br><br>This feature is new and turned on by default in version 10.0.50. |
| Production Control | *Remove Dynamics 365 Guides from the production floor execution interface* | Removes Dynamics 365 Guides from manufacturing execution, setup, and Guides imports, because Dynamics 365 Guides is no longer supported.<br><br>This feature is new and mandatory in version 10.0.50. |
| Production Control | *Restrict actions available on tabs in the production floor execution interface configuration* | When you configure tabs for the production floor execution interface, this feature limits the list of available actions to the actions that are relevant to the selected main view. Only job-related actions are available on the primary toolbar, and only actions that aren't job related are available on the secondary toolbar. |
| Sales and marketing | *Configurable ATP with Receipt Control* | Lets you configure whether purchase orders, transfer orders, and production orders are considered as receipt sources during Available-to-Promise (ATP) calculation. |
| Sales and marketing | *Configurable pricing attributes feature* | Lets you define pricing attributes from table fields and resolve their values both in headquarters and in Commerce channels. |
| Sales and marketing | *Consider inventory status in Available-to-Promise (ATP) calculations* | Lets Available-to-Promise (ATP) calculations consider the inventory status storage dimension when they determine ATP quantities, calculated delivery dates, ATP inquiries, and delivery date simulations. A new parameter on the **Accounts receivable parameters** page controls this behavior. It improves ATP accuracy for organizations that use inventory status to segment inventory across channels, business processes, or operational flows. |
| Sales and marketing | *Optimize transaction scope for sales and marketing reports* | When this feature is enabled, sales and marketing SQL Server Reporting Services (SSRS) preprocessing reports generate data outside the default report transaction scope. This approach prevents long-running transactions and reduces transaction log growth when reports process large volumes of data. Temporary report tables remain on the default connection, so extensions to report data providers can continue to read and update them.<br><br>This feature is new and turned on by default in version 10.0.50. |
| Sales and marketing | *Optimize transaction scope for Sales reports* | When this feature is enabled, Sales SQL Server Reporting Services (SSRS) preprocessing reports generate data outside the default report transaction scope. This approach prevents long-running transactions and reduces transaction log growth when reports process large volumes of data. Temporary report tables remain on the default connection, so extensions to report data providers can continue to read and update them.<br><br>This feature is new and turned on by default in version 10.0.50. |
| Sales and marketing | *Unified Pricing Management Advanced Price Report* | Prices only the products whose prices changed since the previous price report run, instead of pricing the whole report scope every time. Each run still reports every price, because the prices that didn't change are carried forward from the previous run. The first run after you turn on this feature prices the whole scope. |
| Sales and marketing | *Unified Pricing Margin check on POS* | Evaluates the resulting margin when a price override or a manual discount is entered at the point of sale (POS). If the margin is too low, the change either requires manager approval or is blocked. This feature requires Unified pricing management. |
| Warehouse management | *Optimize transaction scope for warehouse management reports* | When this feature is enabled, warehouse management SQL Server Reporting Services (SSRS) preprocessing reports generate data outside the default report transaction scope. This approach prevents long-running transactions and reduces transaction log growth when reports process large volumes of data. Temporary report tables remain on the default connection, so extensions to report data providers can continue to read and update them.<br><br>This feature is new and turned on by default in version 10.0.50. |

## Preview features that are now generally available

The following table lists the features that were introduced as public preview features in a previous version and became generally available in version 10.0.50. As with other new features, most of these features are turned off by default, so you must turn them on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) if you want to use them.

| Module | Feature name | More information |
| --- | --- | --- |
| Production Control | *Record test results from the production floor execution interface* | Lets workers record test results on quality orders directly from the production floor execution interface. |

## Features turned on by default in this release

The following table lists the features that became turned on by default in version 10.0.50. You can still turn these features off in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) if necessary.

| Module | Feature name | More information |
| --- | --- | --- |
| Asset Management | *Financial tags for Asset management forecasts* | Adds support for financial tags on Asset management job type and work order forecasts.<br><br>This feature is new and turned on by default in version 10.0.50. |
| Inventory and warehouse management | *Inventory Visibility integration with Commerce Scale unit managed identity* | Allows Inventory Visibility integration to be turned on using the Commerce Scale unit managed identity, without requiring the Microsoft Entra application ID, secret, or tenant ID.<br><br>This feature is new and turned on by default in version 10.0.50. |
| Inventory and warehouse management | *Optimize transaction scope for Inventory management reports* | When this feature is enabled, Inventory management SQL Server Reporting Services (SSRS) preprocessing reports generate data outside the default report transaction scope. This approach prevents long-running transactions and reduces transaction log growth when reports process large volumes of data. Temporary report tables remain on the default connection, so extensions to report data providers can continue to read and update them.<br><br>This feature is new and turned on by default in version 10.0.50. |
| Production Control | *Financial tags for plan to produce* | Enables financial tag propagation for plan-to-produce production orders, routes, journals, and manufacturing execution.<br><br>This feature is new and turned on by default in version 10.0.50. |
| Sales and marketing | *Optimize transaction scope for sales and marketing reports* | When this feature is enabled, sales and marketing SQL Server Reporting Services (SSRS) preprocessing reports generate data outside the default report transaction scope. This approach prevents long-running transactions and reduces transaction log growth when reports process large volumes of data. Temporary report tables remain on the default connection, so extensions to report data providers can continue to read and update them.<br><br>This feature is new and turned on by default in version 10.0.50. |
| Sales and marketing | *Optimize transaction scope for Sales reports* | When this feature is enabled, Sales SQL Server Reporting Services (SSRS) preprocessing reports generate data outside the default report transaction scope. This approach prevents long-running transactions and reduces transaction log growth when reports process large volumes of data. Temporary report tables remain on the default connection, so extensions to report data providers can continue to read and update them.<br><br>This feature is new and turned on by default in version 10.0.50. |
| Warehouse management | *Optimize transaction scope for warehouse management reports* | When this feature is enabled, warehouse management SQL Server Reporting Services (SSRS) preprocessing reports generate data outside the default report transaction scope. This approach prevents long-running transactions and reduces transaction log growth when reports process large volumes of data. Temporary report tables remain on the default connection, so extensions to report data providers can continue to read and update them.<br><br>This feature is new and turned on by default in version 10.0.50. |

## Features becoming mandatory in this release

The following table lists the features that became mandatory in version 10.0.50. These features still appear in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) but you can no longer turn them off.

| Module | Feature name | More information |
| --- | --- | --- |
| Production Control | *Remove Dynamics 365 Guides from the production floor execution interface* | Removes Dynamics 365 Guides from manufacturing execution, setup, and Guides imports, because Dynamics 365 Guides is no longer supported.<br><br>This feature is new and mandatory in version 10.0.50. |

## Related information

### Platform updates for finance and operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.50 includes platform updates. Learn more in [Platform updates for version 10.0.50 of Finance and Operations apps (December 2026)](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-50.md).

For information about the bug fixes included in version 10.0.50, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=1198101).

### What's new or changed in the Warehouse Management mobile app

The Warehouse Management mobile app is updated regularly following a different schedule than Supply Chain Management. For information about the latest versions and features, go to [What's new or changed in the Warehouse Management mobile app](../warehousing/warehouse-app-whats-new.md).

### What's new or changed in Demand planning

Demand planning in Dynamics 365 Supply Chain Management is updated regularly following a different schedule than Supply Chain Management. For information about the latest versions and features, go to [What's new or changed in Demand planning](../demand-planning/whats-new-demand-planning.md).

### What's new or changed in Planning Optimization

Microsoft updates Planning Optimization monthly. However, based on business requirements, the product team occasionally releases other updates between the scheduled releases. For information about the latest versions and features, go to [Planning Optimization release process and release history](../master-planning/planning-optimization/release-process.md).

### AI at Work Roadmap

Want to know about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [AI at Work Roadmap](https://www.microsoft.com/microsoft-365/roadmap). It captures all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article describes features that are removed or scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

Before Microsoft removes any feature from the product, it announces the deprecation notice in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article 12 months before the removal.

For breaking changes that only affect compilation time but are binary compatible with sandbox and production environments, the deprecation time is less than 12 months. Typically, these changes are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
