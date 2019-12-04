---
# required metadata

title: Preview features in Platform update 32 for Finance and Operations apps (February 2020)
description: This topic lists the features that are in preview in Platform update 32 for Finance and Operations apps. 
author: sericks007
manager: AnnBe
ms.date: 12/04/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope:  Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid:
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2019-11-30
ms.dyn365.ops.version: Platform update 32

---
# Preview features in Platform update 32 for Finance and Operations apps (February 2020)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic lists the preview features that are new or changed for Platform update 32 for Finance and Operations apps. This version has a build number of 7.0.XXXX and is available on the following schedule:

- **Preview release:** December 2019
- **General availability (self-update):** January 2020
- **Auto-update:** February 2020

For more information about Platform update 32, see [Additional resources](whats-new-platform-update-32.md#additional-resources).

## Features included in this release

### File size limit for data management export has been removed

For more information about this feature, see [Data management export file size limit removed](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/finance-operations-crossapp-capabilities/data-management-export-file-size-limit-removed).

### Finance and Operations AOS (kernel) improvements

For more information about this feature, see [Finance and Operations AOS (kernel) improvements](https://community.dynamics.com/365/financeandoperations/b/newdynamicsax/posts/finance-and-operations-aos-kernel-improvements).

### Continued stabilization of saved views

For more information about this feature, see [User productivity – Saved views](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/finance-operations-crossapp-capabilities/user-productivity-saved-views).

### Improved responsiveness of Action Panes on smaller screens

When pages that have an Action Pane are opened on a smaller screen, the Action Pane is collapsed and can't be pinned open.

### Ability to filter on blank values by using the filter pane and filters in grid column headers

Users can now filter for blank values via the filter pane and filters in grid column headers. The syntax that is used to look for a blank value in a column is **""**.

### Continued evolution of the new grid

The new grid provides several benefits:

- **Performance:** The new grid provides improved rendering speed and a faster scrolling experience.
- **Positionally scroll:** Users can now positionally scroll in the data that has been loaded in the web browser. For example, to scroll through 10,000 rows in a grid, select the middle of the scrollbar to immediately go to record 5,000 without having to retrieve data from the server.
- **General improvements:** In the existing grid, grid headers and data are misaligned, and the grid jumps while you scroll or create new records. The new grid eliminates these issues.
- **Reorder columns:** Users can now reorder columns by dragging them. Hover the mouse pointer over the column header, and then drag the gripper control that appears on the left side of the column.
- **Mathematical formulas:** Users can now enter mathematical formulas into numeric cells in a grid. For example, you can enter **=15\*4**. To make the system recognize a value as an expression, start the value with an equal sign (**=**).

The new grid also enables more complex features to be built into it. These additions to the grid will be introduced and enhanced in subsequent monthly updates:

- **Totals:** Business users can see totals for numeric columns in tabular grids. For example, financial users can view totals for a filtered set of transactions for a specific customer. This feature first became available as part of the new grid control feature in Platform update 29, and it will continue to evolve in subsequent platform versions.
- **Fast data entry:** This feature lets users enter data in a grid ahead of the server. Therefore, it minimizes the need for users to wait for the server to validate one row in the grid before they move to another row. This feature first became available as part of the new grid control feature in Platform update 31, and it will continue to evolve in subsequent platform versions.

Starting in Platform update 31, the new grid control can be turned on for qualified environments by using the **Feature management** workspace. (For information about how to turn on the flight, see the following procedure.) For older updates, you can make the new grid control available by adding **&debug=reactGrid** to the environment URL.

To make the new grid available while this feature is in preview, follow these steps.

1. Turn on the flight by using the following SQL statement.

    ```
    INSERT INTO SYSFLIGHTING (FLIGHTNAME, enabled, FLIGHTSERVICEID, PARTITION) VALUES('CLIReactGridEnableFeature', 1, 0, 5637144576);
    ```

2. Reset Microsoft Internet Information Services (IIS) to flush the static flighting cache.
3. In your Finance and Operations app, open the **Feature management** workspace.
4. Select the **New grid control** feature in the list of features, and then, in the details pane, select **Enable now**.

    If **New grid control** doesn't appear in the list of features, select **Check for updates**.

The new grid will be available in all subsequent user sessions that are started.

### Priority-based scheduling for batch jobs
Two new system batch jobs are introduced to prepare existing batch jobs and tasks for the [Priority-based scheduling for batch jobs](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/finance-operations-crossapp-capabilities/priority-based-scheduling-batch-jobs) feature. The two new system batch jobs are:

- **System job to seed batch group associations to batch jobs:** This batch job, with class name **SysMigrateBatchGroupsForPriorityBasedScheduling**, associates batch jobs with batch groups.
- **System job to clean up expired batch heartbeat records:** This batch job, with class name **SysCleanupBatchHeartbeatTable**, cleans up the new internal monitoring **BatchHeartbeatTable** table.

The [Priority-based scheduling for batch jobs](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/finance-operations-crossapp-capabilities/priority-based-scheduling-batch-jobs) feature is currently in restricted preview. The batch jobs are designed to be non-disruptive and there is no impact on current batch job functionality or processing, if the feature is not enabled.

## Additional resources

### Platform update 32 bug fixes

For information about the bug fixes that are included in each update that is part of Platform update 32, sign in to LCS, and view [this KB article](https://fix.lcs.dynamics.com/Issue/).

### Dynamics 365: 2019 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2019 release wave 2 plan](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md) topic describes features that have been removed or deprecated.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

A deprecation notice will be added in the [Removed or deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md) topic 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these changes are functional updates that must be made to the compiler.
