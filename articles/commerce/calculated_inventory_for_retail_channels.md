---
# required metadata

title: Calculating inventory availability for retail channels
description: This topic describes the options available for displaying the on-hand inventory for the store and online channels
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
# Calculating inventory availability for retail channels

This document will outline the ways in which a company can leverage capabilities of the Commerce application to view estimated on-hand availability for products in the online and store channels.

> [!NOTE]
> Due to the architecture of the Commerce solution, which uses multiple servers and databases to ensure scalability and performance, it is important to understand that the available inventory values that are provided through the POS application, the e-Commerce inventory availability API's and/or the on-hand inventory screens of HQ may not be 100% real-time accurate. If transactions for products created in the online or store channel have not yet synced to the Headquarters (HQ) server and database, the **On-hand inventory** screens in HQ will not necessarily show an accurate real-time inventory value for those products.  Conversely, if you have configured your company to allow users in the HQ client or through other integrated applications to sell, receive, return or otherwise adjust inventory out of a store or online warehouse, this can result in the POS or online channel not having all of the information necessary in real-time to be able to show a real-time accurate on-hand value for items.  This document will explain the availabledata synchronization processes that can be run frequently to help limit the latency of data between applications or channels, but it is critical for users to understand that during the operational day, all on-hand availability data that is provided is considered an estimated value.  Any user attempt to compare the on-hand inventory information provided by the application with actual physical inventory on the shelves or to compare the on-hand values shown in POS to the on-hand data found in HQ for the same warehouse may result in a disparity in values. This disparity during the operational day is expected and should not be interpreted by the user as an issue.   Once channel operations have ceased for the day and all transactions have been properly synchronized between HQ and channel, this would be the best time to audit the data and ensure that the values provided in the inventory on-hand API's and forms of our applications are in-sync with the actual physical units you find on your store/warehouse shelves.

## Using the new Inventory lookup API for e-commerce inventory availability request and understanding the channel-side calculation logic

If there is a need to display inventory availability for a product to your customers when they are shopping through an e-commerce site, it is possible to leverage these API’s:

**GetEstimatedAvailabilty** -use this API to get inventory availability for the item within the e-commerce channel’s warehouse or all warehouses linked to the e-commerce channel’s fulfillment group configuration or for warehouses within a certain search area/radius based on longitude and latitude data.

**ProductWarehouseInventoryAvailabilities** – use this API to be able to request inventory for an item from a specific warehouse (such as a retail store warehouse when needing to display inventory for order pickup availability scenarios)

>[!NOTE]
> The above referenced API's replace the older GetProductAvailabilities and GetAvailableInventoryNearby API’s that were in market prior to 10.0.7.

These API's will fetch data from the Commerce server and provide a calculated estimation of on-hand inventory for a particular product/product variant/warehouse combination.  While there are other API's available on the Commerce server that can go directly to HQ to fetch on-hand quantities for products, using these API's is not recommended in an e-commerce environment due to potential performance issues and impact these frequent requests may have on your HQ servers.  Additionally, by calculating the on-hand inventory through the Commerce server, there is a better chance of the calculation including inventory that was sold on recent e-commerce transactions which have not yet been synchronized to HQ yet.  HQ may not know about these transactions, but the Commerce server/channel database has this data and it will be factored in to provide a potentially more accurate estimation of an product's available inventory.

### Getting started with e-commerce calculated inventory availability

Before utilizing these new API’s, parameter changes must be made in HQ to ensure that the inventory value snapshot that is calculated by HQ using the **Product Availability** job is populating correct tables that the API will utilize.

This parameter can be found in the **Retail and Commerce \> Headquarters Setup\> Parameters \>Commerce shared parameters** form on the **Inventory** tab.

In the **Product availability job** parameters, set the parameter to **Use optimized process for Product Availability job**.  This setting is necessary to ensure that the most optimal feature set for calculating the channel available inventory through the retail server is deployed.

Due to the distributed server architecture of our Commerce solution, in order for the API to be able to calculate the best estimate of inventory availability for an item, a periodic snapshot of inventory availability from HQ must be processed and sent to the channel database that is used by the e-commerce Commerce Scale Unit.    This snapshot represents what the HQ knows about inventory availability for a particular product/product variant/warehouse combination.  This may include inventory adjustments or movements that were a result of inventory receipts, shipments or other processes performed in the HQ client that the e-commerce channel would otherwise not be aware of without this synchronization process.

It is important to stress that the HQ database snapshot created by the **Product availability** job only calculates the inventory transactions that have been processed and posted in HQ at the time the snapshot is taken.  This means that if inventory has been sold for a product within a store warehouse through a cash and carry or async customer order sale in the POS application, HQ will not know about the related inventory issue transaction for this sale immediately.  HQ will not be aware of inventory sold for these types of store sales until the P-job uploads those related transaction from that store’s channel database into HQ and the related sales order is created through statement posting/trickle feed posting processes (the process of creating the order in HQ is what creates the related inventory transactions).   For e-commerce channel orders, the inventory transaction is only known to HQ after the transactions are sent to HQ through the P-job and the synchronize orders process has completed.   Therefore it’s important to understand that the inventory snapshot value provided in the **Product availability** job is never guaranteed to be 100% real-time accurate due to the constant sales processing that is occurring across distributed servers.

To take the snapshot of inventory in HQ, navigate to **Retail and Commerce \> Retail and Commerce IT \> Products and inventory \> Product availability** and run the **Product availability** job.  This job can also be scheduled to run in batch.   

Once the **Product availability** job has completed, the data captured must then be pushed to the e-commerce channel databases so that the latest HQ inventory snapshot is available to influence the estimated on-hand inventory calculation.   Navigate to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule** and run the **1130 Product availability** job to synchronize this snapshot data created by the **Product availability** batch job from HQ to your channel database(s).

When requesting inventory availability from the **GetEstimatedAvailabilty** or **ProductWarehouseInventoryAvailabilities** API, there will be a calculation executed to attempt to get the best possible estimation of inventory for the product requested.   The calculation will reference any e-commerce customer orders that are in the channel database that were not included in the **Product availability** snapshot data provided by the **1130** distribution job.  This logic is accomplished by tracking the last processed inventory transaction from HQ and comparing it with the transactions in the channel database.   This provides the waterline that allows the channel-side calculation logic to factor in additional inventory movements that have occurred for customer order sales transactions in the e-commerce channel database and factor them into the estimated inventory value that the API will provide.  

It is important to stress that this channel-side calculation logic will return an ESTIMATED physical available and total available value for the requested product/warehouse.   This value can be displayed on your e-commerce site as desired, or can be used to trigger other business logic on your e-commerce site such as showing an “out of stock” message vs. showing the actual on-hand quantity passed by the API.

Please note that the channel side e-commerce API estimated inventory calculation logic is only able to evaluate inventory based on customer orders that have been created in the channel database but not yet synchronized and posted in HQ.   If your channel database also contains cash and carry transactional sales data for a store specific warehouses, it is important to note that these cash and carry sales will not be factored into the e-commerce channel-side calculation for that store warehuse when used by these e-commerce API's.

## Options for configuration of the inventory lookup operation in the POS channel

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
* **Calculate transactional statements in batch** - for cash and carry transactions created in store, running the trickle feed posting process will ensure that inventory related to these cash and carry sales is updated efficiently.  Ensure you have enabled your system to use [trickle feed posting](https://docs.microsoft.com/en-us/dynamics365/commerce/trickle-feed) to get the most efficient processing of inventory transactions for your cash and carry orders.
** Post transactional statements in batch** - this job is also required for trickle feed posting and follows the previously mentioned  transactional calculation job. This job will post the calculated statements systematically which will then result in sales orders being created in HQ for the cash and carry sales and a more accurate depiction of your store's inventory in HQ.
**Product availability** - this job creates the "snapshot" of inventory from HQ.
**1130 Product availability** - this job found in the **Distribution schedule** form should be run immediately after the **Product availability** job.  This is the job that transports the snapshot inventory data from HQ to the channel databases.

## Additional feature note

It is important to note that when inventory availability is calculated channel-side, this calculation looks at a cache to determine if enough time has passed to justify running the calculation logic again when an inventory availability request is made.  This cache is used to optimize performance.  Currently the default cache is set to 60 seconds.   This means that if you have enabled channel side calculation for your store and you look at the on-hand inventory for a product using the "Inventory lookup** operation and note the value, then you take a sales transaction and sell 1 unit of that product, if you then immediately return to the **Inventory lookup** form to confirm inventory has reduced by 1 - you will not see the reduction of inventory on this form until the cache has cleared.  Therefore users should wait 60 seconds after posting a transaction in POS to check and validate that the inventory has been reduced from on-hand when using the **Channel** configuration for inventory availability as configured in the channels functionality profile.

If your business scenario requires a lower cache time, please contact your product support representative for assistance. 
