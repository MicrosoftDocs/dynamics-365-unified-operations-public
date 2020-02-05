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

When working with inventory in Dynamics 365 Commerce and using the POS application, it is important to note that POS provides limited support for inventory dimensions and certain inventory item types.

The POS solution does not support the following item configurations:

- BOM items (except kit products, which utilize some components of the BOM framework)
- Catch weight items
- Batch-controlled items

The POS application currently does not support the following tracking dimensions in the POS:

- Batch tracking dimension
- Owner dimension

The POS solution provides limited support for the following dimensions. Limited support indicates that the POS may default some of these dimensions into inventory transactions automatically based on warehouse/store setup configuration. POS will not fully support the dimensions in the way they are supported if a sales transaction is manually entered into the ERP. 

- **Warehouse Location** – Users will not have the ability to manage the receiving warehouse location for items received into a store warehouse when the store has not been configured to use the warehouse management process. A default receiving location defined on the store warehouse will be used for these items. If the warehouse management process has been enabled for the store, limited support that prompts the user to choose a receiving location for the entire receipt will be triggered. Items sold from the store will always be sold out of the default location as defined on the store warehouse setup. The location for managing return inventory can be controlled through default return location definition on the store warehouse or based on return reason codes as defined in the return location policy.
- **License plate** – License plates are only applicable when **Use warehouse management process** has been enabled on the item and the store warehouse. In POS, if inventory is received into a store warehouse where the warehouse management process has been enabled, and the location chosen to receive the item into is tied to a location profile that requires license plate control, the POS application will systematically apply a license plate to the receiving line. Users in POS will not have the ability to change or manage this license plate data. If full management of license plates is required, it is suggested the store use the WMS mobile application or the back office ERP client to manage the receipt of these items.
- **Serial number** – The POS application has limited support for single serial number to be registered on a transaction sales line for orders created in POS with serialized items. This serial number is not validated against registered serial numbers already in inventory. If a sales order is created in the call center channel or fulfilled through the ERP and multiple serial numbers are registered to a single sales line during the fulfillment process in the ERP, these serial numbers will not be able to be applied or validated if a return is processed in POS for these orders.
- **Inventory status** – For items that use the warehouse management process and require an inventory status, this status field is not able to be set or modified through the POS application. The default inventory status as defined on the store warehouse configuration will be used when items are received into inventory.

> [!NOTE]
> All organizations must test item configurations through POS in development or test environments before deploying them to production. Test your items by performing regular cash and carry sales transacting and creating customer orders (if applicable) through the POS with your items. Testing must include running a full statement posting processes in your test environment and verifying that there are no issues.
>
> Configuring items in a way that is not supported by the POS application, without proper testing, can result in your statement posting process failing in production without an easy way to correct the issues. Partner or customer customizations to the application may optionally be considered to allow these posting processes to successfully complete. If customizations are not needed, the organization must ensure that the product configuration of your products has been done in a way that is supported by the standard POS application/order creation/statement posting process.

## Purchase orders

Purchase orders are created at the head office. If a warehouse is included in the purchase order header, the order can be received at the store by using Modern POS (MPOS) or Cloud POS through the **Picking/Receiving** operation. After the quantities that are received at the store are entered in the **Receive Now** field in POS for the purchase order document, they can be saved locally or committed. Saving this data locally has no effect on in-stock inventory. Saving should be done only if the user is not ready to post the receipt to HQ and just needs a way to temporarily store the previously entered **Receive Now** data. This saves the receive now data locally to the user's channel database. After the document is processed using the **Commit** option, the **Receive Now** data is sent to HQ and the purchase order receipt will be posted. 

## Transfer orders

A transfer order can specify that a particular store is the location that items can be shipped from or the location the inventory will be received into. If the POS user is the shipping warehouse for a transfer order, they will be able to enter **Ship Now** quantities from POS. The data entered by the shipping store can be saved locally or committed. When saved locally, no updates are made to the transfer order document in HQ. Saving should be done only if the user is not ready to post the shipment to HQ and needs a way to temporarily store the previously entered **Ship Now** data. After the store is ready to confirm shipment, the **Commit** option should be selected. This posts the shipment of the transfer order in HQ so that the receiving warehouse will now be able to receive against it. 

If the POS user is the receiving warehouse for a transfer order, they will be able to enter the **Receive Now** quantities from POS. The data entered by the receiving store can be saved locally or committed. Saving should be done only if the user is not ready to post the receipt to HQ and needs a way to temporarily store the previously entered **Receive Now** data. This saves the receive now data locally to the user's channel database. After the document is processed using the **Commit** option, the **Receive Now** data is sent to HQ and the transfer order receipt will be posted. It's important to note that the receiving store will be restricted to only being able to commit receive quantities that are equal to or less than shipped quantities. An attempt to receive quantities on a transfer order that have not previously shipped will result in errors and the receipt will not be confirmed in HQ.

## Stock counts

Stock counts can be either scheduled or unscheduled. Scheduled stock counts are initiated at the head office, which specifies the items that must be counted. The head office creates a counting document that can be received at the store, where the quantities of actual on-hand stock are entered in MPOS or Cloud POS. Unscheduled stock counts are initiated at a store, and the quantities of actual on-hand stock are updated in either MPOS or Cloud POS. Unlike scheduled stock counts, unscheduled stock counts do not have a predefined list of items. When a stock count of either type is completed, it is committed and sent to the head office. At the head office, the count is validated and posted as a separate step.

## Inventory lookup

The current product quantity on hand for multiple stores and warehouses can be viewed on the **Inventory lookup** page. In addition to the current quantity on hand, the future available to promise (ATP) quantities can be viewed for each individual store. To do so, select the store that you want to view the ATP for and then click **Show store availability**.
