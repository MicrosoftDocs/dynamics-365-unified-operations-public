---
# required metadata

title: Cost controlling mobile workspace
description: This topic provides information about the Cost controlling mobile workspace, which is available for the Microsoft Dynamics 365 for Operations mobile app. This workspace lets cost center managers view information about cost center performance anytime and anywhere. 
author: YuyuScheller
manager: AnnBe
ms.date: 2017-01-12 16 - 53 - 04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 267114
ms.assetid: 612f2988-b2b9-420d-9825-40b99dc0e204
ms.search.region: global
# ms.search.industry: 
ms.author: yuyus
ms.dyn365.ops.intro: Version 1611
ms.search.validFrom: 2016-11-30

---

# Cost controlling mobile workspace

[!include[banner](../includes/banner.md)]


This topic provides information about the Cost controlling mobile workspace, which is available for the Microsoft Dynamics 365 for Operations mobile app. This workspace lets cost center managers view information about cost center performance anytime and anywhere. 

Overview of the Cost controlling mobile workspace
-------------------------------------------------

The **Cost controlling** mobile workspace provides an instant view of the current performance of cost centers by comparing actual costs against the budgeted costs. You can drill down to statuses of individual cost elements. For example, an employee receives an invitation to an international conference, but the organization must cover all the travel expenses. The employee asks his manger whether he can attend the conference. The manager opens the **Cost controlling** mobile workspace on her mobile device to see whether she has budget for the employee to attend the conference.

### Data security

The data in the **Cost controlling** mobile workspace is secured through user credentials. Cost center managers are allowed to see data only for their own cost center. The access-level security is managed in the **Cost accounting** module. Cost accountants define the configuration of the **Cost controlling** mobile workspace in the **Cost accounting** module. After the workspace is published to the Microsoft Dynamics 365 for Operations mobile app, it's available in the app. Therefore, all cost center managers in the organization can view data in the same format.

### Actions, views, and links

The **Cost controlling** mobile workspace for the Dynamics 365 for Operations app provides the following actions, views, and links:

-   **Actions:**
    -   Use **Select configuration** to select a layout.
    -   Use **Select cost object** to select the cost centers to filter data on. **Note:** The cost centers that appear in the list depend on the access that is granted in the **Cost accounting** module.
-   **Views:** Based on the actions that are selected and the configuration in the **Cost accounting** module, you can view the following information on the cards.
    -   Actual vs budget (current period)
    -   Actual vs revised budget (current period)
    -   Actual vs budget (previous period)
    -   Actual vs revised budget (previous period)
    -   Actual vs budget (year to date)
    -   Actual vs revised budget (year to date)

    The following amounts are shown on every card: Actual, Budget, Variance, and Variance %.
-   **Links:**
    -   Details for current period
    -   Details for previous period
    -   Details for year to date

    When you select a link, a card is shown for each cost element. The following amounts are shown on every card: Actual, Budget, Budget variance, Budget variance %, Revised budget, Revised budget variance, and Revised budget variance %. 
    
    [![Card for a cost element ](./media/cost-controlling.png)](./media/cost-controlling.png)

## Prerequisites
Before you can use the **Cost controlling** mobile workspace, make sure that your system administrator has the following prerequisites in place.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Prerequisite</th>
<th>Role</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Dynamics 365 for Operations version 1611 with platform update 3 or later must be implemented.</td>
<td>System administrator</td>
<td>If you don’t already have Dynamics 365 for Operations deployed in your organization, the system administrator should see <a href="http://ax.help.dynamics.com/en/wiki/deploy-an-ax7-demo-environment/">Deploy a Microsoft Dynamics 365 for Operations demo environment</a>.</td>
</tr>
<tr class="even">
<td>KB 4013633 must be implemented.</td>
<td>System administrator</td>
<td>KB 4013633 (an X++ update or metadata hotfix) contains four mobile workspaces for supply chain management. To implement KB 4013633, your system administrator must follow these steps:
<ol>
<li>Download KB 4013633 from Microsoft Dynamics Lifecycle Services (LCS).</li>
<li><a href="https://ax.help.dynamics.com/en/wiki/configuring-and-installing-a-metadata-hotfix-package/">Install the metadata hotfix</a>.</li>
<li><a href="https://ax.help.dynamics.com/en/wiki/create-and-apply-a-deployable-package/">Create a deployable package</a> that contains the <strong>SCMMobile</strong> model, and then upload the deployable package to LCS.</li>
<li><a href="https://ax.help.dynamics.com/en/wiki/apply-a-deployable-package-on-a-dynamics-ax-system/">Apply the deployable package</a> to your Dynamics 365 for Operations system.</li>
</ol></td>
</tr>
<tr class="odd">
<td>The <strong>Cost controlling</strong> mobile workspace must be published to the Dynamics 365 for Operations mobile app.</td>
<td>System administrator</td>
<td><ol>
<li>Start Dynamics 365 for Operations in your browser.</li>
<li>On the <strong>System parameters</strong> page, select <strong>Manage mobile workspaces</strong>.</li>
<li>Select the <strong>Cost object overview</strong> workspace.</li>
<li>Click <strong>Publish mobile workspace</strong>.</li>
</ol></td>
</tr>
</tbody>
</table>

## Download and install the Dynamics 365 for Operations mobile app
Download and install the Dynamics 365 for Operations mobile app from your mobile app store.

-   For Android: [Dynamics 365 for Operations on the Google Play Store](https://play.google.com/store/apps/details?id=com.microsoft.dynamics365.operations.mobile)
-   For iPhone: [Dynamics 365 for Operations on the iTunes apps store](https://itunes.apple.com/us/app/dynamics-365-for-operations/id1180836730?mt=8)

## Sign in to the Dynamics 365 for Operations mobile app
1.  Start the app on your mobile device.
2.  Enter your Dynamics 365 for Operations URL.
3.  Enter the company to sign in to. For example, enter **USMF**.
4.  The first time that you sign in, you’re prompted for the user name and password for your Dynamics 365 for Operations account. Enter your credentials.
5.  After you sign in, you see the available workspaces for your company. Note that if your system administrator later publishes a new workspace, you can pull to refresh the list of mobile workspaces. 

    [![Pull to refresh](./media/pull-to-refresh-list-of-workspaces-183x300.png)](./media/pull-to-refresh-list-of-workspaces.png)

## View the performance of your cost center by using the Cost controlling mobile workspace
1.  On your mobile device, select the **Cost controlling** workspace.
2.  Select **Cost object controlling**.
3.  Select **Actions**.
4.  Select **Select configuration** to select a cost controlling layout.
5.  Select **Done**.
6.  Select **Actions**.
7.  Select **Select cost object** to select the cost centers that you've been granted access to.
8.  Select **Done**.
9.  View the overall performance of your cost center.
10. Select the **Details for current period** link.
11. View the performance of individual cost elements.
12. You can also search for specific cost elements.




