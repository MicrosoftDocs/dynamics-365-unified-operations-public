---
# required metadata

title: Manage store inventory
description: This article describes the types of documents that you can use to manage inventory.
author: josaw1
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: josaw1
ms.search.scope: AX 7.0.0, Operations, Core, Retail
# ms.tgt_pltfrm: 
ms.custom: 21391
ms.assetid: bfef3717-d0e0-491d-8466-d8a9c995177d
ms.search.region: global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Manage store inventory

[!include[banner](includes/banner.md)]


This article describes the types of documents that you can use to manage inventory.

You can use the following types of documents to manage your organization's inventory.

## Purchase orders
Purchase orders are created at the head office. If a retail warehouse is included in the purchase order header, the order can be received at the store by using Modern POS (MPOS) or Cloud POS in Microsoft Dynamics 365 for Retail. After the quantities that are received at the store are entered, they can be saved locally for additional modification. Alternatively, the quantities can be committed and sent to the head office. At the head office, the quantities that were received at the store are displayed in Dynamics 365 for Retail, in the **Receive now** field on the purchase order.

## Transfer orders
A transfer order can specify that a particular store is a location that items can be shipped from. In this case, the transfer order appears at the store as a picking request in MPOS or Cloud POS. After the quantities that are requested are picked, they are committed and sent to the head office. At the head office, the quantities that were picked at the store are displayed in Dynamics 365 for Retail, in the **Ship now** field on the transfer order. A transfer order may specify that a particular store is a location that items can be shipped to. In this case, the transfer order appears at the store as a receiving request in MPOS or Cloud POS. After the quantities that are received at the store are entered, they can be saved locally for additional modification. Alternatively, the quantities can be committed and sent to the head office. At the head office, the quantities that were received at the store are displayed in Dynamics 365 for Retail, in the **Receive now** field on the transfer order.

## Stock counts
Stock counts can be either scheduled or unscheduled. Scheduled stock counts are initiated at the head office, which specifies the items that must be counted. The head office creates a counting document that can be received at the store, where the quantities of actual on-hand stock are entered in MPOS or Cloud POS. Unscheduled stock counts are initiated at a store, and the quantities of actual on-hand stock are updated in either MPOS or Cloud POS. Unlike scheduled stock counts, unscheduled stock counts do not have a predefined list of items. When a stock count of either type is completed, it is committed and sent to the head office. At the head office, the count is validated and posted.

## Inventory lookup
The current product quantity on hand for multiple stores and warehouses can be viewed on the Inventory lookup page. In addition to the current quantity on hand, the future available to promise (ATP) quantities can be viewed for each individual store. To do so, select the store that you want to view the ATP for and then click **Show store availablity**.




