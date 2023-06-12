---
title: Preview of Dynamics 365 Supply Chain Management 10.0.35 (July 2023)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.35. 
author: kamaybac
ms.author: kamaybac
ms.reviewer: kamaybac
ms.search.form:
ms.topic: conceptual
ms.date: 03/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Preview of Dynamics 365 Supply Chain Management 10.0.35 (July 2023)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management preview version 10.0.35. This version has a build number of 10.0.1627 and is available on the following schedule:

- **Preview of release:** May 2023
- **General availability of release (self-update):** July 2023
- **General availability of release (auto-update):** August 2023

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Planning | [Plan for manufacturing with Planning Optimization](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-supply-chain-management/plan-manufacturing-planning-optimization) | *Coming soon* | Enabled by default |
| Warehouse management | [Capture multiple GS1 label segments simultaneously](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-supply-chain-management/capture-multiple-gs1-label-segments-simultaneously) | [GS1 bar codes](../warehousing/gs1-barcodes.md) | Enabled by default |
| Warehouse management | Optimize location directive queries | [Optimize location directive queries](../warehousing/location-directives-optimize.md) | Enabled by default |
| Warehouse management | [Optimize warehouse management implementation and maintenance](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-supply-chain-management/optimize-warehouse-management-implementation-maintenance) | <p>[Get started with setting up the Warehouse management module](../warehousing/get-started-with-setting-up-module.md)<p>[Print labels using an external service](../warehousing/label-printing-using-external-label-service.md)</p><p>[Print labels using the Loftware NiceLabel label service solution](../warehousing/label-printing-using-nicelabel.md)</p><p>[Print labels using the Seagull Scientific BarTender label service solution](../warehousing/label-printing-using-bartender.md)</p><p>[Warehouse groups](../warehousing/warehouse-groups.md)</p><p>[Test location directives with acceptance tests](../warehousing/location-directive-acceptance-tests.md)</p><p>[Enable warehousing telemetry with Application Insights](../warehousing/application-insights-warehousing.md)</p><p>[Monitor Warehouse Management usage and performance](../warehousing/application-insights-monitor-usage-performance.md)</p> | Enabled by default |
| Warehouse management | [Optimize warehouse management processes](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-supply-chain-management/optimize-warehouse-management-processes) | [Analyze warehouse material movement through process mining](../warehousing/warehouse-material-movement-analysis.md) | Enabled by default |

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they're only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

If you want to turn any of these features on or off, you must do so in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Module | Feature name in feature management | More information |
|---|---|---|
| Procurement and sourcing | *Filter by date when assessing supply risks* | Adds a date filter to the supply risk assessment workspace. The filter lets you choose how far into the past to look when calculating vendor performance. You can therefore set up performance calculations that only consider recent events (which are most relevant) while excluding older events. |
| Procurement and sourcing | *Check purchase order expenditure reviewers setup before enabling workflow.* | Checks for purchase order expenditure reviewers setups when activating a workflow. This feature prevents incomplete workflow configurations that use the purchase order expenditure reviewers participants provider from being enabled. |
| Production control | *Enable users to hide or show information in the Gantt chart* | Lets users choose which of the following columns to hide or show on the left side of the Gantt chart used for scheduled activities in production, project accounting, and asset management: **Start/end date and time**, **Operation number**, **Job type**, and **Resource**. |
| Inventory and warehouse management | *Cascade transfer order header date change to lines* | Automatically updates line dates when a transfer order header's ship or receipt date is changed. |
| Sales and marketing | *(Preview) Pricing management workspace* | Provides a pricing management workspace, which lets sales managers know about impending price rule status changes and supports their choice to modify pricing policies. Sales managers can perform light tasks to enable or disable the pricing rules without leaving the workspaces. |
| Sales and marketing | *Keep existing sorting on intercompany sales lines when updating them* | Adds an option that lets users keep existing sorting on intercompany sales line update. |
| Transportation management | *(Preview) Specify Goods In Transit Order when receiving via mobile device.* | Enables workers using a mobile device to choose which specific goods to receive when multiple goods-in-transit orders exist for the same voyage, container, item number, and purchase order number.<br><br>See also [Specify goods-in-transit orders when receiving with a mobile device](in-transit-processing.md#specify-GIT-order). |
| Transportation management | *(Preview) Split Goods In Transit Order quantity and assign batch/serial number when receiving via mobile device.* | Enables workers using a mobile device to assign multiple batch/serial numbers for various quantities of goods received from a goods-in-transit order. All of the assigned batch/serial numbers will be consolidated into one work record and then processed together.<br><br>See also [Assign batch/serial numbers when receiving with a mobile device](in-transit-processing.md#batch-serial). |

## New and updated documentation resources

We have recently added or significantly updated the following help articles. These articles aren't necessarily related to the new features that were added for this release, as listed in the previous sections. However, they might help you get more out of existing features.

| Feature area | New or updated articles |
|---|---|
| Warehouse management | [Inspect details of active Warehouse Management mobile app sessions](../warehousing/work-user-sessions.md) |

## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.35 includes platform updates. To learn more, see [Platform updates for version 10.0.35 of Finance and Operations apps (July 2023)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-35.md).

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.35, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=817204&dbType=3&qc=31515199fa35fbda929b42fcfa31225e2c30e55eef262c4f917d98d8cc57d42d).

### Dynamics 365 and industry clouds: 2023 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2023 release wave 1 plan](/dynamics365/release-plan/2023wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
