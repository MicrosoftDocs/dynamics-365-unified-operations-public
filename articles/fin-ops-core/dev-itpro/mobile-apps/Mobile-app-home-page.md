---
title: Mobile app home page
description: This article describes the finance and operations (Dynamics 365) mobile app and provides links to resources that can help you implement it in your organization.
author: sericks007
ms.date: 05/24/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User, Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sericks
ms.search.validFrom: 2017-02-28
ms.dyn365.ops.version: Platform update 4
ms.collection: get-started
ms.assetid: c99f818f-27b3-4e45-92b4-74272dad0e17
---

# Mobile app home page

[!include [banner](../includes/banner.md)]
[!include [mobile app deprecation](../includes/mobile-app-deprecation-banner.md)]

This article describes the **Finance and operations (Dynamics 365)** mobile app and provides links to resources that can help you implement it in your organization.

## Overview

The mobile app enables your organization to make its business processes available on mobile devices. After your IT admin enables the mobile workspaces for your organization, users can sign in to the app and immediately begin to run business processes from their mobile devices. The mobile app includes the following features that can help increase productivity:

- Users can view, edit, and act on business data, even if they have intermittent network connectivity or their mobile devices are completely offline. When a device reestablishes a network connection, offline data operations are automatically synchronized.
- IT admins or developers can build and publish mobile workspaces that have been tailored to their organization. The app uses your existing code assets. Therefore, you don't have to re-implement your validation procedures, business logic, or security configuration.
- IT admins or developers can easily design mobile workspaces by using the point-and-click workspace designer that is included with the web client.
- IT admins or developers can optionally optimize the offline capabilities of workspaces by using the Business logic extensibility framework. Because data continues to be processed while a device is offline, your mobile scenarios remain rich and fluid, even if devices don't have constant network connectivity.

## Elements of the mobile app
Navigation in the mobile app consists of four basic concepts: the dashboard, workspaces, pages, and actions. 

[![Navigation concepts in the mobile app.](./media/mobilephoneapp1-1024x536.png)](./media/mobilephoneapp1.png)

1. When you start the app, you go to the **dashboard**.
2. On the dashboard, you can see a list of **workspaces** that have been published.
3. In each workspace, you can see a list of **pages** that are available for that workspace.
4. After you're on a page, you can perform several actions. Here are some examples:

    - View detailed data.
    - Navigate to other pages for related data, such as entity details or lines.
    - See a list of **actions** that are available for that page. Actions let you create or edit existing data.

## Implementation process
The following illustration shows the process for implementing both mobile workspaces that are provided by Microsoft and custom mobile workspaces. 

[![Mobile apps implementation process.](./media/Mobile-implementation-process-5.png)](./media/Mobile-implementation-process-5.png)

The following table includes links to resources that can help you implement both mobile workspaces that are provided by Microsoft and custom mobile workspaces. The numbers in the first column correspond to the numbered steps in the previous illustration.

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
<td>Implement the finance and operations app in your organization.</td>
<td><ul><li>If you haven&#39;t yet deployed a version of Microsoft Dynamics 365, see <a href="../deployment/deploy-demo-environment.md">Deploy a demo environment</a>.</li><li>To see a list of mobile workspaces that can be used, see <a href="mobile-workspaces-released.md">Mobile workspaces recently released</a>.</li></ul></td>
</tr>
<tr class="even">
<td>2</td>
<td>System administrator</td>
<td><strong>If you&#39;re using Microsoft Dynamics 365 for Operations version 1611:</strong> Download and install KBs that enable the mobile workspaces that are provided by Microsoft.</td>
<td>See the following topics for more information:
<ul>

<li><a href="../../../finance/cost-accounting/cost-controlling-mobile-workspace.md">Cost controlling mobile workspaces</a></li>
<li><a href="../../../supply-chain/inventory/inventory-on-hand-mobile-workspace.md">Inventory on-hand mobile workspace</a></li>
<li><a href="../../../supply-chain/sales-marketing/sales-orders-mobile-workspace.md">Sales orders mobile workspaces</a></li>
<li><a href="../../../supply-chain/procurement/vendor-collaboration-mobile-workspace.md">Vendor collaboration mobile workspace</a></li>
<li><a href="/dynamics365/project-operations/prod-pma/project-time-entry-mobile-workspace">Project time entry mobile workspace</a></li>
<li><a href="/dynamics365/project-operations/prod-exp/expense-management-mobile-workspace">Expense management mobile workspace</a></li>

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
<td>Use the mobile platform to create custom mobile workspaces.</td>
<td><a href="platform/mobile-platform-home-page.md">Mobile platform</a></td>
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
<td>Apply the deployable package that contains the custom workspaces that are provided by the independent software vendor (ISV).</td>
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
<td>
<a href="https://go.microsoft.com/fwlink/?linkid=850662">Finance and operations app for Android</a><BR/>
<a href="https://go.microsoft.com/fwlink/?linkid=850663">Finance and operations app for iOS</a><BR/>
(Windows Phone unsupported)
</td>
</tr>
<tr class="odd">
<td>9</td>
<td>User</td>
<td>Sign in, and use the mobile app. The app includes the mobile workspaces that have been published by the system administrator.</td>
<td>To see a list of mobile workspaces that are provided by Microsoft, see <a href="mobile-workspaces-released.md">Mobile workspaces recently released</a>.
</td>
</tr>
</tbody>
</table>

## Troubleshooting
[Mobile platform resources](platform/mobile-platform-home-page.md#troubleshooting-the-app)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

