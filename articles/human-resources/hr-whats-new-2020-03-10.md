---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (March 10, 2020)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for March 10, 2020.
author: andreabichsel
ms.date: 03/10/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jaredha
ms.search.validFrom: 2020-03-10
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources (March 10, 2020)

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]



This article describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.2985. The numbers in parentheses in some headings refer to LCS support numbers for reference.

## Can't access skill gap analysis report (394460)

This report isn't supported in Dynamics 365 Human Resources. The menu item to print the SSRS report is removed.

## Incorrect message accessing the Getting Started page (417950)

With this change, security hides this menu item if you don't have access to the form.

## Streamlined task maintenance for employees (380538)

The worker task maintenance form lists all tasks for an employee across onboarding, offboarding, transitions, and business processes. You can delete, reassign, or update the status of tasks.

Example: Benjamin Martin is a benefits administrator. During employee onboarding, tasks are created for Benjamin to review the new employee’s benefit selection. Benjamin has completed the past tasks, and future tasks that need to be completed. Benjamin decides to leave the company, so Benjamin's tasks need to be either re-assigned or removed. The task maintenance form (in the action pane of the **Worker** form) allows all of Benjamin’s tasks to be re-assigned to another worker or removed.  

## Dataverse solution is now available with the following changes:

| Description | Change |
| --- | --- |
| **Job/Position** entity changes | <ul><li>**Compensation region** added</li>|
| **Job position dimension** entity added | <ul><li>**Financial dimensions** added</li>
| **Worker** entity changes | <ul><li>**Name sequence** added</li><li>**Works from home** added</li><li>**Language** added</li><li>**Seniority date** added</li><li>**Anniversary date** added</li><li>**Original hire date** added</li></ul> |
| **Employment** entity changes | <ul><li>**Financial dimensions** added</li><li>**Termination reason** added</li><li>**Termination date** renamed from **Transition date**</li><li>**Probation date** added</li></ul> |
| **Worker address** entity changes | <ul><li>**Street address** added</li><li>**Address line 1**, **Address line 2**, and **Address line 3** marked for deprecation</li></ul> |
| New variable compensation setup entities | <ul><li>**Compensation variable plan type**</li><li>**Compensation variable plan**</li><li>**Vesting rules**</li><li>**Compensation variable plan level**</li></ul> |
| New **Worker calendar employment** entity | <ul><li>**Work calendar entity** added</li></ul> |
| New **Payroll position detail** entity | <ul><li>**Payroll position detail** added</li></ul> |
| New **Title** entity | <ul><li>**Title** added</li></ul> The new **Title** entity is included in Dataverse but isn't referenced from the **Job Position** or **Job** entities at this time. |

> [!NOTE]
> Financial dimensions for both positions and employment provide one-direction integration for updates from Human Resources to Dataverse. Financial dimensions updates don't currently synchronize from Dataverse to Human Resources.

Over the next few weeks, these entity changes will be available in all environments. To manually install the latest Dataverse solution for Human Resources:

1.	Go to the [Power Platform Admin Center](https://admin.powerplatform.microsoft.com).

2.	Select **Environments**.

3.	Find the environment you want to upgrade. The environment should correspond to **Environment name** in the **Dataverse information** section in the **About** form in Human Resources.

4.	Select the environment to view the environment details.

5.	In the action bar at the top, select **Manage Solutions**. A new browser window will open and navigate to **Dynamics 365 Administration Center** in the context of your environment.

6.	In the **Solution** list, select **Dynamics 365 Human Resources Anchor**.

7.	Select **Upgrade** to apply the latest solution.

## In preview

The following preview features are available on February 3, 2020:

- **Leave and absence preview features** - For more information, see [Leave and absence preview features](hr-leave-and-absence-overview.md?leave-and-absence-preview-features).

- **Benefits management preview feature** - For more information, including known issues, see [Benefits management overview](hr-benefits-management-overview.md).

## Coming Soon

### Platform update 33

- Full page apps (Preview) - This preview feature, which requires you to enable the Saved views feature, allows Power Apps and third-party apps to be added as full-page experiences via the dashboard.

- Saved views (Preview) - This preview feature enables saved views, which is a significant enhancement to the personalization subsystem. This feature allows users to have multiple named sets of personalizations per page. You can also publish views to security roles.

- Optimized "is one of" filtering experience - This feature enables an optimized "is one of" filtering experience that makes it easier to enter multiple filter values, has a simpler mechanism to remove individual or all filter values, and has a more compact and intuitive visualization of filter values.

- Recommended fields - Users often need to add fields to a grid or page. This can be difficult with so many available fields. Instead of having to search through a large list, this feature enables the system to surface a set of recommended fields based on what other users most often add in similar scenarios.

- Sticky default actions in grids - This feature ensures that the default action in a grid is linked to a specific column in a grid, regardless of whether that column is moved or hidden.

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2019 release wave 2](/dynamics365-release-plan/2019wave2/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
