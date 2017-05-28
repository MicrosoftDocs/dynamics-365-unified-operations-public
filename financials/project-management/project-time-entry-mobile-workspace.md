---
# required metadata

title: Project time entry mobile workspace 
description: This topic provides information about the Project time entry mobile workspace. This workspace lets users enter and save time against a project by using their mobile device.
author: annbe
manager: AnnBe
ms.date: 05/10/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 272101
ms.assetid: 4505f021-b9bb-4b87-be24-6bf0bd88ee60
ms.search.region: Global
ms.search.industry: Service industries
ms.author: annbe
ms.dyn365.ops.intro: Version 1611
ms.search.validFrom: 2016-11-30

---

# Project time entry mobile workspace

[!include[banner](../includes/banner.md)]



This topic provides information about the **Project time entry** mobile workspace. This workspace lets users enter and save time against a project by using their mobile device.

This workspace can be used with:
- The Dynamics 365 for Finance and Operations, Enterprise Edition mobile app
- The Dynamics 365 for Operations mobile app


Overview of the Project time entry mobile workspace
---------------------------------------------------

As part of their daily work, project resources are often on-site or traveling. The **Project time entry** mobile workspace lets users enter their billable or non-billable time against a project on the mobile device of their choice. Therefore, project resources can record time entries anytime and anywhere. They can also view time entries that have already been recorded. 

Specifically, the **Project time entry** mobile workspace provides these features:

-   For any selected date, enter the number of hours that you spent on a specific task.
-   Search by project name or customer to find the project to enter time for.
-   Specify the category and activity for the time that you spent.
-   Record the time as billable or non-billable for the project.
-   Optionally enter any external or internal comments.

## Prerequisites
The prerequisites differ based on the version of Dynamics 365 that has been deployed for your organization.

If Dynamics 365 for Finance and Operations, Enterprise Edition July 2017 update has been deployed for your organization, the system administrator simply needs to publish the **Project time entry** mobile workspace. For instructions, see [Publish a mobile workspace](/dynamics365/operations/dev-itpro/mobile-apps/publish-mobile-workspace).

If Dynamics 365 for Operations version 1611 with platform update 3 or later has been deployed for your organization, the following system administator must complete the following prerequisites. 

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
<td>KB 4018050 must be implemented.</td>
<td>System administrator</td>
<td>KB 4018050 is an X++ update or metadata hotfix that contains the <strong>Project time entry</strong> mobile workspace. To implement KB 4018050, your system administrator must follow these steps.
<ol>
<li>Download KB 4018050 from Microsoft Dynamics Lifecycle Services (LCS).</li>
<li><a href="/dynamics365/operations/dev-itpro/migration-upgrade/install-metadata-hotfix-package">Install the metadata hotfix</a>.</li>
<li><a href="/dynamics365/operations/dev-itpro/deployment/create-apply-deployable-package">Create a deployable package</a> that contains the <strong>ApplicationSuite</strong> and <strong>ProjectMobile</strong> models, and then upload the deployable package to LCS.</li>
<li><a href="/dynamics365/operations/dev-itpro/deployment/apply-deployable-package-system">Apply the deployable package</a> to your Dynamics 365 for Operations system.</li>
</ol></td>
</tr>
<tr class="even">
<td>The <strong>Project time entry</strong> mobile workspace must be published to the Dynamics 365 for Operations mobile app.</td>
<td>System administrator</td>
<td>See <a href="/dynamics365/operations/dev-itpro/mobile-apps/publish-mobile-workspace">Publish a mobile workspace</a>.</td>
</tr>
</tbody>
</table>


## Download and install the mobile app
You can download and install the mobile app from your mobile app store.

To download and install the Dynamics 365 for Finance and Operations, Enterprise Edition:

-   For Android: [Dynamics 365 for Operations on the Google Play Store](https://play.google.com/store/apps/details?id=com.microsoft.dynamics365.operations.mobile)
-   For iPhone: [Dynamics 365 for Operations on the iTunes apps store](https://itunes.apple.com/us/app/dynamics-365-for-operations/id1180836730?mt=8)

To download and install the Dynamics 365 for Operations mobile app.

-   For Android: [Dynamics 365 for Operations on the Google Play Store](https://play.google.com/store/apps/details?id=com.microsoft.dynamics365.operations.mobile)
-   For iPhone: [Dynamics 365 for Operations on the iTunes apps store](https://itunes.apple.com/us/app/dynamics-365-for-operations/id1180836730?mt=8)

## Sign in to the mobile app
1.  Start the app on your mobile device.
2.  Enter your Dynamics 365 URL.
3.  Enter the company to sign in to. For example, enter **USMF**.
4.  The first time that you sign in, you're prompted for your user name and password. Enter your credentials.
5.  After you sign in, you see the available workspaces for your company. Note that if your system administrator publishes a new workspace later, you can pull to refresh the list of mobile workspaces.

[![Pull to refresh](./media/pull-to-refresh-list-of-workspaces-183x300.png)](./media/pull-to-refresh-list-of-workspaces.png)

## Enter time by using the Project time entry mobile workspace
1.  On your mobile device, select the **Project time entry** workspace.
2.  Select **Time entry**. You see the calendar dates for the current week.
3.  For a selected date, select **Actions** &gt; **New entry**.
4.  Enter the number of hours to record.
5.  Select the project for the time entry. You see a list of the projects that are loaded into your app for offline use. By default, 50 items are loaded, but a developer can change this number. For more information, developers should see [Mobile platform](/dynamics365/operations/dev-itpro/mobile-apps/mobile-platform).
6.  If your project isn't in the list, select **Search**. Search by name, or switch to search by project name or customer.
7.  Select a category. You see a list of the categories that are loaded into your app for offline use. By default, 50 items are loaded, but a developer can change this number. For more information, developers should see [Mobile platform](/dynamics365/operations/dev-itpro/mobile-apps/mobile-platform).
8.  If your category isn't in the list, select **Search**. Search by category, or switch to search by category name.
9.  Select an activity. You see a list of the activities that are loaded into your app for offline use. By default, 50 items are loaded, but a developer can change this number. For more information, developers should see [Mobile platform](/dynamics365/operations/dev-itpro/mobile-apps/mobile-platform).
10. If your activity isn't in the list, select **Search**. Search by activity number, or switch to search by purpose.
11. Select the line property.
12. Optional: Enter any external and internal comments.
13. Select **Done**.





