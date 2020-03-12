---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (March 10, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources.
author: Darinkramer
manager: AnnBe
ms.date: 3/9/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2020-03-09
ms.dyn365.ops.version: Human Resources

---
# "What's new or changed in Dynamics 365 Human Resources (March 10, 2020)"

This article describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.2985. The numbers in parentheses in some headings refer to LCS support numbers for reference.

## Can't access skill gap analysis report - (394460)

This report is not supported in Dynamics 365 Human Resources. The menu item to print the SSRS report has been removed.

## Incorrect message accessing the "Getting Started" page - (417950)

With this change, security will now trim this menu item if you do not have access to the form.

## Streamlined task maintenance for employees - (380538)

The worker task maintenance form lists all tasks for an employee across onboarding, offboarding, transitions, and business processes.  Tasks can be deleted, reassigned or have the status updated.  Example:  Benjamin Martin is the benefits administrator. When individuals are onboarded, tasks are created for Benjamin to review the new employee’s benefit selection.  Benjamin has past tasks that he has completed, and future tasks that need to be completed.  Benjamin decides to leave the company, so his tasks need to either be re-assigned or removed.  The task maintenance form (in the action pane of the Worker form) allows all of Benjamin’s tasks to be re-assigned to another worker or removed.  

## Common Data Service solution is now available with the following changes:

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
| New **Title** entity | <ul><li>**Title** added</li></ul> |
*The new "Title" entity is included in the CDS but will not initially be referenced from Job Position or Job entities.

*Financial dimensions for both positions and employment provide **Single** direction updates from Human Resources to the Common data service.  

Over the course of the next few weeks the above changes will be available in all environments. If you would like to manually install the latest HR CDS Solution, follow the steps below. 

1.	Navigate to https://admin.powerplatform.microsoft.com.
2.	Select Environments.
3.	Find the environment you would like to upgrade. This should correspond to the Environment name in the Common data service information section in the About form found in D365 for Human Resources.
4.	Click on the Name of the environment to go to the environment details.
5.	In the Action bar at the top of the page, click Manage Solutions.  This will open a new browser window and navigate to Dynamics 365 Administration Center in the context of your environment.
6.	In the Solution list, find the Dynamics 365 for Talent Anchor solution and click on it.
7.	Click the Upgrade button to apply the latest Solution version.

## In preview

The following preview features are available on February 3, 2020:

- **Leave and absence preview features** - For more information, see [Leave and absence preview features](hr-leave-and-absence-overview.md?leave-and-absence-preview-features).

- **Benefits management preview feature** - For more information, including known issues, see [Benefits management overview](hr-benefits-management-overview.md).

## Coming Soon

### Platform update 33

- (Preview) full page apps - This preview feature, which requires the Saved views feature to be enabled, allows Power Apps and third-party apps to be added as full-page experiences via the dashboard
- (Preview) Saved views - This preview feature enables saved views, which is a significant enhancement to the personalization subsystem. This feature allows users to have multiple named sets of personalizations per page. Views can also be published to security roles.
- Optimized "is one of" filtering experience - This feature enables an optimized "is one of" filtering experience that makes it easier to enter multiple filter values, has a simpler mechanism to remove individual or all filter values, and has a more compact and intuitive visualization of filter values.
- Recommended fields - Users often need to add fields to a grid or page; however, with the large number of available fields, this can be difficult. Instead of having to search through a large list, this feature enables the system to surface a set of recommended fields based on what other users most often add in similar scenarios
- Sticky default actions in grids - This feature ensures that the default action in a grid is linked to a specific column in a grid, regardless of whether that column is moved or hidden.
