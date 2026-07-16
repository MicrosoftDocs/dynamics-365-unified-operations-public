---
title: Create and edit Business performance analytics reports
description: Learn how to create and edit reports in Business performance analytics, including outlines on duplicating, renaming, sharing, and deleting reports.
author: jkhaira7
ms.author: jkhaira 
ms.reviewer: twheeloc
ms.date: 06/23/2026
ms.topic: how-to
audience: Application User
---

# Create and edit Business performance analytics reports

Business performance analytics enables you to create or customize reports that include the data fields you're interested in. You can also change any visuals on the reports. To view all available reports, select **Reports** in the **Data explorer** pane on the left. Select **Refresh** to ensure that you have the most up-to-date reports.

> [!VIDEO https://learn-video.azurefd.net/vod/player?id=76bfa0c6-43bb-43fb-9ccf-291bb887c92d]


## Create a new report

To create a new report, follow these steps:

1. In Business performance analytics, in the **Data explorer** section, go to **Reports**.
1. Select **New**. Select either a Power BI or an Excel report.
1. Select **Start with a blank report** – Enter a report name and select **Create**.

    - If you select a Power BI report, the report opens directly in your browser. You can then start to add data fields and build the report.
    - If you select a Microsoft Excel report, you're prompted to open a local copy of the report on your desktop. The first time you create a Business performance analytics Microsoft Excel report, you might need to download and install an add-in. 

## Edit a report

After you open a report, you can edit the visuals or data fields by selecting **Edit**.

>[!NOTE]
> You can't edit reports of the **Microsoft** type. You must duplicate them as described to create a **Custom** type report, which you can edit.

## Duplicate a report

To duplicate a report that isn't currently open, follow these steps:

1. In Business performance analytics, in the **Data explorer** section, go to **Reports**.
1. Select the report to duplicate. (You can duplicate only one report at a time.)
1. Select **Duplicate**. The duplicate report becomes available on the **Reports** page. 

To duplicate a report that's currently open, select **Duplicate** on the report.

After the report is duplicated, you receive a "Report duplicated" message that contains a link to the duplicate report.

## Rename a report

To rename a report that isn't currently open, follow these steps:

1. In Business performance analytics, in the **Data explorer** section, go to **Reports**.
1. Select the report to rename. (You can rename only one report at a time.)
1. Select **Rename**.
1. Enter a new name, and then save it.

To rename a report that's currently open, select **Rename** on the report.

>[!NOTE]
> You can't rename reports of the **Microsoft** type. You must duplicate them to create **Custom** type report, which you can rename.

## Delete a report

To delete one or more reports, follow these steps:

1. In Business performance analytics, in the **Data explorer** section, go to **Reports**.
1. Select the reports to delete.
1. Select **Delete**.

>[!NOTE]
> You can't delete reports of the **Microsoft** type. You can only delete **Custom** type reports.

## Share a report
To share a report that isn't currently open, follow these steps:
1. In Business performance analytics, in the Data explorer section, go to **Reports**.
1. Select the report to share and select **Share**.
1. A dropdown opens where you can copy a link to share with another user or enter an email address and send an in-app notification. You can send an email to the recipient when a file isn't shared.
1. Specify whether to provide **Edit** or **View** access to the report. 

>[!NOTE]
> You can't share **Microsoft** type reports. To share a report, you must duplicate it to create a **Custom** type report.
> Only admin users see a **Share** button, which currently has no functionality.
> An admin grants access to Microsoft reports by using **Roles**. Users with access to a Microsoft report can duplicate and share it with others who didn't originally have access.
> If you're not a Business performance analytics admin, sharing is restricted to users within the same business unit, as defined by your Dataverse security.

## Remove edit columns and edit filters buttons

Pages in the Business performance analytics app might display **Edit columns** and **Edit filters** buttons. The administrator controls the functionality of these buttons. The administrator can activate or deactivate these buttons at any time by going to the Power Platform Admin Center. Select **Settings** > **Product** > **Feature**. Turn on or off the **Show the Edit column button on views** and **Show the Edit filter button on views** to activate or deactivate these buttons. 
