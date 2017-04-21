---
# required metadata

title: Sales orders mobile workspace
description: This topic provides information about the Sales orders mobile workspace, which is available for the Microsoft Dynamics 365 for Operations mobile app. This workspace helps you stay up to date on your sales orders anywhere and anytime. 
author: YuyuScheller
manager: AnnBe
ms.date: 2017-01-12 16 - 53 - 31
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
ms.custom: 267134
ms.assetid: 0ce96511-002b-4de7-b31e-4303f94edc84
ms.search.region: global
ms.search.industry: Manufacturing
ms.author: mirzaab
ms.dyn365.ops.intro: Version 1611
ms.search.validFrom: 2016-11-30

---

# Sales orders mobile workspace

This topic provides information about the Sales orders mobile workspace, which is available for the Microsoft Dynamics 365 for Operations mobile app. This workspace helps you stay up to date on your sales orders anywhere and anytime. 

Overview of the Sales orders mobile workspace
---------------------------------------------

The **Sales orders** mobile workspace accesses Microsoft Dynamics 365 for Operations and lets you view detailed information about each sales order. This information includes the status of the order, contact information for the customer, and contact information for the order taker. The **Sales orders** mobile workspace provides an instant view of sales orders. You can view all sales orders, view sales orders by customer, or view information about a specific sales order. The mobile workspace provides two views to help you analyze sale orders in depth.

### View all sales orders

This view lists all sales orders.

-   Use one of the following filters to select the sales orders to view:
    -   Search by sales order
    -   Search by customer account
    -   Search by customer name
    -   Search by status
    -   Search by release status
    -   Search by created date and time
-   After you select sales orders, you can view the details of specific orders. Specifically, you can view the following information:
    -   Customer name and address information
    -   Various dates for the sales order, such as the requested ship date and the confirmed ship date
    -   Contact information for the order taker
    -   Customer contact information
    -   Order lines
    -   Shipments that show how and when a sales order was shipped

### View orders for a customer

This view lists sales orders by customer.

-   Use one of the following filters to view orders for a customer:
    -   Search by name
    -   Search by account
-   After you select a customer, you can view the following information:
    -   Customer name and group
    -   Customer contact information
    -   Customer sales orders and details about those sales orders:
        -   Customer name and address information
        -   Various sales order dates
        -   Contact information for the order taker
        -   Customer contact information
        -   Order lines
        -   Shipments that show how and when a sales order was shipped

## Prerequisites
Before you can use the **Sales orders** mobile workspace, make sure that your system administrator has the following prerequisites in place.

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
<td>KB 4013633 must be implemented.</td>
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
<td>The <strong>Sales orders</strong> mobile workspace must be published to the Dynamics 365 for Operations mobile app.</td>
<td>System administrator</td>
<td><ol>
<li>Start Dynamics 365 for Operations in your browser.</li>
<li>On the <strong>System parameters</strong> page, select <strong>Manage mobile workspaces</strong>.</li>
<li>Select the <strong>Sales orders</strong> workspace.</li>
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
5.  After you sign in, you see the available workspaces for your company. Note that if your system administrator later publishes a new workspace, you can pull to refresh the list of mobile workspaces. [![Pull to refresh](./media/pull-to-refresh-list-of-workspaces-183x300.png)](./media/pull-to-refresh-list-of-workspaces.png)

## View information about sales orders for a customer by using the mobile workspace
1.  On your mobile device, select the **Sales orders** workspace.
2.  Select **View orders for a customer**.
3.  Use account or customer name information to find the customer.
4.  Select the customer.
5.  Select **Contact information** or **Sales orders**. If you select **Sales orders**, a list of sales orders for the customer is shown.
6.  Select **Sales order**. You can now view information about sales order lines, information about shipments, customer contact information, and contact information for the order taker.


