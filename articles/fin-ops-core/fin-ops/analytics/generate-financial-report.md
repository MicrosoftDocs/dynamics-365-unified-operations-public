---
title: Generate financial reports
description: Learn about generating a financial report, including a table that provides definitions and states for various statuses.
author: jinniew
ms.author: aolson
ms.topic: how-to
ms.date: 11/13/2024
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-05-31
ms.search.form: FinancialReports
ms.dyn365.ops.version: AX 7.0.1
ms.assetid: 271df6f4-12b7-4b3e-b2d7-36ea98ef1871
---

# Generate financial reports

[!include [banner](../../../finance/includes/banner.md)]

This article provides information about generating a financial report.

To generate a report, follow these steps:
1. Open the report definition, select **Generate**.
2. The **Report queue status** page opens and indicates the location of your report in the queue.

As the report generation progresses, the following report queue status indicators may be visible on the **Report queue status** page.

| Status          | State | Description|
|-----------------|--------|--------------------|
| Queueing        | Interim |The report definition is validated before the report is put in the generation queue.                    |
| Queued          | Interim | The report enters the report generation queue and waits to be processed.                      |
| Processing      | Interim | This status typically follows the **Queued** status and usually transitions to a **Final** state when processing is complete.       |
| PostProcessing | Interim | This status follows the **Processing** status and indicates that all the report data is collected, but that derivative actions, such as calculation and rollup, are being performed.|
| Cancelling      | Interim | The reporting is canceled at the user's request. This state results from a user-requested cancellation for a report in the **Queued** or **Processing** state. The system attempts to put the report in the **Canceled** state, unless the system is too far along and must finalize it in another state. |
| Canceled        | Final | The report is finished processing but didn't complete due to a user-requested stop.            |
| Completed       | Final | The report is ready for use.                      |
| Failed          | Final | The report finished processing but failed and shouldn't be used. |

By default, the generated report opens in the Web Viewer. The following options are available for generating reports:

- Set up a schedule to generate a report or group of reports automatically
- Check for missing accounts or data in a report, and validate the accuracy of a report

When you generate a report, the options that you've specified on the **Report definition** tabs are used.

## Generate a financial report

To generate a financial report, go to **General ledger** \> **Inquiries and reports** \> **Financial reports**.

- Select a report to generate and select **Generate**.
- Fill in the **Report date** field and select **OK**.

After the report has been generated, the report is available to view in the **Reports** section.
You can select to **View** or **Delete** the report.

To generate a report using **Report designer**, follow these steps:
1. Open the report definition, click **Generate** .
2. The **Report queue status** page opens and indicates the location of your report in the queue. By default, the generated report opens in the Web Viewer.

### What to expect once report generation request is submitted?
 - Once customer submitted a report generation request, the report appears in the **Report queue status** page under **Report queue list**.
 - If multiple report generation requests are submitted at the same time, up to three reports can be processed at the same time on an Financial report process service instance and up to five reports can be processed concurrently in an environment.
 - The report generation queue is a First in First out queue.
 - Report generation can be cancelled before it enters final state by selecting the report and click **Remove**. Once the report is cancelled successfully, the report will be **Canceled**.
 
## Report groups

**Report groups** are an efficient way to generate several reports at the same time. For example, at month-end your users generate eight reports every month. Create a **Report group** and rather than selecting **Generate** for each of the eight reports in the group. Select **Generate** for the report group and the eight reports are generated in one step. When the reports in the selected report group have been generated, go to **Financial reports** (**General ledger > Inquires and reports > Financial reports**) to view the individual reports. 

To set up a report group, follow these steps: 

1. In **Report designer**, select **Report groups**. 
2. Select the existing report definitions to include in your report group. 
3. Select override company, detail, and date settings from each of the reports that will be included in the group.
   We recommend setting the **Company**, **Period**, **Year**, and **Detail level** for each report. 
4. Save the report group.

## Schedule report generation
Many companies have a core set of reports that are run at scheduled intervals to align with their business processes. You can schedule a report to be generated regularly, such as daily, weekly, monthly, or annually. This can be a single report or a group of reports that includes multiple companies. You must enter your credentials for each of the companies that are specified, such as those in a reporting tree definition. If the credentials aren't valid, the report will display only the information that you've permission to access, such as the company that you are logged on to at the time. Output information is read first from the report group, and then from the individual reports.

As report schedules are created and saved, they're displayed in the navigation pane under **Report schedules**. You can create folders to organize the reports. If a single report in a schedule does not run, all other reports will continue to run.

> [!IMPORTANT]
> To create, modify, and delete report schedules, you must have the role of designer or administrator. When a report is run, the credentials of the user who created the schedule are used to generate the report.

### Create a report schedule

1. In **Report designer**, on the **File** menu, select **New**, and then select **Report schedule**. The **New report schedule** dialog box opens.
2. Under **Settings**, select an individual report or a report group to schedule. Only reports or report groups for the company or building block selection that you are currently logged on to are available.
3. Select the **Active** checkbox to turn on the report schedule. Only the creator of the report or an administrator can activate or deactivate a report schedule.
4. Under **Frequency**, in the **Start recurrence** field, select the date when the schedule is to start. By default, the current system date of the client computer is selected.
5. In the **Run report at** field, select the time when the report should run. If you enter a time that is before the current system time, the report runs on the next scheduled date.
6. In **Recurrence pattern**, specify how often the report is run. By default, **Daily** is selected with an **Interval (days)** value of **1**. Other options include **Weekly**, **Monthly**, and **Yearly**.
7. In **Range of recurrence**, select when the report should stop being generated.

    - **No end date** – The report schedule runs indefinitely.
    - **Set number of occurrences** – The report schedule runs for the specified number of times, and then is deactivated.
    - **End by** – The report schedule ends on the specified date.

8. Select **Save**. In the **Save as** dialog box, enter a unique name and description for the report schedule.

To copy a report schedule, you must have the role of designer or administrator. Even if an administrator modifies the report schedule, the report maintains the credentials of the user who created the report.

### Copy a report schedule

1. In Report designer, select **Report schedules**, and open a report schedule to copy.
2. Go to **File**, select **Save as**. Enter a new name and description for the schedule in the **Save as** dialog box. Select **OK**, and the new schedule is displayed in the navigation pane.
3. In the new schedule, modify the fields and information as needed, and select **Save** on the toolbar, or select **Save** on the **File** menu.

To delete a report schedule, you must be the owner of the report schedule or have a role of administrator.

### Delete a report schedule

1. In Report designer, select **Report schedules** in the navigation pane.
2. Select the report schedule to delete, and then select **Delete** or click **Delete**.
3. In the **Deletion verification** dialog box, select **Yes** to permanently delete the report schedule. If you don't have permission to delete the schedule, a message is displayed and the report isn't deleted.

### Credentials and report schedules

If you don't enter credentials that are required for all companies included in the reports, you receive the following message when you save the report schedule: "You must enter your credentials for the companies that are contained in this report schedule. Select the **Permissions** button to enter in your credentials."

For example, a user logs on to Company A. The user creates a schedule for a report that uses a reporting tree definition to collect data from multiple companies. When this report schedule is saved, the user is prompted to enter the credentials for the other companies that are specified in the reporting tree definition. When your credentials expire, the affected reports in the report schedule aren't generated until the credentials have been updated. A message is displayed in the report queue indicating that permissions must be updated. The report schedule fails if any of the following scenarios occur (because they require credentials):

- A new company has been added to a report tree for an individual report.
- A report in a report group has been modified.
- A new report for an additional company has been added to a report group.

To continue, click **Permissions** in the **Report scheduling** dialog box, and then enter the appropriate credentials.

## Missing account analysis feature
You can search for financial accounts and dimensions that might be missing across all row definitions, reporting tree definitions, and report definitions in a building block group. This is useful when you create or update several accounts or building blocks during a short time period, and you want to verify that all new information is included in your reports.

Missing accounts are determined by using the lowest and highest values from the row definition or reporting tree definition, and then displays a list of accounts that aren't in the row definition or reporting tree definition, but that are in the financial data. If a missing account is greater than or less than the values in the row definition, that account isn't included in the list of missing accounts.

> [!TIP]
> For validation purposes, this process should be run before you generate monthly reports and when you create new building blocks.

Reports that have ranges of values are less likely to have missing accounts. When possible, use ranges in the building block to include new accounts when they're created. If any report definition is set to @ANY company, then you can log on to a specific company and run a missing account analysis for that company.

> [!NOTE]
> If a new company has been added, you must add the new company to the reporting trees in any existing reports or the company won't be included in the missing account analysis.

### Run missing account analysis

1. In Report designer, select **Tools**, and then select **Missing account analysis**.
2. In **Company filter**, select a company to filter results on, or select **All (no filter)** to display results from all available companies.
3. In **Dimension filter**, select a dimension to filter results on, or select **All (no filter)** to view all dimension information for all available dimensions.
4. In **Group by**, select an option for sorting the results. You can sort results according to the building block that is affected, or you can sort results by dimension and value sets.
5. Review the displayed results. When you select an item in the upper pane, the lower pane displays additional information about the exception. This includes related dimensions, values, and reports.
6. To open the affected item, select the associated icon that's displayed in the list pane, or right-click the item and select **Open**. To select multiple items, hold down the **Ctrl** key while you select the items in the lower pane.
7. If any values, building blocks, or reports are returned that shouldn't be included in the analysis, right-click the item and select **Exclude**, or select the **Exclude** checkbox next to the item to remove the item from the list. Excluded items aren't included when the list is refreshed. To select multiple items, hold down the **Ctrl** key while you select the items in the lower pane. To view all items, including any results that you previously selected to exclude from the analysis, select the **Show excluded building blocks and values** checkbox, and then select **Refresh**.
8. Select **Refresh** to refresh exceptions that you've addressed. Select **Yes** to perform a full refresh of all of the results, or select **No** to perform a partial refresh of addressed items.

    > [!NOTE]
    > The page is automatically refreshed when it opens unless the page has been opened in the last 15 minutes.

9. When the issues are resolved, select **OK** to close the dialog box.

## Keyboard shortcuts for missing account analysis
When you run a missing account analysis, the following keyboard shortcuts are available.

| To do this                           | Press |
|--------------------------------------|----------------------------|
| Filter by company                    | Alt+C                      |
| Filter by dimension                  | Alt+D                      |
| Select the Group by field            | Alt+G                      |
| Show excluded blocks and values      | Alt+S                      |
| Refresh results                      | Alt+R                      |
| Exclude the selected building block  | Alt+X                      |
| Exclude the selected row definition  | Ctrl+B                     |
| Exclude the selected dimension value | Ctrl+D                     |
| Open the selected report definition  | Ctrl+R                     |
| Open the selected row definition     | Ctrl+O                     |


## Additional resources

[Financial reporting](financial-reporting-intro.md)

[Report Designer interface](report-designer-interface.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
