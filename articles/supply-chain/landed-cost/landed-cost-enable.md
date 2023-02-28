---
title: Turn on the Landed cost module for your system
description: This article describes how to turn the Landed cost module and its optional extra features on or off.
author: Weijiesa
ms.date: 09/24/2021
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

To use any part of the Landed cost module functionality, the *Landed cost* feature must be turned on for your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on as needed. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Transportation management*
- **Feature name:** *Landed cost*

The *Landed cost* feature requires Supply Chain Management version 10.0.17 or higher.

## Turn the shipping container batch mode feature on or off

[!INCLUDE [preview-banner-section](../../includes/preview-banner-section.md)]

If you'd like to be able to use batch mode when creating and updating shipping containers for Landed cost (optional), then you can also enable this feature for your system. Creating and updating shipping containers in background mode can provide better system performance when working with shipping containers that contain a large number of shipping lines.

Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on or off as needed. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Transportation management*
- **Feature name:** *(Preview) Enable shipping container creation and update in batch mode*

The *(Preview) Enable shipping container creation and update in batch mode* feature requires Supply Chain Management version 10.0.33 or higher.
