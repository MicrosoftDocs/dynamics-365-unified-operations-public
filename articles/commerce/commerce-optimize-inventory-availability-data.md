---
title: Optimize your inventory data
description: This article describes how to configure batch jobs to optimize channel-side calculation.
author: hhainesms
ms.date: 09/01/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: hhaines
ms.search.validFrom: 2020-02-11
ms.dyn365.ops.version: Release 10.0.10
ms.custom: 
ms.assetid: 
---
# Optimize your inventory data

[!include [banner](../includes/banner.md)]

To ensure the best possible estimate of inventory, it's critical that you use the following Commerce batch jobs and run them frequently:

- **P-job** – The P-job is found on the **Distribution schedules** page and should be run frequently. This job brings e-Commerce orders, asynchronous customer orders that POS created, and cash-and-carry orders that POS created from the channel databases into Commerce Headquarters, so that they can be processed further. Until this data is synced from the channel to Commerce Headquarters, Commerce Headquarters has no information about inventory adjustments to products in the warehouses that result from those transactions.
- **Synchronize orders** – This job processes the raw transactional data in Commerce Headquarters that the P-job provides and converts e-Commerce and asynchronous customer order transactions into sales orders in Commerce Headquarters. Until this job is processed and the sales orders are created, no inventory transactions are created. Therefore, on-hand inventory in Commerce Headquarters won't consider the transactions.
- **Calculate transactional statements in batch** – For cash-and-carry transactions that are created in the store, the trickle feed posting process ensures that inventory that is related to the sales is updated efficiently. To get the most efficient processing of inventory transactions for cash-and-carry orders, make sure that you configure your system to use [trickle feed posting](./trickle-feed.md).
- **Post transactional statements in batch** – This job is also required for trickle feed posting. It follows the **Calculate transactional statements in batch** job. This job systematically posts the calculated statements, so that sales orders for cash-and-carry sales are created in Commerce Headquarters and Commerce Headquarters more accurately reflects your store's inventory.
- **Product availability** – This job creates the snapshot of inventory from Commerce Headquarters.
- **1130 (Product availability)** – This job is found on the **Distribution schedules** page and should be run immediately after the **Product availability** job. This job transports the inventory snapshot data from Commerce Headquarters to the channel databases.

> [!NOTE]
> - It is a best practice to run the **Product availability** and **1130** jobs on an hourly basis, and to schedule P-job, synchronize orders, and trickle feed posting-related jobs with the same or higher frequency.
> - For performance reasons, when channel-side inventory availability calculations are used to make an inventory availability request using the e-Commerce API's or the POS channel-side inventory logic, the calculation uses a cache to determine whether enough time has passed to justify running the calculation logic again. The default cache is set to 60 seconds. For example, you turned on channel-side calculation for your store and viewed the on-hand inventory for a product on the **Inventory lookup** page. If one unit of the product is then sold, the **Inventory lookup** page won't show the reduced inventory until the cache has been cleared. After users post transactions in POS, they should wait 60 seconds before they verify that the on-hand inventory has been reduced.

If your business scenario requires a smaller cache time, contact your product support representative for assistance.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
