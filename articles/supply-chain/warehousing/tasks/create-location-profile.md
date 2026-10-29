---
title: Create a location profile
description: Learn how to create and configure location profiles in Dynamics 365 Supply Chain Management. Includes a field reference for all location profile settings and common configuration examples.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ai-usage: ai-assisted
ms.search.form: WHSLocationProfile
ms.topic: how-to
ms.date: 10/29/2026
ms.custom:
  - bap-template
---

# Create a location profile

[!INCLUDE [banner](../../includes/banner.md)]

Assign a location profile to every warehouse location. The location profile defines the properties and rules for that location, such as whether the location allows mixed items, which inventory dimensions it tracks, and how it participates in replenishment. Locations that share the same profile follow the same rules.

Location profiles are a key part of warehouse configuration. Set them up when you first configure a warehouse, and then assign each one to the locations that should follow its rules. Learn more in [Warehouse configuration overview](../warehouse-configuration.md).

## Create a location profile

To create a new location profile, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Warehouse** > **Location profiles**.
1. On the Action Pane, select **New**.
1. In the **Location profile ID** field, enter a unique identifier for the profile (for example, *BULK* or *PICK-01*).
1. In the **Name** field, enter a descriptive name (for example, *Bulk storage* or *Picking zone floor 1*).
1. On the **General** FastTab, configure the location format, location type, and mixing and tracking rules that control what you can store at locations that use this profile. For details about each field, see the [General FastTab](#general-fasttab) section.
1. If you set **Enable location product dimension specific mixing** to *Yes* on the **General** FastTab, use the **Allowed product dimension mixing** FastTab to specify which product dimensions (such as size, color, or style) can be mixed at the same location. For details, see the [Allowed product dimension mixing FastTab](#allowed-product-dimension-mixing-fasttab) section.
1. On the **Dimensions** FastTab, define the physical storage capacity of locations that use this profile, including the volumetric method and dimensions. For details, see the [Dimensions FastTab](#dimensions-fasttab) section.
1. On the **Replenishment** FastTab, control whether replenishment can exceed the location's stocking capacity. For details, see the [Replenishment FastTab](#replenishment-fasttab) section.
1. On the Action Pane, select **Save**.

## General FastTab

The **General** FastTab defines the core behavior of locations that use this profile. The following fields are available:

- **Location format** – Select the location format that defines the naming structure for this location. Location formats define the segments used in location names, such as aisle, rack, shelf, and bin. Set up location formats on the **Location formats** page (**Warehouse management** > **Setup** > **Warehouse** > **Location formats**).
- **Location type** – Select the location type. Location types group locations that serve a similar purpose in the warehouse, such as staging, picking, bulk storage, or bay doors. Some types are used by system processes. For example, the staging and final shipping location types are defined on the **Warehouse management parameters** page.
- **Dock management profile ID** – Select the dock management profile to use for this location. The profile defines which inventory types can't be mixed at the location. This field is relevant for receiving locations, where inbound loads are managed at dock doors.
- **Use license plate tracking** – Set to *Yes* to require that every inventory movement to or from this location is associated with a license plate. This option is required for locations that participate in warehouse management processes (WMS). When enabled, items must be placed on a license plate before they can be stored at the location.
- **Allow negative inventory** – Set to *Yes* to allow negative on-hand inventory at the location. Enable this option when you need to allow inventory to be picked from a location even when the system shows zero on-hand. This option isn't available for locations that use license plate tracking.
- **Allow mixed items** – Set to *Yes* to allow different item numbers to be stored at the same location. When set to *No*, each location can hold only one item number at a time. If you enable this option, you must also enable **Allow mixed inventory batches**.
- **Enable location product dimension specific mixing** – Set to *Yes* to allow product variants, such as different sizes, colors, or configurations, to be mixed at the same location. When you enable this option, you must also configure the **Allowed product dimension mixing** FastTab to specify which dimensions can be mixed. This option is only available when **Allow mixed items** is set to *No*. Learn more in [Location product dimension mixing](../location-product-dimension-mixing.md).
- **Allow mixed inventory statuses** – Set to *Yes* to allow items that have different inventory statuses, such as *Available* and *Blocked*, to be stored at the same location. If this option is disabled, you must move goods to another empty location before you can change their inventory status.
- **Allow mixed inventory batches** – Set to *Yes* to allow items from different inventory batches to be stored at the same location.
- **Prevent multiple owners** – Set to *Yes* to prevent items that are owned by different owners from being stored at the same location. This option is relevant for warehouses that manage consignment inventory or inventory owned by multiple parties. Learn more in [Prevent multiple owners at a warehouse location](../prevent-multiple-owners-locations.md).
- **Allow cycle counting** – Set to *Yes* to allow cycle counting processes to include this location. Cycle counting is a warehouse process that verifies on-hand inventory quantities. Consider setting this option to *No* for receiving and staging areas, where inventory is held only temporarily while it waits to be picked up. Learn more in [Cycle counting](../cycle-counting.md).
- **Generate check digit** – Set to *Yes* to automatically generate a check digit for the locations that use this profile. Workers scan or enter the check digit to confirm that they're at the correct location during mobile device transactions.
- **Override rules for batch days** – Set to *Yes* to allow mixing of inventory batches whose expiration dates differ by more than the number of days normally allowed by the batch-days rules.
- **Allowed container type group** – Select the container type group that limits which container types can be stored at this location. When a group is assigned, a license plate can be stored only if its container type is allowed. Define the allowed container types on the **Allowed container types** page. This field is available only when **Use license plate tracking** is set to *Yes*. Leave the field blank to allow all container types.
- **Enable item in location** – Set to *Yes* to enable the system to track which items have been placed in this type of location. This information can be used to optimize directed put-away.
- **Enable location activity date and time** – Set to *Yes* to have the system track when inventory was last moved to or from this location. This information can be used to sort locations by activity level.
- **Enable location status** – Set to *Yes* to enable location status tracking. When enabled, the system maintains the **Location status** and **Aging date** fields on the location, and you can change a location's status, such as to block it for new put-away. Learn more in [Warehouse location status](../warehouse-location-status.md).
- **Enable license plate positioning** – Set to *Yes* to allow license plates to be assigned a specific position within the location, such as position 1 or position 2. This feature is useful for locations that hold multiple pallets. Learn more in [Location license plate positioning](../location-license-plate-positioning.md).
- **Display mobile device LP position** – Set to *Yes* to show the license plate position to workers on their mobile device during adjustment-in and counting operations.

## Allowed product dimension mixing FastTab

The **Allowed product dimension mixing** FastTab is available when the **Enable location product dimension specific mixing** option on the **General** FastTab is set to *Yes*. Use it to define which product dimensions, such as **Size**, **Color**, **Style**, and **Configuration**, can be mixed at the same location. Learn more in [Location product dimension mixing](../location-product-dimension-mixing.md).

## Dimensions FastTab

The **Dimensions** FastTab defines physical capacity settings for locations that use this profile. The following fields are available:

- **Storage unit** – Select the unit of measure used to calculate the storage capacity of the location (for example, *PL* for pallet or *Box*).
- **Volumetric method used for inventory location** – Select the method used to calculate how much space is available at the location. Options include *Usable dimensions* (which calculates available space based on the physical dimensions of the location) and *Use location volume* (which uses a fixed volume value).
- **Usable location height**, **Usable location width**, **Usable location depth** – Enter the physical dimensions of the location. These values are used when the volumetric method is set to *Usable dimensions*.
- **Usable location volume** – Enter the total usable volume of the location. This value is used when the volumetric method is set to *Use location volume*.

## Replenishment FastTab

The **Replenishment** FastTab controls how replenishment interacts with locations that use this profile. The following fields are available:

- **Exceed location capacity** – Set to *Yes* to allow replenishment processes to place inventory at the location even when the location is already at its maximum stocking capacity. When you enable this option, the other fields on this FastTab become available. Learn more in [Replenishment over location capacity](../replenishment-over-location-capacity.md).
- **Work availability threshold type** – Select the method used to determine when extra replenishment work should be released to the location. This field is only available when **Exceed location capacity** is set to *Yes*. Options include:
    - *Quantity* – Release extra replenishment work based on a specific quantity value. When selected, the **Overflow quantity** and **Overflow unit** fields become available. Use this option when locations don't use volumetrics or when you have consistent replenishment quantities.
    - *Percent* – Release extra replenishment work based on a percentage of the location's capacity (from stocking limits or volumetrics). When selected, the **Overflow percentage** field becomes available. Use this option when picking locations use volumetrics.
- **Overflow quantity** – Enter the quantity at which the location overflows. When the sum of on-hand quantity and work quantity is below this value, extra replenishment work is released. Any replenishment work above this value is blocked. This field is only available when **Work availability threshold type** is set to *Quantity*.
- **Overflow unit** – Select the unit of measure associated with the overflow quantity (for example, *PL* for pallet). This field is only available when **Work availability threshold type** is set to *Quantity*.
- **Overflow percentage** – Enter the percentage of location capacity at which extra replenishment work is released. This field is only available when **Work availability threshold type** is set to *Percent*.

## Common location profile configurations

The following examples show typical configurations for common warehouse zones. Use these examples as starting points and adjust them based on your warehouse requirements.

### Bulk storage

Bulk storage locations hold large quantities of goods on pallets. Items are typically stored and retrieved by pallet, and multiple items or batches often share the same zone.

- **Use license plate tracking** – *Yes*
- **Allow mixed items** – *Yes*
- **Allow mixed inventory batches** – *Yes*
- **Allow mixed inventory statuses** – *Yes*
- **Allow cycle counting** – *Yes*
- **Exceed location capacity** – *No*

### Picking locations

Picking locations are forward-pick positions where workers pick individual items to fill orders. These locations are typically replenished from bulk storage.

- **Use license plate tracking** – *Yes*
- **Allow mixed items** – *No*
- **Allow mixed inventory batches** – *Yes*
- **Allow cycle counting** – *Yes*
- **Exceed location capacity** – *Yes* (with overflow quantity configured to control replenishment flow)

### Receiving (bay door)

Receiving locations represent inbound dock doors where goods arrive. They need maximum flexibility because arriving loads might contain any mix of items and statuses.

- **Use license plate tracking** – *Yes*
- **Allow mixed items** – *Yes*
- **Allow mixed inventory batches** – *Yes*
- **Allow mixed inventory statuses** – *Yes*
- **Dock management profile ID** – Set to the appropriate dock profile

### Staging

Staging locations are temporary holding areas used during outbound processing. Goods are moved here before loading onto transport.

- **Use license plate tracking** – *Yes*
- **Allow mixed items** – *Yes*
- **Allow mixed inventory batches** – *Yes*
- **Allow mixed inventory statuses** – *No*

## Related information

- [Warehouse configuration overview](../warehouse-configuration.md)
- [Location product dimension mixing](../location-product-dimension-mixing.md)
- [Location stocking limits](../location-stocking-limits.md)
- [Warehouse location status](../warehouse-location-status.md)
- [Cycle counting](../cycle-counting.md)
