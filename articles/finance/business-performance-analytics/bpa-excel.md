---

title: Business performance analytics Excel add-in
description: This article provides information about the business performance analytics excel add-in.
author: jinniew
ms.author: jiwo
ms.reviewer: twheeloc 
ms.date: 1/11/2024
ms.topic: welcome
ms.prod: 
ms.technology:
ms.custom:
ms.search.form: business-performance-analytics
audience: Application User
ms.application-unique-name: msdyn_BusinessPerformanceAnalytics
---

# Business performance analytics Excel add-in

> [!NOTE]
> The functionality that's described in this article is available as part of a preview release. The functionality and the content of this article are subject to change. For more information about how to
> participate in the public preview for business performance analytics, contact <bpaquestions@service.microsoft.com>.

Business performance analytics Excel add-in exposes the same business performance analytics dataset that is available in Power BI embedded report in Microsoft Excel desktop.
 - After you open the Excel report in Excel desktop, an **Analytics** tab will be available on the top ribbon of your spreadsheet. This tab contains two buttons: **Save** and **Settings**.
 - **Save** - allows users to save changes back to the business performance analytics app. If you don't click this button, your changes are only saved locally.
 - **Settings** - allows users to access relevant documentation, third-party notices, and terms and conditions associated with the add-in. You can select how you would like warnings to be displayed.

## Prerequisites

 - Business performance analytics Excel add-in isn't supported on Microsoft Excel Online or Microsoft Excel for Mac OS.
 - We recommend using the 64-bit version of Microsoft Excel. In this version, the workbook size is limited by the available memory and system resources. The workbook size for the 32-bit Excel version is limited to 2gb.
 - Customers must upgrade to the Current channel for Microsoft Office updates. For more information, see [Microsoft Office updates](/officeupdates/current-channel). The Excel add-in won't work as expected without this release. 

### Limitations and considerations

1. We don't recommend analyzing business performance analytics data or storing results outside of the pivot table format in the Excel add-in. The business performance analytics dataset in the Excel add-in can only be used with a pivot table or pivot chart, without impacting access controls.
 - If a user creates an Excel report using the original pivot table connected to the business performance analytics dataset and shares it with another user, the recipient sees the data that they have access to.
 - If a user creates an Excel report and stores some data in the report outside of the pivot table, this data may not be removed when the report is saved to the business performance analytics app or shared with another users. The recipient may see data they don't typically have access to if this data resides outside of the pivot table.

For example: 
 - A user creates an Excel report with data stored outside the original pivot table connected to the business performance analytics dataset. A simple tabular table that references the original pivot is reconstructed when the Excel report is reopened. If the same report is shared with another user who doesn't have the same data access, they may get #REF errors.
 - If a user creates an Excel report with data stored outside the original pivot table connected to the business performance analytics dataset, in plain text format without referencing the original pivot, this data is retained. Another user who doesn't have the same data access can read this plain text data when the report is shared with them.
 - If a user creates an Excel report with data stored outside the original pivot table connected to the business performance analytics dataset, by converting the pivot table into cube value, another user with
different data access will see errors in the cells. Users can still see the underlying data by navigating to the formula in the cell.
 - If a user uses other data source and connections in the Excel report other than the business performance analytics dataset, these connections break after the report is saved to business performance analytics. Pivot objects for these external connections remain but the data doesn't refresh when the report is opened from the business performance analytics app. 


2. Renaming the Excel report - When you click **Open in Desktop** to open an Excel report, you may be prompted to rename the file and choose a download path. Each file name contains a suffix in this 
format: 83c5dfe2-3398-ee11-be36-6045bd0878d1. We recommend that you don't rename the file or remove this suffix. For example, for a report named Test Report 9 83c5dfe2-3398-ee11-be36-6045bd0878d1, don't remove 
the suffix 83c5dfe2-3398-ee11-be36-6045bd0878d1 before opening the report.

If you chose to remove the suffix before opening the report for this first time, this breaks the connection that allows access the business performance analytics dataset or report back to the business performance analytics app. After you have opened the report for the first time, you can rename the report or remove the suffix without this impacting your connection to the dataset or the ability to save the report back to business performance analytics. The ability to rename a report is limited to the owner of the report. 

4. Sharing the Excel report - Sharing in business performance analytics works similarly for both Power BI and Excel reports. Users may also use **Sharing** in Excel desktop or share the report with another user using email. The recipient is able to open the report provided they have the business performance analytics Excel add-in. After opening the report, users are asked to log in with their credentials and a pivot table will be reconstructed with the access this user has. Users won't have access to any additional data that isn't the pivot.

5. Collaborating and saving back to the app - Multiple collaborators may be working on the same report at once using their local copy. If these collaborators can edit the report, this allows them to save their changes back to the business performance analytics app. The last user to save their changes has their version saved to the business performance analytics app. If a newer version of the report is available when a user attempts to the save their changes to the business performance analytics app, they receive a warning, but they can still choose to override. There isn't a way to recover a previous version of the report from the business performance analytics app. 

6. Working on the local copy for extended period - If a user chooses not to save their report back to the business performance analytics app and continues working on their local copy of the report for an extended 
period, the report continues to work as long as they have access to the business performance analytics app and data. They will continue receiving updates made to the dataset. When the report is saved to the app, they override any other version of the report. The user is warned that they're overriding a newer version of the report. They can choose to override. This is important if there are shared reports and multiple collaborators are working on the same report. 

 
