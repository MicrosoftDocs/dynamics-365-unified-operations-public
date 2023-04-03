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

The Landed cost feature itself, plus each of its available add-on features, are listed and described in the following table. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of each feature and turn it on as needed. Each feature in the table is listed under the *Transportation management* module in the **Feature management** workspace in Supply Chain Management.

| Feature name and requirements | Feature description |
|---|---|
| <p>**Feature name:**</br>*Landed cost*/p><p>**Version required:**</br>10.0.17 or higher</p> | This feature provides the basic Landed cost module. To use any part of the Landed cost module functionality, including the other features listed in this table, the *Landed cost* feature must be turned on for your system. |
| <p>**Feature name:**</br>*(Preview) Enable shipping container creation and update in batch mode*</p><p>**Version required:**</br>10.0.33 or higher</p> | This feature for the Landed cost module makes it possible to use batch mode when you create and update shipping containers for Landed cost. By creating and updating shipping containers in background mode, you can help improve system performance when you work with shipping containers that have many shipping lines. |
| <p>**Feature name:**</br>*(Preview) Enable split vendor invoice journal line per cost type code and voyage id from multiple voyages*</p><p>**Version required:**</br>10.0.33 or higher</p> | This feature for the Landed cost module enables businesses to better allocate transportation costs associated with multiple voyages. With this feature, when a user is creating a vendor invoice journal for multiple voyages, each cost type code will have its own journal line that includes the voyage name in its description. This allows for easier reconciliation. |
| <p>**Feature name:** *(Preview) Source document and accounting distribution support for Landed Cost*</p><p>**Version required:** 10.0.34 or higher</p> | This feature for the Landed cost module enables landed costs to be included in the accounting distribution of purchased product receipts, which makes it easy to identify and track these costs. It supports the association of freight cost from landed cost with their corresponding source documents, providing a more accurate and comprehensive view of the total cost of goods received. With this functionality, you can gain greater visibility into the expenses associated with your purchases and transportation, allowing for better cost analysis and management. See also [Show landed costs in the accounting distribution of product receipts](manage-voyages.md#source-doc-post) |
