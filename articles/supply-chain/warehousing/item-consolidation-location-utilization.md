---
# required metadata

title: Item consolidation - location utilization
description: This article provides information about functionality that makes it easy for warehouse managers to view and filter the volumetric utilization of locations across the warehouse. Managers can select locations and create inventory movement work directly from the Item Consolidation page to consolidate items and therefore make better use of warehouse space.
author: Mirzaab
ms.date: 08/09/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
ms.search.form: WHSPhysDimUOM, WHSMovementType, WHSItemConsolidationForm, WHSRFMenu, WHSRFMenuItem
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2020-07-16
ms.dyn365.ops.version: 10.0.7
---

# Item consolidation - location utilization

[!include [banner](../includes/banner.md)]

This article provides information about functionality that makes it easy for warehouse managers to view and filter the volumetric utilization of locations across the warehouse. Managers can select locations and create inventory movement work directly from the **Item Consolidation** page to consolidate items and therefore make better use of warehouse space.

## Turn on the features

Before you can use the features that are described in this article, you must turn them on in your system. Admins can use the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace to check the status of the features and turn them on if they are required. Turn on both the following features, in the order that they are listed in. (Both features are for the **Warehouse management** module.)

1. *Warehouse location status*<br>(As of Supply Chain Management version 10.0.29, this feature is mandatory and can't be turned off. For more information, see [Warehouse location status](warehouse-location-status.md).)
2. *Item consolidation location utilization*<br>(As of Supply Chain Management version 10.0.29, this feature is turned on by default. As of Supply Chain Management version 10.0.32, it's mandatory and can't be turned off.)

## Warehouse location status

The *Warehouse location status* feature adds four new fields to the **Locations** page to track additional information about the current state of the location:

- **Item number** – The item that is currently in the location. If the location contains multiple items, this field will be blank.
- **Last activity date and time** – The timestamp of the last warehouse transaction that was performed against the location.
- **Aging date** – The date when the inventory in the location was brought into the warehouse. This date is calculated based on the license plate aging date. Although this date is accurate for license plate–tracked locations, it might not be accurate for locations that aren't license plate–tracked.
- **Location status** – The status of the location. Four values are available:

    - **Undetermined** – The location profile doesn't track status. Therefore, the current status is unknown.
    - **Empty** – No inventory is currently in the location.
    - **Picking** – Outbound transactions have been performed against the location after it was last empty.
    - **Storage** – Only inbound transactions have been performed since the location was last empty.

These fields let warehouse managers get a better overview of the status of the locations in the warehouse. They also allow for more advanced reporting and filtering.

## Set up item consolidation and location utilization

This section describes how to prepare your system to use item consolidation and location utilization. The procedures use sample values from the standard demo data. If you plan to work through the example scenario that is provided later in this article, select the **USMF** legal entity (which contains the standard demo data), and create each record that is described in this section. If you don't plan to work through the example scenario, the values that are provided here can be considered examples of the types of setup that you must complete to use the features.

### Released product

1. Go to **Product information management \> Products \> Released products**.
1. In the **Item number** field, select *M9201*, and open the details page.
1. On the Action Pane, on the **Manage inventory** tab, in the **Warehouse** group, select **Physical dimensions**.
1. On the **Physical dimension** page, on the Action Pane, select **New**.

    A new line is added to the grid. The **Item number** field is preset.

1. In the **Unit** field, select *ea*. The remaining fields on the line are automatically set.
1. Select **Save**, and close the page.

### Location profile

1. Go to **Warehouse management \> Setup \> Warehouse \> Location profiles**.
1. In the list of location profiles, select **FLOOR-05**.
1. On the Action Pane, select **Edit**.
1. On the **General** FastTab, make sure that both the following options are set to *Yes*:

    - Enable item in location
    - Enable location status

1. Select **Save**.

    > [!IMPORTANT]
    > If the **Enable item in location** and **Enable location status** options were already set to *Yes*, skip ahead to the instructions for setting up the **Dimensions** FastTab in step 10. If the options weren't already set to *Yes*, you must run a consistency check for the **Warehouse management** module after you manually set them. In this case, continue to the next step.

1. To run the consistency check, go to **System administration \> Periodic tasks \> Database \> Consistency check**.
1. In the **Consistency check** dialog box, set the following values:

    - **Module:** *Warehouse management*
    - **Check/Fix:** *Check*
    - **From date:** Leave this field blank.
    - **Warehouse location status consistency check:** Select this check box.

1. Select **OK**.

    > [!TIP]
    > When the consistency check is completed, you receive a notification. Open the [Action Center](../../fin-ops-core/fin-ops/get-started/user-interface-elements.md#notifications) to view the message. Select **Message details** to view the details.
    >
    > If the message for the consistency check states, "Incorrect location status information found for location XXXX in warehouse XX," you must run the consistency check again. This time, set the **Check/Fix** field to *Fix error*. View the messages to make sure that no errors were found.

1. You must now finish setting up the location profile. Go back to **Warehouse management \> Setup \> Warehouse \> Location profiles**, select location profile **FLOOR-05**, and then, on the Action Pane, select **Edit**.
1. On the **Dimensions** FastTab, set the following values:

    - **Volume utilization percentage:** *100*
    - **Volumetric method used for inventory location:** *Use location volume*
    - **Actual location height:** *10*
    - **Actual location width:** *10*
    - **Actual location depth:** *10*
    - **Maximum weight:** *100*

1. Select **Save**.

### Mobile device menu items

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. On the Action Pane, select **New** to create a menu item for sorting.
1. In the header, set the following values:

    - **Menu item name:** *Adjust In*
    - **Title:** *Adjust In*
    - **Mode:** *Work*
    - **Use existing work:** *No*

1. On the **General** FastTab, set the following values:

    - **Work creation process:** *Adjustment in*
    - **Inventory adjustment types:** *Adjust in*

1. Select **Save**.

### Mobile device menu

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu**.
1. In the list of menus, select **Inventory**.
1. On the Action Pane, select **Edit**.
1. In the **Available Menus And Menu Items** list, find and select the **Adjust In** menu item.
1. Select the right arrow button to move **Adjust In** to the **Menu Structure** list. In this way, you add the new menu item to the selected menu.
1. Select **Save**.

### Movement types

1. Go to **Warehouse management \> Setup \> Inventory \> Movement types**.
1. On the Action Pane, select **New**, and then set the following values:

    - **Movement type code:** *CONSOLIDATE*
    - **Description:** *Consolidate locations*
    - **Work class ID:** *InvMov*

1. Select **Save**.

## Example scenario

The following scenario uses the Warehouse Management mobile app to make an inventory *adjustment in* to two locations in the warehouse.

### Add inventory to locations

1. Sign in to the mobile device as a user who is set up for warehouse *51*.
1. Go to **Inventory \> Adjust In**.

    You will now enter the first location adjustment.

1. In the **Adjustment in** task, select the location to make the inventory adjustment for. In the **LOC** field, select *LP-001*.
1. Confirm the location.
1. Create a license plate ID for the item that will be added to the location. In the **LP** field, enter *LP00101*.
1. Confirm the license plate.
1. Enter the item that will be added to the license plate. In the **ITEM** field, enter *M9201*.
1. Confirm the item.
1. Enter the quantity of the item that will be added. In the **QTY** field, enter *10*.
1. Confirm the quantity.

    You receive a "Work Completed" message. You will now enter the second location adjustment.

1. In the **Adjustment in** task, select the location to make the inventory adjustment for. In the **LOC** field, select *LP-002*.
1. Confirm the location.
1. Create a license plate ID for the item that will be added to the location. In the **LP** field, enter *LP00201*.
1. Confirm the license plate.
1. Enter the item that will be added to the license plate. In the **ITEM** field, enter *M9201*.
1. Confirm the item.
1. Enter the quantity of the item that will be added. In the **QTY** field, enter *15*.
1. Confirm the quantity.

    You receive a "Work Completed" message.

1. Select the Menu button (sometimes referred to as the hamburger or the hamburger button), and then select **Cancel** to exit the **Adjustment in** task.

### Consolidate locations

1. Go to **Warehouse management \> Periodic tasks \> Item consolidation**.
1. In the header, select a warehouse to do the consolidation for. In the **Warehouse** field, enter *51*.

    A record is shown for each location where item *M9201* was adjusted. The **Utilization percentage** column shows the volumetric utilization of each location.

1. To consolidate inventory, select all the locations that must be consolidated, and then, on the Action Pane, select **Consolidate Inventory**.
1. In the **Consolidate inventory** dialog box, specify the location and movement type that should be used to create the work for inventory movement. Set the following values:

    - **Location:** *LP-001*
    - **Movement type code:** *CONSOLIDATE*

1. Select **OK**.
1. You receive an informational message that shows the movement work that was created. Make a note of the movement work ID.

### View movement work

1. Go to **Warehouse management \> Work \> Work details**.
1. View the work that was created. Use the movement work ID from the inventory consolidation to filter or search the work grid.

    In this scenario, an existing location that had inventory was used as the inventory consolidation location. Therefore, only one work ID was created.

    > [!NOTE]
   > The system creates one work ID for each move that must be completed. If you specify a location that already contains inventory, only one work ID is created. If you specify a new location, two work IDs are created.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
