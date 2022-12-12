---
title: Manage inbound putaway based on container types
description: This article describes how to use container types to drive the putaway process.
author: perlynne
ms.author: perlynne
ms.reviewer: kamaybac
ms.search.form: WHSContainerType, WHSAllowedContainerTypeGroup, WHSLocationProfile, WHSLocationLimit, WHSParameters, InventLocation, WHSUOMSeqGroupTable, WHSRFMenuItem,  UnitOfMeasureLookup, UnitOfMeasureConversion 
ms.topic: how-to
ms.date: 12/12/2022
ms.custom: bap-template
---

# Manage inbound putaway based on container types

[!include [banner](../../includes/banner.md)]

When running warehouse receiving processes for various kinds of handling units (such as octabin pallets or Euro-pallets in different sizes), you can optimize the putaway process by using container types. Instead of using the item master volumetric data for calculating the putaway location capacity, each license plate registration can be linked to a container type that holds the physical dimension data, which can then be used to choose a valid putaway location.

## Set up container types

By associating a container type with a license plate, you can control storage policies based on that container type. To set up a container type, follow these steps:

1. Go to **Warehouse management \> Setup \> Containers \> Container types**.
1. Do one of the following steps:
    - To create a new container type, select **New** on the Action Pane.
    - To edit an existing container type, select it on the list pane and then select **Edit** on the Action Pane.
1. Enter the following values in the header of your new or selected record:
    - **Container type code** – Enter a unique name or identifier for the container type.
    - **Description** – Enter a short description of the container type.
1. On the **General** FastTab, make the following settings:
    - **Tare weight** – Enter the weight of the container when it's empty.
    - **Maximum net weight** – Enter the maximum weight of the container when packed.
    - **Container length**, **Container width**, **Container height**, and **Container volume** – Enter the physical dimensions of the container. These values are required in order to make volumetric location load calculations, but aren't required for calculating [location stocking limits](#stocking-limits).
    - **Flexible volume dimensions** – Set to *Yes* if the volume depends on the container volume plus the inventory that is put into it. Set to *No* if the volume is considered fixed and doesn't depend on the inventory that is put into the container. This setting doesn't affect existing containerization processes.
    - **Unit** – Specify the handling unit for the container, such as *Euro-pallet* or *Octabin*. This unit applies to the container standard itself, not to its dimensions (such as height, length, and so on). If you'll configure your system to use this container type for calculating [location stocking limits](#stocking-limits), you must specify a unit here. If necessary, system is able to convert between handling units used by different container types when calculating location stocking limits.
    - In the **Maximums** section, in the **Length**, **Width**, **Height**, and **Volume** fields, enter the maximum physical dimensions that the container can handle.
    - **Attributes** – You can define additional attributes for container types that are associated with other operations that use containers. For more information, see [Containerization](wave-containerization.md).

1. Select **Save** on the Action Pane.

## Define allowed container type groups

Use the **Allowed container type groups** page to prevent locations from holding various kinds of container types. To limit locations to specific container types, the records that are defined on this page must be associated with a location profile. Follow these steps to set up an allowed container type group:

1. Go to **Warehouse management \> Setup \> Containers \> Allowed container type groups**.
1. Do one of the following steps:
    - To create a new container type, select **New** on the Action Pane.
    - To edit an existing container type, select it on the list pane and then select **Edit** on the Action Pane.
1. Enter the following values in the header of your new or selected record:
    - **Allowed container type group name** – Enter a unique name or identifier for the group.
    - **Allow unspecified container types** – Set to *Yes* to allow license plates that aren't associated with a container type to be put into locations in this group. Set to *No* to require all license plates stored in locations in this group to be associated with a container type.
1. On the **Details** FastTab, specify the container types that can be put into locations in this group.
    - Use the **New** and **Delete** buttons to add or remove rows in the grid.
    - For each row, select a **Container type**.
1. Select **Save** on the Action Pane.

## Assign container type groups to location profiles

Assign a container type group to a location profile to make sure that only license plates that meet the criteria of that group can be placed into locations where that location profile applies. You can only assign a container type group to location profiles where license plate tracking is enabled.

Follow these steps to assign a container type group to a location profile:

1. Go to **Warehouse management \> Setup \> Warehouse \> Location profiles**.
1. Select the target profile from the list pane and select **Edit** on the Action Pane.
1. On the **General** FastTab, set **Use license plate tracking** to *Yes*.
1. In the **Allowed container type group** field, select the container type group that applies to the selected location profile.
1. Select **Save** on the Action Pane.

## <a name="stocking-limits"></a>Define location stocking limits based on container types

*Location stocking limits* enable you to limit how much inventory the system will try to store at a given location when generating putaway work. You can set limits based on individual products or product variants, or based on container types. This section described how to set up stocking limits based on container types. For more information about other types of location stocking limits, see [Location stocking limits](location-stocking-limits.md).

When you set location stocking limits based on container types, the system checks the number of each type of container already stored at a location to decide whether there's room for an incoming container to be added there. During this calculation, the system can convert between different container types based on their respective handling units provided an applicable unit conversion is available (see the note later in this article).

When the system is looking for a location that has room to store an incoming container, it evaluates the container type limits first. If no matching container-type constraints are found, it evaluates the settings at the product or variant level instead. To prevent the product-level settings from being used for a given combination of location profile and container type, set up a container-based limit where the **Allow unlimited quantity** option is selected.

To set up location stocking limits based on container types:

1. Go to **Warehouse management \> Setup \> Warehouse \> Location stocking limits**.
1. Open the **Container types** tab.
1. Each row in the grid here establishes a stocking limit based on warehouse, location, and container type. Use the **New** and **Delete** buttons in the toolbar here to add or remove rows as needed. For each row, make the following settings:
    - **Warehouse** – Select the warehouse where the stocking limit for the row applies.
    - **Location profile ID** – Select the location profile assigned to the locations where the row applies. You can only select location profiles that have an **Allowed container type group** assigned.
    - **Container type** – Select the container type for which the current row applies. You can only select container types that have a **Unit** assigned and that belong to the **Allowed container type group** assigned to the selected  **Location profile ID**.
    - **Allow unlimited quantity** – Use this checkbox to control whether to establish a stocking limit for the warehouse, location profile, and container type selected for this row. Choose one of the following options:
        - *Cleared* – The location can only hold a limited number of containers of the selected type. For rows where this check box is cleared, you must specify the quantity that can be stocked in the location.
        - *Selected* – The location can contain an unlimited number of the specified container type. This will prevent the stocking limit settings on the **Products** and **Product variants** tabs from being evaluated where the current row applies.
    - **Quantity** – If the **Allow unlimited quantity** checkbox is cleared, then enter the limit that applies for the current row here (using the units shown in the **Unit** field).
    - **Unit** – Shows the handling unit that applies the **Quantity** limit set for the current row (if any). This value is read-only and is based on the unit that is assigned to the selected **Container type**. The system will convert between compatible handling units if necessary.
1. Select **Save** on the Action Pane.

> [!NOTE]
> Depending on the unit conversion factors available, locations may be able to store more than one container type even though you can only define one of the units in the location stocking limits. The system applies the unit conversion to evaluate the related units.
>
> For example, suppose you have the two handling units *1-PL* and *1/2-PL*, each associated with a container type that has the following [unit conversion](../pim/tasks/manage-unit-measure.md) defined: *1-PL = 2 × 1/2-PL*. In this case, it doesn't matter whether a row on the **Container types** tab of the **Location stocking limits** page is set with **Quantity** = *4* for **Unit** = *1/2-PL* or with **Quantity** = *2* for **Unit** = *1-PL*. In each case, the row will allow the following combinations of location loads.
>
>| Number of 1/1-Pallets | Number of 1/2-Pallets | Maximum location load |
>|---|---|---|
>| 2 | 0 | Yes |
>| 1 | 0 | No |
>| 1 | 1 | No |
>| 1 | 2 | Yes |
>| 0 | 0 | No |
>| 0 | 1 | No |
>| 0 | 2 | No |
>| 0 | 3 | No |
>| 0 | 4 | Yes |

## Define how a default container type is assigned

The logic for assigning a container type to a license plate can be controlled through default values. You can assign a default container type at any of several levels in the system, which uses the following hierarchy (from most specific to most general). The most specific level where a default container type is defined will apply.

1. Existing license plate container type
1. Mobile device menu items
1. Unit sequence groups
1. Warehouse
1. Warehouse management parameters
1. (None)

### Assign a default container type at the global (warehouse management parameters) level

The default container type assigned using the **Warehouse management parameters** page will apply everywhere where no other default is assigned. To define the default container type at the **Warehouse management parameters** level, follow these steps:

1. Go to **Warehouse management \> Setup \> Warehouse management parameters**.
1. Open the **General** tab.
1. Expand the **License plates** FastTab.
1. In the **Default container type** field, assign a container type.
1. Select **Save** on the Action Pane.

### Assign a default container type to a warehouse

To define the default container type at the **Warehouses** level, follow these steps:

1. Go to **Warehouse management \> Setup \> Warehouse \> Warehouses**.
1. Do one of the following steps:
    - To create a new warehouse, select **New** on the Action Pane.
    - To edit an existing warehouse, select it on the list pane and then select **Edit** on the Action Pane.
1. Expand the **Warehouse** FastTab.
1. In the **Inventory** field group, in the **Default container type** field, assign a container type.
1. Select **Save** on the Action Pane.

### Assign default container types to units in unit sequence groups

*Unit sequence groups* establish a collection of units by which an inventory item can be counted and stored. For example, wine might be counted by the bottle, by the case (of 12 bottles), or by the pallet (of 84 cases). Each unit in a sequence is typically used for a different purpose, and each can be assigned a default container type. To define the default container type at the **Unit sequence groups** level, follow these steps:

1. Go to **Warehouse management \> Setup \> Warehouse \> Unit sequence groups**.
1. Do one of the following steps:
    - To create a new group, select **New** on the Action Pane.
    - To edit an existing group, select it on the list pane and then select **Edit** on the Action Pane.
1. On the **Line details** FastTab, either select the line where you want to assign a container type or select **New** from the toolbar to create a new one.
1. In the **Default container type** field, assign a container type.
1. Select **Save** on the Action Pane.

### Assign default container types to mobile device menu items

When receiving a shipment, workers will typically use the Warehouse Management mobile app to register the incoming inventory, and start by selecting a menu item configured to receive a certain combination of item, warehouse, and/or location. Administrators can assign a default container type for each menu item, and control whether or not warehouse workers can see and edit the container type. To define the default container type at the **Mobile device menu items** level, follow these steps:

1. Go to **Warehouse management \> Setup \> Containers \> Container types** and make a note of each **Container type code** value that you'll want to use as a default container type for your menu item. You'll need these codes later, and you'll need to enter the exact values as free text (rather than select from a drop-down list).
1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. Do one of the following steps to select or create an inbound menu item. (An inbound menu item is a menu item designed to help workers register arriving inventory, as established by its **Work creation process** setting.)
    - To create a new inbound menu item, select **New** on the Action Pane.
    - To edit an existing inbound menu item, select it on the list pane and then select **Edit** on the Action Pane.
1. On the **General** FastTab, make the following settings:
    - **Use default data** – Set to *Yes*. This setting enables the **Default data** button on the Action Pane, which you'll use to establish one or more default container types for this menu item.
    - **Display container type** – If you want the default container type to be shown (and editable) in the mobile app, then set this to *Yes*. If you want the container type to be hidden (and therefore hardcoded to the applicable default), then set this option to *No*.
1. On the Action Pane, select **Default data**.
1. The **Default data** page opens. The grid here shows a row for each default setting that applies for the current menu item. You can set up as many default container types as you want, each for a different combination of warehouse and location. Or set up just one default that applies to all warehouses and locations. For each row where you want to set up a default container type, make the following settings:
    - **Default data field** – Select *Container type*.
    - **Warehouse:** Select the destination warehouse to use with this row. Leave this field blank to create a row that applies for all warehouses where a specific default container type isn't assigned.
    - **Location:** This field lists all the locations that are available for the selected warehouse. Select the destination location to use with this row. Leave this field blank to create a row that applies for all locations in the selected warehouse where a specific default container type isn't assigned.
    - **Hardcoded value:** Enter the **Container type code** for the container type to use as the default for this row. Use the exact value that you noted in step 1.
1. Continue working on the **Default data** page until you have set up all the rows you need for the current menu item.
1. Select **Save** on the Action Pane.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]