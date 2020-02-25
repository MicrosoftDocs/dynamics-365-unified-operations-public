---
# required metadata

title: Calculate inventory availability for retail channels
description: This topic describes the options that are available for showing the on-hand inventory for the store and online channels.
author: hhainesms
manager: annbe
ms.date: 02/25/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: hhainesms
ms.search.validFrom: 2020-02-11
ms.dyn365.ops.version: Release 10.0.10

---
# Calculate inventory availability for retail channels

[!include [banner](../includes/banner.md)]

This topic describes how a company can use Microsoft Dynamics 365 Commerce to view estimated on-hand availability for products in the online and store channels.

## Accuracy of calculation

Commerce uses multiple servers and databases to ensure scalability and performance. Therefore, it's important that you understand that the available inventory values that are provided through the point of sale (POS) application, the e-Commerce inventory availability application programming interfaces (APIs), and the on-hand inventory pages in Commerce Headquarters might not be 100-percent accurate in real time. If transactions that are created for products in the online or store channel haven't yet been synced to the Commerce Headquarters server and database, the on-hand inventory pages in Commerce Headquarters might not show an accurate real-time inventory value for those products. Conversely, if you configured your company so that users in Commerce Headquarters or other integrated applications can sell, receive, return, or otherwise adjust inventory out of a store or online warehouse, the POS or online channel might not have all the information that is required to show an accurate real-time on-hand value for items.

This topic explains the data synchronization processes that can be run frequently to help limit the latency of data between applications or channels. However, it's critical that you understand that all on-hand availability data that is provided during the operational day is considered an estimated value. Therefore, if you try to compare the on-hand inventory information that the application provides with actual physical inventory on the shelves, or if you try to compare the on-hand values that are shown in POS with the on-hand data that you find for the same warehouse in Commerce Headquarters, the values might differ. This difference during the operational day is expected and should not be considered an issue. If you want to audit data and make sure that the values that are provided in the inventory availability APIs and Commerce Headquarters match the actual physical units that you find on your store or warehouse shelves, the best time to do it is after channel operations have stopped for the day and all transactions have been correctly synced between Commerce Headquarters and the channel.

## Use inventory lookup APIs for e-Commerce inventory availability requests

You can use the following APIs to show inventory availability for a product when your customers are shopping on an e-Commerce site.

- **GetEstimatedAvailabilty** – Use this API to get inventory availability for the item in the e-Commerce channel warehouse or all warehouses that are linked to the configuration of the fulfillment group for the e-Commerce channel. This API can also be used for warehouses in a specific search area or radius, based on longitude and latitude data.
- **ProductWarehouseInventoryAvailabilities** – Use this API to request inventory for an item from a specific warehouse. For example, you can use it to show inventory availability in scenarios that involve order pickup.

> [!NOTE]
> These APIs replace the **GetProductAvailabilities** and **GetAvailableInventoryNearby** APIs in Dynamics 365 Retail version 10.0.7 and earlier.

Both APIs fetch data from the Commerce server and provide an estimate of on-hand inventory for a specific combination of a product or product variant and a warehouse. Although other APIs that are available on the Commerce server can go directly to Commerce Headquarters to fetch on-hand quantities for products, we don't recommend that they be used in an e-Commerce environment because of potential performance issues and the related impact that these frequent requests can have on your Commerce Headquarters servers. Additionally, if the on-hand inventory is calculated through the Commerce server, the calculation is more likely to include inventory that was sold in recent e-Commerce transactions that haven't yet been synced to Commerce Headquarters. Although Commerce Headquarters might not have information about these transactions, the Commerce server and channel database have the data. Therefore, the data will be factored in and can help provide a more accurate estimate of a product's available inventory.

### Get started with e-Commerce calculated inventory availability

Before you use the two APIs that were mentioned earlier, you must make a parameter change in Commerce Headquarters to ensure that the snapshot of inventory values that Commerce Headquarters calculates by using the **Product Availability** job enters data in the correct tables.

To set the parameter, follow these steps.

1. Go to **Retail and Commerce \> Headquarters Setup \> Parameters \> Commerce shared parameters**.
1. On the **Inventory** tab, in the **Product availability job** section, select **Use optimized process for Product Availability job**. This setting ensures that the optimal feature set is used to calculate the channel's available inventory through the Commerce server.

Before the APIs can calculate the best estimate of inventory availability for an item, a periodic snapshot of inventory availability from Commerce Headquarters must be processed and sent to the channel database that the e-Commerce Commerce Scale Unit uses. The snapshot represents the information that Commerce Headquarters has about inventory availability for a specific combination of a product or product variant and a warehouse. It can include inventory adjustments or movements that are caused by inventory receipts, or by shipments or other processes that are performed in Commerce Headquarters and that the e-Commerce channel has information about only because of the synchronization process.

The database snapshot that the **Product availability** job creates calculates only the inventory transactions that were processed and posted in Commerce Headquarters at the time when the snapshot was taken. If inventory was sold for a product in a store warehouse through a cash-and-carry or asynchronous customer order sale in the POS application, Commerce Headquarters won't immediately have information about the related inventory issue transaction for the sale. It will have information about the inventory that is sold for these types of store sales only after the P-job uploads the related transaction from the store's channel database into Commerce Headquarters and the related sales order is created through statement posting or the trickle feed posting processes. The process of creating the order in Commerce Headquarters creates the related inventory transactions. For e-Commerce channel orders, Commerce Headquarters has information about the inventory transactions only after the transactions are sent to Commerce Headquarters through the P-job and the order synchronization process is completed. Therefore, it's important that you understand that the inventory snapshot value that is provided in the **Product availability** job might not be 100-percent accurate in real time because of the constant sales processing that occurs across distributed servers.

To take a snapshot of inventory in Commerce Headquarters, follow these steps.

1. Go to **Retail and Commerce \> Retail and Commerce IT \> Products and inventory \> Product availability**.
1. Select **OK** to run the **Product availability** job. You can also schedule this job so that it's run in a batch.

After the **Product availability** job has finished running, the data that was captured must be pushed to the e-Commerce channel databases, so that the latest Commerce Headquarters inventory snapshot can be considered in the calculation of estimated on-hand inventory.

1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
1. Run the **1130** (**Product availability**) job to sync the snapshot data that the **Product availability** job created from Commerce Headquarters to your channel databases.

When inventory availability is requested from the **GetEstimatedAvailabilty** or **ProductWarehouseInventoryAvailabilities** API, a calculation is run to try to get the best possible estimate of inventory for the product. The calculation references any e-Commerce customer orders that are in the channel database but that weren't included in the snapshot data that the 1130 job provided. This logic is performed by tracking the last processed inventory transaction from Commerce Headquarters and comparing it with the transactions in the channel database. It provides a baseline for the channel-side calculation logic, so that the additional inventory movements that occurred for customer order sales transactions in the e-Commerce channel database can be factored into the estimated inventory value that the API provides.

The channel-side calculation logic returns an estimated physically available value and a total available value for the requested product and warehouse. The values can be shown on your e-Commerce site if you want, or they can be used to trigger other business logic on your e-Commerce site. For example, you can show an "out of stock" message instead of the actual on-hand quantity that the API passed.

The calculation logic that the channel-side e-Commerce APIs use for the estimated inventory value can evaluate inventory based only on customer orders that have been created in the channel database but that haven't yet been synced and posted in Commerce Headquarters. If your channel database also contains transactional data for cash-and-carry sales for store-specific warehouses, the cash-and-carry sales aren't factored into the channel-side e-Commerce calculation for those warehouses.

## Configure the inventory lookup operation in the POS channel

In Retail version 10.0.9 and earlier, the **Inventory lookup** operation from POS used a real-time service call to Commerce Headquarters to get inventory information for the selected product, for both the user's current store and any other stores that are configured for the fulfillment group as part of the channel configuration for the store. In Commerce version 10.0.10 and later, you can turn off real-time service calls to Commerce Headquarters. Instead, you can use channel-side calculation on the Commerce server to determine the on-hand inventory that is physically available for the store and any other locations that are defined in the fulfillment group. This channel-calculated inventory configuration is also useful for locations where internet connectivity is unreliable, because you don't have to be online to get inventory lookups from Commerce Headquarters.

When channel-side calculation is correctly configured and managed, it can provide a more reliable estimate of the current store inventory, because it uses the transactional data that is in the Commerce channel database but that Commerce Headquarters might not yet have information about. For example, if you use the existing real-time service call for inventory lookups in POS, Commerce Headquarters probably won't yet have information about a cash-and-carry sale that just occurred for a product. Therefore, the on-hand inventory value that Commerce Headquarters returns for that product will probably exceed the store's actual on-hand inventory by one unit. However, if you use channel-side calculation, the cash-and-carry sale can be factored into the calculation and deducted from the on-hand value that is shown. Although the values that both the channel-side calculation and the real-time service call provide are only estimates of on-hand inventory, the value that the channel-side calculation provides is much more likely to be accurate for the current store.

### Get started with POS channel-side calculated inventory availability

To use the channel-side calculation logic and turn off real-time service calls for inventory lookups from the POS application, you must first make two parameter changes. You must then sync the changes to the channel through the distribution schedule process.

To set the first parameter, follow these steps.

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**.
1. On the **Inventory** tab, in the **Product availability job** section, select **Use optimized process for Product Availability job**. This setting ensures that the optimal feature set is used to calculate the channel's available inventory through the Commerce server.

To set the second parameter, follow these steps.

1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**.
1. Select a functionality profile.
1. On the **Functions** FastTab, in the **Invent availability calculation** section, change the value of the **Invent availability calculation mode** field from **Real time service** to **Channel**. By default, all functionality profiles use real-time service calls. Therefore, you must change the value of this field if you want to use channel-side calculation logic. Every retail store that is linked to the selected functionality profile will be affected by this change.

To update the servers, follow these steps.

1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
1. Run the **1070** (**Channel configuration**) job.

After the configuration is completed, the information that is provided about physically available inventory no longer uses a real-time service call when a user in the POS application uses the **Inventory lookup** operation (standard and matrix views). Instead, data about physically available inventory for the current store and all the stores in the fulfillment group is calculated based on the last-known snapshot that was delivered to the channel database from Commerce Headquarters. The snapshot value is further refined by the channel-side calculation to adjust the physically available value, based on additional sales or return transactions that exist for the selected product in the channel database that were not included in the last synchronized snapshot from the 1130 job. If the channel database doesn't contain transactional data for any of the warehouses or stores in the fulfillment group, it contains no additional transactions that can be factored into a recalculation of the value. Therefore, the best estimate of on-hand inventory that can be shown for those warehouses or stores is the data from the last-known Commerce Headquarters snapshot.

The **Order fulfillment** screens of POS also leverage the channel side calculation to show on-hand inventory for items when an order fulfillment line is selected and a user views the **Details** panel for on-hand inventory for the selected item.

## Optimize your inventory data

To ensure the best possible estimate of inventory, it's critical that you use the following Commerce batch jobs and run them frequently:

- **P-job** – The P-job is found on the **Distribution schedules** page and should be run frequently. This job brings e-Commerce orders, asynchronous customer orders that POS created, and cash-and-carry orders that POS created from the channel databases into Commerce Headquarters, so that they can be processed further. Until this data is synced from the channel to Commerce Headquarters, Commerce Headquarters has no information about inventory adjustments to products in the warehouses that result from those transactions.
- **Synchronize orders** – This job processes the raw transactional data in Commerce Headquarters that the P-job provides and converts e-Commerce and asynchronous customer order transactions into sales orders in Commerce Headquarters. Until this job is processed and the sales orders are created, no inventory transactions are created. Therefore, on-hand inventory in Commerce Headquarters won't consider the transactions.
- **Calculate transactional statements in batch** – For cash-and-carry transactions that are created in the store, the trickle feed posting process ensures that inventory that is related to the sales is updated efficiently. To get the most efficient processing of inventory transactions for cash-and-carry orders, make sure that you configure your system to use [trickle feed posting](https://docs.microsoft.com/dynamics365/commerce/trickle-feed).
- **Post transactional statements in batch** – This job is also required for trickle feed posting. It follows the **Calculate transactional statements in batch** job. This job systematically posts the calculated statements, so that sales orders for cash-and-carry sales are created in Commerce Headquarters and Commerce Headquarters more accurately reflects your store's inventory.
- **Product availability** – This job creates the snapshot of inventory from Commerce Headquarters.
- **1130 (Product availability)** – This job is found on the **Distribution schedules** page and should be run immediately after the **Product availability** job. This job transports the inventory snapshot data from Commerce Headquarters to the channel databases.

> [!NOTE]
> For performance reasons, when channel-side inventory availability calculations are used to make an inventory availability request using the e-Commerce API's or the new POS channel-side inventory logic, the calculation uses a cache to determine whether enough time has passed to justify running the calculation logic again. The default cache is set to 60 seconds. For example, you turned on channel-side calculation for your store and viewed the on-hand inventory for a product on the **Inventory lookup** page. If one unit of the product is then sold, the **Inventory lookup** page won't show the reduced inventory until the cache has been cleared. After users post transactions in POS, they should wait 60 seconds before they verify that the on-hand inventory has been reduced.

If your business scenario requires a smaller cache time, contact your product support representative for help.
