---
# required metadata

title: Store inventory management
description: This topic describes the types of documents that you can use to manage inventory.
author: rubencdelgado
manager: AnnBe
ms.date: 01/18/2019
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

This topic describes the types of documents that you can use to manage inventory.

You can use the following types of documents to manage your organization's inventory.

When working with inventory in Dynamics 365 for Retail and using the POS application, it is important to note that POS provides limited support for inventory dimensions and certain inventory item types.  

The POS solution does not support the following item configurations:
- BOM items (except kit products, which utilize some components of the BOM framework)
- Catch weight items
- Batch-controlled items

The POS application currently does not support the following tracking dimensions in the POS:
- Batch tracking dimension
- Owner dimension

The POS solution provides limited support for the following dimensions. Limited support indicates that the POS may default some of these dimensions into inventory transactions automatically based on warehouse/store setup configuration. POS will not fully support the dimensions in the way they are supported if a sales transaction is manually entered into the ERP. 

- Location
- License plate (only applicable when **Uuse warehouse management process** has been enabled on the item and the store warehouse)
- Serial number
- Inventory status

> [!NOTE]
> All organizations must test item configurations through POS in development or test environments before deploying them to production. Test your items by performing regular cash and carry sales transacting and creating customer orders (if applicable) through the POS with your items. Testing must include running a full statement posting processes in your test environment and verifying that there are no issues.
> Configuring items in a way that is not supported by the POS application, without proper testing, can result in your statement posting process failing in production without an easy way to correct the issues. Partner or customer customizations to the application may optionally be considered to allow these posting processes to successfully complete. If customizations are not needed, the organization must ensure that the product configuration of your products has been done in a way that is supported by the standard POS application/order creation/statement posting process.

## Purchase orders

Purchase orders are created at the head office. If a retail warehouse is included in the purchase order header, the order can be received at the store by using Modern POS (MPOS) or Cloud POS in Microsoft Dynamics 365 for Retail. After the quantities that are received at the store are entered, they can be saved locally for additional modification. Alternatively, the quantities can be committed and sent to the head office. At the head office, the quantities that were received at the store are displayed in Dynamics 365 for Retail, in the **Receive now** field on the purchase order.

## Transfer orders

A transfer order can specify that a particular store is a location that items can be shipped from. In this case, the transfer order appears at the store as a picking request in MPOS or Cloud POS. After the quantities that are requested are picked, they are committed and sent to the head office. At the head office, the quantities that were picked at the store are displayed in Dynamics 365 for Retail, in the **Ship now** field on the transfer order. A transfer order may specify that a particular store is a location that items can be shipped to. In this case, the transfer order appears at the store as a receiving request in MPOS or Cloud POS. After the quantities that are received at the store are entered, they can be saved locally for additional modification. Alternatively, the quantities can be committed and sent to the head office. At the head office, the quantities that were received at the store are displayed in Dynamics 365 for Retail, in the **Receive now** field on the transfer order.

## Stock counts

Stock counts can be either scheduled or unscheduled. Scheduled stock counts are initiated at the head office, which specifies the items that must be counted. The head office creates a counting document that can be received at the store, where the quantities of actual on-hand stock are entered in MPOS or Cloud POS. Unscheduled stock counts are initiated at a store, and the quantities of actual on-hand stock are updated in either MPOS or Cloud POS. Unlike scheduled stock counts, unscheduled stock counts do not have a predefined list of items. When a stock count of either type is completed, it is committed and sent to the head office. At the head office, the count is validated and posted.

## Inventory lookup

The current product quantity on hand for multiple stores and warehouses can be viewed on the Inventory lookup page. In addition to the current quantity on hand, the future available to promise (ATP) quantities can be viewed for each individual store. To do so, select the store that you want to view the ATP for and then click **Show store availability**.
