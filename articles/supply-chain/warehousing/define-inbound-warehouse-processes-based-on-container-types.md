---
title: Define inbound warehouse processes based on container types
description: This article describes how to use container types to drive put-away processes.
author: perlynne
ms.date: 12/12/2022
ms.topic: business-process
ms.search.form: WHSContainerType, WHSAllowedContainerTypeGroup, WHSLocationProfile, WHSLocationLimit, WHSParameters, InventLocation, WHSUOMSeqGroupTable, WHSRFMenuItem,  UnitOfMeasureLookup, UnitOfMeasureConversion 
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: perlynne
ms.search.validFrom: 2022-12-01
ms.dyn365.ops.version: 10.0.32
---


# Define inbound warehouse processes based on container types
[!include [banner](../../includes/banner.md)]

When running warehouse receiving processes for different kind of handling units like octabin-pallets, euro-pallets in different sizes etc. you can optimize the put-away process by using container types.
In stead of using the item master volumetric data for the put-away location capacity calculations, each license plate registration can be linked to a container type holding the physical dimension data, which can be used to decide a valid put-away location.

## Create a container type
By associating a container type – with a license plate, you can control the storage policies, based on the container type.

1.  Go to **Warehouse management \> Setup \> Containers \> Container types**.
1.  If you are using volumetric location load calculation, be sure to enter the physical dimensions that are related to the container type. When **Flexible volume dimensions** is selected, the volume depends on the container volume plus the inventory that is put into the container. When **Flexible volume dimensions** is cleared, the volume is considered fixed and does not depend on the inventory that is put into the container. This setting does not affect existing containerization processes. If you are using **Location stocking limits**, use the **Unit** field. Unit conversions between container types can be used as a ratio to calculate storage capacity within locations.

## Define the allowed container type groups
If locations should be prevented from holding different kinds of container types, use the **Allowed container type groups** page.If you want to limit locations to specific container types, the records that are defined on this page must be associated with a location profile.

1.  Go to **Warehouse management \> Setup \> Containers \> Allowed container type groups**.
1.  If you select **Allow unspecified container types**, license plates that are not associated with a container type can be put into the locations.
1.  Under **Details**, click **New**, and then select the container types allowed for current group.

## Define a location profile
When you assign an allowed container type group to a location profile, license plates can be stored only if allowed container types are associated with them. You can enable this functionality only when **Use license plate tracking** is selected.

1.  Go to **Warehouse management \> Setup \> Warehouse \> Location profiles**.
1.  Having **Use license plate tracking** enabled as well makes editing possible in the **Allowed container type group** field to assign a container type group

## Define location stocking limits
As part of the location stocking limits functionality, the **Container types** option can be used to enable searches for available location capacity that is based on the number of license plates (container types). This includes the use of internal unit conversions between the various container types.

The **Container types** information is evaluated first, as part of the location stocking limits functionality. If no constraints are found, the settings at the product level are used. To prevent the product-level settings from being used, you can create a record where **Allow unlimited quantity** is selected. You cannot change the value in the **Unit** field. The default value is based on the unit that is assigned to the selected container type.

To create a new location stocking limit process around container types:
1.  Go to **Warehouse management \> Setup \> Warehouse \> Location stocking limits**.
2.  On the **Container types** tab, click **New** to create a record.
3.  In the **Warehouse** field, select the warehouse to define stocking limits for.
4.  Select a location profile ID. It will only be possible to select a location profile having a **Allowed container type group** assigned.
5.  Select the **Allow unlimited quantity** check box to indicate that the location quantity is unlimited. If this check box is cleared, you must specify the container type and quantity that can be stocked in the location.
6.  Assign a container type.
7.  The **Unit** field is updated automatically, based on the container type that you selected.
8.  In the **Quantity** field, enter the quantity for the stocking limit, based on the selected container type.

> [!NOTE]
> Depending on the existing unit conversions between the container type units, locations can store a greater variety of container types, but it will only be possible to define one of the units in the location stocking limits, the unit conversion will be used to handle the other related units.
> As a example for the two units *1-PL* and unit *1/2-PL*, each associated with a container type having the following [unit conversion](../pim/tasks/manage-unit-measure.md) definition between them: **1-PL = 2∙1/2-PL** - it does not matter if you define the **Quantity = 4** for the **Unit = 1/2-PL** or  **Quantity = 2** for the **Unit = 1-PL** in **Container types location stocking limits** to achieve the following resulting combinations of location loads.
>| Number of 1/1-Pallets | Number of ½-Pallets | Maximum location load |
>|-----------------------|---------------------|-----------------------|
>| 2                     | 0                   | Yes                   |
>| 1                     | 0                   | No                    |
>| 1                     | 1                   | No                    |
>| 1                     | 2                   | Yes                   |
>| 0                     | 0                   | No                    |
>| 0                     | 1                   | No                    |
>| 0                     | 2                   | No                    |
>| 0                     | 3                   | No                    |
>| 0                     | 4                   | Yes                   |

## Define how a default container type is assigned
The logic for assigning a container type to a license plate can be controlled through default values. The user can change the default values on the mobile device.

Conceptually, the defaulting starts from here: **Existing License plate container type \> Mobile device menu items \> Unit sequence groups \> Warehouse \> Warehouse management parameters** \> **\[Blank\]**

To define the default container type from the **Warehouse management parameters**, follow these steps:

1.  Go to **Warehouse management \> Setup \> Warehouse management parameters**.
2.  On the **General** tab, look up **License plates**.
3.  In the **Default container type** field, assign a container type.

To define the default container type from the **Warehouses**, follow these steps:

1.  Go to **Warehouse management \> Setup \> Warehouse \> Warehouses**
2.  Select or create a warehouse.
3.  Look up Warehouse management.
4.  In the **Inventory** field group, in the **Default container type** field, assign a container type.

To define the default container type from the **Unit sequence groups**, follow these steps:

1.  Go to **Warehouse management \> Setup \> Warehouse \> Unit sequence groups**
2.  Select or create a unit sequence group.
3.  Select or add line details.
4.  In the **Default container type** field, assign a container type.

To define the default container type from **Mobile device menu items**, follow these steps:

1.  Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**
2.  Select or create an inbound mobile device menu item.
3.  Select **Use default data**.
4.  Click **Default data**.
5.  Use the container type as part of the **Default data field** value, and assign a value in the **Hardcoded value** field.

## Define the container type display option on the mobile device pages
For each inbound mobile device menu item, you can control whether the container type should be shown. The association of the default container type with the license plate occurs even if the container type is not shown.

1.  Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**
2.  Select or create an inbound mobile device menu item.
3.  To show the container type as part of the mobile device page, select **Display container type** if available.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]