---
# required metadata

title: Calculate inventory availability for retail channels
description: This topic describes the options available for displaying the on-hand inventory for the store and online channels.
author: hhainesms
manager: annbe
ms.date: 02/11/2020
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

This topic describes the ways in which a company can use Commerce to view estimated on-hand availability for products in the online and store channels.

> [!NOTE]
> Commerce uses multiple servers and databases to ensure scalability and performance, so it is important to understand that the available inventory values that are provided through the point of sale (POS) application, the e-Commerce inventory availability APIs, and the on-hand inventory pages in Commerce Headquarters (HQ) may not be 100% real-time accurate. If transactions for products created in the online or store channel have not yet synced to the HQ server and database, the on-hand inventory pages in HQ will not necessarily show an accurate real-time inventory value for those products. Conversely, if you configured your company to allow users in HQ or other integrated applications to sell, receive, return or otherwise adjust inventory out of a store or online warehouse, the POS or online channel may not have all of the information necessary to show an accurate real-time on-hand value for items. This topic explains the data synchronization processes that can be run frequently to help limit the latency of data between applications or channels, but it is critical to understand that during the operational day, all on-hand availability data provided is considered an estimated value. Any  attempt to compare the on-hand inventory information provided by the application with actual physical inventory on the shelves, or to compare the on-hand values shown in POS to the on-hand data found in HQ for the same warehouse, may result in a disparity in values. This disparity during the operational day is expected and should not be interpreted as an issue. The best time to audit data and ensure that the values provided in the inventory on-hand APIs and in HQ are in-sync with the actual physical units you find on your store or warehouse shelves is after channel operations stop for the day and all transactions have been properly synchronized between HQ and the channel.

## Use inventory lookup APIs for e-Commerce inventory availability requests

You can use the following APIs to display inventory availability for a product when your customers are shopping on an e-Commerce site.

- **GetEstimatedAvailabilty**: use this API to get inventory availability for the item within the e-Commerce channel warehouse or all warehouses linked to the e-Commerce channel fulfillment group configuration. It can also be used for warehouses within a certain search area or radius based on longitude and latitude data.

- **ProductWarehouseInventoryAvailabilities**: use this API to request inventory for an item from a specific warehouse. For example, use it to display inventory in order pickup availability scenarios.

>[!NOTE]
> These APIs replace the **GetProductAvailabilities** and **GetAvailableInventoryNearby** APIs in Retail versions 10.0.7 and earlier.

The APIs listed above fetch data from the Commerce server and provide an estimation of on-hand inventory for a particular product or product variant and warehouse combination. While there are other APIs available on the Commerce server that can go directly to HQ to fetch on-hand quantities for products, they are not recommended in an e-Commerce environment because of potential performance issues and the related impact these frequent requests may have on your HQ servers. Additionally, by calculating the on-hand inventory through the Commerce server, there is a better chance of the calculation including inventory sold in recent e-Commerce transactions that have not yet been synchronized to HQ. HQ may not know about these transactions, but the Commerce server/channel database has this data and it will be factored in to provide a potentially more accurate estimation of an product's available inventory.

### Get started with e-Commerce calculated inventory availability

Before using the APIs above, you must make parameter changes in HQ to ensure that the inventory value snapshot calculated by HQ using the **Product Availability** job is populating the correct tables.

To change the parameter:
1. Go to **Retail and commerce \> Headquarters Setup\> Parameters \> Commerce shared parameters**,
1. Click the **Inventory** tab.
1. In the **Product availability job** section, select **Use optimized process for Product Availability job**. This setting ensures that the most optimal feature set for calculating the channel available inventory through the Commerce server is deployed.

In order for the API to calculate the best estimate of inventory availability for an item, a periodic snapshot of inventory availability from HQ must be processed and sent to the channel database that is used by the e-Commerce Commerce Scale Unit. The snapshot represents what HQ knows about inventory availability for a particular product or product variant and warehouse combination. The snapshot may include inventory adjustments or movements resulting from inventory receipts, or shipments or other processes performed in HQ that the e-Commerce channel would otherwise not be aware of without the synchronization process.

The HQ database snapshot created by the **Product availability** job only calculates the inventory transactions that were processed and posted in HQ at the time the snapshot is taken. If inventory was sold for a product within a store warehouse through a cash and carry or async customer order sale in the POS application, HQ will not immediately know about the related inventory issue transaction for this sale. HQ will not be aware of inventory sold for these types of store sales until the P-job uploads the related transaction from the store’s channel database into HQ and the related sales order is created through statement posting or the trickle feed posting processes. The process of creating the order in HQ is what creates the related inventory transactions. For e-Commerce channel orders, the inventory transaction is only known to HQ after the transactions are sent to HQ through the P-job and the synchronize orders process is finished. It is important, therefore, to understand that the inventory snapshot value provided in the **Product availability** job is never guaranteed to be 100% real-time accurate due to the constant sales processing that occurs across distributed servers.

To take the snapshot of inventory in HQ:
1. Go to **Retail and commerce \> Retail and Commerce IT \> Products and inventory \> Product availability**.
1. Run the **Product availability** job. This job can also be scheduled to run in batch.   

Once the **Product availability** job is finished, the captured data must then be pushed to the e-Commerce channel databases so that the latest HQ inventory snapshot is available to influence the estimated on-hand inventory calculation.

1. Go to **Retail and commerce \> Retail and Commerce IT \> Distribution schedule**.
1. Run the **1130 Product availability** job to synchronize this snapshot data created by the **Product availability** batch job from HQ to your channel databases.

When requesting inventory availability from the **GetEstimatedAvailabilty** or **ProductWarehouseInventoryAvailabilities** APIs, a calculation is executed to attempt to get the best possible estimation of inventory for the product. The calculation references any e-Commerce customer orders that are in the channel database that were not included in the **Product availability** snapshot data provided by the **1130** distribution job. This logic is accomplished by tracking the last processed inventory transaction from HQ and comparing it with the transactions in the channel database. It provides the waterline that allows the channel-side calculation logic to factor in additional inventory movements that occurred for customer order sales transactions in the e-Commerce channel database and factor them in to the estimated inventory value that the API provides.  

The channel-side calculation logic returns an estimated physical available and total available value for the requested product and warehouse. The value can be displayed on your e-Commerce site as desired, or can be used to trigger other business logic on your e-Commerce site. For exmple, you can display an “out of stock” message instead of displaying the actual on-hand quantity passed by the API.

The estimated inventory calculation logic used by the channel side e-Commerce API is only able to evaluate inventory based on customer orders created in the channel database but not yet synchronized and posted in HQ. If your channel database also contains cash and carry transactional sales data for store specific warehouses, the cash and carry sales are not factored into the e-Commerce channel-side calculation for that store warehouse.

## Configure the inventory lookup operation in the POS channel

Prior to version 10.0.10, whenever using the **Inventory lookup** operation from the POS, the application would leverage a real-time service call to HQ to get inventory information for the selected product for the user's current store as well as any other store's configured for the user store's fulfillment group as part of that store's channel configuration.   This capability is still in place, but beginning in version 10.0.10, companies will now have the option of disabling this real-time service call to HQ and instead using a "channel-side calculation" on the Commerce server to determine the physical available on-hand inventory for the user's store and any other locations defined in that store's fulfillment group. This “channel” calculated inventory configuration is also beneficial for locations where internet connectivity is spotty and there is a desire to limit the need to be online to get inventory lookups from HQ.

When properly configured and managed, the channel-side calculation has the ability to provide a more reliable estimation of the user's current store inventory because it will leverage the transactional data that is in the Commerce channel database that HQ may not know about yet.  For example, if using the existing real-time service call for inventory lookup in POS, a cash and carry sale that just occurred for an product will probably not be known by HQ yet and therefore the on-hand inventory value returned by HQ for that product will most likely be 1 unit higher than what the store actually has on-hand.  By using the channel-side calculation, this cash and carry sale can be factored into the calculation and deducted from the on-hand value displayed.  While both the channel-side or the real-time service methods are still considered an estimation of on-hand inventory, the channel-side calculation has a much better chance of accuracy (at least for the user's current store).

### Getting started with POS channel-side calculated inventory availability

If a company wants to use the channel-side calculation logic and disable the use of the real-time service call for inventory lookups from the POS application, the user must first make two configuration changes.  These changes must then be synchronized to the channel through the **Distribution schedule** process.

* Navigate to **Retail and Commerce \> Headquarters Setup\> Parameters \>Commerce shared parameters** form on the **Inventory** tab.
In the **Product availability job** parameters, set the parameter to **Use optimized process for Product Availability job**.  This setting is necessary to ensure that the most optimal feature set for calculating the channel available inventory through the retail server is deployed.

 * Navigate to **Retail and Commerce \> Channel Setup \> POS Setup \> POS profiles \> Functionality profiles** and select a functionality profile.  From the **Functions** fasttab, configure the **Inventory availability calculation mode** setting from **Real time service** to **Channel**.  By default, all functionality profiles will be set to **Real time service** and must be changed purposefully by the company if channel-side calculation logic is desired.  Any retail store that is linked to this functionality profile will be affected by this change.  
 
 Once these settings have been changed, the company must run the **1070 Channel configuration** job from the **Distribution schedules** form to ensure the changes are updated to the Commerce servers.  
 
 Upon completion of the channel-side configuration, when a user in the POS application uses the **Inventory lookup** operation from POS, the information provided about physical available inventory on this form will no longer utilize a real-time service call.  The physical available inventory data for the user’s current store as well as for all other store’s in the fulfillment group will be calculated based on the last known snapshot delivered to the channel database from HQ.   This snapshot value from HQ is further refined by the channel-side calculation to adjust the physical available value based on additional sales or returns transactions for the selected product that exist in the channel database and have been determined to have not have been included in the last synchronized HQ snapshot from the 1130 job.   Please note that if the channel database does not house transactional data for any of the warehouses/stores in the fulfillment group, then the best estimation of on hand inventory that can be displayed for those warehouses will be the last known snapshot data from HQ as no additional transactions exist in that channel database that can be factored into re-calculate that value.

## Optimizing your inventory data

To ensure the best inventory estimation value possible, it is imperative that the company leverage these Commerce batch jobs and run them frequently

* **P-job**. The P-job found in the **Distribution schedule** should be run frequently.  This job takes e-commerce orders, async customer orders created by POS and cash and carry orders created by POS and brings the transactions from the channel databases into HQ so that they can be further processed.  Until this transaction data is synchronized from the channel to HQ, HQ has no way of knowing about inventory adjustments to products in the warehouses related to these transactions.
* **Synchronize orders**.  This job processes the raw transaction data in HQ that was provided by the P-job and converts e-commerce and async customer order transactions into sales orders in HQ.   Until this job is processed and the orders are created, there are no inventory transactions created and therefore on-hand inventory in HQ will not be considering these transactions until they turn into sales orders.
* **Calculate transactional statements in batch** - for cash and carry transactions created in store, running the trickle feed posting process will ensure that inventory related to these cash and carry sales is updated efficiently.  Ensure you have enabled your system to use [trickle feed posting](https://docs.microsoft.com/dynamics365/commerce/trickle-feed) to get the most efficient processing of inventory transactions for your cash and carry orders.
** Post transactional statements in batch** - this job is also required for trickle feed posting and follows the previously mentioned  transactional calculation job. This job will post the calculated statements systematically which will then result in sales orders being created in HQ for the cash and carry sales and a more accurate depiction of your store's inventory in HQ.
**Product availability** - this job creates the "snapshot" of inventory from HQ.
**1130 Product availability** - this job found in the **Distribution schedule** form should be run immediately after the **Product availability** job.  This is the job that transports the snapshot inventory data from HQ to the channel databases.

## Additional feature note

It is important to note that when inventory availability is calculated channel-side, this calculation looks at a cache to determine if enough time has passed to justify running the calculation logic again when an inventory availability request is made.  This cache is used to optimize performance.  Currently the default cache is set to 60 seconds.   This means that if you have enabled channel side calculation for your store and you look at the on-hand inventory for a product using the "Inventory lookup** operation and note the value, then you take a sales transaction and sell 1 unit of that product, if you then immediately return to the **Inventory lookup** form to confirm inventory has reduced by 1 - you will not see the reduction of inventory on this form until the cache has cleared.  Therefore users should wait 60 seconds after posting a transaction in POS to check and validate that the inventory has been reduced from on-hand when using the **Channel** configuration for inventory availability as configured in the channels functionality profile.

If your business scenario requires a lower cache time, please contact your product support representative for assistance. 
