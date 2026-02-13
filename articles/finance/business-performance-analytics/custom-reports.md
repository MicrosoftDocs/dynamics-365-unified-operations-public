---
title: Custom report migration
description: Learn how to import, export, and restore custom reports in Business performance analytics.
author: yashkv1 
ms.author: twheeloc
ms.custom:
ms.topic: how-to
ms.reviewer: twheeloc 
audience: Application User
ms.date: 1/27/2025
---

# Custom report migration

This article explains how to back up, export, and restore custom reports. This process helps ensure that your organization's data remains consistent and up to date.

The process has two main stages:

- Export custom reports from the source organization.
- Import custom reports into the target organization.

## Terminology

- **Source organization** – The organization that you back up and export from.
- **Target organization** – The organization that you import the solution and reports into.

## Prerequisites

Before you import or export reports, the following prerequisites must be in place:

- You must have a system administrator role.
- Both the target organization and the source organizations must have Business performance analytics version 2.2.3079.1350 or later.

## Export

To export custom reports from the source organization, follow these steps:

1. Navigate to the administration home page in the source environment.
2. Select **Manage** on the **Import/Export reports** tile.
3. Select the **Export** tab, and then select **+ New** on the ribbon.
4. Either create a new solution or select an existing unmanaged solution:
    - To select an existing solution, follow these steps:
        1. Select the solution that the reports should be exported to. We don't recommend using an unmanaged solution that contains objects other than reports, it might cause issues with the export.

    - To create a new solution, follow these steps:
        1. Select a publisher.
        2. Enter a display name and unique name.
           The display name is limited to 256 characters. The unique name is limited to 256 characters, including the publisher prefix, and mustn't contain spaces or special characters other than underscores (_).

5. After the setup is complete, select the solution from the list, and then select **Export** in the upper right.
6. Remain on the page until the export is complete. 
7. To download the solution as a .zip file, click the **Download solution** button. 

## Import

To import custom reports into the target organization, follow these steps:

1. Navigate to the administration home page in the target environment.
2. Select **Manage** on the **Import/Export reports** tile.
3. Select the **Import** tab, and then select **+ New** on the ribbon.
4. Find the .zip or .cab file that contains the exported reports.
5. Remain on the page until the import is complete.
6. After a green banner appears that indicates a successful import, select **Import** in the upper right.

    > [!NOTE]
    > You don't have to remain on the page after you select this button. Your reports should appear within a few minutes.


## Notes and limitations

- A report that you're importing into the target organization might have the same name as an existing report in that organization. In this case, the unique name of the solution is appended to the name of the report that is being imported.

    > [!NOTE]
    > Report names have a 100-character limit. Any characters above this limit are truncated. After truncation, if the appended name of a report that is being imported remains the same as the name of an existing report, the report isn't imported.

- If you backed up or imported reports by using this feature, the following behavior occurs when the **Business performance analytics restore custom reports** flow is run:

    - The content of the reports is overwritten by the report that was backed up or imported last.
    - The name of the report isn't updated.

- If you import reports again from the same source organization, any backups of those reports in target organizations are overwritten by the values in the imported solution.

- **Managed solutions (not recommended):** We don't recommend that you export and then import your backup solution as a managed solution. However, if you do, the following information applies:

    - Any backups in the target organization layer their changes on top of the imported backup solution. 
    - To move your reports from the target organization to any other organization, import the managed backup solution first.
    - If you imported the managed solution, deleted it, and then backed up the target organization, you can't import again from the same source organization. Otherwise, conflicts are created.
    - The backed-up version in the unmanaged solution overwrites the contents of the managed solution even if imported again.

    > [!NOTE]
    > We recommend that you use a managed solution only if you don't plan to back up the target organization.

- **Unmanaged solutions (recommended):** We recommend that you export and then import your backup solution as an unmanaged solution. In this case, the following information applies:

    - You can't import custom reports from the same source organization by using a managed solution.
    - You can use the same solution to back up the imported reports.
    - You can back up new reports to the imported solution.

        > [!NOTE]
        > We recommend this action only if you keep everything as a bundle.

    - You can export the backup solution again.
    - If you create a second backup solution, only reports that haven't been backed up are added to the second backup solution. Any reports in the first backup solution remain in that solution.
