---
# required metadata

title: Store inventory management
description: This topic describes the types of documents that you can use to manage inventory.
author: rubencdelgado
manager: AnnBe
ms.date: 05/15/2020
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

When you work with inventory in Microsoft Dynamics 365 Commerce and use the point of sale (POS) application, it's important that you be aware that POS provides limited support for some inventory dimensions and some inventory item types. The POS application doesn't support the full range of item configuration capabilities that is available through the item configuration options in Dynamics 365 Supply Chain Management.

The POS solution currently doesn't support the following product dimensions and item configurations:

- Configuration product dimension and bill of materials (BOM) items (except retail kit products, which use some components of the BOM framework)
- Catch weight items
- Version product dimension-controlled items

The POS application currently doesn't support the following tracking dimensions in the POS:

- Batch tracking dimension
- Owner dimension

POS provides limited support for the following dimensions. In other words, POS might automatically enter some of these dimensions in inventory transactions, based on the configuration of the warehouse or store setup. POS won't fully support the dimensions in the way that they are supported if a sales transaction is manually entered in Commerce headquarters. 

- **Warehouse Location** – When they use the new [Inbound operation](https://docs.microsoft.com/dynamics365/commerce/pos-inbound-inventory-operation) and [Outbound operation](https://docs.microsoft.com/dynamics365/commerce/pos-outbound-inventory-operation) POS operations, users can select a warehouse inventory location to receive items into or ship outbound transfer order items out of. If they use the obsolete **Picking and receiving** operation, limited location management support is available for receiving and shipping outbound transfers. That support is available only if the **Use warehouse management process** option has been turned on for the item and the store warehouse. An inventory location can't currently be used with the **Stock count** operation or the **Inventory lookup** operation.
- **License plate** – License plates are applicable only when the **Use warehouse management process** option has been turned on for the item and the store warehouse. In POS, if inventory is received into a store warehouse by using the **Inbound operation** operation or the **Picking and receiving** operation where the warehouse management process has been turned on, and if the location that has been selected to receive the item into is linked to a location profile that requires license plate control, the POS application systematically applies a license plate to the receiving line. POS users can't change or manage this license plate data. If full management of license plates is required, we recommend that the store use the [warehousing app](https://docs.microsoft.com/dynamics365/supply-chain/warehousing/install-configure-warehousing-app) or the back-office client to manage the receipt of these items.
- **Serial number** – The POS application provides limited support for registration of a single serial number on a sales transaction  line for orders that are created in POS and include serialized items. This serial number isn't validated against registered serial numbers that are already in inventory. If a sales order is created in the call center channel or fulfilled through enterprise resource planning (ERP), and multiple serial numbers are registered on a single sales line during the fulfillment process in ERP, those serial numbers can't be applied or validated if a return is processed for the order in POS. When inventory is received by using the **Inbound operation** operation, users can [register or confirm the serial numbers received](https://docs.microsoft.com/dynamics365/commerce/pos-serialized-items).
- **Inventory status** – For items that use the warehouse management process and require an inventory status, this status field can't be set or modified through the POS application. The default inventory status that is defined in the store warehouse configuration is used when items are received into inventory.

> [!NOTE]
> All organizations must test item configurations through POS in development or test environments before they deploy those item configurations to production environments. Test your items by using them to perform regular cash-and-carry sales transactions and create customer orders (if applicable) through POS. You should also test POS fulfillment and inventory processes (such as inventory receiving and order fulfillment operations) before you deploy any new item configurations, to make sure that the POS application can support them. Testing must include running a full statement posting process in your test environment and verifying that no issues occur when orders for these items are created and posted in Commerce headquarters.
>
> If items are configured in a way that the POS application doesn't support, and appropriate testing isn't done, data failures that aren't easily corrected or that aren't covered through standard product support might occur during the order creation process.

## Purchase orders

Purchase orders are created in Commerce headquarters. If a store warehouse is included in the purchase order header or on purchase order lines, the lines can be received at the store by using the [Inbound operation](https://docs.microsoft.com/dynamics365/commerce/pos-inbound-inventory-operation) operation in POS. 

## Transfer orders

Transfer orders can be created in Commerce headquarters, or through either the [Inbound operation](https://docs.microsoft.com/dynamics365/commerce/pos-inbound-inventory-operation) or [Outbound operation](https://docs.microsoft.com/dynamics365/commerce/pos-outbound-inventory-operation) operation in POS. Use the **Inbound operation** POS operation to create a transfer order request to have inventory sent to the store from another warehouse or store location. Use the **Outbound operation** POS operation to create a transfer order request to have inventory shipped from the store to another warehouse or store location. After a transfer order for a store is created, that store can manage the receipt of inventory for the transfer order through the **Inbound operation** operation in POS. If the store is shipping inventory to another location, the **Outbound operation** operation in POS is used to manage that store's outbound shipment process.

## Stock counts

Stock counts can be either scheduled or unscheduled. Scheduled stock counts are created through Commerce headquarters by creating a Counting journal document that is linked to the store's warehouse. This journal specifies the items that must be counted. The store can then access these predefined counting journals and act on them by using the **Stock count** operation in POS. Store users initiate an unscheduled stock count as it's required when they use the **Stock count** operation in POS. Unlike scheduled stock counts, unscheduled stock counts don't have a predefined list of items. When a stock count of either type is completed in POS, it's committed and sent to the head office. At the head office, the count must then be validated and posted in Commerce headquarters as a separate step.

## Inventory lookup

The product quantity that is currently on hand for multiple stores and warehouses can be viewed on the **Inventory lookup** page. In addition to the current on-hand quantity, the future available-to-promise (ATP) quantities can be viewed for each store. Select the store to view the ATP quantities for, and then select **Show store availability**. For information about the configuration options that are available, see [Calculate inventory availability for retail channels](https://docs.microsoft.com/dynamics365/commerce/calculated-inventory-retail-channels).
