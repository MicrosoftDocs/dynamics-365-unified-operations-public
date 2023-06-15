---
title: Calculate inventory availability for retail channels
description: This article describes how a company can use Microsoft Dynamics 365 Commerce to view estimated on-hand availability for products in the online and store channels.
author: hhainesms
ms.date: 01/30/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: hhaines
ms.search.validFrom: 2020-02-11

---
# Calculate inventory availability for retail channels

[!include [banner](../includes/banner.md)]

This article describes how a company can use Microsoft Dynamics 365 Commerce to view estimated on-hand availability for products in the online and store channels.

## Accuracy of inventory availability

Commerce uses multiple servers and databases to ensure scalability and performance. It's important to understand that the available inventory values provided through the point of sale (POS) application, the e-commerce inventory availability application programming interfaces (APIs), and the on-hand inventory pages in Commerce headquarters might not be 100 percent accurate in real time. If transactions that are created for products in the online or store channel haven't yet been synced to headquarters, the on-hand inventory pages in headquarters might not show an accurate real-time inventory value for those products. Conversely, if you configured your company so that users in headquarters or other integrated applications can sell, receive, return, or otherwise adjust inventory out of a store or online warehouse, the POS or online channel might not have all the information that is required to show accurate real-time values for items.

It's critical to understand that all on-hand availability data that is provided during the operational day is considered an estimated value. Therefore, if you try to compare the on-hand inventory information that the application provides with actual physical inventory on the shelves, or if you try to compare the on-hand values shown in POS with the on-hand data that you find for the same warehouse in headquarters, the values might differ. This difference during the operational day is expected and shouldn't be considered an issue. If you want to audit data and make sure that the values provided in POS, APIs, and headquarters match the actual physical units that you find on your store or warehouse shelves, the best time to do it is after channel operations have stopped for the day and all transactions have been correctly synced between headquarters and the channels.

## Channel-side inventory calculation

The channel-side inventory calculation is a mechanism that takes the last-known channel inventory data in Commerce headquarters as a baseline, and then factors in additional inventory changes that occurred on the channel side that aren't included in that baseline to calculate a near-real-time estimated on-hand inventory. 

The following inventory changes are currently considered in the channel-side inventory calculation logic:

- Inventory sold through cash-and-carry orders in store
- Inventory sold through customer orders in store or online channel
- Inventory returned to store
- Inventory fulfilled (pick, pack, ship) from store warehouse

[!INCLUDE[footer-include](../includes/footer-banner.md)]
