---
# required metadata

title: Store inventory management
description: This topic describes the types of documents that you can use to manage inventory.
author: rubencdelgado
manager: AnnBe
ms.date: 04/23/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 21391
ms.assetid: bfef3717-d0e0-491d-8466-d8a9c995177d
ms.search.region: global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---

# Store inventory management

[!include [banner](includes/banner.md)]

When working with inventory in Dynamics 365 Commerce and using the Point of Sale(POS) application, it is important to note that POS provides limited support for certain inventory dimensions and certain inventory item types.  The POS application should not be expected to support the full breadth of item configuration capabilities that are available through the item configuration options within the Dynamics 365 Supply Chain application.

The POS solution currently does not support the following product dimensions/item configurations:

- Configuration product dimension/BOM items (except for retail kit products, which does utilize some components of the BOM framework)
- Catch weight items
- Version product dimension controlled items

The POS application currently does not support the following tracking dimensions in the POS:

- Batch tracking dimension
- Owner dimension

The POS solution provides limited support for the following dimensions. Limited support indicates that the POS may default some of these dimensions into inventory transactions automatically based on warehouse/store setup configuration. POS will not fully support the dimensions in the way they are supported if a sales transaction is manually entered into the backend ERP application. 

- **Warehouse Location** – When using the new [Inbound operation](https://docs.microsoft.com/en-us/dynamics365/commerce/pos-inbound-inventory-operation) and [Outbound operation](https://docs.microsoft.com/en-us/dynamics365/commerce/pos-outbound-inventory-operation), users will have the ability to select a warehouse inventory location to receive items into or ship outbound transfer order items out of.   If using the deprecated **Picking and receiving** operation, only limited location management support is enabled for receiving and shipping outbound transfers and it is only available if the **Use warehouse management process** has been enabled on the item and the store warehouse.  Inventory location cannot currently be used with the **Stock count** operation or the **Inventory lookup** operation.
- **License plate** – License plates are only applicable when **Use warehouse management process** has been enabled on the item and the store warehouse. In POS, if inventory is received into a store warehouse using the **Inbound operation** or the **Picking and receiving** operation where the warehouse management process has been enabled, and the location chosen to receive the item into is tied to a location profile that requires license plate control, the POS application will systematically apply a license plate to the receiving line. Users in POS will not have the ability to change or manage this license plate data. If full management of license plates is required, it is suggested the store use the [Warehousing mobile application](https://docs.microsoft.com/en-us/dynamics365/supply-chain/warehousing/install-configure-warehousing-app) or the back office ERP client to manage the receipt of these items.
- **Serial number** – The POS application has limited support for single serial number to be registered on a transaction sales line for orders created in POS with serialized items. This serial number is not validated against registered serial numbers already in inventory. If a sales order is created in the call center channel or fulfilled through the ERP and multiple serial numbers are registered to a single sales line during the fulfillment process in the ERP, these serial numbers will not be able to be applied or validated if a return is processed in POS for these orders.  When receiving inventory using the **Inbound operation** it will be possible to [register or confirm the serial numbers received](https://docs.microsoft.com/en-us/dynamics365/commerce/pos-serialized-items)
- **Inventory status** – For items that use the warehouse management process and require an inventory status, this status field is not able to be set or modified through the POS application. The default inventory status as defined on the store warehouse configuration will be used when items are received into inventory.

> [!NOTE]
> All organizations must test item configurations through POS in development or test environments before deploying them to production. Test your items by performing regular cash and carry sales transacting and creating customer orders (if applicable) through the POS with your items. Testing POS fulfillment and inventory processes such as inventory receiving and order fulfillment operations should also be done prior to deploying any new item configurations to ensure the Point of Sale application can support them. Testing must include running a full statement posting processes in your test environment and verifying that there are no issues with creating and posting the orders in HQ for these items.
>
> Configuring items in a way that is not supported by the POS application, without proper testing, can result in data failures to the order creation process that cannot easily be corrected and would not be covered through standard product support.

## Purchase orders

Purchase orders are created in Commerce Headquarters (HQ). If a store warehouse is included in the purchase order header or lines, those lines can be received at the store by using the [Inbound operation](https://docs.microsoft.com/en-us/dynamics365/commerce/pos-inbound-inventory-operation) in POS. 

## Transfer orders

Transfer orders can be created in Commerce Headquarters (HQ) or through the [Inbound operation](https://docs.microsoft.com/en-us/dynamics365/commerce/pos-inbound-inventory-operation) or [Outbound operation](https://docs.microsoft.com/en-us/dynamics365/commerce/pos-outbound-inventory-operation) in POS. Use the **Inbound operation** to create a transfer order request to have inventory sent to the store from another warehouse/store location.  Use the **Outbound operation** to create a transfer order request for shipping inventory from the store to another warehouse/store location.  Once a transfer order for a store has been created, that store can manage the receipt of inventory for that transfer order through the **Inbound operation** in POS.  If the store is shipping inventory out to another location, the **Outbound operation** in POS would be used to manage that store's outbound shipment process.

## Stock counts

Stock counts can be either scheduled or unscheduled. Scheduled stock counts are created through the Commerce Headquarters (HQ) by creating a **Counting journal** document tied to the store's warehouse.  This journal will specify the items that must be counted. These pre-defined counting journals can then be accessed and acted upon by the store using the **Stock count** operation in POS. Unscheduled stock counts are initiated ad-hoc by the store user when using the **Stock count** operation in POS. Unlike scheduled stock counts, unscheduled stock counts do not have a predefined list of items. When a stock count of either type is completed in POS, it is committed and sent to the head office. At the head office, the count must then be validated and posted in HQ as a separate step.

## Inventory lookup

The current product quantity on hand for multiple stores and warehouses can be viewed on the **Inventory lookup** page. In addition to the current quantity on hand, the future available to promise (ATP) quantities can be viewed for each individual store. To do so, select the store that you want to view the ATP for and then click **Show store availability**.  Refer to the documentation on [calculated inventory](https://docs.microsoft.com/en-us/dynamics365/commerce/calculated-inventory-retail-channels) to understand different configuration options.
