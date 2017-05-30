---
# required metadata

title: Mobile app home page
description: This topic describes the Microsoft Dynamics 365 for Finance and Operations, Enterprise Edition mobile app and provides links to resources that can help you implement it in your organization.
author: sericks007
manager: AnnBe
ms.date: 05/28/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
ms.custom: 272853
ms.assetid: c99f818f-27b3-4e45-92b4-74272dad0e17
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.dyn365.ops.intro: Platform update 4
ms.search.validFrom: 2017-02-28

---

# Mobile app home page

[!include[banner](../includes/banner.md)]


This topic describes the mobile app for:
- Microsoft Dynamics 365 for Finance and Operations, Enterprise Edition
- Microsoft Dynamics 365 for Opertaions 

Overview
--------

The mobile app enables your organization to make its business processes available on mobile devices. After your IT admin enables the mobile workspaces for your organization, users can sign in to the app and immediately begin to run business processes from their mobile devices. The mobile app includes the following features that can help increase productivity:

-   Users can view, edit, and act on business data, even if they have intermittent network connectivity or their mobile devices are completely offline. When a device reestablishes a network connection, offline data operations are automatically synchronized with Dynamics 365 for Finance and Operations, Enterprise Edition or Dynamics 365 for Operations.
-   IT admins or developers can build and publish mobile workspaces that have been tailored to their organization. The app uses your existing code assets. Therefore, you don't have to re-implement your validation procedures, business logic, or security configuration.
-   IT admins or developers easily design mobile workspaces by using the point-and-click workspace designer that is included with the web client.
-   IT admins or developers can optionally optimize the offline capabilities of workspaces by using the Business logic extensibility framework. Because data continues to be processed while a device is offline, your mobile scenarios remain rich and fluid, even if devices don't have constant network connectivity.

## Elements of the mobile app
Navigation in the mobile app consists of four simple concepts: the dashboard, workspaces, pages, and actions. 

[![Navigation concepts in the mobile app](./media/mobilephoneapp1-1024x536.png)](./media/mobilephoneapp1.png)

1. When you start the app, you go to the **dashboard**.
2. On the dashboard, you can see a list of **workspaces** that have been published.
3. In each workspace, you can see a list of **pages** that are available for that workspace.

Once you are on a page, you can do several things, such as:
-   View detailed data.
- Navigate to other pages for related data, such as entity details or lines.
-   See a list of **actions** that are available for that page. Actions let you create or edit existing data.


## Implementation process
The following illustration shows the process for implementing mobile workspaces provided by Microsoft, or custom mobile workspaces. 

![Mobile apps implementation process](./media/Mobile-implementation-process-5.png)

The following table includes links to resources that can help you implement mobile workspaces provided by Microsoft, or custom mobile workspaces. The numbers in the first column correspond to the numbered steps in the previous illustration.

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Step</th>
<th>Role</th>
<th>Action</th>
<th>Resources to help you complete the action</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>1</td>
<td>System administrator</td>
<td><p>Implement Dynamics 365 for Finance and Operations, Enterprise Edition or Dynamics 365 for Operations in your organization.</td>
<td>If you haven't deployed a version of Dynamics 365 yet, see <a href="../deployment/deploy-demo-environment.md">Deploy a demo environment</a>.<br></br>To see a list of mobile workspaces that can be implemented with the version of Dynamics 365 that you deployed, see <a href="mobile-workspaces-released.md">Mobile workspaces recently released</a>.</p></td>
</tr>
<tr class="even">
<td>2</td>
<td>System administrator</td>
<td><strong>If you are using Dynamics 365 for Operations version 1611:</strong> Download and install KBs that enable the mobile workspaces that are provided by Microsoft.</td>
<td>See the following topics for more information:
<ul>
<li><a href="/dynamics365/operations/financials/cost-accounting/cost-controlling-mobile-workspace">Cost controlling mobile workspaces</a></li>
<li><a href="/dynamics365/operations/supply-chain/inventory/inventory-on-hand-mobile-workspace">Inventory on-hand mobile workspace</a></li>
<li><a href="/dynamics365/operations/supply-chain/sales-marketing/sales-orders-mobile-workspace">Sales orders mobile workspaces</a></li>
<li><a href="/dynamics365/operations/supply-chain/procurement/vendor-collaboration-mobile-workspace">Vendor collaboration mobile workspace</a></li>
<li><a href="/dynamics365/operations/supply-chain/procurement/purchase-order-mobile-workspace">Purchase order approval mobile workspace</a></li>
<li><a href="/dynamics365/operations/financials/project-management/project-time-entry-mobile-workspace">Project time entry mobile workspace</a></li>
<li><a href="/dynamics365/operations/financials/expense-management/expense-management-mobile-workspace">Expense management mobile workspace</a></li>
</ul></td>
</tr>
<tr class="odd">
<td>3</td>
<td>System administrator</td>
<td>Publish the mobile workspaces that are provided by Microsoft.</td>
<td><a href="publish-mobile-workspace.md">Publish a mobile workspace</a>
</td>
</tr>
<tr class="even">
<td>4</td>
<td>Developer or independent software vendor (ISV)</td>
<td>Use the mobile framework to create custom mobile workspaces.</td>
<td><ul>
<li><a href="mobile-platform.md">Mobile framework</a></li>
<li><a href="http://ax.help.dynamics.com/en/wiki/operations-mobile-workspace-x-apis/">Workspace X++ APIs</a></li>
</ul></td>
</tr>
<tr class="odd">
<td>5</td>
<td>ISV</td>
<td>Create a deployable package that contains custom mobile workspaces, and upload the package to Microsoft Dynamics Lifecycle Services (LCS).</td>
<td><a href="../deployment/create-apply-deployable-package.md">Create a deployable package</a></td>
</tr>
<tr class="even">
<td>6</td>
<td>System administrator</td>
<td>Apply the deployable package that contains the custom workspaces that are provided by the ISV.</td>
<td><a href="../deployment/apply-deployable-package-system.md">Apply a deployable package</a></td>
</tr>
<tr class="odd">
<td>7</td>
<td>System administrator</td>
<td>Publish the custom mobile workspaces that are provided by the ISV.</td>
<td><a href="publish-mobile-workspace.md">Publish a mobile workspace</a></td>
</tr>
<tr class="even">
<td>8</td>
<td>User</td>
<td>Download and install the mobile app.</td>

<td>For Dynamics 365 for Finance and Operations, Enterprise Edition:<ul>
<li>For Android: <a href="https://go.microsoft.com/fwlink/?linkid=850662">Dynamics 365 for Finance and Operations, Enterprise Edition on the Google Play Store</a></li>
<li>For iPhone: <a href="https://go.microsoft.com/fwlink/?linkid=850663">Dynamics 365 for Finance and Operations, Enterprise Edition on the iTunes apps store</a></li></ul>
For Dynamics 365 for Operations:
<ul>
<li>For Android: <a href="https://play.google.com/store/apps/details?id=com.microsoft.dynamics365.operations.mobile">Dynamics 365 for Operations on the Google Play Store</a></li>
<li>For iPhone: <a href="https://itunes.apple.com/us/app/dynamics-365-for-operations/id1180836730?mt=8">Dynamics 365 for Operations on the iTunes apps store</a></li>

</ul></td>
</tr>
<tr class="odd">
<td>9</td>
<td>User</td>
<td>Sign in, and use the mobile app. The app includes the mobile workspaces that have been published by the system administrator.</td>
<td>To see a list of mobile workspaces provided by Microsoft, see <a href="mobile-workspaces-released.md">Mobile workspaces recently released</a>.
</td>
</tr>
</tbody>
</table>





