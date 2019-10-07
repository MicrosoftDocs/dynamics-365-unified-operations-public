---
# required metadata

title: Preview features in Platform update 31 for Finance and Operations apps (January 2020)
description: This topic describes features that are in preview in Platform update 31 for Finance and Operations apps. 
author: tonyafehr
manager: AnnBe
ms.date: 10/02/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: tfehr
ms.search.scope:  Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid:
ms.search.region: Global
# ms.search.industry: 
ms.author: tfehr
ms.search.validFrom: 2020-10-31
ms.dyn365.ops.version: Platform update 31

---
# Preview features in Platform update 31 for Finance and Operations apps (January 2020)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic describes preview features that are new or changed for Platform update 31 for Finance and Operations apps. This version has a build number of 7.0.XXXX. While the general availability date is in January, the new features are available for early release in October. For more information about Platform update 31, see [Additional resources](whats-new-platform-update-31.md#additional-resources).

## Data management export file size limitation of 256MB has been removed
Exporting files using data management had a limitation of maximum flie size of 256MB. This limitation has been removed. This change is guarded by a flight DMFBlobSize256 which can be enabled to revert back to old behavior if any issues are encountered due to this change.

## Optimization of Data management workspace load
Loading of data management workspace has been slow under certain conditions. There are new optimizations put in place to reduce the time it takes to load the workspace.

## Inefficient memory usage by Data management export/import jobs
There have been several issues reported where the memory consumed by data management export/import jobs have been high enough to result in performance issues for users. The SSIS package execution logic has been optimized to address this issue. This change is OFF be default as its guarded by a flight. After getting validations through PEAP and CAAP process, the change will be enabled as default in a later platform update.

## Feature
Provide a brief description of the feature and explain how it helps customers. Provide a link to an article where customers can read details about the feature.

## Feature
Provide a brief description of the feature and explain how it helps customers. Provide a link to an article where customers can read details about the feature.


## Additional resources

### Platform update 31 bug fixes
For information about the bug fixes included in each of the updates that are part of Platform update 31, sign in to Lifecycle Services (LCS) and view this [KB article](https://fix.lcs.dynamics.com/).

### Dynamics 365: 2019 release wave 2 plan
Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2019 release wave 2 plan](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features
The [Removed or deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md) topic describes features that have been removed or deprecated.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.
