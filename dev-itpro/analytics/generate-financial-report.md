---
# required metadata

title: Generate a financial report
description: This topic provides information about generating a financial report. 
author: ShylaThompson
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: FinancialReports
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: ShylaThompson
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 68843
ms.assetid: 271df6f4-12b7-4b3e-b2d7-36ea98ef1871
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# Generate a financial report

This topic provides information about generating a financial report. 

To generate a report, open the report definition and then click the Generate button in the toolbar. The Report Queue Status window will open and indicate the location of your report in the queue. By default, the generated report will open in the Web Viewer.
| ![Note](https://i-technet.sec.s-msft.com/areas/global/content/clear.gif "Note")**Note**        |
|------------------------------------------------------------------------------------------------|
| You can generate reports only to folders and locations to which you have permission to access. |

The following table explains the options that are available for generating reports.

| Option                                                                                | For more information |
|---------------------------------------------------------------------------------------|----------------------|
| Set up a schedule to generate a report or group of reports automatically              |                      |
| Check for missing accounts or data in a report, and validate the accuracy of a report |                      |

When you generate a report, the options that you have specified on the Report definition tabs are used. The Output and Distribution tab lets you specify a report library location, which provides an easy way to share the report.

## Schedule report generation
Many companies have a core set of reports that are run at scheduled intervals to align with their business processes. You can schedule a report to be generated regularly, such as daily, weekly, monthly, or annually. This can be a single report or a group of reports that includes multiple companies. You must enter your credentials for each of the companies that are specified, such as those in a reporting tree definition. If the credentials are not valid, the report will display only the information that you have permission to access, such as the company that you are logged on to at the time. Output information is read first from the report group, and then from the individual reports.

As report schedules are created and saved, they are displayed in the navigation pane under Report Schedules. You can create folders to organize the reports. If a single report in a schedule does not run, all other reports will continue to run.
| ![Important](https://i-technet.sec.s-msft.com/areas/global/content/clear.gif "Important")**Important**                                                                                                           |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| To create, modify, and delete report schedules, you must have the role of designer or administrator. When a report is run, the credentials of the user who created the schedule are used to generate the report. |

### Create a report schedule

1.  In Report Designer, on the File menu, click New, and then select Report schedule. The New Report Schedule dialog box opens.
2.  Under Settings, select an individual report or a report group to schedule. Only reports or report groups for the company or building block selection that you are currently logged on to are available.
3.  Select the Active check box to turn on the report schedule. Only the creator of the report or an administrator can activate or inactivate a report schedule.
4.  Click the Permissions button to enter company credentials. By default, your logon information is used for the company that you are logged on to. If other companies are included, such as in reporting tree definitions, select Use separate credentials, and then enter the credentials for any other company that is included in the report schedule. You can select Windows Authentication or type a user name and password for each company. Select the Save credentials check box to save the credentials for these companies, and then click OK to close the dialog box.
5.  Under Frequency, in the Start recurrence field, select the date when the schedule is to start. By default, the current system date of the client computer is selected.
6.  In the Run report at field, select the time when the report should run. If you enter a time that is before the current system time, the report runs on the next scheduled date.
7.  In the Recurrence pattern area, specify how often the report is run. By default, Daily is selected with an Interval (days) value of 1. Other options include Weekly, Monthly, and Yearly.
8.  In the Range of recurrence area, select when the report should stop being generated.
    -   No end date – The report schedule runs indefinitely.
    -   Set number of occurrences – The report schedule runs for the specified number of times, and then is inactivated.
    -   End by – The report schedule ends on the specified date.

9.  Click Save in the toolbar. In the Save As dialog box, enter a unique name and description for the report schedule.

To copy a report schedule, you must have the role of designer or administrator. Even if an administrator modifies the report schedule, the report maintains the credentials of the user who created the report.
### Copy a report schedule

1.  In Report Designer, click Report Schedules in the navigation pane, and open a report schedule to copy.
2.  On the File menu, click Save As, and then enter a new name and description for the schedule in the Save As dialog box. Click OK, and the new schedule is displayed in the navigation pane.
3.  In the new schedule, modify the fields and information as needed, and then click Save on the toolbar, or click Save on the File menu.

To delete a report schedule, you must be the owner of the report schedule or have a role of administrator.
### Delete a report schedule

1.  In Report Designer, click Report Schedules in the navigation pane.
2.  Select the report schedule to delete, and then click Delete or press the Delete key.
3.  In the deletion verification dialog box, click Yes to permanently delete the report schedule. If you do not have permission to delete the schedule, a message is displayed and the report is not deleted.

### Credentials and report schedules

If you do not enter credentials that are required for all companies included in the reports, you receive the following message when you save the report schedule: “You must enter your credentials for the companies that are contained in this report schedule. Select the Permissions button to enter in your credentials.”

For example, Phyllis logs on to Company A using her logon and password. She creates a schedule for a report that uses a reporting tree definition to collect data from multiple companies. When this report schedule is saved, Phyllis is prompted to enter the credentials for the other companies that are specified in the reporting tree definition. When your credentials expire, the affected reports in the report schedule are not generated until the credentials have been updated. A message is displayed in the report queue to indicate that permissions must be updated. The report schedule fails if any of the following scenarios occur (because they require credentials):
-   A new company has been added to a report tree for an individual report.
-   A report in a report group has been modified.
-   A new report for an additional company has been added to a report group.

To continue, click the Permissions button in the Report Scheduling dialog box, and then enter the appropriate credentials.

## Missing account analysis feature
You can search for financial accounts and dimensions that might be missing across all row definitions, reporting tree definitions, and report definitions in a building block group. This is useful when you create or update several account or building blocks during a short time period, and you want to verify that all new information is included in your reports.

Missing accounts are determined by using the lowest and highest values from the row definition or reporting tree definition, and then displays a list of accounts that are not in the row definition or reporting tree definition, but that are in the financial data. If a missing account is greater than or less than the values in the row definition, that account is not included in the list of missing accounts.
| ![Tip](https://i-technet.sec.s-msft.com/areas/global/content/clear.gif "Tip")**Tip**                                             |
|----------------------------------------------------------------------------------------------------------------------------------|
| For validation purposes, this process should be run before you generate monthly reports and when you create new building blocks. |

Reports that have ranges of values are less likely to have missing accounts. When possible, use ranges in the building block to include new accounts when they are created. If any report definition is set to @ANY company, then you can log on to a specific company and run a missing account analysis for that company.
| ![Note](https://i-technet.sec.s-msft.com/areas/global/content/clear.gif "Note")**Note**                                                                                           |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| If a new company has been added, you must add the new company to the reporting trees in any existing reports or the company will not be included in the missing account analysis. |

### Run missing account analysis

1.  In Report Designer, click Tools, and then click Missing Account Analysis.
2.  In the Company filter field, select a company to filter results on, or select All (no filter) to display results from all available companies.
3.  In the Dimension filter field, select a dimension to filter results on, or select All (no filter) to view all dimension information for all available dimensions.
4.  In the Group by field, select an option for sorting the results. You can sort results according to the building block that is affected, or you can sort results by dimension and value sets.
5.  Review the displayed results. When you select an item in the upper pane, the lower pane displays additional information about the exception. This includes related dimensions, values, and reports.
6.  To open the affected item, click the associated icon that is displayed in the list pane, or right-click the item and select Open. To select multiple items, hold down the Ctrl key while you select the items in the lower pane.
7.  If any values, building blocks, or reports are returned that should not be included in the analysis, right-click the item and select Exclude, or select the Exclude check box next to the item to remove the item from the list. Excluded items are not included when the list is refreshed. To select multiple items, hold down the Ctrl key while you select the items in the lower pane.To view all items, including any results that you previously selected to exclude from the analysis, select the Show excluded building blocks and values check box, and then click Refresh.
8.  Click Refresh to refresh exceptions that you have addressed. Click Yes to perform a full refresh of all of the results, or click No to perform a partial refresh of addressed items.
    | ![Note](https://i-technet.sec.s-msft.com/areas/global/content/clear.gif "Note")**Note**                    |
    |------------------------------------------------------------------------------------------------------------|
    | The form is automatically refreshed when it opens, unless the form has been opened in the last 15 minutes. |

9.  When the issues are resolved, click OK to close the dialog box.

## Keyboard shortcuts for missing account analysis
When you run a missing account analysis, the following keyboard shortcuts are available.

| To do this                           | Use this keyboard shortcut |
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

 
See also
--------

[Financial reporting](financial-reporting-intro.md)

[Report Designer interface](report-designer-interface.md)
