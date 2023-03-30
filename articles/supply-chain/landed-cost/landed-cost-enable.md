---
title: Turn on the Landed cost module for your system
description: This article describes how to turn the Landed cost module and its optional extra features on or off.
author: Weijiesa
ms.date: 03/03/2023
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: weijiesa
ms.search.validFrom: 2021-09-24
ms.dyn365.ops.version: 10.0.17
---

# Turn on the Landed cost module for your system

[!include [banner](../includes/banner.md)]

This article describes how to turn the Landed cost module and its optional extra features on or off.

## Turn the Landed cost feature on or off

Before you can use any part of the Landed cost module functionality, the *Landed cost* feature must be turned on for your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on as needed. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Transportation management*
- **Feature name:** *Landed cost*

The *Landed cost* feature requires Microsoft Dynamics 365 Supply Chain Management version 10.0.17 or later.

## Turn the shipping container batch mode feature on or off

[!INCLUDE [preview-banner-section](../../includes/preview-banner-section.md)]

If you want to be able to use batch mode when you create and update shipping containers for Landed cost, you can also turn on this optional feature for your system. By creating and updating shipping containers in background mode, you can help improve system performance when you work with shipping containers that have a large number of shipping lines.

Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on or off as needed. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Transportation management*
- **Feature name:** *(Preview) Enable shipping container creation and update in batch mode*

The *(Preview) Enable shipping container creation and update in batch mode* feature requires Supply Chain Management version 10.0.33 or later.

## Turn split cost type codes for multiple voyages in the vendor invoice journale feature on or off

This feature for the Landed cost module enables business to better allocate transportation costs associated with multiple voyages. With this feature, when a user is creating a vendor invoice journal for multiple voyages, each cost type code will have its own journal line that includes the voyage name in its description. This allows for easier reconciliation. 

Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on or off as needed. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Transportation management*
- **Feature name:** *(Preview) Enable split vendor invoice journal line per cost type code and voyage id from multiple voyages*

The *(Preview) Enable split vendor invoice journal line per cost type code and voyage id from multiple voyages* feature requires Supply Chain Management version 10.0.32 or later.


## Turn Source document and accounting distribution support for Landed Cost feature on or off

This feature allows for the inclusion of landed costs in the accounting distribution of purchase product receipts, enabling customers to easily identify and track these costs. Specifically, it supports the association of freight cost from landed cost with their corresponding source documents, providing a more accurate and comprehensive view of the total cost of goods received. With this functionality, customers can gain greater visibility into the expenses associated with their purchases and transportation, allowing for better cost analysis and management.

Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on or off as needed. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Transportation management*
- **Feature name:** *(Preview) Source document and accounting distribution support for Landed Cost*

The *(Preview) Source document and accounting distribution support for Landed Cost* feature requires Supply Chain Management version 10.0.34 or later.
