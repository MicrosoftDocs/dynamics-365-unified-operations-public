---
# required metadata

title: Sales orders mobile workspace
description: This topic provides information about the Sales orders mobile workspace. This workspace helps you stay up to date about your sales orders anywhere and anytime. 
author: Mirzaab
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

[!include[banner](../includes/banner.md)]

This topic provides information about the **Sales orders** mobile workspace. This workspace helps you stay up to date about your sales orders anywhere and anytime. 

This mobile workspace is intended to be used with the Microsoft Dynamics 365 for Unified Operations mobile app.

## Overview
The **Sales orders** mobile workspace lets you view detailed information about each sales order. This information includes the status of the order, contact information for the customer, and contact information for the order taker. The **Sales orders** mobile workspace provides an instant view of sales orders. You can view all sales orders, view sales orders by customer, or view information about a specific sales order. 

The mobile workspace provides two views to help you analyze sale orders in depth.

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
The prerequisites differ, based on the version of Microsoft Dynamics 365 that has been deployed for your organization.

### Prerequisites if you use Microsoft Dynamics 365 for Finance and Operations, Enterprise edition July 2017 update 
If the Dynamics 365 for Finance and Operations, Enterprise edition July 2017 update has been deployed for your organization, the system administrator must publish the **Sales orders** mobile workspace. For instructions, see [Publish a mobile workspace](/dynamics365/unified-operations/dev-itpro/mobile-apps/publish-mobile-workspace).

### Prerequisites if you use Dynamics 365 for Operations version 1611 with platform update 3 or later
If Dynamics 365 for Operations version 1611 with platform update 3 or later has been deployed for your organization, the system administrator must complete the following prerequisites. 

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
<td>Implement KB 4013633.</td>
<td>System administrator</td>

<td>KB 4013633 is an X++ update or metadata hotfix that contains the <strong>Cost controlling</strong> mobile workspace. To implement KB 4013633, your system administrator must follow these steps.
<ol>
<li><a href="/dynamics365/unified-operations/dev-itpro/migration-upgrade/download-hotfix-lcs">Download the metadata hotfix from Microsoft Dynamics Lifecycle Services (LCS)</a>.</li>
<li><a href="/dynamics365/unified-operations/dev-itpro/migration-upgrade/install-metadata-hotfix-package">Install the metadata hotfix</a>.</li>
<li><a href="/dynamics365/unified-operations/dev-itpro/deployment/create-apply-deployable-package">Create a deployable package</a> that contains the <strong>SCMMobile</strong> model, and then upload the deployable package to LCS.</li>
<li><a href="/dynamics365/unified-operations/dev-itpro/deployment/apply-deployable-package-system">Apply the deployable package</a>.</li>

</ol></td>
</tr>
<tr class="even">
<td>Publish the <strong>Sales orders</strong> mobile workspace.</td>
<td>System administrator</td>
<td>See <a href="/dynamics365/unified-operations/dev-itpro/mobile-apps/publish-mobile-workspace">Publish a mobile workspace</a>.</td>
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
4.  After you sign in, the available workspaces for your company is shown. Note that if your system administrator publishes a new workspace later, you will have to refresh the list of mobile workspaces.

[![Pull to refresh](./media/pull-to-refresh-list-of-workspaces-183x300.png)](./media/pull-to-refresh-list-of-workspaces.png)

## View information about sales orders for a customer by using the Sales order mobile workspace

1.  On your mobile device, select the **Sales orders** workspace.
2.  Select **View orders for a customer**.
3.  Use account or customer name information to find the customer.
4.  Select the customer.
5.  Select **Contact information** or **Sales orders**. If you select **Sales orders**, a list of sales orders for the customer is shown.
6.  Select **Sales order**. You can now view information about sales order lines, information about shipments, customer contact information, and contact information for the order taker.
