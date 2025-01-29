---
title: Create and edit Business performance analytics reports
description: Learn how to create and edit reports in Business performance analytics, including outlines on duplicating, renaming, sharing, and deleting reports.
author: jkhaira7
ms.author: jkhaira 
ms.reviewer: twheeloc
ms.date: 11/14/2024
ms.topic: conceptual
audience: Application User
---

# Create and edit Business performance analytics reports

Business performance analytics lets you create or customize reports that include the data fields that you're interested in. You can also change any visuals on the reports. To view all available reports, select **Reports** in the **Data explorer** pane on the left. Select **Refresh** to ensure that you have the most up-to-date reports.

> [!VIDEO https://learn-video.azurefd.net/vod/player?id=76bfa0c6-43bb-43fb-9ccf-291bb887c92d]


## Create a new report

To create a new report, follow these steps.

1. In Business performance analytics, in the **Data explorer** section, go to **Reports**.
2. Select **New**. Select either a Power BI or an Excel report.
3. Select **Start with a blank report** – Enter a report name and select **Create**.

    - If you selected a Power BI report, the report will open directly in your browser. You can then start to add data fields and build the report.
    - If you selected a Microsoft Excel report, you will be prompted to open a local copy of the report on your desktop. The first time creating a Business performance analytics Microsoft Excel report, you may have to download and install an add-in. 

## Edit a report

After you open a report, you can edit the visuals or data fields by selecting **Edit**.

>[!NOTE]
> You can't edit reports of the **Microsoft** type. You must duplicate them as described to create a **Custom** type report, which can be edited.

## Duplicate a report

To duplicate a report that isn't currently open, follow these steps.

1. In Business performance analytics, in the **Data explorer** section, go to **Reports**.
2. Select the report to duplicate. (You can duplicate only one report at a time.)
3. Select **Duplicate**. The duplicate report becomes available on the **Reports** page. 

To duplicate a report that's currently open, select **Duplicate** on the report.

After the report is duplicated, you receive a "Report duplicated" message that contains a link to the duplicate report.

## Rename a report

To rename a report that isn't currently open, follow these steps.

1. In Business performance analytics, in the **Data explorer** section, go to **Reports**.
2. Select the report to rename. (You can rename only one report at a time.)
3. Select **Rename**.
4. Enter a new name, and then save it.

To rename a report that's currently open, select **Rename** on the report.

>[!NOTE]
> You can't rename reports of the **Microsoft** type. You must duplicate them to create **Custom** type report, which can be renamed.

## Delete a report

To delete one or more reports, follow these steps.

1. In Business performance analytics, in the **Data explorer** section, go to **Reports**.
2. Select the report or reports to delete.
3. Select **Delete**.

>[!NOTE]
> You can't delete reports of the **Microsoft** type. Only **Custom** type reports can be deleted.

## Share a report
To share a report that isn't currently open, follow these steps:
1. In Business performance analytics, in the Data explorer section, go to **Reports**.
2. Select the report to share and select **Share**.
3. A dropdown will open to copy a link to share with another user or enter an email address and send an in-app notification. You can send an email to the recipient when a file isn't shared.
4. Specify to provide **Edit** or **View** access to the report. 

>[!NOTE]
> You can't share **Microsoft** type reports. To share a report, you must duplicate it to create a **Custom** type report.
> Only admin users may see a **Share** button, which currently has no functionality.
> Access to Microsoft reports is granted by an admin using **Roles**. Users with access to a Microsoft report can duplicate and share it with others who did not originally have access.
> If you aren't a Business performance analytics admin, sharing is restricted to users within the same business unit, as defined by your Dataverse security.

## Remove edit columns and edit filters buttons

Pages in the Business performance analytics app may display **Edit columns** and **Edit filters** buttons. The button's functionality is controlled by the administrator for the environment. The administrator can activate or deactivate these buttons at any time by going to the Power Platform Admin Center. Select **Settings** > **Product** > **Feature**. Activate or deactivate these buttons by turning on or off the **Show the Edit column button on views** and **Show the Edit filter button on views**. 
