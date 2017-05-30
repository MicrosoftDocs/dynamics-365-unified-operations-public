---
# required metadata

title: Inventory on-hand mobile workspace
description: This topic provides information about the Inventory on-hand mobile workspace. This workspace helps you gain mobile insights into reserved and available inventory anytime and anywhere.
author: YuyuScheller
manager: AnnBe
ms.date: 05/10/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 267094
ms.assetid: 3fa385ba-894d-4a9e-b394-ef3697abf895
ms.search.region: global
ms.search.industry: Manufacturing
ms.author: mirzaab
ms.dyn365.ops.intro: Version 1611
ms.search.validFrom: 2016-11-30

---

# Inventory on-hand mobile workspace

[!include[banner](../includes/banner.md)]


This topic provides information about the **Inventory on-hand** mobile workspace. This workspace helps you gain insights into reserved and available inventory anytime and anywhere.

This workspace can be used with:
- The Dynamics 365 for Finance and Operations, Enterprise Edition mobile app
- The Dynamics 365 for Operations mobile app

Overview of the Inventory on-hand mobile workspace
--------------------------------------------------

Typically, companies have multiple shipments and multiple receipts of inventory every day. These movements constantly change the on-hand inventory status. The **Inventory on-hand** mobile workspace lets you see the cross-company, on-hand inventory status, so that you can gain the latest insights into inventory data on the mobile device of your choice. Regardless of whether you work in the warehouse, purchasing, sales, manufacturing, or management, or have other roles, you can access on-hand inventory data anytime and anywhere. 

The mobile workspace provides an instant view of the on-hand status across facilities. It lets you view on-hand inventory across facilities, current material reservations, and unreserved on-hand inventory. You can also enter item numbers to query on-hand inventory, and can do a filtered search for on-hand products or variants. 

Specifically, the mobile workspace provides these features:

-   You can search by product number or product name to find products to view the on-hand inventory status for.

-   For the selected products, you can view the following information:
    -   On-hand inventory per site
    -   On-hand inventory per warehouse
    -   On-hand inventory per location
    -   On-hand inventory per batch (for batch-controlled products)
    -   On-hand inventory per inventory status
    
-   Product on-hand inventory is shown in the following ways:
    -   By physical inventory (This view represents the total amount.)
    -   By physical reserved (This view represents the reserved amount.)
    -   By available physical (This view represents available amount that has no reservations.)

## Prerequisites
The prerequisites differ based on the version of Dynamics 365 that has been deployed for your organization.

If Dynamics 365 for Finance and Operations, Enterprise Edition July 2017 update has been deployed for your organization, the system administrator simply needs to publish the **Inventory on-hand** mobile workspace. For instructions, see [Publish a mobile workspace](/dynamics365/operations/dev-itpro/mobile-apps/publish-mobile-workspace).

If Dynamics 365 for Operations version 1611 with platform update 3 or later has been deployed for your organization, the system administator must complete the following prerequisites. 

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
<td>KB 4018050 is an X++ update or metadata hotfix that contains the <strong>Inventory on-hand</strong> mobile workspace. To implement KB 4018050, your system administrator must follow these steps.
<ol>
<li><a href="/dynamics365/operations/dev-itpro/migration-upgrade/download-hotfix-lcs">Download the metadata hotfix from Lifecycle Services (LCS)</a>.</li>
<li><a href="/dynamics365/operations/dev-itpro/migration-upgrade/install-metadata-hotfix-package">Install the metadata hotfix</a>.</li>
<li><a href="/dynamics365/operations/dev-itpro/deployment/create-apply-deployable-package">Create a deployable package</a> that contains the <strong>SCMMobile</strong> model, and then upload the deployable package to LCS.</li>
<li><a href="/dynamics365/operations/dev-itpro/deployment/apply-deployable-package-system">Apply the deployable package</a>.</li>
</ol></td>
</tr>
<tr class="even">
<td>Publish the <strong>Inventory on-hand</strong> mobile workspace.</td>
<td>System administrator</td>
<td>See <a href="/dynamics365/operations/dev-itpro/mobile-apps/publish-mobile-workspace">Publish a mobile workspace</a>.</td>
</tr>
</tbody>
</table>

## Download and install the mobile app
To download and install the Dynamics 365 for Finance and Operations, Enterprise Edition mobile app:

-   For Android: [Dynamics 365 for Finance and Operations, Enterprise Edition on the Google Play Store](https://go.microsoft.com/fwlink/?linkid=850662)
-   For iPhone: [Dynamics 365 for Finance and Operations, Enterprise Edition on the iTunes apps store](https://go.microsoft.com/fwlink/?linkid=850663)

To download and install the Dynamics 365 for Operations mobile app:

-   For Android: [Dynamics 365 for Operations on the Google Play Store](https://play.google.com/store/apps/details?id=com.microsoft.dynamics365.operations.mobile)
-   For iPhone: [Dynamics 365 for Operations on the iTunes apps store](https://itunes.apple.com/us/app/dynamics-365-for-operations/id1180836730?mt=8)

## Sign in to the mobile app
1.  Start the app on your mobile device.
2.  Enter your Dynamics 365 URL.
3.  Enter the company to sign in to. For example, enter **USMF**.
4.  The first time that you sign in, you're prompted for your user name and password. Enter your credentials.
5.  After you sign in, you see the available workspaces for your company. Note that if your system administrator publishes a new workspace later, you can pull to refresh the list of mobile workspaces.

    [![Pull to refresh](./media/pull-to-refresh-list-of-workspaces-183x300.png)](./media/pull-to-refresh-list-of-workspaces.png)

## View the onhand inventory for a product by using the Inventory onhand mobile workspace
1.  On your mobile device, select the **Inventory on-hand** workspace.
2.  Select **Check on-hand for an item**. You see a list of the products that are loaded into your app for offline use. By default, 50 items are loaded, but a developer can change this number. For more information, developers should see [Mobile platform](/dynamics365/operations/dev-itpro/mobile-apps/mobile-platform).
3.  If your item isn't in the list, select **Search more**. Search by product number, or switch to a search by product name.
4.  Select a product. If the item has an image, the image is shown.
5.  Select one of the following options to view the status of on-hand inventory:
    -   View on-hand per site
    -   View on-hand per warehouse
    -   View on-hand per location
    -   View on-hand per batch (for batch-controlled products)
    -   View on-hand per inventory status

    Product on-hand inventory is shown in the following ways:
    -   By physical inventory (This view represents the total amount.)
    -   By physical reserved (This view represents the reserved amount.)
    -   By available physical (This view represents the available amount that has no reservations.)





