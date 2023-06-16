---
title: Turn on the Landed cost module and related features for your system
description: This article describes how to turn the Landed cost module and its optional extra features on or off.
author: Weijiesa
ms.author: weijiesa
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 04/20/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Turn on the Landed cost module and related features for your system

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article describes how to turn the Landed cost module and its optional related features on or off.

The following table describes the *Landed cost* feature and each of its available add-on features. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of each feature and turn it on as needed. In the **Feature management** workspace in Microsoft Dynamics 365 Supply Chain Management, every feature in this table is listed under the *Transportation management* module.

| Feature name and requirements | Feature description |
|---|---|
| <p>**Feature name:**<br>*Landed cost*</p><p>**Version required:**<br>10.0.17 or later</p> | This feature provides the basic Landed cost module. To use any part of the Landed cost module's functionality, including the other features that are described in this table, you must turn on the *Landed cost* feature for your system. |
| <p>**Feature name:**<br>*(Preview) Enable shipping container creation and update in batch mode*</p><p>**Version required:**<br>10.0.33 or later</p> | This feature for the Landed cost module lets you use batch mode when you create and update shipping containers for Landed cost. By creating and updating shipping containers in background mode, you can help improve system performance when you work with shipping containers that have many shipping lines. |
| <p>**Feature name:**<br>*(Preview) Enable split vendor invoice journal line per cost type code and voyage id from multiple voyages*</p><p>**Version required:**<br>10.0.33 or later</p> | This feature for the Landed cost module enables businesses to better allocate transportation costs that are associated with multiple voyages. After this feature is turned on, when a user creates a vendor invoice journal for multiple voyages, each cost type code will have its own journal line that includes the voyage name in its description. Therefore, reconciliation is easier. |
| <p>**Feature name:**<br>*(Preview) Source document and accounting distribution support for Landed Cost*</p><p>**Version required:**<br>10.0.34 or later</p> | This feature for the Landed cost module enables landed costs to be included in the accounting distribution of purchased product receipts. Therefore, these costs can easily be identified and tracked. The feature supports the association of freight cost from landed cost with the corresponding source documents. Therefore, it provides a more accurate and comprehensive view of the total cost of goods that are received. By helping you gain more visibility into the expenses that are associated with your purchases and transportation, this functionality allows for better cost analysis and management. For more information, see [Show landed costs in the accounting distribution of product receipts](manage-voyages.md#source-doc-post). |
| <p>**Feature name:**<br>*(Preview) Specify Goods In Transit Order when receiving via mobile device*</p><p>**Version required:**<br>10.0.35 or later</p> | This feature for the Landed cost module enables workers to select a specific goods-in-transit order for receiving when multiple goods-in-transit orders exist for the same voyage, container, item number, and purchase order number. For more information, see [Specify goods-in-transit orders when receiving with a mobile device](in-transit-processing.md#specify-GIT-order).  |
| <p>**Feature name:**<br>*(Preview) Split Goods In Transit Order and assign batch/serial number when receiving via mobile device*</p><p>**Version required:**<br>10.0.35 or later</p> | This feature for the Landed cost module enables workers using a mobile device to assign multiple batch/serial numbers for different quantities of goods received from goods-in-transit orders. During the receiving process, all assigned batch/serial numbers will be consolidated into one work record and they will be processed together. For more information, see [Assign batch/serial numbers when receiving with a mobile device](in-transit-processing.md#batch-serial). |
