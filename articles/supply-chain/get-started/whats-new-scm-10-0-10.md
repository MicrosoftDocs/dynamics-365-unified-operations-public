---
# required metadata

title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.10 (May 2020)
description: This topic describes features that are either new or changed in Dynamics 365 Supply Chain Management 10.0.10. 
author: kamaybac
manager: AnnBe
ms.date: 03/11/2020
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
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: kamaybac
ms.search.validFrom: 2020-03-11 
ms.dyn365.ops.version: 10.0.10

---
# What's new or changed in Dynamics 365 Supply Chain Management 10.0.10 (May 2020)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management, preview version 10.0.10. This version <!-- KFM, check this: has a build number of 10.0.420 and --> is available as follows:

- **Preview release:** March 2020
- **General availability (self-update):** April 2020
- **Auto-update:** May 2020

## Features included in this release

The following feature is new in this release. The feature title links to additional information on the [Release plans](https://docs.microsoft.com/dynamics365/release-plans/) site. You must enable this feature using [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) before you can use it.

- [Quality management for warehouse processes](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/dynamics365-supply-chain-management/quality-management-warehouse-processes)


## Incremental updates included in this release

The features described in this section provide minor enhancements and fixes that haven't been announced on the [Release plans](https://docs.microsoft.com/dynamics365/release-plans/) site.

### Include items with on-hand when pre-processing filters are enabled

This feature ensures that items with on-hand will always be included in the master planning run when the **Pre-processing: Automatically filter by items with direct demand** setting is enabled on the **Master planning parameters** page. 

To use this capability, you must enable the _Include items with on-hand when pre-processing filters are enabled_ feature in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). For more information, see [Improve master planning performance](../master-planning/master-planning-performance.md).

> [!IMPORTANT]
> If you are relying on *Explosion* or *Net change update* functionality for manufacturing planning processes, then this feature must be enabled. Otherwise, incorrect on-hand data may show up in the **Net requirements** form for the items without direct demand and incorrect planned orders may be generated during explosion.

### Use existing catch weight tags

This feature adds support for using a mobile device to report a production order as finished when catch weight tags have been registered in advance for the appropriate order.

Use the **Mobile device menu items** page to add this feature to any mobile-device menu item that uses the _Report as finished and put away_ work creation process. The feature requires that the "Generate catch weight tag" setting be disabled for the used menu item, and also that you are using catch weight tag tacking for "Product, tracking, and all storage dimensions" as part of the "Catch weight item handling policy" setup.

To use this capability, you must enable the _Use existing catch weight tags when reporting production orders as finished_ feature in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). For more information, see [Catch weight product processing with warehouse management](../warehousing/catch-weight-processing.md).

## Additional resources

### Platform update 34

Microsoft Dynamics 365 Supply Chain Management 10.0.10 includes Platform update 34. To learn more, see [Preview features in Platform update 34](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-update-34.md)

### Bug fixes

For information about the bug fixes included in each of the updates that are part of 10.0.10, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=424137&dbType=3&qc=bf63d49dcc96e51eb42ac1dd66c6c5e5d7548f1e176f729e324ea3353b9860cb).

### Dynamics 365: 2020 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2020 release wave 1 plan](https://docs.microsoft.com/dynamics365-release-plan/2020wave1/index). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) topic describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.
