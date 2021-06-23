---
# required metadata

title: Personnel management workspace
description: This article describes the conceptual elements of the Personnel management workspace. 
author: andreabichsel
ms.date: 06/23/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: HcmPosition, HcmPersonnelManagementWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.author: anbichse
ms.reviewer: anbichse
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 269054
ms.assetid: 889a8fab-0eef-45c2-91fc-ff2f4d44d54f
ms.search.region: Global
# ms.search.industry: 
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Personnel management workspace

The personnel management workspace contains a vast amount of content! It contains personnel movements, tracks employee changes, open positions, address changes, expiring records, analytics and provides links to detail forms. The purpose of this topic is provide detailed information regarding each section of the workspace.

## Activity tab

The activity tab contains groupings of workers in various stages of the employment process. The stages are:

-   Candidates to hire

-   Starting soon

-   Recent hires

-   Exiting

-   Exited

When a worker is in any of the stages listed above, certain actions are available as a button on the card or under the ellipses in the upper right corner. The actions available are listed in the detailed sections below.

### Candidates to hire

The candidates to hire section of the Personnel Management workspace is populated via multiple sources.

1.  Odata entity

2.  LinkedIn integration

3.  Manually entered in the product

When candidates are in the Candidates to hire section, the following actions can be taken by selecting the ellipses on the candidate card:

-   Dismiss candidate

-   Do not hire

-   Hire

**Tip**: If the candidate list is being populated from XXX entity in CDS, the same candidates will display across all legal entities because a legal entity has not be associated to the candidate.

### Starting soon

The starting soon list, is a list of workers with a start date in the future. The list is sorted by start date; with the start date closest to today being listed first.

If the manager does not display on the card, it means that a position has not been assigned for that worker.

**Tip:** It is recommended to assign a position to the worker before applying a checklist, as sometimes tasks are assigned to the newly hired employee’s manager. Without a position assigned, the new employee’s manager cannot be determined. In that case the onboarding tasks intended for the manager will be assigned to the checklist owner instead.

When a worker is in the starting soon section, the following actions will be available to them:

-  Assign position

-  Verify employment

-  Assign fixed compensation

-  Assign variable compensation

-  View in Hierarchy

-  Apply checklist\*\*

\*\*Indicates the default action that displays as a button on the card.

### Recent hires

The recent hires list, is a list of workers with a start date in the recent past. The list is sorted by start date; with the start date closest to today being listed first. Be default, workers hired in the past 7 days will display in this list. To change this setting, navigate to Human Resources parameters – General tab – Recent hires date range. The period of time for viewing data in this section can be set to days, months, years. For example: You may to see individuals who have started in the past 14 days. You would set Period = 14 and Unit = Days.

Tip: This setting is in Human Resources Parameters, which sets parameters per company. Therefore, the time frame in which you see recent new hires, can be different between companies. For example, in USMF you may want to see all new hires from the past 7 days. However, in USSI you would like to see all new hires from past 14 days. You would navigate to Human Resources parameters in each company to set this.

If the manager does not display on the card, it means that a position has not been assigned for that worker.

When a worker is in the starting soon section, the following actions will be available to them:

-  Assign position

-  Verify employment

-   fixed compensation

-  Assign variable compensation

-  View in Hierarchy

-  Apply checklist\*\*

\*\*Indicates the default action that displays as a button on the card.

### Exiting

The Exiting list, is a list of workers with a termination in the future. The list is sorted by termination date; with the termination date closest to today being listed first. By default, workers with a termination date in the upcoming 7 days will display in this list. To change this setting, navigate to Human Resources parameters – General tab – View exiting workers date range. The period of time for viewing data in this section can be set to days, months, years. For example: You may want to see individuals who will be terminated in the next 14 days. You would set Period = 14 and Unit = Days.

When a worker is in the Exiting section, the following actions will be available to them:

-  Apply checklist\*\*

-  Verify employment

-  View in Hierarchy

\*\*Indicates the default action that displays as a button on the card.

### Exited

The Exited list is a list of workers with a termination in the recent past. The list is sorted by termination date; with the termination date closest to today being listed first. By default, workers with a termination date in the past 7 days will display in this list. To change this setting, navigate to Human Resources parameters – General tab – View exited workers date range. The period of time for viewing data in this section can be set to days, months, years. For example: You may want to see individuals who were terminated in the past 14 days. You would set Period = 14 and Unit = Days.

When a worker is in the Exited section, the following actions will be available to them:

-  Apply checklist\*\*

-  Verify employment

-  View in Hierarchy

\*\*Indicates the default action that displays as a button on the card.

## Employee changes tab

The Employee changes tab provides a list of all Worker Personnel Actions. This list is not available by default. To enable this functionality navigate to Human Resources Shared Parameters Personnel Actions and enable Worker Actions.

Learn more about Personnel Actions here (Link to Personnel Actions page).

## Position changes tab

The Position changes tab provides a list of all Position Personnel Actions. This list is not available by default. To enable this functionality navigate to Human Resources Shared Parameters Personnel Actions and enable Personnel Actions.

Learn more about Personnel Actions here (Link to Personnel Actions page).

## Open positions tab

The Open positions tab provides a list of all open positions. Positions in the list must have an activation of today or older, and must not have a current worker assignment.

Tip: The list looks at the worker assignment as of today, therefore, if a position has a future dated worker assignment, the position will continue to show in the list. Once the worker assignment effective date is met, the position will be removed from the list.

## Expiring records tab

The Expiring records tab provides a list of items that will be expiring or have expired for the workers in the company that the user is logged into. The following is a list of items that will show in this tab:

-  Certificates

-  Identification

-  Probations

-  Screenings

-  Tests

To change whether expired or expiring records display in this list, navigate to Human Resources parameters – General tab – Expiring records range or Expired records range. The period of time for viewing data in this section can be set to days. For example: You may want to see records expiring in the next 14 days. You would set Number of days = 14.

Tip: If you set Expired records range or Expiring records range = 0 in Parameters, then those records will not be displayed in the list.

## Employees Tile

The Employees tile shows the number of employees that are employed in the company that the user is currently logged into. When you select the Employees tile, a new page displays the details of the employees.

## Contractors Tile

The Contractors tile shows the number of contractors that are employed in the company that the user is currently logged into. When you select the Contractors tile, a new page displays the details of the contractors.

## Open positions Tile

The Open positions tile provides a count of all open positions. When you select the **Open postions** tile, a new page displays the details of any open positions. Positions must have an activation of today or older, and must not have a current worker assignment to be counted in the tile.

Tip: The tile looks at the position as of today. Therefore, if a position has a future dated worker assignment, the position will continue to show in the list. Once the worker assignment effective date is met, the position will be removed from the list.

## Approvals Tile

The Open positions tile provides a count of all workflow items that are pending the current users approval. When you select the Approvals tile, a new page displays the details of any workflow items needing approval.

## Address changes Tile

The address changes tile provides a count of how many address changes occurred in the number of days specified in the **Human resources parameters** page.

When you select the **Address changes** tile, a new page displays the details of any address changes. You can optionally select **Include future address changes** in the upper-right corner to display address changes with a future date.

Learn more about viewing and managing address changes here: <https://docs.microsoft.com/en-us/dynamics365/human-resources/hr-personnel-view-address-changes>
