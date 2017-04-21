---
# required metadata

title: Inventory on-hand mobile workspace
description: This topic provides information about the Inventory on-hand mobile workspace, which is available for the Microsoft Dynamics 365 for Operations mobile app. This workspace helps you gain mobile insights into reserved and available inventory anytime and anywhere.
author: YuyuScheller
manager: AnnBe
ms.date: 2017-01-12 16 - 44 - 40
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
ms.custom: 267094
ms.assetid: 3fa385ba-894d-4a9e-b394-ef3697abf895
ms.search.region: global
ms.search.industry: Manufacturing
ms.author: mirzaab
ms.dyn365.ops.intro: Version 1611
ms.search.validFrom: 2016-11-30

---

# Inventory on-hand mobile workspace

This topic provides information about the Inventory on-hand mobile workspace, which is available for the Microsoft Dynamics 365 for Operations mobile app. This workspace helps you gain mobile insights into reserved and available inventory anytime and anywhere.

Overview of the Inventory on-hand mobile workspace
--------------------------------------------------

Typically, companies have multiple shipments and multiple receipts of inventory every day. These movements constantly change the on-hand inventory status. The **Inventory on-hand** mobile workspace lets you see the cross-company, on-hand inventory status, so that you can gain the latest insights into inventory data on the mobile device of your choice. Regardless of whether you work in the warehouse, purchasing, sales, manufacturing, or management, or have other roles, you can access on-hand inventory data anytime and anywhere. The mobile workspace provides an instant view of the on-hand status across facilities. It lets you view on-hand inventory across facilities, current material reservations, and unreserved on-hand inventory. You can also enter item numbers to query on-hand inventory, and can do a filtered search for on-hand products or variants. Specifically, the mobile workspace provides these features:

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
Before you can use the **Inventory on-hand** mobile workspace, make sure that your system administrator has the following prerequisites in place.

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
<td>Microsoft Dynamics 365 for Operations version 1611 with platform update 3 or later must be implemented.</td>
<td>System administrator</td>
<td>If you don’t already have Dynamics 365 for Operations deployed in your organization, the system administrator should see <a href="http://ax.help.dynamics.com/en/wiki/deploy-an-ax7-demo-environment/">Deploy a Microsoft Dynamics 365 for Operations demo environment</a>.</td>
</tr>
<tr class="even">
<td>KB 4013633 must be implemented.</td>
<td>System administrator</td>
<td>KB 4013633 (an X++ update or metadata hotfix) contains four mobile workspaces for supply chain management. To implement KB 4013633, your system administrator must follow these steps:
<ol>
<li>Download KB 4013633 from Microsoft Dynamics Lifecycle Services (LCS).</li>
<li><a href="https://ax.help.dynamics.com/en/wiki/configuring-and-installing-a-metadata-hotfix-package/">Install the metadata hotfix</a>.</li>
<li><a href="https://ax.help.dynamics.com/en/wiki/create-and-apply-a-deployable-package/">Create a deployable package</a> that contains the <strong>SCMMobile</strong> model, and then upload the deployable package to LCS.</li>
<li><a href="https://ax.help.dynamics.com/en/wiki/apply-a-deployable-package-on-a-dynamics-ax-system/">Apply the deployable package</a> to your Dynamics 365 for Operations system.</li>
</ol></td>
</tr>
<tr class="odd">
<td>The <strong>Inventory on-hand</strong> mobile workspace must be published to the Dynamics 365 for Operations mobile app.</td>
<td>System administrator</td>
<td><ol>
<li>Start Dynamics 365 for Operations in your browser.</li>
<li>On the <strong>System parameters</strong> page, select <strong>Manage mobile workspaces</strong>.</li>
<li>Select the <strong>Inventory on-hand</strong> workspace.</li>
<li>Click <strong>Publish mobile workspace</strong>.</li>
</ol></td>
</tr>
</tbody>
</table>

## Download and install the Dynamics 365 for Operations mobile app
Download and install the Dynamics 365 for Operations mobile app from your mobile app store.

-   For Android: [Dynamics 365 for Operations on the Google Play Store](https://play.google.com/store/apps/details?id=com.microsoft.dynamics365.operations.mobile)
-   For iPhone: [Dynamics 365 for Operations on the iTunes apps store](https://itunes.apple.com/us/app/dynamics-365-for-operations/id1180836730?mt=8)

## Sign in to the Dynamics 365 for Operations mobile app
1.  Start the app on your mobile device.
2.  Enter your Dynamics 365 for Operations URL.
3.  Enter the company to sign in to. For example, enter **USMF**.
4.  The first time that you sign in, you’re prompted for the user name and password for your Dynamics 365 for Operations account. Enter your credentials.
5.  After you sign in, you see the available workspaces for your company. Note that if your system administrator later publishes a new workspace, you can pull to refresh the list of mobile workspaces. [![Pull to refresh](./media/pull-to-refresh-list-of-workspaces-183x300.png)](./media/pull-to-refresh-list-of-workspaces.png)

## View the onhand inventory for a product by using the Inventory onhand mobile workspace
1.  On your mobile device, select the **Inventory on-hand** workspace.
2.  Select **Check on-hand for an item**. You see a list of the products that are loaded into your app for offline use. By default, 50 items are loaded, but a developer can change this number. For more information, developers should see [Dynamics 365 for Operations mobile platform](http://ax.help.dynamics.com/en/wiki/mobile-development-handbook/).
3.  If your item isn't in the list, select **Search more** to do an online search in Dynamics 365 for Operations. Search by product number, or switch to a search by product name.
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



