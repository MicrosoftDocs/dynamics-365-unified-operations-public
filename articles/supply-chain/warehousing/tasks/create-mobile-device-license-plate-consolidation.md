---
title: Create a mobile device menu item for license plate consolidation
description: Learn how license plate consolidation merges the contents of one license plate into another, and how to create the mobile device menu item that warehouse workers use to run it.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ai-usage: ai-assisted
ms.search.form: WHSRFMenuItem, WHSRFMenu
ms.topic: how-to
ms.date: 10/29/2026
ms.custom:
  - bap-template
---

# Create a mobile device menu item for license plate consolidation

[!INCLUDE [banner](../../includes/banner.md)]

License plate consolidation lets a warehouse worker merge the contents of one license plate into another license plate in the same location. The work that's associated with the two license plates is then combined, so the remaining steps are performed once instead of twice.

For example, two picks for the same shipment both end at the same staging location, and both must go to the same dock. If the worker consolidates the two license plates at the staging location, only one move is required for the merged inventory. This behavior reduces the number of work transactions, the number of labels, and the amount of handling.

A warehouse manager typically creates the menu item. A warehouse worker then uses it on a mobile device.

## How license plate consolidation works

The worker scans the license plate to merge and then scans the target license plate. The system moves the on-hand inventory to the target license plate, transfers the open pick work to the target license plate's work, and cancels the origin work lines that are no longer required.

Consolidation is validated before it occurs. Both license plates must meet all the following conditions:

- They must be in the same location. Consolidation is currently supported only in staging locations.
- They must both be associated with work, and each must be set as the target license plate on that work.
- They must both have an open pick work line.
- Their work must have the same work order type.
- They must belong to the same load.
- Their shipments must have identical delivery information. In other words, the shipments must be for the same customer and the same delivery details.
- Their remaining work lines must match.
- Their related work must not be blocked.
- The license plate to merge must differ from the target license plate.

If any condition isn't met, the mobile device shows an error message that explains which condition failed, and the consolidation doesn't occur.

The following scenarios aren't currently supported:

- Consolidating license plates that have work lines that are part of a containerization flow.
- Consolidating packed containers.
- Reversing work that resulted from a consolidation.
- Reducing the picked quantity for load lines while the related consolidated work is incomplete.

## Prerequisites

Before you begin, make sure that the warehouse is enabled for warehouse management processes, and that the outbound flow creates the staging step where consolidation should occur. Learn more in [Warehouse handling of outbound loads for sales, transfer, and outbound shipment orders](../outbound-load-handling.md).

## Create the mobile device menu item

The menu item runs as an indirect activity, because consolidation isn't work that the system assigns to a worker. Instead, the worker starts it when two license plates can be merged. To create the menu item, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Mobile device** > **Mobile device menu items**.
1. On the Action Pane, select **New**.
1. On the header of the new record, set the following fields:
    - **Menu item name** – Enter a unique name to identify the menu item. For example, enter *Consolidate LP*.
    - **Title** – Enter the title that workers see on the mobile device menu. The title doesn't have to be unique.
    - **Mode** – Select *Indirect*.
    - **Activity code** – Select *Consolidate license plates*.

1. On the **General** FastTab, set the **Cancel remaining origin work lines** option. This option determines what happens when the origin license plate has work steps beyond the current pick or put step:
    - *Yes* – Those remaining work lines are canceled when the license plates are merged. This value is the default value, and it's the value that the standard demo data uses. Downstream lines for activities such as printing, or an extra pick and put pair that moves items to a staging area, are removed because the merged license plate no longer requires them.
    - *No* – Consolidation doesn't occur if any downstream work lines exist. Select this value when your work template generates lines that must be completed before consolidation, such as data capture, special packaging, or a quality assurance activity. The worker then receives a message that states that the license plate is associated with work that has additional steps, and that canceling those steps isn't allowed on the menu item.

    Regardless of this setting, consolidation always occurs at the last staging area before loading.

1. On the Action Pane, select **Save**.

## Add the menu item to a mobile device menu

Workers can't reach the new menu item until it belongs to a menu. To make it available, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Mobile device** > **Mobile device menu**.
1. Select the menu that the relevant workers use.
1. Select **Edit**.
1. Select the new menu item in the list of available menu items, and then select the arrow to move it into the menu structure.
1. On the Action Pane, select **Save**.

## Related information

- [Create and configure mobile device menu items](../configure-mobile-devices-warehouse.md)
- [License plate build on the warehouse app](../license-plate-build.md)
- [Set up a mobile device menu item for completing mixed license plates](../mobile-device-complete-mixed-lp-menu.md)
- [License plate receiving via the Warehouse Management mobile app](../warehousing-mobile-device-app-license-plate-receiving.md)
- [Warehouse handling of outbound loads for sales, transfer, and outbound shipment orders](../outbound-load-handling.md)
