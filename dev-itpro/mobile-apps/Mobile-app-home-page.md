---
# required metadata

title: Dynamics 365 for Operations mobile app home page
description: This topic describes the Microsoft Dynamics 365 for Operations mobile app and provides links to resources that can help you implement it in your organization.
author: sericks007
manager: AnnBe
ms.date: 04/10/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
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

# Dynamics 365 for Operations mobile app home page

[!include[banner](../includes/banner.md)]

[!include[banner](../includes/banner.md)]


This topic describes the Microsoft Dynamics 365 for Operations mobile app and provides links to resources that can help you implement it in your organization.

Overview
--------

The Microsoft Dynamics 365 for Operations mobile app enables your organization to make its business processes available on mobile devices. After your IT admin enables the mobile workspaces feature for your organization, users can sign in to the app and immediately begin to run business processes from their mobile devices. The Dynamics 365 for Operations mobile app includes the following features that can help increase productivity:

-   Users can view, edit, and act on business data, even if they have intermittent network connectivity or their mobile devices are completely offline. When a device reestablishes a network connection, offline data operations are automatically synchronized with Dynamics 365 for Operations.
-   IT admins or developers can build and publish mobile workspaces that have been tailored to their organization. The app uses your existing code assets. Therefore, you don't have to re-implement your validation procedures, business logic, or security configuration.
-   IT admins or developers easily design mobile workspaces by using the point-and-click workspace designer that is included with the Dynamics 365 for Operations web client.
-   IT admins or developers can optionally optimize the offline capabilities of workspaces by using the Business logic extensibility framework. Because data continues to be processed while a device is offline, your mobile scenarios remain rich and fluid, even if devices don't have constant network connectivity.

## Elements of the mobile app
Navigation in the mobile app consists of four simple concepts: the dashboard, workspaces, pages, and actions. 

[![Navigation concepts in the mobile app](./media/mobilephoneapp1-1024x536.png)](./media/mobilephoneapp1.png)

-   When you start the app, you go to the **dashboard**.
-   On the dashboard, you can see a list of **workspaces** that are published in your Dynamics 365 for Operations environment.
-   In each workspace, you can see a list of **pages** that are available for that workspace.
-   On a page, you can view data that is collected from one or more pages in Dynamics 365 for Operations.
-   From a page, you can navigate to other pages for related data, such as entity details or lines.
-   On a page, you can also see a list of **actions** that are available for that page.
-   Actions let you create or edit existing data.

## Implementation process
The following illustration shows the process for implementing the Dynamics 365 for Operations mobile app in your organization. 

[![Mobile apps implementation process](./media/mobile-implementation-process_4.png)]

The following table includes links to resources that can help you implement the Dynamics 365 for Operations mobile app in your organization. The numbers in the first column correspond to the numbered steps in the previous illustration.

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
<td>Implement Dynamics 365 for Operations for the organization.</td>
<td>If you don't already have Dynamics 365 for Operations deployed in your organization, see <a href="https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/deployment/deploy-demo-environment">Deploy a Microsoft Dynamics 365 for Operations demo environment</a>.</td>
</tr>
<tr class="even">
<td>2</td>
<td>System administrator</td>
<td>Download and install KBs that enable the mobile workspaces that are provided by Microsoft.</td>
<td>See the &quot;Prerequisites&quot; section in the topic about the mobile workspace that your organization wants to use:
<ul>
<li><a href="https://docs.microsoft.com/en-us/dynamics365/operations/financials/cost-accounting/cost-controlling-mobile-workspace">Cost controlling mobile workspaces</a></li>
<li><a href="https://docs.microsoft.com/en-us/dynamics365/operations/supply-chain/production-control/inventory-on-hand-mobile-workspace">Inventory on-hand mobile workspace</a></li>
<li><a href="https://docs.microsoft.com/en-us/dynamics365/operations/supply-chain/production-control/sales-orders-mobile-workspace">Sales orders mobile workspaces</a></li>
<li><a href="https://docs.microsoft.com/en-us/dynamics365/operations/supply-chain/procurement/vendor-collaboration-mobile-workspace">Vendor collaboration mobile workspace</a></li>
<li><a href="https://docs.microsoft.com/en-us/dynamics365/operations/financials/project-management/project-time-entry-mobile-workspace">Project time entry mobile workspace</a></li>
</ul></td>
</tr>
<tr class="odd">
<td>3</td>
<td>System administrator</td>
<td>Publish the mobile workspaces that are provided by Microsoft.</td>
<td>See the &quot;Prerequisites&quot; section in the topic about the mobile workspace that your organization wants to use:
<ul>
<li><a href="https://docs.microsoft.com/en-us/dynamics365/operations/financials/cost-accounting/cost-controlling-mobile-workspace">Cost controlling mobile workspaces</a></li>
<li><a href="https://docs.microsoft.com/en-us/dynamics365/operations/supply-chain/production-control/inventory-on-hand-mobile-workspace">Inventory on-hand mobile workspace</a></li>
<li><a href="https://docs.microsoft.com/en-us/dynamics365/operations/supply-chain/production-control/sales-orders-mobile-workspace">Sales orders mobile workspaces</a></li>
<li><a href="https://docs.microsoft.com/en-us/dynamics365/operations/supply-chain/procurement/vendor-collaboration-mobile-workspace">Vendor collaboration mobile workspace</a></li>
<li><a href="https://docs.microsoft.com/en-us/dynamics365/operations/financials/project-management/project-time-entry-mobile-workspace">Project time entry mobile workspace</a></li>
</ul></td>
</tr>
<tr class="even">
<td>4</td>
<td>Developer or independent software vendor (ISV)</td>
<td>Use the Dynamics 365 for Operations mobile framework to create custom mobile workspaces.</td>
<td><ul>
<li><a href="https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/mobile-apps/mobile-platform">Dynamics 365 for Operations mobile framework</a></li>
<li><a href="http://ax.help.dynamics.com/en/wiki/operations-mobile-workspace-x-apis/">Dynamics 365 for Operations workspace X++ APIs</a></li>
</ul></td>
</tr>
<tr class="odd">
<td>5</td>
<td>ISV</td>
<td>Create a deployable package that contains custom mobile workspaces, and upload the package to Microsoft Dynamics Lifecycle Services (LCS).</td>
<td><a href="https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/deployment/create-apply-deployable-package">Generate a deployable package</a></td>
</tr>
<tr class="even">
<td>6</td>
<td>System administrator</td>
<td>Apply the deployable package that contains the custom workspaces that are provided by the ISV.</td>
<td><a href="https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/deployment/apply-deployable-package-system">Apply a deployable package on a Microsoft Dynamics 365 for Operations system</a></td>
</tr>
<tr class="odd">
<td>7</td>
<td>System administrator</td>
<td>Publish the custom mobile workspaces that are provided by the ISV.</td>
<td><a href="https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/mobile-apps/publish-mobile-workspace">Publish a mobile workspace</a></td>
</tr>
<tr class="even">
<td>8</td>
<td>User</td>
<td>Download and install the Dynamics 365 for Operations mobile app.</td>
<td><ul>
<li>For Android: <a href="https://play.google.com/store/apps/details?id=com.microsoft.dynamics365.operations.mobile">Dynamics 365 for Operations on the Google Play Store</a></li>
<li>For iPhone: <a href="https://itunes.apple.com/us/app/dynamics-365-for-operations/id1180836730?mt=8">Dynamics 365 for Operations on the iTunes apps store</a></li>
</ul></td>
</tr>
<tr class="odd">
<td>9</td>
<td>User</td>
<td>Sign in, and use the Dynamics 365 for Operations mobile app. The app includes the mobile workspaces that have been published.</td>
<td>Microsoft has provided the following mobile workspaces:
<ul>
<li><a href="https://docs.microsoft.com/en-us/dynamics365/operations/financials/cost-accounting/cost-controlling-mobile-workspace">Cost controlling mobile workspaces</a></li>
<li><a href="https://docs.microsoft.com/en-us/dynamics365/operations/supply-chain/production-control/inventory-on-hand-mobile-workspace">Inventory on-hand mobile workspace</a></li>
<li><a href="https://docs.microsoft.com/en-us/dynamics365/operations/supply-chain/production-control/sales-orders-mobile-workspace">Sales orders mobile workspaces</a></li>
<li><a href="https://docs.microsoft.com/en-us/dynamics365/operations/supply-chain/procurement/vendor-collaboration-mobile-workspace">Vendor collaboration mobile workspace</a></li>
<li><a href="https://docs.microsoft.com/en-us/dynamics365/operations/financials/project-management/project-time-entry-mobile-workspace">Project time entry mobile workspace</a></li>
</ul></td>
</tr>
</tbody>
</table>



See also
--------

[Mobile workspaces recently released for the Dynamics 365 for Operations mobile app](mobile-workspaces-released.md)




