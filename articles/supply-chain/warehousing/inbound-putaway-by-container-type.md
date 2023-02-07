---
title: Manage inbound putaway based on container types
description: This article describes how to use container types to drive the putaway process.
author: perlynne
ms.author: perlynne
ms.reviewer: kamaybac
ms.search.form: WHSContainerType, WHSAllowedContainerTypeGroup, WHSLocationProfile, WHSLocationLimit, WHSParameters, InventLocation, WHSUOMSeqGroupTable, WHSRFMenuItem, UnitOfMeasureLookup, UnitOfMeasureConversion 
ms.topic: how-to
ms.date: 12/12/2022
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Manage inbound putaway based on container types

[!include [banner](../../includes/banner.md)]

When you run warehouse receiving processes for various types of handling units (such as octabin pallets or Euro-pallets in different sizes), you can use container types to optimize the putaway process. Instead of using the item master's volumetric data to calculate the capacity of the putaway location, you can link each license plate registration to a container type that holds the physical dimension data. That data can then be used to select a valid putaway location.

## Set up container types

By associating a container type with a license plate, you can control storage policies based on that container type.

Follow these steps to set up a container type.

1. Go to **Warehouse management \> Setup \> Containers \> Container types**.
1. Follow one of these steps:

    - To create a new container type, select **New** on the Action Pane.
    - To edit an existing container type, select it in the list pane, and then select **Edit** on the Action Pane.

1. On the header of the new or selected record, set the following fields:

    - **Container type code** – Enter a unique name or identifier for the container type.
    - **Description** – Enter a short description of the container type.

1. On the **General** FastTab, set the following fields:

    - **Tare weight** – Enter the weight of the container when it's empty.
    - **Maximum net weight** – Enter the maximum weight of the container when it's packed.
    - **Container length**, **Container width**, **Container height**, and **Container volume** – Enter the physical dimensions of the container. These values are required for calculations of volumetric location loads, but they aren't required for calculations of [location stocking limits](#stocking-limits).
    - **Flexible volume dimensions** – Set this option to *Yes* if the volume depends on the container volume plus the inventory that's put into the container. Set it to *No* if the volume is considered fixed and doesn't depend on the inventory that's put into the container. This setting doesn't affect existing containerization processes.
    - **Unit** – Specify the handling unit for the container, such as *Euro-pallet* or *Octabin*. This unit applies to the container standard itself, not to its dimensions (such as height and length). If you'll configure your system to use this container type to calculate [location stocking limits](#stocking-limits), you must specify a unit here. When the system calculates location stocking limits, it can, as required, convert between the handling units that are used by different container types.
    - **Length**, **Width**, **Height**, and **Volume** (in the **Maximums** section) – Enter the maximum physical dimensions that the container can handle.
    - **Attributes** – You can define additional attributes for container types that are associated with other operations that use containers. For more information, see [Containerization](wave-containerization.md).

1. On the Action Pane, select **Save**.

## Define allowed container type groups

Use the **Allowed container type groups** page to prevent locations from holding some container types. To limit locations to specific container types, you must associate the records on this page with a location profile.

Follow these steps to set up an allowed container type group.

1. Go to **Warehouse management \> Setup \> Containers \> Allowed container type groups**.
1. Follow one of these steps:

    - To create a new container type, select **New** on the Action Pane.
    - To edit an existing container type, select it in the list pane, and then select **Edit** on the Action Pane.

1. On the header of the new or selected record, set the following fields:

    - **Allowed container type group name** – Enter a unique name or identifier for the group.
    - **Allow unspecified container types** – Set this option to *Yes* to allow license plates that aren't associated with a container type to be put into locations in this group. Set it to *No* if all license plates that are stored in locations in this group must be associated with a container type.

1. On the **Details** FastTab, specify the container types that can be put into locations in this group.

    - Use the **New** button to add rows to the grid and the **Delete** button to remove rows.
    - For each row, select a container type.

1. On the Action Pane, select **Save**.

## Assign container type groups to location profiles

By assigning a container type group to a location profile, you ensure that only license plates that meet the criteria of that group can be put into locations where the location profile applies. You can assign a container type group only to location profiles where license plate tracking is enabled.

Follow these steps to assign a container type group to a location profile.

1. Go to **Warehouse management \> Setup \> Warehouse \> Location profiles**.
1. Select the target profile in the list pane, and then select **Edit** on the Action Pane.
1. On the **General** FastTab, set the **Use license plate tracking** option to *Yes*.
1. In the **Allowed container type group** field, select the container type group that applies to the selected location profile.
1. On the Action Pane, select **Save**.

## <a name="stocking-limits"></a>Define location stocking limits based on container types

*Location stocking limits* let you limit the amount of inventory that the system will try to store at a given location when it generates putaway work. The limits can be based on individual products or product variants, or they can be based on container types. This section described how to set up stocking limits that are based on container types. For more information about other types of location stocking limits, see [Location stocking limits](location-stocking-limits.md).

When you set up location stocking limits that are based on container types, the system checks the number of each type of container that's already stored at a location to calculate whether there's room to add an incoming container there. During this calculation, the system can convert between different container types based on their handling units, provided that an applicable unit conversion is available (see the note later in this section).

When the system is looking for a location that has room to store an incoming container, it first evaluates the container type limits. If no matching container type constraints are found, it evaluates the settings at the product or variant level. To prevent the product-level settings from being used for a specific combination of a location profile and a container type, set up a container-based limit where the **Allow unlimited quantity** checkbox is selected.

Follow these steps to set up location stocking limits that are based on container types.

1. Go to **Warehouse management \> Setup \> Warehouse \> Location stocking limits**.
1. On the **Container types** tab, each row in the grid defines a stocking limit that's based on a warehouse, a location, and a container type. Use the **New** and **Delete** buttons on the toolbar to add and remove rows as required. For each row, set the following fields:

    - **Warehouse** – Select the warehouse where the stocking limit for the row applies.
    - **Location profile ID** – Select the location profile that's assigned to the locations where the row applies. You can select only location profiles that an allowed container type group is assigned to.
    - **Container type** – Select the container type that the current row applies to. You can select only container types that a unit is assigned to, and that belong to the allowed container type group that's assigned to the selected location profile ID.
    - **Allow unlimited quantity** – Use this checkbox to establish a stocking limit for the warehouse, location profile, and container type that are selected for this row.

        - *Selected* – The location can contain an unlimited number of the specified container type. In this case, the stocking limit settings on the **Products** and **Product variants** tabs aren't evaluated when the current row applies. 
        - *Cleared* – The location can hold only a limited number of containers of the selected type. For rows where this checkbox is cleared, you must specify the quantity that can be stocked in the location.

    - **Quantity** – If the **Allow unlimited quantity** checkbox is cleared, enter the quantity limit that applies to the current row. The read-only **Unit** field specifies the handling unit that applies to the quantity that you enter. The **Unit** value is based on the unit that's assigned to the selected container type. The system will convert between compatible handling units as required.

1. On the Action Pane, select **Save**.

> [!NOTE]
> Even though you can define only one unit in each location stocking limit, locations might be able to store more than one container type, depending on the unit conversion factors that are available. The system applies unit conversion to evaluate the related units.
>
> For example, you have the two handling units, *1-PL* and *1/2-PL*. Each is associated with a container type where the following [unit conversion](../pim/tasks/manage-unit-measure.md) is defined: *1-PL* = 2 &times; *1/2-PL*. In this case, it doesn't matter whether a row on the **Container types** tab of the **Location stocking limits** page is set up so that **Quantity** = *4* and **Unit** = *1/2-PL*, or **Quantity** = *2* and **Unit** = *1-PL*. In both cases, the row will allow the following combinations of location loads.
>
> | Number of 1/1-Pallets | Number of 1/2-Pallets | Maximum location load |
> |---|---|---|
> | 2 | 0 | Yes |
> | 1 | 0 | No |
> | 1 | 1 | No |
> | 1 | 2 | Yes |
> | 0 | 0 | No |
> | 0 | 1 | No |
> | 0 | 2 | No |
> | 0 | 3 | No |
> | 0 | 4 | Yes |

## Define how a default container type is assigned

The logic for assigning a container type to a license plate can be controlled through default values. You can assign a default container type at any of several levels in the system. The system then uses the following hierarchy, from most specific to most general. The most specific level where a default container type is defined will apply.

1. Existing license plate container type
1. Mobile device menu items
1. Unit sequence groups
1. Warehouse
1. Warehouse management parameters
1. (None)

### Assign a default container type at the global (Warehouse management parameters) level

The default container type that's assigned at the global level (that is, on the **Warehouse management parameters** page) will apply wherever no other default container type is assigned.

Follow these steps to define the default container type at the Warehouse management parameters level.

1. Go to **Warehouse management \> Setup \> Warehouse management parameters**.
1. On the **General** tab, on the **License plates** FastTab, in the **Default container type** field, assign a container type.
1. On the Action Pane, select **Save**.

### Assign a default container type to a warehouse

Follow these steps to define the default container type at the warehouse level.

1. Go to **Warehouse management \> Setup \> Warehouse \> Warehouses**.
1. Follow one of these steps:

    - To create a new warehouse, select **New** on the Action Pane.
    - To edit an existing warehouse, select it in the list pane, and then select **Edit** on the Action Pane.

1. On the **Warehouse** FastTab, in the **Inventory** section, in the **Default container type** field, assign a container type.
1. On the Action Pane, select **Save**.

### Assign default container types to units in unit sequence groups

*Unit sequence groups* establish a collection of units that an inventory item can be counted and stored by. For example, wine might be counted by the bottle, by the case (of 12 bottles), or by the pallet (of 84 cases). Each unit in a sequence is typically used for a different purpose, and a default container type can be assigned to each.

Follow these steps to define the default container type at the unit sequence groups level.

1. Go to **Warehouse management \> Setup \> Warehouse \> Unit sequence groups**.
1. Follow one of these steps:

    - To create a new group, select **New** on the Action Pane.
    - To edit an existing group, select it in the list pane, and then select **Edit** on the Action Pane.

1. On the **Line details** FastTab, either select the line where you want to assign a container type, or select **New** on the toolbar to create a new line.
1. In the **Default container type** field, assign a container type.
1. On the Action Pane, select **Save**.

### Assign default container types to mobile device menu items

When workers receive a shipment, they typically use the Warehouse Management mobile app to register the incoming inventory. To begin, they select a menu item that's configured to receive a specific combination of an item, a warehouse, and/or a location. Administrators can assign a default container type for each menu item, and can control whether warehouse workers can see and edit the container type.

Follow these steps to define the default container type at the mobile device menu item level.

1. Go to **Warehouse management \> Setup \> Containers \> Container types**.
1. Make a note of each **Container type code** value that you want to use as a default container type for your menu item. You'll need these codes later, and you'll have to enter them, as free text, exactly as they appear here. You won't be able to select them in a drop-down list.
1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. Follow one of these steps to select or create an inbound menu item. (An inbound menu item is a menu item that's designed to help workers register arriving inventory, as established by its **Work creation process** setting.)

    - To create a new inbound menu item, select **New** on the Action Pane.
    - To edit an existing inbound menu item, select it in the list pane, and then select **Edit** on the Action Pane.

1. On the **General** FastTab, set the following fields:

    - **Use default data** – Set this option to *Yes*. The **Default data** button then becomes available on the Action Pane. You'll use that button to define one or more default container types for the menu item.
    - **Display container type** – Set this option to *Yes* if you want the default container type to be shown (and editable) in the mobile app. Set it to *No* if you want the container type to be hidden (and therefore hardcoded to the applicable default container type).

1. On the Action Pane, select **Default data**.
1. On the **Default data** page, the grid has a row for each default setting that applies to the current menu item. You can set up as many default container types as you want, each for a different combination of a warehouse and a location. Alternatively, you can set up just one default container type that applies to all warehouses and locations. For each row where you want to set up a default container type, set the following fields:

    - **Default data field** – Select *Container type*.
    - **Warehouse** – Select the destination warehouse to use with this row. Leave this field blank to create a row that applies to all warehouses where a specific default container type isn't assigned.
    - **Location** – Select the destination location to use with this row. This field lists all the locations that are available for the selected warehouse. Leave this field blank to create a row that applies to all locations in the selected warehouse where a specific default container type isn't assigned.
    - **Hardcoded value** – Enter the **Container type code** value for the container type that you want to use as the default container type for this row. Use the exact value that you noted in step 1.

1. Continue to work on the **Default data** page until you've set up all the rows that you need for the current menu item.
1. On the Action Pane, select **Save**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
