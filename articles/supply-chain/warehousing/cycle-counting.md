---
title: Cycle counting
description: Learn how you can use cycle counting with the warehousing solution that's available in Warehouse management, including a step-by-step process.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form: WHSCycleCountPlan, WHSCycleCountPlanListPage, WHSCycleCountThreshold, WHSWorkTableListPage, SalesShipmentDeviation, WHSRFMenuItemCycleCount, WHSWorkLineCycleCount
ms.topic: how-to
ms.date: 11/19/2025
ms.custom:
  - bap-template
---

# Cycle counting

[!include [banner](../includes/banner.md)]

This article describes how you can use cycle counting with the warehousing solution that's available in Warehouse management. This article doesn't apply to the warehousing solution that's available in Inventory management.

Cycle counting is a warehouse process that you can use to audit on-hand inventory items. The cycle counting process involves three steps:

1. **Create cycle counting work** – You can automatically create cycle counting work based on threshold parameters for items or by using a cycle counting plan. Alternatively, you can manually create cycle counting work by using the item or warehouse parameters on the **Cycle count work by item** page or the **Cycle count work by location** page.
1. **Process the cycle count** – After creating cycle counting work, you count items in a warehouse location and use a mobile device to enter the result in Dynamics 365 Supply Chain Management. Alternatively, you can count items in a warehouse location without creating cycle counting work. This process is referred to as *spot cycle counting*.
1. **Resolve differences in the counted value** – After a cycle count, any items that have differences in the counted value have a work status of *Pending review* on the **All work** page. You can resolve these differences on the **Cycle count work pending review** page.

The following illustration shows the cycle counting process. ![Process flow for cycle counting.](./media/performcyclecountinginawarehouselocation.jpg)

## Cycle counting prerequisites

The following table shows the prerequisites that must be in place before you can use cycle counting.

| Prerequisite | Description |
|---|---|
| Item | The item must be enabled for warehouse management processes (WMS). |
| Warehouse | The warehouse must be enabled for warehouse management processes (WMS). To enable the warehouse for WMS, on the **Warehouses** page, select the warehouse, and then select the **Use warehouse management processes** option. To enable workers to move pallets during a cycle count, on the **Warehouse management** FastTab, select the **Allow pallet moves during cycle counting** option. |
| Work pools | Optional: Create a work pool to segregate the warehouse work, based on the type of work (in this case, cycle counting work). |
| Locations | Enable cycle counting for locations. To enable cycle counting for a warehouse location, on the **Location profiles** page, select the **Allow cycle counting** option. |
| Warehouse management parameters | Set up parameters for cycle counting. On the **Warehouse management parameters** page, specify the default adjustment type code, work class ID, and work priority for cycle counting. |
| Mobile device | <ul><li>Create a menu item for one of the following methods on the **Mobile device menu items** page:<ul><li>User directed cycle counting</li><li>System directed cycle counting</li><li>Cycle count grouping</li><li>Spot cycle counting</li></ul></li><li>Set up a menu for the mobile device.</li><li>Create a work user account, and assign a mobile device menu to the work user ID.</li></ul> |
| Related setup task | Set up a cycle counting plan for a warehouse location. |

## Automatically create cycle counting work

You can schedule recurring creation of cycle counting work by setting up cycle counting thresholds or cycle counting plans.

- A cycle counting threshold indicates the quantity or percentage limit of inventory items. The system automatically creates cycle counting work when the threshold limit is reached.
- A cycle counting plan creates cycle counting work either immediately or periodically through a batch job. When cycle counting work is created, the counting work line includes information about the location to count. The on-hand inventory that is associated with this location isn't blocked, and is therefore available for reservation and outbound processing, even though open counting work exists.

### Create cycle counting work based on threshold parameters for items

You can configure the system to create cycle counting work when the number of items falls below a specific threshold value in a location. For example, there are 60 items in a location that has a cycle counting threshold of 40. During a sales order transaction, a worker picks 25 items from the location and puts them in a staging location. Because the new item count, 35, is less than the threshold quantity, the system automatically creates cycle counting work for the location.

### Schedule cycle counting work

You can schedule cycle counting plans to create cycle counting work immediately or periodically. By setting up cycle counting plans, you can control the work pool that cycle counting work is created for, the maximum number of cycle counts that are created for items in different locations, and the number of days before a warehouse location is counted again. For example, an item is available in three locations in the warehouse, and the maximum number of cycle counts is set to *2*. In this case, when you run the cycle counting plan, two cycle counts are created for the two locations where the item is present. As another example, you set the number of days between cycle counts to *5*. In this case, cycle counting work is created every five days. However, if you process cycle counting work on day 3, the next cycle counting work is created five days after the last cycle counting was processed, on day 8.

## Create cycle counting work manually

To create cycle counting work manually, use the **Cycle count work by item** or **Cycle count work by location** page. You can specify the maximum number of cycle counts to create. For example, if the warehouse manager specifies a value of *5*, the system creates cycle counting work for five locations, even if the item is present in 10 locations. You can also select a work pool ID to assign to the cycle counting work IDs that the system creates. When you process a work pool ID for cycle counting, you process the cycle counting work IDs that are assigned to the work pool as a group.

> [!NOTE]
> When cycle counting work is created, it's always created for the whole location. This rule applies regardless of which method you use to create cycle counting work (for example, manual or automatic) or which query you use (the query is only used to select which locations to create cycle counting work for). That means that neither the item nor the tracking dimensions are set on the work line. The **Cycle counting transactions** page creates information about the specific item and tracking dimensions when a worker starts the counting process on a mobile device. The only exception is the *Partial location* cycle counting process, which supports counting based on item or product variant (learn more in [Define partial location cycle counting process](tasks/define-partial-location-cycle-counting-process.md)).

## Perform a cycle count by using a mobile device

The Warehouse Management mobile app provides the following methods for processing cycle counting work:

- **User directed** – The worker specifies a cycle counting work ID that has a status of *Open*.
- **System directed** – Supply Chain Management assigns a cycle counting work ID to the worker.
- **Cycle count grouping** – The worker groups cycle counting work IDs that are specific to a particular location, zone, or work pool.
- **Spot cycle counting** – The worker counts items in a warehouse location at any time, even if no open cycle counting work exists for that location. To initiate spot cycle counting in a location, the worker enters the location ID. If no open cycle counting work exists for that location, then the system creates a new work record for spot cycle counting. If open cycle counting work does exist for the location, then the existing work record is used for spot cycle counting.

The following example shows how you can perform spot cycle counting by using the Warehouse Management mobile app. The instructions that workers see on the device vary, depending on the setup of the menu item for spot cycle counting.

1. On the mobile device, select the menu item to process spot cycle counting work.
1. Register the location to perform spot cycle counting for.
1. Register and confirm the item number and the counted item quantity. The status of the cycle counting work is updated to either *Pending review* or *Closed* on the **All work** page, depending on the parameters that are set on the **Worker** page.
1. Repeat step 3 as needed to count the remaining items in the location, and confirm that no additional items are available for counting.

> [!NOTE]
>
> - Counting workflows in the mobile app provide an **Add LP or item** button, which lets workers count on-hand inventory that the system doesn't expect, though with a few limitations. For example, in license-plate controlled locations, you can only count each license plate once. As a result, when counting batch-tracked items, workers can only count one batch per license plate. Similarly, if a license plate contains multiple items, only one of those items can be counted.
> - If the unit sequence group for an item has multiple units enabled for cycle counting, workers are asked to provide a quantity for each unit and the system adds these quantities together. For example, if an item has a unit sequence group with *boxes* and *pieces*, then the worker is prompted to enter the number of boxes (for example, 2 boxes) and then the number of pieces (for example, 5 pieces). If the unit conversion between boxes and pieces is 10, the total counted quantity is 25 pieces. This design enables workers to count full boxes first and then any leftover pieces afterwards. If there are only full boxes, the worker should enter zero when asked for the number of pieces.
> - The system never shows the expected quantity to count. This design prevents intentional miscounts. To allow the user to double-check the count, use the **Number of attempts** setting on the mobile device menu item (select **Cycle counting** on the Action Pane). This setting allows a worker to repeat a count when necessary.
> - The **Skip** button shown during the *System directed* cycle counting mobile device flow doesn't just skip the item that is currently being counted. Instead, it skips the entire cycle counting work record and goes to the next available record. If no other cycle counting work record is available, the app stays on the current work record and shows an error message stating that no other work is available. This behavior is also true for the *Partial location* cycle counting flow, where the **Skip** button changes to the next available cycle counting work record. Because there can't be two *Open*, *In process*, or *Pending review* cycle counting work records for the same location, selecting the **Skip** button nearly always results in skipping counting at the current location and changing to the next one.
> - To prevent accidental selection, the **Cancel** button isn't shown during *cycle counting* mobile workflows.

## Resolve cycle counting differences

A cycle counting difference occurs in the following scenarios if the **Is a cycle count supervisor** option is set to *No* for a work user ID:

- The counted value isn't within the deviation limits specified in the **Maximum percentage limit** or **Maximum quantity limit** fields on the **Work users** page. For example, the on-hand inventory quantity in a location is *50*, and the deviation limit for the work user is *10*. If the worker enters a value that isn't between *40* and *60*, a difference occurs.
- The counted value differs from the on-hand inventory quantity, and no deviation limits are set.

You can adjust differences in the counted value and then accept the counted value on the **Cycle count pending review** page. You can verify the modified count of the item quantity on the **On hand by location** page. The counted value is rejected if you don't approve the difference.

## Related information

- [Set up mobile devices for warehouse work](configure-mobile-devices-warehouse.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
