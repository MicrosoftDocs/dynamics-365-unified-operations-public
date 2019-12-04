---
# required metadata

title: Preview features in Platform update 32 for Finance and Operations apps (February 2020)
description: This topic lists the features that are in preview in Platform update 32 for Finance and Operations apps. 
author: sericks007
manager: AnnBe
ms.date: 11/26/2019
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

Wen Data management is used to export files, there is a maximum file size of 256 megabytes (MB). In Platform update 32, you can remove this limit by implementing flight **DMFBlobSize256**. If this feature causes issues after you turn it on, you can revert to the previous behavior.

### Finance and Operations AOS (kernel) improvements

As Microsoft focuses on continuous improvements to provide a more reliable and stable experience for its customers, these improvements are a required milestone.

Starting in Platform update 32, AOS (kernel) will uptake Visual C++ 17 runtime libraries to take advantage of compiler performance optimizations. Platform engineers will benefit from the new upgrade while they use their development environments to provide a more robust and reliable experience for our customers.

This change requires that existing environments be updated so that they use the Visual C++ 17 redistributables.

- For Microsoft-managed Standard Acceptance Test sandbox and higher (Tier 2 and higher) environments, and production environments, the Visual C++ 17 redistributables are already installed. No action is required.
- For Microsoft-managed dev (Tier 1) environments, customers, partners, and independent software vendors (ISVs) must restart their virtual machines (VMs) before they apply Platform update 32.
- For non-managed dev, build, test, demo (Tier 1), and on-premises environments, customers, partners, and ISVs must download and install the Visual C++ 17 redistributables from the Shared asset library in Microsoft Dynamics Lifecycle Services (LCS) and restart their machines.

If the latest redistributables are already installed, no action is required.

If you apply Platform update 32, and the redistributables are missing, you might receive an error message when you start your services. In this case, the following procedure can help resolve the issue.

To install the redistributables, follow these steps.

1. In LCS, select the **Shared asset library** tile.
2. In the list of asset types, select **Model**.
3. Select **VC++ 17 Redistributables**.

    The download starts automatically.

4. Apply the redistributables on your machine, and restart it.

### Continued stabilization of saved views

For more information about saved views, see [User productivity – Saved views](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/finance-operations-crossapp-capabilities/user-productivity-saved-views).

### Improved responsiveness of Action Panes on smaller viewports

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
Two new system batch jobs are introduced to prepare existing batch job and tasks for the [Priority-based scheduling for batch jobs](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/finance-operations-crossapp-capabilities/priority-based-scheduling-batch-jobs) feature:

- **System job to seed batch group associations to batch jobs** with class name **SysMigrateBatchGroupsForPriorityBasedScheduling** associates batch jobs with batch groups.
- **System job to clean up expired batch heartbeat records** with class name **SysCleanupBatchHeartbeatTable** cleans up the new internal monitoring **BatchHeartbeatTable** table.

This feature is currently in restricted preview. The batch jobs are designed to be non-disruptive and there is no impact on current batch job functionality or processing, if the feature is not enabled.

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
