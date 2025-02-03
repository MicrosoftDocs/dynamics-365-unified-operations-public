---
title: Manage CAPA activities
description: CAPA activities will be automatically created for you as CAPA cases are acted upon. When a stage is advanced, CAPA activities will be created and assigned to the appropriate person responsible with a due date depending on how the CAPA process was defined.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# Manage CAPA activities

[!include [banner](../../includes/banner.md)]

After CAPA cases are created and if CAPA processes are being used, CAPA activities will be automatically created for you as CAPA cases are acted upon. When a stage is advanced, CAPA activities will be created and assigned to the appropriate person responsible with a due date depending on how the CAPA process was defined. CAPA activities can be viewed using its own menu group where you have the ability to view All CAPA activities and All Open CAPA activities as well as CAPA activities due in the current week or that are past due. Each of these options is also available where they are filtered by the current user so that only activities where the user is responsible would be included.

## CAPA activity list pages

| **Path: Home \> Common \> Activities \> CAPA activities \> All CAPA activites OR My CAPA activities OR All open CAPA activities OR My open CAPA activities OR All CAPA activities due this week OR My CAPA activities due this week OR All CAPA activities past due OR My CAPA activities past due** | &nbsp; | &nbsp; |
|--|--|--|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** |  |  |
| Action | Create a New CAPA activity that is defined as an Action. |  |
| Appointment | Create a New CAPA activity that is defined as an Appointment. |  |
| Event | Create a New CAPA activity that is defined as an Event. |  |
| Task | Create a New CAPA activity that is defined as a Task. |  |
| Edit | Open the CAPA activity for editing. |  |
| Set as complete | Selects the option of Closed on the CAPA activity. | This represents the action of completing the work that was called for on the CAPA activity. |
| Edit in grid | Open a new window in edit mode and edit any available fields directly in the list page grid. |  |
| Delete | Delete the selected CAPA activity. | **Note:** You cannot delete an activity that is assigned to someone else but you can delete your own. |
| Attendees | View or change the attendees if the selected CAPA activity has a Category of Appointment. | Can create new activities from here by using the Actions option from the CAPA process. |
| Recurrence pattern | View or change the recurrence pattern if the selected CAPA activity has a Category of Appointment. |  |
| Refresh | Update the contents of this list page. |  |
| Export to Microsoft Excel | Export CAPA activity records to a Microsoft Excel worksheet. |  |
| Attachments | View a list of documents attached to the selected CAPA activity. |  |
| **Fields** |  |  |
| Date | The start date for the CAPA activity. |  |
| Purpose | The purpose or description of the CAPA activity. |  |
| Priority | The priority of the CAPA activity. | **The valid Priorities for Activities are Low, Normal or High.** |
| Category | The category of the CAPA activity. | **Valid category options are Action, Appointment, Event and Task.** |
| Type | The type of CAPA activity. | **These are user defined types that can be used for grouping and/or reporting.** |

## Running CAPA case trending analysis

You run trending analysis to view in graphical format the volume of CAPA cases by category to analyze whether the frequency of specific issues that resulted in cases are increasing or declining over time. You can include all CAPA cases in a trending analysis or only those cases that were created as of a specific from date.

To run trending analysis using information collected for CAPA cases, use the **Trending analysis** form.

| **Path: Inventory management \> Inquiries \> CAPA management \> Trending analysis** | &nbsp; | &nbsp; |
|--|--|--|
| **Label Name** | **Description** | **Examples/Hints** |
| **Tabs** |  |  |
| Data | Specify the criteria to use for the trending analysis. |  |
| Analytics by category | View the results of the trending analysis by category. The results are determined based on the criteria you select on the Data tab. If you select all three data options, then three graphs appear on this tab after you run the analysis. Otherwise, only the graphs for the options you select display. |  |
| Analytics by subcategory | View the results of the trending analysis by subcategory. The results are determined based on the criteria you select on the Data tab. You select a CAPA category and up to two data options. |  |
| **Fields** |  |  |
| From date | Select the start date for the analysis. To include all CAPA cases for the current year in the analysis, accept the system default date. Otherwise, specify a different from date. | Defaults to the first day of the current year |
| To date | Select the end date for the analysis. To include all CAPA cases for the current year in the analysis, accept the system default date. Otherwise, specify a different from date. | Defaults to the current date |
| Number of cases opened by | Select this check box to display trending results on a pie chart, which shows the total number of CAPA cases opened by specific users over the date period defined. |  |
| Number of cases by category | Select this check box to display trending results on a pie chart, which shows the total number of CAPA cases by category over the date period defined. |  |
| Trending of cases by category | Select this check box to display trending results on a Line graph, which shows the total number of CAPA cases by category over the date period defined. |  |
| CAPA category | The category assigned to the CAPA case. |  |
| Number of cases by subcategory (Top 10) | Select this check box to display trending results on a pie chart, which shows the CAPA cases by the top 10 subcategories over the date period defined. |  |
| Trending of cases by subcategory (Top 10) | Select this check box to display trending results on a Line graph, which shows the CAPA cases by the top 10 subcategories over the date period defined. |  |
