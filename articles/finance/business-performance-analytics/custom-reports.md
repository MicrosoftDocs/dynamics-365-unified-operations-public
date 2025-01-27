---
title: Custom report migration
description: Learn how to import, export, and restore custom reports in Business performance analytics.
author: lizmota
ms.author: lizmota
ms.custom:
ms.topic: how-to
ms.reviewer: twheeloc 
audience: Application User
ms.date: 1/16/2025
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
- Both the target organization and the source organizations must have Business performance analytics version 2.0.29241185 or later.
- You must update the connection of the **Business performance analytics backup custom reports** and **Business performance analytics restore custom reports** flows in the target and source organizations. To update the connection, follow these steps.

    1. Go to [Power Apps](https://make.powerapps.com).
    1. Select the organization.
    1. Go to **Flows**, and select one of the flows in the list.
    1. Select **Edit**.
    1. Either select an existing connection or create a new one.
    1. Select **Save**.
    1. Repeat the preceding steps for the other flow.

## Export

To export custom reports from the source organization, follow these steps.

1. Go to [Power Apps](https://make.powerapps.com).
1. Confirm that you're in the source organization.
1. Create a solution in the organization. Learn more in [Create a solution](/power-apps/maker/data-platform/create-solution).

    - Follow the steps for creating a solution in the first part of the article.
    - Make a note of the value that you enter in the **Name** field. You will need this value later.

1. Go to **Flows**.
1. Find the **Business performance analytics backup custom reports** flow, and select **Run**.

    1. In the **Solution unique name** field, enter the **Name** value that you made a note of.
    1. Select **Run flow**.

1. The run time depends on the number of existing reports. You can monitor the progress in the **Business performance analytics move custom reports to solution** flow.
1. When the flow finishes running, go to the **Solutions** page.
1. Export the solution that you created. Learn more in [Export from Power Apps](/power-apps/maker/data-platform/export-solutions#export-from-power-apps).

    In the **Export this solution** dialog box, select either **Managed** or **Unmanaged** as the type of package to export.

## Import

To import custom reports into the target organization, follow these steps.

1. Go to [Power Apps](https://make.powerapps.com).
1. Confirm that you're in the target organization.
1. Import the solution that was exported from the source organization. Learn more in [Import solutions](/power-apps/maker/data-platform/import-update-export-solutions).
1. When the import is completed, go to **Flows**.
1. Find the **Business performance analytics restore custom reports** flow, and select **Run**.
1. The run time depends on the number of reports in the system. You can monitor the progress in the **Business performance analytics custom report restore flow** flow.

When the flow finishes running, the reports are ready to use.

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
    - The backed-up version in the unmanaged solution overwrites the contents of the managed solution.

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
