---
title: Turn on the Landed cost module and related features for your system
description: This article describes how to turn the Landed cost module and its optional extra features on or off.
author: Weijiesa
ms.author: weijiesa
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 08/09/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Turn on the Landed cost module and related features for your system

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article describes how to turn the **Landed cost** module and its optional related features on or off.

The following table describes the *Landed cost* feature and each of its available add-on features. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of each feature and turn it on as needed. In the **Feature management** workspace in Microsoft Dynamics 365 Supply Chain Management, every feature in this table is listed under the **Transportation management** module.

| Feature name and requirements | Feature description |
|---|---|
| <p>**Feature name:**<br>*Landed cost*</p><p>**Version required:**<br>10.0.17 or later</p> | This feature provides the basic **Landed cost** module. To use any part of the **Landed cost** module's functionality, including the other features that are described in this table, you must turn on the *Landed cost* feature for your system. |
| <p>**Feature name:**<br>*Generate data manually on voyage editor*</p><p>**Version required:**<br>10.0.31 or later</p> | <p>This feature modifies the **Voyage editor** page so that it updates the inbound order list (based on the current filter settings) only when you manually select **Generate data** on the Action Pane.</p><p>Without this feature, the page updates the inbound order list each time that you change a filter setting. This behavior can cause performance issues when a large amount of data is available.</p><p>For more information, see [The Voyage editor page](manage-voyages.md#voyage-editor).</p> |
| <p>**Feature name:**<br>*Enable shipping container creation and update in batch mode*</p><p>**Version required:**<br>10.0.33 or later</p> | This feature for the **Landed cost** module lets you use batch mode when you create and update shipping containers for Landed cost. By creating and updating shipping containers in background mode, you help improve system performance when you work with shipping containers that have many shipping lines. |
| <p>**Feature name:**<br>*Enable split vendor invoice journal line per cost type code and voyage id from multiple voyages*</p><p>**Version required:**<br>10.0.33 or later</p> | This feature for the **Landed cost** module enables businesses to better allocate transportation costs that are associated with multiple voyages. After this feature is turned on, when a user creates a vendor invoice journal for multiple voyages, each cost type code will have its own journal line that includes the voyage name in its description. Therefore, reconciliation is easier. |
| <p>**Feature name:**<br>*Performance improvements for post receipt function in Landed Cost*</p><p>**Version required:**<br>10.0.33 or later</p> | This feature helps improve the performance of the **Landed cost** module by reducing the amount of information that's queried and updated when product receipts are posted for large purchase orders. |
| <p>**Feature name:**<br>*(Preview) Source document and accounting distribution support for Landed Cost*</p><p>**Version required:**<br>10.0.34 or later</p> | This feature for the **Landed cost** module enables landed costs to be included in the accounting distribution of purchased product receipts. Therefore, these costs can easily be identified and tracked. The feature supports the association of freight cost from Landed cost with the corresponding source documents. Therefore, it provides a more accurate and comprehensive view of the total cost of goods that are received. By helping you gain more visibility into the expenses that are associated with your purchases and transportation, this functionality allows for better cost analysis and management. For more information, see [Show landed costs in the accounting distribution of product receipts](estimate-manage-landed-costs.md#source-doc-post). |
| <p>**Feature name:**<br>*(Preview) Specify Goods In Transit Order when receiving via mobile device*</p><p>**Version required:**<br>10.0.35 or later</p> | This feature for the **Landed cost** module enables workers to select a specific goods-in-transit order for receiving when multiple goods-in-transit orders exist for the same voyage, container, item number, and purchase order number. For more information, see [Specify goods-in-transit orders when receiving with a mobile device](in-transit-processing.md#specify-GIT-order).  |
| <p>**Feature name:**<br>*(Preview) Split Goods In Transit Order quantity and assign batch/serial number when receiving via mobile device.*</p><p>**Version required:**<br>10.0.35 or later</p> | This feature for the **Landed cost** module lets workers who use a mobile device assign multiple batch/serial numbers for different quantities of goods that are received from goods-in-transit orders. During the receiving process, all assigned batch/serial numbers are consolidated into one work record and processed together. For more information, see [Assign batch/serial numbers when receiving with a mobile device](in-transit-processing.md#batch-serial). |
