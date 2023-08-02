---
# required metadata

title: Store inventory management
description: This article describes the types of documents that you can use to manage inventory.
author: BrianShook
ms.date: 01/12/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.assetid: bfef3717-d0e0-491d-8466-d8a9c995177d
ms.search.region: global
ms.search.industry: Retail
ms.author: hhaines
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---

# Commerce inventory management

[!include [banner](includes/banner.md)]

When you work with inventory in Microsoft Dynamics 365 Commerce and use any of the Commerce applications that are connected to a Commerce Scale Unit (CSU), it's important to know that the order processing logic in CSU provides limited support for some inventory dimensions and some inventory item types. Commerce applications don't support the full range of item configuration capabilities that is available through the item configuration options in Dynamics 365 Supply Chain Management.

The Commerce applications running on CSU don't support the following product dimensions and item configurations:

- Configuration product dimension and bill of materials (BOM) items (except retail kit products, which use some components of the BOM framework)
- Catch weight items
- Version product dimension-controlled items

The Commerce applications running on CSU do not support the following tracking dimensions:
- Owner dimension

- The point of sale (POS) application can offer limited support for the following dimensions. POS may automatically enter some of the dimensions in inventory transactions, based on the configuration of the warehouse or store setup. POS won't fully support the dimensions in the way that they are supported if a sales transaction is manually entered in Commerce headquarters, however. 

- **Warehouse Location** – When they use the new [Inbound operation](./pos-inbound-inventory-operation.md) and [Outbound operation](./pos-outbound-inventory-operation.md) POS operations, users can select a warehouse inventory location to receive items into or ship outbound transfer order items out of. If they use the obsolete **Picking and receiving** operation, limited location management support is available for receiving and shipping outbound transfers. That support is available only if the **Use warehouse management process** option has been turned on for the item and the store warehouse. An inventory location can't currently be used with the **Stock count** operation or the **Inventory lookup** operation.

- **License plate** – License plates are applicable only when the **Use warehouse management process** option has been turned on for the item and the store warehouse. In POS, if inventory is received into a store warehouse by using the **Inbound operation** operation or the **Picking and receiving** operation where the warehouse management process has been turned on, and if the location that has been selected to receive the item into is linked to a location profile that requires license plate control, the POS application systematically applies a license plate to the receiving line. POS users can't change or manage this license plate data. If full management of license plates is required, we recommend that the store use the [warehousing app](../supply-chain/warehousing/install-configure-warehousing-app.md) or the back-office client to manage the receipt of these items.

- **Serial number** – The POS application provides limited support for registration of a single serial number on a sales transaction  line for orders that are created in POS and include serialized items. This serial number isn't validated against registered serial numbers that are already in inventory. If a sales order is created in the call center channel or fulfilled through enterprise resource planning (ERP), and multiple serial numbers are registered on a single sales line during the fulfillment process in ERP, those serial numbers can't be applied or validated if a return is processed for the order in POS. When inventory is received by using the **Inbound operation** operation, users can [register or confirm the serial numbers received](./pos-serialized-items.md).

- **Batch ID** - The POS application provides limited support during statement posting if a batch-controlled item is sold, but POS users aren't able to define the batch ID that was sold or picked when using the POS application.

- **Inventory status** – For items that use the warehouse management process and require an inventory status, this status field can't be set or modified through the POS application. The default inventory status that is defined in the store warehouse configuration is used when items are received into inventory.

> [!NOTE]
> All organizations must test item configurations through Commerce apps in development or test environments before they deploy those item configurations to production environments. Test your items by using them to perform regular cash-and-carry sales transactions in POS and create customer orders (if applicable) through POS, call center or e-commerce to validate they can be fully supported. You should also test POS fulfillment and inventory processes (such as inventory receiving and order fulfillment operations) before you deploy any new item configurations, to make sure that the POS application can support them. Testing must include running a full statement/order posting process in your test environment and verifying that no posting issues occur when orders for these items are created and posted in Commerce headquarters.
>
> If items are configured in a way that isn't supported by the Commerce applications and appropriate testing isn't done, data failures that aren't easily corrected or may not be able to be corrected at all, may occur.

## Purchase orders

Purchase orders are created in Commerce headquarters. If a store warehouse is included in the purchase order header or on purchase order lines, the lines can be received at the store by using the [Inbound operation](./pos-inbound-inventory-operation.md) operation in POS. 

## Transfer orders

Transfer orders can be created in Commerce headquarters, or through either the [Inbound operation](./pos-inbound-inventory-operation.md) or [Outbound operation](./pos-outbound-inventory-operation.md) operation in POS. Use the **Inbound operation** POS operation to create a transfer order request to have inventory sent to the store from another warehouse or store location. Use the **Outbound operation** POS operation to create a transfer order request to have inventory shipped from the store to another warehouse or store location. After a transfer order for a store is created, that store can manage the receipt of inventory for the transfer order through the **Inbound operation** operation in POS. If the store is shipping inventory to another location, the **Outbound operation** operation in POS is used to manage that store's outbound shipment process.

## Stock counts

Stock counts can be either scheduled or unscheduled. Scheduled stock counts are created through Commerce headquarters by creating a Counting journal document that is linked to the store's warehouse. This journal specifies the items that must be counted. The store can then access these predefined counting journals and act on them by using the **Stock count** operation in POS. Store users initiate an unscheduled stock count as it's required when they use the **Stock count** operation in POS. Unlike scheduled stock counts, unscheduled stock counts don't have a predefined list of items. When a stock count of either type is completed in POS, it's committed and sent to the head office. At the head office, the count must then be validated and posted in Commerce headquarters as a separate step.

## Inventory lookup

The product quantity that is currently on hand for multiple stores and warehouses can be viewed on the **Inventory lookup** page. In addition to the current on-hand quantity, the future available-to-promise (ATP) quantities can be viewed for each store. Select the store to view the ATP quantities for, and then select **Show store availability**. For information about the configuration options that are available, see [Calculate inventory availability for retail channels](./calculated-inventory-retail-channels.md).


[!INCLUDE[footer-include](../includes/footer-banner.md)]