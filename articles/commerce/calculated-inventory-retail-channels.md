---
# required metadata

title: Calculate inventory availability for retail channels
description: This topic describes how a company can use Microsoft Dynamics 365 Commerce to view estimated on-hand availability for products in the online and store channels.
author: hhainesms
ms.date: 09/01/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: hhaines
ms.search.validFrom: 2020-02-11
ms.dyn365.ops.version: Release 10.0.10

---
# Calculate inventory availability for retail channels

[!include [banner](../includes/banner.md)]

This topic describes how a company can use Microsoft Dynamics 365 Commerce to view estimated on-hand availability for products in the online and store channels.

## Accuracy of inventory availability

Commerce uses multiple servers and databases to ensure scalability and performance. Therefore, it's important that you understand that the available inventory values that are provided through the point of sale (POS) application, the e-commerce inventory availability application programming interfaces (APIs), and the on-hand inventory pages in Commerce headquarters might not be 100 percent accurate in real time. If transactions that are created for products in the online or store channel haven't yet been synced to headquarters, the on-hand inventory pages in headquarters might not show an accurate real-time inventory value for those products. Conversely, if you configured your company so that users in headquarters or other integrated applications can sell, receive, return, or otherwise adjust inventory out of a store or online warehouse, the POS or online channel might not have all the information that is required to show accurate real-time values for items.

It's critical to understand that all on-hand availability data that is provided during the operational day is considered an estimated value. Therefore, if you try to compare the on-hand inventory information that the application provides with actual physical inventory on the shelves, or if you try to compare the on-hand values that are shown in POS with the on-hand data that you find for the same warehouse in headquarters, the values might differ. This difference during the operational day is expected and should not be considered an issue. If you want to audit data and make sure that the values provided in POS, APIs, and headquarters match the actual physical units that you find on your store or warehouse shelves, the best time to do it is after channel operations have stopped for the day and all transactions have been correctly synced between headquarters and the channels.

## Channel-side inventory calculation

The channel-side inventory calculation is a mechanism that takes the last-known channel inventory data in Commerce headquarters as a baseline, and then factors in additional inventory changes that occurred on the channel side that aren't included in that baseline to calculate a near-real-time estimated on-hand inventory. 

The following inventory changes are currently considered in the channel-side inventory calculation logic:

- Inventory sold through cash-and-carry orders in store
- Inventory sold through customer orders in store or online channel
- Inventory returned to store
- Inventory fulfilled (pick, pack, ship) from store warehouse

To use the channel-side inventory calculation, you must enable the **Optimized product availability calculation** feature.

If your Commerce environment is in release **10.0.8 through 10.0.11**, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce** \> **Commerce shared parameters**.
1. On the **Inventory** tab, in the **Product availability job** field, select **Use optimized process for product availability job**.

If your Commerce environment is in release **10.0.12 or later**, follow these steps.

1. In Commerce headquarters, go to **Workspaces \> Feature management**, and enable the **Optimized product availability calculation** feature.
1. If your online and store channels use the same fulfillment warehouses, you must also enable the **Enhanced e-Commerce channel-side inventory calculation logic** feature. In that way, the channel-side calculation logic will consider the unposted transactions that are created in the store channel. (Those transactions can be cash-and-carry transactions, customer orders, and returns.)
1. Run the **1070** (**Channel configuration**) job.

If your Commerce environment was upgraded from a release that is earlier than Commerce version 10.0.8, after you enable the **Optimized product availability calculation** feature, you must also run **Initialize commerce scheduler** for the feature to take effect. To run the initialization, go to **Retail and Commerce** \> **Headquarters setup** \> **Commerce scheduler**.

To use the channel-side inventory calculation, as a prerequisite a periodic snapshot of inventory data from headquarters created by the **Product availability** job must be sent to the channel databases. The snapshot represents the information that headquarters has about inventory availability for a specific combination of a product or product variant and a warehouse. It includes only the inventory transactions that were processed and posted in headquarters at the time when the snapshot was taken, and it might not be 100 percent accurate in real time because of the constant sales processing that occurs across distributed servers.

- If inventory was sold for a product in a store through a cash-and-carry or asynchronous customer order sale in the POS application, headquarters won't immediately have information about the related inventory issue transaction for the sale. Headquarters will have information about the inventory that is sold for these types of store sales only after the P-job uploads the related transaction from the store's channel database into headquarters and the related sales orders are created through statement posting or the trickle feed posting processes. The process of creating the orders in headquarters creates the related inventory transactions. 
- For e-commerce channel orders, headquarters has information about the inventory transactions only after the transactions are sent to headquarters through the P-job and the order synchronization process is completed.

To take a snapshot of inventory in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Retail and Commerce IT \> Products and inventory \> Product availability**.
1. Select **OK** to run the **Product availability** job. You can also schedule this job to run in batch.

After the **Product availability** job has finished running, the data that was captured must be pushed to the channel databases, so that the latest headquarters inventory snapshot can be considered in the channel-side calculation of estimated on-hand inventory.

To sync snapshot data from headquarters to your channel databases, follow these steps.

1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
1. Run the **1130** (**Product availability**) job to sync the snapshot data that the **Product availability** job has created from headquarters to your channel databases.

## Inventory availability APIs for e-commerce

Commerce provides the following APIs for e-commerce scenarios to query inventory availability of a product:

- **GetEstimatedAvailability** – Use this API to query inventory for a product or product variant in the online channel warehouse or warehouses that are linked to the online channel's fulfillment group.
- **GetEstimatedProductWarehouseAvailability** – Use this API to query inventory for a product or product variant from a specific warehouse.

> [!NOTE]
> These APIs replace the **GetProductAvailabilities** and **GetAvailableInventoryNearby** APIs in Commerce release 10.0.7 and earlier.

Both APIs internally use the channel-side calculation logic and return estimated **physical available** quantity, **total available** quantity, **unit of measure (UoM)**, and **inventory level** for the requested product and warehouse. The returned values can be shown on your e-commerce site if you want, or they can be used to trigger other business logic on your e-commerce site. For example, you can prevent the purchase of products with an "out of stock" inventory level.

Although other APIs that are available in Commerce can go directly to headquarters to fetch on-hand quantities for products, we don't recommend that they be used in an e-commerce environment because of potential performance issues and the impact that these frequent requests can have on your headquarters servers. Additionally, with channel-side calculation, the two APIs mentioned above can provide a more accurate estimate of a product's availability by taking into account the transactions created in the channels that aren't yet known to headquarters.

To define how product quantity should be returned in the API output, follow these steps.

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**.
1. Select the **Inventory** tab, and then on the **Inventory availability APIs for e-Commerce** FastTab configure the value of the **Quantity in API output** setting.
1. Run the **1070** (**Channel configuration**) job to sync the latest setting to channels.

The **Quantity in API output** setting provides three options:

- **Return inventory quantity** – Physical available and total available quantity of a requested product are returned in API output.
- **Return inventory quantity subtracting inventory buffer** – The quantity returned in the API output is adjusted by subtracting the inventory buffer value. For more information about the inventory buffer, see [Configure inventory buffers and inventory levels](inventory-buffers-levels.md).
- **Not return inventory quantity** – Only the inventory level is returned in the API output. For more information about inventory levels, see [Configure inventory buffers and inventory levels](inventory-buffers-levels.md).

You can use the `QuantityUnitTypeValue` API parameter to specify the unit type in which you would like the APIs to return quantity. This parameter supports the **inventory unit** (default), **purchase unit**, and **sell unit** options. The returned quantity is rounded to the defined precision of the corresponding unit of measure (UOM) in headquarters.

The **GetEstimatedAvailability** API offers the following input parameters to support different query scenarios:

- `DefaultWarehouseOnly` – Use this parameter to query inventory for a product in the online channel's default warehouse. 
- `FilterByChannelFulfillmentGroup` and `SearchArea` – Use these two parameters to query inventory for a product from all pickup locations within a specific search area, based on `longitude`, `latitude`, and `radius`. 
- `FilterByChannelFulfillmentGroup` and `DeliveryModeTypeFilterValue` – Use these two parameters to query inventory for a product from specific warehouses that are linked to an online channel's fulfillment group and are configured to support certain modes of delivery. The `DeliveryModeTypeFilterValue` parameter supports the **all** (default), **shipping**, and **pickup** options. For example, in a scenario where an online order can be fulfilled from multiple shipping warehouses, you can use these two parameters to query a product's inventory availability in all of those shipping warehouses. The API in this case returns the product's on-hand quantity and inventory level in each of the shipping warehouses, plus an aggregated quantity and an aggregated inventory level from all shipping warehouses in the query scope.
 
The Commerce buy box, store selector, wishlist, cart, and cart icon modules consume the APIs and parameters mentioned above to display inventory level messages across the e-commerce site. Commerce site builder provides various inventory settings to control merchandising and purchase behavior. For more information, see [Apply inventory settings](inventory-settings.md).

## POS inventory lookup with channel-side calculation

In the Commerce release 10.0.9 and earlier, the **Inventory lookup** operation in POS used a real-time service call to headquarters to get inventory information for the selected product for both the user's current store and any other stores that are configured for the fulfillment group as part of the channel configuration for the store. In Commerce release 10.0.10 and later, you can turn off real-time service calls to headquarters and instead use channel-side calculation on the Commerce server to determine the on-hand inventory that is physically available for the store and any other locations that are defined in the fulfillment group. This channel-calculated inventory configuration is also useful for locations where internet connectivity is unreliable, because you don't have to be online to get inventory lookups headquarters.

When channel-side calculation is correctly configured and managed, it can provide a more reliable estimate of the current store inventory because it uses the transactional data that is in the Commerce channel database but that headquarters might not yet have information about. For example, if you use the existing real-time service call for inventory lookups in POS, headquarters probably won't yet have information about a cash-and-carry sale that just occurred for a product. Therefore, the on-hand inventory value that headquarters returns for that product will probably exceed the store's actual on-hand inventory by one unit. However, if you use channel-side calculation, the cash-and-carry sale can be factored into the calculation and deducted from the on-hand value that is shown. Although the values that both the channel-side calculation and the real-time service call provide are only estimates of on-hand inventory, the value that the channel-side calculation provides is much more likely to be accurate for the current store.

To configure the POS **Inventory lookup** operation in Commerce headquarters to use the channel-side calculation logic and turn off real-time service call, you must first enable the **Optimized product availability calculation** feature through the **Feature management** workspace in Commerce headquarters, and then follow these steps.

1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**.
1. Select a functionality profile.
1. On the **Functions** FastTab, in the **Inventory availability calculation** section, change the value of **Inventory availability calculation mode** from **Real time service** to **Channel**. By default, all functionality profiles use real-time service calls. You must change the value of this field if you want to use channel-side calculation logic. Every retail store that is linked to the selected functionality profile will be affected by this change.

You must then sync the changes to the channels through the distribution schedule process in headquarters by following these steps.

1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
1. Run the **1070** (**Channel configuration**) job.

After the configuration is completed, the information that is provided about physically available inventory no longer uses a real-time service call when a user in the POS application uses the **Inventory lookup** operation (standard and matrix views). Instead, data about physically available inventory for the current store and all the stores in the fulfillment group is calculated based on the last-known snapshot that was delivered to the channel database from Commerce Headquarters. The snapshot value is further refined by the channel-side calculation to adjust the physically available value, based on additional sales or return transactions that exist for the selected product in the channel database that were not included in the last synchronized snapshot from the 1130 job. If the channel database doesn't contain transactional data for any of the warehouses or stores in the fulfillment group, it contains no additional transactions that can be factored into a recalculation of the value. Therefore, the best estimate of on-hand inventory that can be shown for those warehouses or stores is the data from the last-known Commerce Headquarters snapshot.

The **Order fulfillment** screens of POS also leverage the channel side calculation to show on-hand inventory for items when an order fulfillment line is selected and a user views the **Details** panel for on-hand inventory for the selected item.

## Optimize your inventory data

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
