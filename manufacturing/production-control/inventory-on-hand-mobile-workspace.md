---
# required metadata

title: Inventory on-hand mobile workspace for Microsoft Dynamics 365 for Operations app
description: The Inventory on-hand mobile workspace helps you gain mobile insights into reserved and available inventory anytime and anywhere. 
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
# ms.reviewer: 121
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 267094
ms.assetid: 85058f55-e566-40e2-9234-42d3e4fe5ff6
ms.search.region: global
ms.search.industry: Manufacturing
ms.author: mirzaab
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Inventory on-hand mobile workspace for Microsoft Dynamics 365 for Operations app

The Inventory on-hand mobile workspace helps you gain mobile insights into reserved and available inventory anytime and anywhere. 

Prerequisites
-------------

| Prerequisite                                                         | Description                                                                                                                                        |
|----------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| Read about the Microsoft Dynamics 365 for Operations mobile platform | [Dynamics 365 for Operations mobile platform](/dev-itpro/mobile-apps/mobile-platform)                                   |
| Dynamics 365 for Operations                                          | An environment that has Microsoft Dynamics 365 for Operations version 1611 and Microsoft Dynamics for Operations platform update 3 (November 2016) |
| Hotfix KB 3215650                                                    | Install the hotfix to enable the workspaces that are provided in your Microsoft Dynamics 365 for Operations.                                       |
| Mobile device that has the Dynamics 365 for Operations app installed | Download the Dynamics 365 for Operations app from your mobile app store.                                                                           |

## Introduction
Typically, companies have multiple shipments and multiple receipts of inventory every day. These movements constantly change the on-hand inventory status. The Inventory on-hand mobile workspace lets you see the cross-company on-hand inventory status, so that you can gain the latest insights into inventory data on the mobile device of your choice. Regardless of whether you work in the warehouse, purchasing, sales, manufacturing, or management, or have other roles, you can access the on-hand inventory data anytime and anywhere. The mobile workspace provides an instant view of the on-hand status across facilities, and lets you view on-hand inventory across facilities, current material reservations, and unreserved on-hand inventory. You can also enter item numbers to query on-hand inventory, and perform a filtered search for on-hand products or variants. Specifically, the mobile workspace provides these features:

-   You can search by product number or product name to find products to view the on-hand inventory status for.
-   For the selected products, you can view the following information:
    -   On-hand inventory per site
    -   On-hand inventory per warehouse
    -   On-hand inventory per location
    -   On-hand inventory per batch (for batch-controlled products)
    -   On-hand inventory per inventory status

<!-- -->

-   Product on-hand inventory is shown in the following ways:
    -   By physical inventory (This view represents the total amount.)
    -   By physical reserved (This view represents the reserved amount.)
    -   By available physical (This view represents available amount that has no reservations.)

## Get started
To get started on your mobile device:

1.  From your mobile app store, download and install the Microsoft Dynamics 365 for operations app.
2.  Start the app on your device.
3.  Enter your Dynamics 365 URL.
4.  Enter the company to sign in to. For example, enter **USMF**.
5.  The first time that you sign in, you're prompted for the user name and password for your Microsoft Dynamics 365 for Operations account. Enter your credentials. After you sign in, you see the available workspaces for your company.

To view workspaces on your mobile app, you must first publish the desired workspaces to the Dynamics 365 for Operations app.

1.  Start Dynamics 365 for Operations.
2.  Go to **System administration** &gt; **Setup** &gt; **system parameters**.
3.  Select **Manage mobile app**.
4.  Select the workspace to publish to the mobile platform.
5.  Select **Publish workspace**.
6.  Refresh your device to see the published workspaces.

## View the onhand inventory for a product
1.  On your mobile device, select the **Inventory on-hand** workspace.
2.  Select **Check on-hand for an item**. You see a list of the products that are loaded into your app for offline use. By default, 50 items are loaded, but you can change this number. For more information, see the pre-read handbook.
3.  If your item isn't in the list, select **Search more** to do an online search in Dynamics 365 for Operations. Search by product number, or switch to a search by product name.
4.  Select a product. If the item has an image, the image is shown.
5.  Select one of the following options to view the on-hand inventory status:
    -   View on-hand per site
    -   View on-hand per warehouse
    -   View on-hand per location
    -   View on-hand per batch (for batch-controlled products)
    -   View on-hand per inventory status

    Product on-hand inventory is shown in the following ways:
    -   By physical inventory (This view represents the total amount.)
    -   By physical reserved (This view represents the reserved amount.)
    -   By available physical (This view represents the available amount that has no reservations.)



