---
# required metadata

title: Manage store inventory
description: This article describes the types of documents that you can use to manage inventory.
author: josaw1
manager: AnnBe
ms.date: 2015-12-09 18 - 39 - 11
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: josaw1
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 21391
ms.assetid: 0912e60b-1acf-4d9f-953c-3ccda785241f
ms.search.region: global
ms.search.industry: Retail
ms.author: rubendel
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Manage store inventory

This article describes the types of documents that you can use to manage inventory.

You can use the following types of documents to manage your organization's inventory.

## Purchase orders
Purchase orders are created at the head office. If a retail warehouse is included in the purchase order header, the order can be received at the store by using Retail and commerce in Microsoft Dynamics AX Modern POS or Cloud POS. After the quantities that are received at the store are entered, they can be saved locally for additional modification. Alternatively, the quantities can be committed and sent to the head office. At the head office, the quantities that were received at the store are displayed in Microsoft Dynamics AX, in the **Receive now** field on the purchase order.
Transfer orders
---------------

A transfer order can specify that a particular store is a location that items can be shipped from. In this case, the transfer order appears at the store as a picking request in Modern POS or Cloud POS. After the quantities that are requested are picked, they are committed and sent to the head office. At the head office, the quantities that were picked at the store are displayed in Microsoft Dynamics AX, in the **Ship now** field on the transfer order. A transfer order may specify that a particular store is a location that items can be shipped to. In this case, the transfer order appears at the store as a receiving request in Modern POS or Cloud POS. After the quantities that are received at the store are entered, they can be saved locally for additional modification. Alternatively, the quantities can be committed and sent to the head office. At the head office, the quantities that were received at the store are displayed in Microsoft Dynamics AX, in the **Receive now** field on the transfer order.

## Stock counts
Stock counts can be either scheduled or unscheduled. Scheduled stock counts are initiated at the head office, which specifies the items that must be counted. The head office creates a counting document that can be received at the store, where the quantities of actual on-hand stock are entered in Modern POS or Cloud POS. Unscheduled stock counts are initiated at a store, and the quantities of actual on-hand stock are updated in either Modern POS or Cloud POS. Unlike scheduled stock counts, unscheduled stock counts do not have a predefined list of items. When a stock count of either type is completed, it is committed and sent to the head office. At the head office, the count is validated and posted.



