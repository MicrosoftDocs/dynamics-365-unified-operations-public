---
# required metadata

title: Project time entry mobile workspace 
description: This topic provides information about the Project time entry mobile workspace. This workspace lets users enter and save time against a project by using their mobile device.
author: KimANelson
manager: AnnBe
ms.date: 06/16/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Core, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 272101
ms.assetid: 4505f021-b9bb-4b87-be24-6bf0bd88ee60
ms.search.region: Global
ms.search.industry: Service industries
ms.author: knelson
ms.dyn365.ops.intro: Version 1611
ms.search.validFrom: 2016-11-30

---

# Project time entry mobile workspace

[!include[banner](../includes/banner.md)]

This topic provides information about the **Project time entry** mobile workspace. This workspace lets users enter and save time against a project by using their mobile device.

This mobile workspace is intended to be used with the Microsoft Dynamics 365 for Unified Operations mobile app. 

## Overview
As part of their daily work, project resources are often on-site or traveling. The **Project time entry** mobile workspace lets users enter their billable or non-billable time against a project on the mobile device of their choice. Therefore, project resources can record time entries anytime and anywhere. They can also view time entries that have already been recorded. 

Specifically, in the **Project time entry** mobile workspace, users can perform these tasks:

-   For any selected date, enter the number of hours that you spent on a specific task.
-   Search by project name or customer to find the project to enter time for.
-   Specify the category and activity for the time that you spent.
-   Record the time as billable or non-billable for the project.
-   Optionally enter any external or internal comments.

## Prerequisites
The prerequisites differ, based on the version of Microsoft Dynamics 365 that has been deployed for your organization.

### Prerequisites if you use Microsoft Dynamics 365 for Finance and Operations, Enterprise edition (July 2017) 
If Microsoft Dynamics 365 for Finance and Operations, Enterprise edition (July 2017) has been deployed for your organization, the system administrator must publish the **Project time entry** mobile workspace. For instructions, see [Publish a mobile workspace](../../dev-itpro/mobile-apps/publish-mobile-workspace.md).

### Prerequisites if you use Microsoft Dynamics 365 for Operations version 1611 with platform update 3 or later
If Microsoft Dynamics 365 for Operations version 1611 with platform update 3 or later has been deployed for your organization, the system administrator must complete the following prerequisites. 

<table>
<thead>
<tr class="header">
<th>Prerequisite</th>
<th>Role</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">

<td>Implement KB 4018050.</td>
<td>System administrator</td>
<td>KB 4018050 is an X++ update or metadata hotfix that contains the <strong>Project time entry</strong> mobile workspace. To implement KB 4018050, your system administrator must follow these steps.
<ol>
<li><a href="../../dev-itpro/migration-upgrade/download-hotfix-lcs.md">Download the metadata hotfix from Microsoft Dynamics Lifecycle Services (LCS)</a>.</li>
<li><a href="../../dev-itpro/migration-upgrade/install-metadata-hotfix-package.md">Install the metadata hotfix</a>.</li>
<li><a href="../../dev-itpro/deployment/create-apply-deployable-package.md">Create a deployable package</a> that contains the <strong>ApplicationSuite</strong> and <strong>ProjectMobile</strong> models, and then upload the deployable package to LCS.</li>
<li><a href="../../dev-itpro/deployment/apply-deployable-package-system.md">Apply the deployable package</a>.</li>

</ol></td>
</tr>
<tr class="even">
<td>Publish the <strong>Project time entry</strong> mobile workspace.</td>
<td>System administrator</td>
<td>See <a href="../../dev-itpro/mobile-apps/publish-mobile-workspace.md">Publish a mobile workspace</a>.</td>
</tr>
</tbody>
</table>

## Download and install the mobile app

Download and install the Dynamics 365 for Unified Operations mobile app:

-   [For Android phones](https://go.microsoft.com/fwlink/?linkid=850662)
-   [For iPhones](https://go.microsoft.com/fwlink/?linkid=850663)

## Sign in to the mobile app
1.  Start the app on your mobile device.
2.  Enter your Dynamics 365 URL.
3.  The first time that you sign in, you're prompted for your user name and password. Enter your credentials.
4.  After you sign in, the available workspaces for your company are shown. Note that if your system administrator publishes a new workspace later, you will have to refresh the list of mobile workspaces.

[![Pull to refresh](./media/pull-to-refresh-list-of-workspaces-183x300.png)](./media/pull-to-refresh-list-of-workspaces.png)

## Enter time by using the Project time entry mobile workspace
1.  On your mobile device, select the **Project time entry** workspace.
2.  Select **Time entry**. The calendar dates for the current week are shown.
3.  For a selected date, select **Actions** &gt; **New entry**.
4.  Enter the number of hours to record.
5.  Select the project for the time entry. A list shows the projects that are loaded into your app for offline use. By default, 50 items are loaded, but a developer can change this number. For more information, see [Mobile platform](../../dev-itpro/mobile-apps/platform/mobile-platform-home-page.md).
6.  If your project isn't in the list, select **Search**. Search by name, or switch to search by project name or customer.
7.  Select a category. A list shows the categories that are loaded into your app for offline use. By default, 50 items are loaded, but a developer can change this number. For more information, see [Mobile platform](../../dev-itpro/mobile-apps/platform/mobile-platform-home-page.md).
8.  If your category isn't in the list, select **Search**. Search by category, or switch to search by category name.
9.  Select an activity. A list shows the activities that are loaded into your app for offline use. By default, 50 items are loaded, but a developer can change this number. For more information, see [Mobile platform](../../dev-itpro/mobile-apps/platform/mobile-platform-home-page.md).
10. If your activity isn't in the list, select **Search**. Search by activity number, or switch to search by purpose.

11. Select the line property.
12. Optional: Enter any external and internal comments.
13. Select **Done**.
