---
# required metadata

title: Configure Display older batches within warehouse on a mobile device
description: This topic describes how you set up your mobile device to diaplay a list of locations with older batches than the current location of a work line.
author: Mirzaab
manager: AnnBe
ms.date: 05/26/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  WHSRFMenuItem
audience: Application User
# ms.devlang: 
# ms.reviewer: bis
# ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 269384
ms.search.region: Global
# ms.search.industry: 
ms.author: mirzaab
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Configure Display older batches within warehouse on a mobile device

[!include[banner](../includes/banner.md)]

Using this configuration, a warehouse worker can show a list of locations with older batches than the current location of the work line. 
The list of locations that are displayed to warehouse workers includes information about the older batches in the location with the expiration date and the physical inventory of each batch. You can choose to pick from a new location or to continue picking from the current location. 
- Pick from a new location: If you click a new location to pick from, the  current work line will be updated to use the new location and work will continue as normal with the new location. For the new location to be valid, it must have enough available quantity for the whole work line. If the required quantity is not available, the work line will not be updated and you will be returned to the list. 
- Continue picking from the current location: If you click to continue with the current work line location, the quantities for the work line will continue to be picked from the original location.

## Where it applies
Display older batches within warehouse is configured on mobile device menu items and it effects the pick for batch below items.

## Set up Display older batches within warehouse
The configuration **Display older batches within warehouse** is available on mobile device menu items when the option **Pick oldest batch** is set to **Warn**.

- Under **Warehouse management** > **Setup** > **Mobile device** > **Mobile device menu items**, set the **Use existing work** to **Yes** for the menu item, and select **Warn** in the **Pick oldest batch** field. 

