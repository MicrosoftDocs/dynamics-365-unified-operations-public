---

title: Business performance analytics Excel add-in
description: This article provides information about the business performance analytics Microsoft Excel add-in.
author: jinniew
ms.author: jiwo
ms.reviewer: twheeloc 
ms.date: 07/26/2024
ms.topic: article
ms.custom:
ms.search.form: business-performance-analytics
audience: Application User
ms.application-unique-name: msdyn_BusinessPerformanceAnalytics
---

# Business performance analytics Excel add-in

The business performance analytics Microsoft Excel add-in exposes the same business performance analytics dataset that's available on the Power BI embedded report in the Excel desktop app.

- When you open the Excel report in the Excel desktop app, an **Analytics** tab is available on the ribbon. This tab has two buttons: **Save** and **Settings**.

    - **Save** – Save changes back to the business performance analytics app. If you don't select this button, your changes are saved only locally.
    - **Settings** – Access relevant documentation, third-party notices, and terms and conditions that are associated with the Excel add-in. You can also specify how you want warnings to be shown.

## Prerequisites

- The business performance analytics Excel add-in isn't supported in Excel Online or Excel for Mac.
- We recommend that you use the 64-bit version of Excel. In that version, the workbook size is limited only by the available memory and system resources. For the 32-bit version, the workbook size is limited to 2 gigabytes (GB).
- Customers must upgrade to Current Channel for Microsoft Office updates. Otherwise, the Excel add-in won't work as expected. For more information, see [Release notes for Current Channel](/officeupdates/current-channel).

### Create a Microsoft Excel Report
1.	Go to **Reports** in business performance analytics.
2.	Click **New report**, enter a name of the report.
3.	In the **Report type** field, select **Excel**. 
4.	Click **Create**. If this the first time creating an Excel report, install the **Business performance analytics Excel add-in**. If you have installed the add-in and created Excel reports before, an updated version of the add-in may be installed if available. 
5.	A new Excel report is downloaded to your local device. Open the report.
6.	The report appears as a blank pivot table with the business performance analytics dataset connected.
7.	You may be required to sign in again using your business performance analytics credentials.
8.	Drag and drop any fields in the pivot table and build the report.
9.	When finished, save the changes to the business performance analytics app.


### Save the Excel Report
1.	To save the Excel report to business performance analytics, go to the **Business performance analytics** ribbon on the top Excel pane.
2.	Click **Save**. Your changes are saved to business performance analytics. You must click **Save** to reflect the changes in the business performance analytics app.



### Limitations and considerations

- **Analyzing and storing data** – We do **not** recommend that you analyze business performance analytics data or store results outside the PivotTable format in the Excel add-in. Access controls are affected if the business performance analytics dataset in the Excel add-in isn't used with a PivotTable or PivotChart.

    - If a user creates an Excel report by using the original PivotTable that's connected to the business performance analytics dataset and then shares the report with another user, the recipient sees only the data that they have access to.
    - If a user creates an Excel report and stores some of the report data outside the PivotTable, the data that resides outside the PivotTable might not be removed when the report is saved to the business performance analytics app or shared with another user. Therefore, the recipient might see data that they don't typically have access to.

    Here are some examples:

    - A user creates an Excel report where data is stored outside the original PivotTable that's connected to the business performance analytics dataset. When the Excel report is reopened, a simple table that references the original pivot is reconstructed. In this case, if the report is shared with another user who doesn't have the same data access, that user might receive \#REF errors.
    - A user creates an Excel report where data is stored outside the original PivotTable that's connected to the business performance analytics dataset. The data is in plain text format and doesn't reference the original pivot. In this case, this data is retained. If the report is shared with another user who doesn't have the same data access, that user can read the plain text data.
    - A user converts the PivotTable that's connected to the business performance analytics dataset into cube values to create an Excel report where data is stored outside the original PivotTable. In this case, another user who has different data access will see errors in the cells. However, that user can still view the underlying data by going to the formula in the cell.
    - A user creates an Excel report that uses data sources and connections other than the business performance analytics dataset. In this case, the external connections are broken after the report is saved to business performance analytics. Although Pivot objects for these external connections remain, the data isn't updated when the report is opened from the business performance analytics app.

- **Renaming the Excel report** – When you select **Open in Desktop** to open an Excel report, you might be prompted to rename the file and choose a download path. Each file name contains a suffix, such as **83c5dfe2-3398-ee11-be36-6045bd0878d1**. We do **not** recommend that you rename the file or remove this suffix. For example, for a report that's named **Test Report 9 83c5dfe2-3398-ee11-be36-6045bd0878d1**, don't remove the suffix **83c5dfe2-3398-ee11-be36-6045bd0878d1** before you open the report.

    If you remove the suffix before you open the report for the first time, you break the connection that enables access to the business performance analytics dataset, and that also enables the report to be saved back to the business performance analytics app. However, when you open the report for the first time, you can rename the report or remove the suffix without affecting your connection to the dataset or the ability to save the report back to business performance analytics. Only the owner of the report can rename it.

- **Sharing the Excel report** – Sharing in business performance analytics works in a similar way for Power BI reports and Excel reports. Users can also share the report with other users by using **Sharing** in the Excel desktop app or by using email. Recipients can open the report only if they have the business performance analytics Excel add-in. When a user opens the report, they're prompted to sign in by using their credentials. A PivotTable is then reconstructed, based on the access that the user has. The user can't access any additional data that isn't the pivot.
- **Collaborating and saving back to the app** – Multiple collaborators might work on the same report at the same time by using their local copy. Collaborators who can edit the report can also save their changes back to the business performance analytics app. The last user to save their changes has their version saved to the business performance analytics app. If a newer version of the report is available when a user tries to save their changes to the business performance analytics app, they receive a warning. However, they can choose to override the newer version of the report. There's no way to recover a previous version of the report from the business performance analytics app.
- **Working on a local copy for an extended period** – If a user works on their local copy of the report for an extended period without saving their changes back to the business performance analytics app, the report continues to work for as long as the user has access to the business performance analytics app and data. The user continues to receive updates that are made to the dataset. When the user finally saves their changes back to the app, they're warned that they're overriding a newer version of the report. However, they can choose to override the newer version. This behavior is important if there are shared reports, and multiple collaborators are working on the same report.
