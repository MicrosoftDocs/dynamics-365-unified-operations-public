---
title: What's new or changed in Platform update 32 for finance and operations apps (February 2020)
description: Learn about the features that are in preview in Platform update 32 for finance and operations apps added in the February 2020 update. 
author: sericks007
ms.author: sericks
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.date: 04/12/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2019-11-30
ms.dyn365.ops.version: Platform update 32
---

# What's new or changed in Platform update 32 for finance and operations apps (February 2020)

[!include [banner](../../../finance/includes/banner.md)]

This article lists features that are new or changed for Platform update 32 for finance and operations apps. This version has a build number of 7.0.5493 and is available on the following schedule:

- **Preview release:** December 2019
- **General availability (self-update):** January 2020
- **Auto-update:** February 2020

For more information about Platform update 32, see [Additional resources](#additional-resources).

## Features included in this release

### File size limit for data management export has been removed

For more information about this feature, see [Data management export file size limit removed](/dynamics365-release-plan/2019wave2/finance-operations-crossapp-capabilities/data-management-export-file-size-limit-removed).

### Finance and operations AOS (kernel) improvements

For more information about this feature, see [finance and operations AOS (kernel) improvements](https://community.dynamics.com/365/financeandoperations/b/newdynamicsax/posts/finance-and-operations-aos-kernel-improvements).

### Continued stabilization of saved views

For more information about this feature, see [User productivity – Saved views](/dynamics365-release-plan/2019wave2/finance-operations-crossapp-capabilities/user-productivity-saved-views).

### Improved responsiveness of Action Panes on smaller screens

For more information about this feature, see [Improved experience on mobile devices – Phase 1](/dynamics365-release-plan/2019wave2/finance-operations-crossapp-capabilities/improved-experience-mobile-devices-phase-1).

### Ability to filter on blank values by using the filter pane and filters in grid column headers

For more information about this feature, see [User productivity – Filtering enhancements](/dynamics365-release-plan/2019wave2/finance-operations-crossapp-capabilities/user-productivity-filtering-enhancements).

### Continued evolution of the new grid

For more information about this feature, see [User productivity – New grid](/dynamics365-release-plan/2019wave2/finance-operations-crossapp-capabilities/user-productivity-new-grid).

### Priority-based scheduling for batch jobs
Two new system batch jobs are introduced to prepare existing batch jobs and tasks for the [Priority-based scheduling for batch jobs](/dynamics365-release-plan/2019wave2/finance-operations-crossapp-capabilities/priority-based-scheduling-batch-jobs) feature. The two new system batch jobs are:

- **System job to seed batch group associations to batch jobs:** This batch job, with class name **SysMigrateBatchGroupsForPriorityBasedScheduling**, associates batch jobs with batch groups.
- **System job to clean up expired batch heartbeat records:** This batch job, with class name **SysCleanupBatchHeartbeatTable**, cleans up the new internal monitoring **BatchHeartbeatTable** table.

The Priority-based scheduling for batch jobs feature is currently in restricted preview. The batch jobs are designed to be non-disruptive and there is no impact on current batch job functionality or processing, if the feature is not enabled.

## Additional resources

### Platform update 32 bug fixes

For information about the bug fixes that are included in each update that is part of Platform update 32, sign in to LCS, and view [this KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=400369&dbType=3&qc=30ab94ba46d00083bda800e9a50600fa1fdf63a47c33e8e83f74774b6d245f27).

### Dynamics 365: 2019 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2019 release wave 2 plan](/dynamics365-release-plan/2019wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) article describes features that have been removed, or that are planned for removal in platform updates of finance and operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

A deprecation notice will be added in the [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) article 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these changes are functional updates that must be made to the compiler.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
