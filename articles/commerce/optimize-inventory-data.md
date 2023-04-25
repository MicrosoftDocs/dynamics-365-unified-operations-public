---
title: Optimize inventory data
description: This article describes how to configure batch jobs to optimize channel-side calculation in Microsoft Dynamics 365 Commerce.
author: hhainesms
ms.date: 01/30/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: hhaines
ms.search.validFrom: 2020-02-11

---
# Optimize inventory data

[!include [banner](../includes/banner.md)]

This article describes how to configure batch jobs to optimize channel-side calculation in Microsoft Dynamics 365 Commerce.

To ensure the best possible estimate of inventory, it's critical that you use the following Commerce headquarters batch jobs and run them often:

- **P-job** – This job is found on the **Distribution schedules** page and should be run often. It brings e-commerce orders, asynchronous customer orders that point of sale (POS) created, and cash-and-carry orders that POS created from the channel databases into Commerce headquarters for further processing. Until this data is synced from the channel to Commerce headquarters, Commerce headquarters has no information about inventory adjustments that those transactions cause for products in the warehouses.
- **Synchronize orders** – This job processes the raw transactional data in Commerce headquarters that the P-job provides, and converts e-commerce and asynchronous customer order transactions into sales orders in Commerce headquarters. Until this job is processed and the sales orders are created, no inventory transactions are created. Therefore, on-hand inventory in Commerce headquarters won't consider the transactions.
- **Calculate transactional statements in batch** – For cash-and-carry transactions that are created in the store, the trickle-feed posting process ensures efficient updates of inventory that's related to the sales. To get the most efficient processing of inventory transactions for cash-and-carry orders, make sure that you configure your system to use [trickle-feed posting](./trickle-feed.md).
- **Post transactional statements in batch** – This job is also required for trickle-feed posting and follows the **Calculate transactional statements in batch** job. It systematically posts the calculated statements, so that sales orders for cash-and-carry sales are created in Commerce headquarters to more accurately reflect your store's inventory.
- **Product availability** – This job creates a snapshot of inventory from Commerce headquarters.
- **1130 (Product availability)** – This job is found on the **Distribution schedules** page and should be run immediately after the **Product availability** job. It delivers the inventory snapshot data from Commerce headquarters to the channel databases.

> [!NOTE]
> - As a best practice, the **Product availability** and **1130** jobs should be run hourly. The P-job, the synchronize orders job, and trickle-feed posting–related jobs should be scheduled at the same or a higher frequency.
> - For performance reasons, when channel-side inventory availability calculation is used to request inventory availability by using the e-commerce APIs or the POS channel-side inventory logic, the calculation uses a cache to determine whether enough time has passed to justify running the calculation logic again. The default cache is set to 60 seconds. For example, you turned on channel-side calculation for your store and viewed the on-hand inventory for a product on the **Inventory lookup** page. If one unit of the product is then sold, the **Inventory lookup** page won't show the reduced inventory until the cache has been cleared. After users post transactions in POS, they should wait 60 seconds before they verify that the on-hand inventory has been reduced.

If your business scenario requires a smaller cache time, contact your product support representative for help.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
