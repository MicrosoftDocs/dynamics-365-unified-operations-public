---
# required metadata

title: Personnel management workspace
description: This topic describes the conceptual elements of the Personnel management workspace. 
author: twheeloc
ms.date: 11/03/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: HcmPosition, HcmPersonnelManagementWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.author: twheeloc
ms.reviewer: twheeloc
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


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

The **Personnel management** workspace includes a vast amount of content. It contains personnel movements, tracks employee changes, open positions, address changes, expiring records, and analytics, and provides links to specific information. This topic provides detailed information about each part of the workspace.

## Activity tab

The **Activity** tab contains sections that group workers based on their stage in the employment process:

- **Candidates to hire**
- **Starting soon**
- **Recent hires**
- **Exiting**
- **Exited**

When a worker is in one of these stages, specific actions are available as a button on the card, or on the menu that appears when you select the ellipsis (**...**) in the upper-right corner. The following subsections describe the sections of the **Activity** tab and list the actions that are available.

### Candidates to hire

The **Candidates to hire** section of the workspace is filled in from multiple sources:

- An Open Data Protocol (OData) entity
- LinkedIn integration
- Data that is manually entered in the product

When candidates appear in the **Candidates to hire** section, you can perform the following actions by selecting the ellipsis on the candidate card:

- **Dismiss candidate**
- **Do not hire**
- **Hire**

> [!NOTE]
> If the candidate list is being populated from Microsoft Dataverse, the same candidates will display across all legal entities because a legal entity has not been associated to the candidate.

### Starting soon

The **Starting soon** section lists workers who have a start date in the future. The list is sorted by start date. The start date that is closest to today's data is listed first.

If the manager doesn't appear on the card, a position hasn't been assigned for the worker.

> [!NOTE] 
> We recommend that you assign a position to a worker before you apply a checklist. Sometimes, onboarding tasks are assigned to a newly hired employee's manager. However, if no position is assigned, the new employee's manager can't be determined. In that case, the onboarding tasks that are intended for the manager will be assigned to the checklist owner instead.

When workers appear in the **Starting soon** section, the following actions are available for them:

- Assign position
- Verify employment
- Assign fixed compensation
- Assign variable compensation
- View in Hierarchy
- Apply checklist\*\*

\*\* This action is the default action. It appears as a button on the card.

### Recent hires

The **Recent hires** section lists workers who have a start date in the recent past. The list is sorted by start date. The start date that is closest to today's date is listed first.

By default, the list shows workers who were hired in the last seven days. To change this setting, on the **Human Resources parameters** page, on the **General** tab, define a time frame for **Recent hires**. The data in the **Recent hires** section can be shown for a specific number of days, months, or years. For example, to view the list of workers who were hired in the last 14 days, set the **Period** field to **14** and the **Unit** field to **Days**.

> [!NOTE]
> The settings on the **Human Resources parameters** page are company specific. Therefore, the time frame that you view recent hires for can vary by company. For example, in the USMF company, you might want to view all new hires from the last seven days. However, in the USSI company, you might want to view all new hires from the last 14 days. In this case, open the **Human Resources parameters** page in each company, and set the parameters as required.

If the manager doesn't appear on the card, a position hasn't been assigned for the worker.

When workers appear in the **Recent hires** section, the following actions are available for them:

- Assign position
- Verify employment
- Fixed compensation
- Assign variable compensation
- View in hierarchy
- Apply checklist\*\*

\*\* This action is the default action. It appears as a button on the card.

### Exiting

The **Exiting** section lists workers who have a termination date in the future. The list is sorted by termination date. The termination date that is closest to today's date is listed first. 

By default, the list shows workers who have a termination date in the next seven days. To change this setting, on **Human Resources parameters** page, on the **General** tab, define a time frame for **View exiting workers**. The data in the **Exiting** section can be shown for a specific number of days, months, or years. For example, to view the list of workers who will be terminated in the next 14 days, set the **Period** field to **14** and the **Unit** field to **Days**.

When workers appear in the **Exiting** section, the following actions are available for them:

- Apply checklist\*\*
- Verify employment
- View in Hierarchy

\*\* This action is the default action. It appears as a button on the card.

### Exited

The **Exited** section lists workers who have a termination date in the recent past. The list is sorted by termination date. The termination date that is closest to today's date is listed first.

By default, the list shows workers who have a termination date in the last seven days. To change this setting, on the **Human Resources parameters** page, on the **General** tab, define a time frame for **View exited workers**. The data in the **Exited** section can be shown for a specific number of days, months, or years. For example, to view the list of workers who were terminated in the last 14 days, set the **Period** field to **14** and the **Unit** field to **Days**.

When worker appear in the **Exited** section, the following actions are available for them:

- Apply checklist\*\*
- Verify employment
- View in hierarchy

\*\* This action is the default action. It appears as a button on the card.

## Employee changes tab

The **Employee changes** tab provides a list of all worker personnel actions. This list isn't available by default. To enable the functionality, on the **Human resources shared parameters** page, on the **Personnel actions** tab, set the **Enable worker actions** option to **Yes**.

## Position changes tab

The **Position changes** tab provides a list of all position personnel actions. This list isn't available by default. To enable the functionality, on the **Human resources shared parameters** page, on the **Personnel actions** tab, set the **Enable position actions** option to **Yes**.

## Open positions tab

The **Open positions** tab lists all open positions. To appear in the list, positions must have an activation date of today or earlier, and they must not have a current worker assignment.

> [!NOTE]
> The list considers the worker assignment as of today. Any position that has a future-dated worker assignment will continue to appear in the list. However, after the effective date of the worker assignment is reached, the position will be removed from the list.

## Expiring records tab

The **Expiring records** tab lists all items that have expired or will expire for the workers in the company that the user is signed in to. The following items appear in the list:

- **Certificates**
- **Identification**
- **Probations**
- **Screenings**
- **Tests**

To specify whether the list shows expired records or expiring records, on the **Human Resources parameters** page, on the **General** tab, define a time frame for either **Expiring records** or **Expired records**. The data on the **Expiring records** tab can be shown for a specific number of days. For example, to view the list of records that will expire in the next 14 days, set the **Number of days** field to **14**.

> [!NOTE] 
> If you set the time frame for **Expired records** or **Expiring records** to **0** on the **Human Resources parameters** page, the list won't show any of those records.

## Employees tile

The **Employees** tile provides a count of all employees who are employed in the company that the user is currently signed in to. When you select the **Employees** tile, a new page shows the details of the employees.

## Contractors tile

The **Contractors** tile provides a count of all contractors who are employed in the company that the user is currently signed in to. When you select the **Contractors** tile, a new page shows the details of the contractors.

## Open positions tile

The **Open positions** tile provides a count of all open positions. When you select the **Open positions** tile, a new page shows the details of the open positions. To be included in the count, positions must have an activation date of today or earlier, and they must not have a current worker assignment.

> [!NOTE]
> The tile considers the worker assignment as of today. Any position that has a future-dated worker assignment will continue to be included in the count. However, after the effective date of the worker assignment is reached, the position will be excluded from the count.

## Approvals tile

The **Approvals** tile provides a count of all workflow items that are pending the current user's approval. When you select the **Approvals** tile, a new page shows the details of the workflow items that require your approval.

## Address changes tile

The **Address changes** tile provides a count of all the address changes that occurred during the number of days that is specified on the **Human Resources parameters** page. When you select the **Address changes** tile, a new page shows the details of any address changes. In the upper-right corner of the page, you can select **Include future address changes** to view address changes that have a future date.

For more information about how to view and manage address changes, see [View and manage address changes](hr-personnel-view-address-changes.md).
