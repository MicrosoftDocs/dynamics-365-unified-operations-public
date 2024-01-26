---
# required metadata

title: Create and edit business performance analytics reports
description: This article describes how to create and edit reports in business performance analytics.
author: jkhaira7
ms.author: jkhaira 
ms.reviewer: twheeloc
ms.date: 12/18/2023
ms.topic: conceptual
ms.prod: 
ms.technology: 
audience: Application User
ms.application-unique-name: msdyn_BusinessPerformanceAnalytics
---

# Create and edit business performance analytics reports

> [!NOTE]
> The functionality that's described in this article is available as part of a preview release. The functionality and the content of this article are subject to change. For more information about how to participate in the public preview for business performance analytics, contact <bpaquestions@service.microsoft.com>.

Business performance analytics lets you create or customize reports that include the data fields that you're interested in. You can also change any visuals on the reports. 

## Create a new report

To create a new report, follow these steps.

1. In business performance analytics, in the **Data explorer** section, go to **Reports**.
2. Click **New**. Select either a Power BI or an Excel report.
3. Select **Start with a blank report** – Enter a report name and click **Create**.
 - If you selected a Power BI report, the report will open directly in your browser. You can then start to add data fields and build the report.
 - If you selected a Microsoft Excel report, you will be prompted to open a local copy of the report on your desktop. The first time creating a business performance analytics Microsoft Excel report, you may have to download and install an add-in. 
 

## Edit a report

After you open a report, you can edit the visuals or data fields by selecting **Edit**.

Reports of the **Microsoft** type can't be edited. You must duplicate them as described in the next section. You can then edit the duplicate report. 

## Duplicate a report

To duplicate a report that isn't currently open, follow these steps.

1. In business performance analytics, in the **Data explorer** section, go to **Reports**.
2. 2. Select the report to duplicate. (You can duplicate only one report at a time.)
3. Select **Duplicate**. The duplicate report becomes available on the **Reports** page. 

To duplicate a report that's currently open, select **Duplicate** on the report.

After the report is duplicated, you receive a "Report duplicated" message that contains a link to the duplicate report.

## Rename a report

To rename a report that isn't currently open, follow these steps.

1. In business performance analytics, in the **Data explorer** section, go to **Reports**.
2. Select the report to rename. (You can rename only one report at a time.)
3. Select **Rename**.
4. Enter a new name, and then save it.

To rename a report that's currently open, select **Rename** on the report.

## Delete a report

You can't delete reports of the **Microsoft** type. You can delete only reports of the **Custom** type. You can delete multiple reports at the same time.

To delete one or more reports, follow these steps.

1. In business performance analytics, in the **Data explorer** section, go to **Reports**.
2. Select the report or reports to delete.
3. Select **Delete**.

## Share a report
To share a report that isn't currently open, follow these steps:
1. In business performance analytics, in the Data explorer section, go to **Reports**.
2. Select the report to share and select **Share**.
3. A dropdown will open to copy a link to share with another user or enter an email address and send an in-app notification. You can send an email to the recipient when a file isn't shared.
4. Specify to provide **Edit** or **View** access to the report. 

>[!NOTE:]
> Only admin users may also see an additional **Share** button. This button currently doesn't provide any use.
>Access to the Microsoft report is provided to users by an admin using **Roles**. A user who has access to a Microsoft report can duplicate the report and share it with others users who did not originally have access to the report.

## Remove edit columns and edit filters buttons

Pages in the business performance analytics app may display **Edit columns** and **Edit filters** buttons. The button's functionality is controlled by the administrator for the environment. The administrator can activate or deactivate these buttons at any time by going to the Power Platform Admin Center. Select **Settings** > **Product** > **Feature**. Activate or deactivate these buttons by turning on or off the **Show the Edit column button on views** and **Show the Edit filter button on views**. 




