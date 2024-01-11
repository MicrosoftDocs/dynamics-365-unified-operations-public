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


## Business Performance Analytics Excel Add-In exposes the same business performance analytics dataset typically available in Power BI embedded report in Microsoft Excel Desktop
Once you open the Excel report in Excel Desktop, you will see an "Analytics" tab on the top ribbon of your spreadsheet. This tab contains two buttons: "Save" and "Settings".
The "Save" button in the Analytics tab allows you to save changes back to the business performance analytics app. If you do not click this button, your changes are only saved locally.
The "Settings" button allows you access the relevant documentation, third-party notices and terms and conditions associated with the add-in. You can also choose how you would like warnings to be displayed.
Pre-requisites
Business Performance Analytics Excel Add-in is not supported on Microsoft Excel Online or Micrsoft Excel for Mac OS.
We recommend using the 64-bit version of Microsoft Excel because in this version, the workbook size is limited only by the available memory and system resources. However, the workbook size for the 32-bit Excel 
version is limited to 2gb.
For the Excel add-in to work correctly, customers must be upgraded to the Current Channel for Microsoft Office updates (https://learn.microsoft.com/en-us/officeupdates/current-channel). Alternatively, customers 
may perform a one-time office update that allows them access the January 2023 release of Microsoft Excel. Without this pre-requisite being met, the Excel add-in will not work as expected. 

### Limitations and considerations
We do not recommend analyzing business performance analytics data or storing results outside of the pivot table format in the Excel add-in: Business performance analytics dataset in the Excel add-in can only be
used with a pivot table or pivot chart, without impacting access controls. 
That is, if a user creates an Excel report using the original pivot table connected to the business performance analytics dataset and shares it with another user, then the recipient will see only the data that 
their admin has given them access to. 
However, if a user creates an Excel report and stores some data in the report outside of the pivot table (e.g. in a text box or a plain chart), this data may not be removed when the report is saved back to the
business performance analytics app or shared with another users. The recipient may, therefore, see data they do not typically have access to if this data resides outside of the pivot table. For example: 
If a user creates an Excel report with data stored outside the original pivot table connected to the business performance analytics dataset, such as in a simple tabular table, that references the original pivot,
this simple tabular table will be reconstructed when the Excel report is reopened. However, if the same report is shared with another user who does not have the same data access, they may get #REF errors for 
fields where they do not have access. 
If a user creates an Excel report with data stored outside the original pivot table connected to the business performance analytics dataset, in plain text format without referencing the original pivot, this data
will be retained. Another user who does not have the same data access will be able to read this plain text data when the report is shared with them. 
If a user creates an Excel report with data stored outside the original pivot table connected to the business performance analytics dataset, by converting the pivot table into cube value, another user with
different data access will see errors in the cells but they can still see the underlying data by navigating to the formulae in the cell. 
If a user uses other data source and connections in the Excel report other than the business performance analytics dataset, these connections will break once the report is saved back to business performance 
analytics. Pivot objects for these external connections will remain but the data will no longer refresh when the report is opened from the business performance analytics app. 
Renaming the Excel report: When you click the "Open in Desktop" button to open an Excel report, you may be prompted to rename the file and choose a download path. Each file name will contain a suffix in this 
format: 83c5dfe2-3398-ee11-be36-6045bd0878d1. We recommend that you do not rename the file or remove this suffix. For example, for a report named Test Report 9 83c5dfe2-3398-ee11-be36-6045bd0878d1, do not remove 
the suffix 83c5dfe2-3398-ee11-be36-6045bd0878d1 before opening the report. If you choose to remove the suffix before you have opened the report for this first time, this will break the connection that allows you 
to access the business performance analytics dataset or same the report back to the business performance analytics app. Once you have opened the report for the first time, you can rename the report or remove the 
suffix without this impacting your connection to the dataset or the ability to save the report back to business performance analytics. The ability to rename a report is limited to the owner of the report. 
Sharing the Excel report: Sharing in business performance analytics works similarly for both Power BI and Excel reports. However, a user may also use the in-build sharing button in Excel desktop or share the
report with another user via email. In these cases, the sharing will still work. That is, the recipient will be able to open the report provided they have the business performance analytics Excel add-in. Upon 
opening the report, the user will be asked to login with their credentials and a pivot table will be reconstructed with the access this user has. Any additional data (not in pivot), this user will have access to.
Collaborating and saving back to the app: In case of a shared report, multiple collaborators may be working on the same report at once using their local copy. If these collaborators have "edit" access, this will 
allow them to save their changes back to the business performance analytics app. The last collaborator to save their changes will prevail and their version will be saved back to the business performance analytics 
app. If a newer version of the report is available when a user attempts to the save their changes back to the business performance analytics app, they will receive a warning, but they can still choose to override. There is currently no way to recover a previous version of the report from the business performance analytics app. 
Working on the local copy for extended period: If a user chooses not to save their report back to the business performance analytics app and continues working on their local copy of the report for an extended 
period, the report will continue to work for them so long as they have access to the BPA app and data. They will continue receiving any updates made to the dataset. However, if and when they choose the report
back to the app, they will override any other version of the report. The user will be warned that they are overriding a newer version of the report. However, they can still choose to override. This is important 
to consider in the case of shared reports where multiple collaborators may be working on the same report. 

 
