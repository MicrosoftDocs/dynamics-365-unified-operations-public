---
title: Configure Display older batches within warehouse on a mobile device
description: Learn how to set up a mobile device to display a list of locations with batches older than the current location of a work line.
author: Mirzaab
ms.author: mirzaab
ms.topic: article
ms.date: 05/26/2017
ms.reviewer: kamaybac
ms.search.form:  WHSRFMenuItem
---

# Configure Display older batches within warehouse on a mobile device

[!include [banner](../includes/banner.md)]

The **Display older batches within warehouse** configuration lets you display a list of locations with batches older than the current location of the work line. The list of locations that are displayed includes information about the older batches in the location with the expiration date and the physical inventory of each batch. You can choose to pick from a new location or to continue picking from the current location. 
- Pick from a new location - If you select a new location to pick from, the  current work line will be updated to use the new location and work will continue as usual with the new location. For the new location to be valid, it must have enough available quantity for the whole work line. If the required quantity is not available, the work line will not be updated, and the list will display. 
- Continue picking from the current location - If you continue with the current work line location, the quantities for the work line will continue to be picked from the original location.

## Where it applies
Display older batches within warehouse is configured on mobile device menu items and affects the pick for batch below items.

## Set up Display older batches within warehouse
The **Display older batches within warehouse** configuration is available on mobile device menu items when the **Pick oldest batch** option is set to **Warn**.

- Under **Warehouse management** > **Setup** > **Mobile device** > **Mobile device menu items**, set **Use existing work** to **Yes** for the menu item, and select **Warn** in the **Pick oldest batch** field. 



[!INCLUDE[footer-include](../../includes/footer-banner.md)]