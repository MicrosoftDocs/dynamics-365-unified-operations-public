---
# required metadata

title: Preview of Dynamics 365 Supply Chain Management 10.0.17 (April 2021) 
description: This topic describes features that are either new or changed in Dynamics 365 Supply Chain Management 10.0.17. 
author: kamaybac
manager: annbe
ms.date: 11/20/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: kamaybac
ms.search.validFrom: 2020-11-31 
ms.dyn365.ops.version: 10.0.17
---

# Preview of Dynamics 365 Supply Chain Management 10.0.17 (April 2021)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic lists features that are either new or changed in the Microsoft Dynamics 365 Supply Chain Management preview of version 10.0.17. This version has a build number of 10.0.689 <!--KFM: Update to final build number --> and is available as follows:

- **Preview of release:** February 2021
- **General availability of release (self-update):** March 2021
- **General availability of release (auto-update):** April 2021

## Features included in this release

The following features are included in this release. Some of the listed features are still in preview, while others may already be generally available. Follow the links to the [release plan](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/finance-operations/dynamics365-supply-chain-management/planned-features) to see the official release dates for each feature.

- Apply rules for grouping work orders while running a maintenance plan
- Approve and save vendor-submitted bank details
- Asset Management mobile workspace
- Bill customers for maintenance work
- Coverage time fence support for Planning Optimization
- Enable change management on existing products
- Inventory Visibility Add-in for Dynamics 365 Supply Chain Management <!--KFM: Announced for November, which was public preview. We have a new topic about how to configure it, so maybe move this down to the next section with a link to that new topic, if it's ready. -->
- Landed cost
- Manufacturing execution with scale units in the cloud
- [Packing vs. storage dimensions](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/dynamics365-supply-chain-management/packing-vs.-storage-dimensions)<br> - For more information, see <!--KFM: Add new topic link -->
- Plan maintenance based on accumulated asset counter values
- Purchase requisition support for Planning Optimization
- Saved views for inventory and logistics
- Saved views for planned orders
- Saved views for production control
- Schedule warehouse work creation
- Set default financial dimensions for inventory standard cost revaluation vouchers
- [Small parcel shipping (SPS)](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/dynamics365-supply-chain-management/small-package-shipping-sps)<br> - For more information, see <!--KFM: Add new topic link -->
- Warehouse execution with scale units in the cloud
- Warehouse management mobile application

Most of these features must be enabled using [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) before you can use them.

## New and updated documentation resources

We have recently added or significantly updated the following help topics. They aren't necessarily related to the new features added for this release, as listed in the previous section, but they may help you to get more out of existing features.

- Asset Management mobile workspace <!--KFM: Add new topic link, Johan -->
- [Configure product filters for warehouse transactions](../warehousing/filters-and-filter-codes.md)
- [Design the production floor execution interface](../production-control/production-floor-execution-tabs.md)
- [Intercompany planning](../master-planning/planning-optimization/Intercompany-planning.md)
- [Inventory marking with Planning Optimization](../master-planning/planning-optimization/marking.md)
- [Master planning with demand forecasts](../master-planning/planning-optimization/demand-forecast.md)
- Override the default reservation principle for materials in production <!--KFM: Add new topic link, Johan -->
- [Production planning](../master-planning/planning-optimization/production-planning.md) <!--KFM: Remember to add YouTube link to this topic -->
- [Partial location cycle counting](../warehousing/partial-location-cycle-counting.md)
- [Pick line grouping](../warehousing/pick-line-grouping.md)
- [Purchase requisitions in master planning](../master-planning/planning-optimization/purchase-requisitions.md)
- [Troubleshoot cost management](../cost-management/troubleshoot-costmanagement.md)
- [Troubleshoot inventory operations](../inventory/troubleshoot-inventory-operations.md)
- Warehouse execution on scale units <!--KFM: Add new topic link, Per -->
- Warehouse orders for cloud and edge scale units  <!--KFM: Add new topic link, Per -->
- [Warehouse slotting](../warehousing/warehouse-slotting.md)

## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.17 includes platform updates. To learn more, see [Platform updates for version 10.0.17 of Finance and Operations apps (April 2021)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-17.md). <!--KFM: Confirm platform link -->

### Bug fixes

For information about the bug fixes included in each of the updates that are part of 10.0.17, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=528995&dbType=3&qc=267a545fabd24e111868bedc16716f5713a785ed096cdb6209526f41631e41db)<!--KFM: Get new KB link -->

### Dynamics 365: 2020 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2020 release wave 2 plan](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/index). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) topic describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.
