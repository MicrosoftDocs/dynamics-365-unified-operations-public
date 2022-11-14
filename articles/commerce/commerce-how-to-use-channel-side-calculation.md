---
title: How to use channel-side inventory calculation
description: This article describes how  to configure channel-side calculation in Microsoft Dynamics 365 Commerce.
author: hhainesms
ms.date: 11/14/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: hhaines
ms.search.validFrom: 2020-02-11

---
# How to use channel-side inventory calculation

[!include [banner](../includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This article describes how  to configure channel-side calculation in Microsoft Dynamics 365 Commerce.

## Enable the feature

To use the channel-side inventory calculation, you must first enable the **Optimized product availability calculation** feature.

### For Commerce version 10.0.29 and later

The **Optimized product availability calculation** feature is marked as mandatory (in other words, enabled by default and not allowed to be disabled) in Commerce version 10.0.29 and later. No action is needed to enable the feature.

### For Commerce versions 10.0.12 through 10.0.28

If you are using Commerce versions 10.0.12 through 10.0.28, follow these steps to enable the **Optimized product availability calculation** feature.

1. In Commerce headquarters, go to **Workspaces \> Feature management**.
1. Find and enable the **Optimized product availability calculation** feature.
1. If your online and store channels use the same fulfillment warehouses, you must also enable the **Enhanced e-Commerce channel-side inventory calculation logic** feature. The channel-side calculation logic will then consider unposted transactions that are created in the store channel. Unposted transactions can be cash-and-carry transactions, customer orders, and returns.
1. Run the **1070** (**Channel configuration**) job.

If your Commerce environment was upgraded from a release that is earlier than Commerce version 10.0.8, after you enable the **Optimized product availability calculation** feature, for the feature to take effect you must also run the **Initialize commerce scheduler** at **Retail and Commerce \> Headquarters setup \> **Commerce scheduler**.

### For Commerce versions 10.0.8 through 10.0.11

If you are using Commerce versions 10.0.8 through 10.0.11, follow these steps to enable the **Optimized product availability calculation** feature.

1. In headquarters, go to **Retail and Commerce \> Commerce shared parameters**.
1. On the **Inventory** tab, for **Product availability job**, select **Use optimized process for product availability job**.

## Configure the Product availability job

To use channel-side inventory calculation, as a prerequisite a periodic snapshot of inventory data from headquarters created by the **Product availability** job must be sent to the channel databases. The snapshot represents the information that headquarters has about inventory availability for a specific combination of a product or product variant and a warehouse. The snapshot only includes the inventory transactions that were processed and posted in headquarters at the time when the snapshot was taken, and may not be 100 percent accurate in real time because of the constant sales processing that occurs across distributed servers.

- If inventory was sold for a product in a store through a cash-and-carry or asynchronous customer order sale in the POS application, headquarters won't immediately have information about the related inventory issue transaction for the sale. Headquarters will have information about the inventory that is sold for these types of store sales only after the **P-job** uploads the related transaction from the store's channel database into headquarters and the related sales orders are created through statement posting or the trickle feed posting processes. The process of creating the orders in headquarters creates the related inventory transactions.
- For e-commerce channel orders, headquarters has information about the inventory transactions only after the transactions are sent to headquarters via the **P-job** and the order synchronization process is completed.

To take a snapshot of inventory in headquarters, follow these steps.

1. Go to **Retail and Commerce \> Retail and Commerce IT \> Products and inventory \> Product availability**.
1. Select **OK** to run the **Product availability** job. You can also schedule this job to run in batch.

## Configure the Distribution schedule job

After the **Product availability** job has finished running, the data that was captured must be pushed to the channel databases so the latest headquarters inventory snapshot can be considered in the channel-side calculation of estimated on-hand inventory.

To sync snapshot data from headquarters to your channel databases, follow these steps.

1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
1. Run the **1130** (**Product availability**) job to sync the snapshot data that the **Product availability** job has created from headquarters to your channel databases.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
