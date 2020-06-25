---
# required metadata

title: Item consolidation - location utilization
description: This feature makes it easy for warehouse managers to view and filter the volumetric utilization of location across the warehouse. Mangers can select locations and create inventory movement work straight from the page to consolidate items and therefore make better use of warehouse space.
author: Mirzaab
manager: tfehr
ms.date: 06/25/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2020-06-25
ms.dyn365.ops.version: Release 10.0.9
---

# Item consolidation - location utilization

This feature makes it easy for warehouse managers to view and filter the volumetric utilization of location across the warehouse. Mangers can select locations and create inventory movement work straight from the page to consolidate items and therefore make better use of warehouse space.

## Enable the features

Before you can use the features described in this topic, you must enable them on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable it if needed. Enable the following two features (both from the *Warehouse management* module), in order:

1. *Warehouse location status*
2. *Item consolidation location utilization*

## Warehouse location status

The *Warehouse location status* feature adds four new fields to the **Locations** page to track additional information about the current state of the location:

- **Item number** - Item that is currently in the location. If the location contains multiple items, this field will be blank.

- **Last activity date and time** - Timestamp of the last warehouse transaction that was performed against the location

- **Aging date** - The date the inventory in the location was brought into the warehouse. It is calculated based on the license plate aging date. Accurate for license plate tracked locations, but not guaranteed to be accurate for non license plate tracked locations.

- **Location status** - Provides four options:
  - **Undetermined**: Location profile does not track status. Current status unknown
  - **Empty**: No inventory currently in the location
  - **Picking**: Outbound transactions have been performed against the location after it was last empty
  - **Storage**: Only inbound transactions have been performed since the location was last empty

These fields allow warehouse managers to get a better overview of the status of the locations in the warehouse and enable more advanced reporting and filtering.

## Set up item consolidation and location utilization

This section describes how to prepare your system to make use of item consolidation and location utilization. The procedures provided here use sample values that come from the standard demo data. If you plan to run the example scenario provided later in this topic, then select the **USMF** legal entity (which contains the standard demo data) and create each record described in this section. If you won't run the example scenario, then just consider the values provided here to be examples of the types of setup required to use these features.

### Released product

1. Go to **Product information management > Products > Released products**.
1. Select **Item number** - *M9201* and open the details page.
1. On the Action Pane, open the **Manage inventory** tab and, in the **Warehouse** group, select **Physical dimensions**.
1. The **Physical dimension** page opens. Select **New** on the Action Pane.
1. A new line is added to the grid. The **Item number** field is pre-populated.
1. In the **Unit** field, select *ea*. The rest of the fields on the line will auto populate.
1. Select **Save** and close the page.

### Location profile

1. Go to **Warehouse management > Setup >  Warehouse > Location profiles**.
1. Select **FLOOR-05** from the list of location profiles.
1. Select **Edit** on the Action Pane.
1. In the **General** FastTab, ensure that the following have been enabled:
    - **Enable item in location** - *Yes*
    - **Enable location status** - *Yes*

1. Select **Save**.

    > [!IMPORTANT]
    > If **Enable item in location** and **Enable location status** were already enabled, then skip ahead to the instructions for setting up the **Dimensions** FastTab.
    >
    > If those settings weren't already enabled, you must run a consistency check for the warehouse module after enabling them; continue to the next step for instructions.

1. To run the consistency check, start by going to **System administration > Periodic tasks > Database > Consistency check**.
1. In the **Consistency check** dialog box, select the following:
    - **Module** - *Warehouse management*
    - **Check/Fix** - *Check*
    - **From date** - leave blank
    - **Warehouse location status consistency check** - Select this check box
    - Select **OK**

    > [!TIP]
    > When the check process is completed, you will receive a notification. Open the [Action Center](../../fin-ops-core/fin-ops/get-started/user-interface-elements.md#notifications) to view the message. Select **Message details** button to view the details.
    >
    > If the message for Warehouse location consistency check indicates **Incorrect location status information found for location XXXX in warehouse XX.** you must run the consistency check again with **Check/Fix** set to *Fix error*. Check messages for 0 errors found.

1. Now you must finish setting up the location profile. Go to **Warehouse management > Setup >  Warehouse > Location profiles**.
1. Select **FLOOR-05** from the list of location profiles.
1. Select **Edit** on the Action Pane.
1. Expand the **Dimensions** FastTab, and enter the following:
    - **Volume utilization percentage** - *100*
    - **Volumetric method used for inventory location** - *Use location volume*
    - **Actual location height** - *10*
    - **Actual location width** - *10*
    - **Actual location depth** - *10*
    - **Maximum weight** - *100*

1. Select **Save**.

### Mobile device menu items

1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu items**.
1. Select **New** on the Action Pane, and create a new menu item to be used for sorting.
1. In the header, enter the following:
    - **Menu item name** – *Adjust In*
    - **Title** – *Adjust In*
    - **Mode** – *Work*
    - **Use existing work** – *No*

1. On the **General** FastTab, select the following:
    - **Work creation process** – *Adjustment in*
    - **Inventory adjustment types** - *Adjust in*

1. Select **Save**.

### Mobile device menu

1. Go to **Warehouse management >  Setup > Mobile device > Mobile device menu**.
1. Select **Inventory** from the list of menus.
1. Select **Edit** on the Action Pane.
1. In the **Available Menus And Menu Items** list, scroll until you find the menu item **Adjust In**.
1. Select **Adjust In** in the list then select the arrow button **(→)** to move the menu item into the **Menu Structure** list and add the newly created menu item to the desired menu.
1. Select **Save**.

### Movement types

1. Go to **Warehouse management > Setup > Inventory > Movement types**.
1. Select **New** from the Action Pane and enter the following:
    - **Movement type code** - *CONSOLIDATE*
    - **Description** - *Consolidate locations*
    - **Work class ID** - *InvMov*
  
1. Select **Save**.

## Example scenario

The following scenario uses the warehouse app running on a mobile device to make an inventory *adjustment in* to two locations in the warehouse.

### Add inventory to locations

1. Sign in to the mobile device with a user setup for Warehouse **51**.
1. Go to **Inventory > Adjust In**.
1. Enter the first location adjustment.
1. On the **Adjustment in** task, select the location to make the inventory adjustment:
    - **LOC** - *LP-001*

1. Confirm the location.
1. Create a license plate ID for the item that will be added to the location:
    - **LP** - *LP00101*

1. Confirm the license plate.
1. Enter the item to be added to the license plate:
    - **ITEM** - *M9201*

1. Confirm the item.
1. Enter the quantity of the item to be added:
    - **QTY** - *10*

1. Confirm the quantity.
1. A **Work Completed** message is displayed.
1. Enter the second location adjustment.
1. On the **Adjustment in** task, select the location to make the inventory adjustment:
    - **LOC** - *LP-002*

1. Confirm the location.
1. Create a license plate ID for the item that will be added to the location:
    - **LP** - *LP00201*

1. Confirm the license plate.
1. Enter the item to be added to the license plate:
    - **ITEM** - *M9201*

1. Confirm the item.
1. Enter the quantity of the item to be added:
    - **QTY** - *15*

1. Confirm the quantity.
1. A **Work Completed** message is displayed.
1. Select the menu button ( **≡** ), then select **Cancel** to exit the adjustment task.

### Consolidate locations

1. Go to **Warehouse management > Periodic tasks > Item Consolidation**.
1. In the header, select a warehouse to perform the consolidation. Enter the following:
    - **Warehouse** - *51*

1. Records will be displayed, one for each location that the item M9201 was adjusted. The **Utilization percentage** column shows the volumetric usage of each location.
1. To consolidate inventory, select all the locations to be consolidated, and select **Consolidate Inventory** on the Action Pane.
1. The **Consolidate inventory** dialog box opens.
1. Enter the location and movement type to be used to create the Work for inventory movement. Enter the following:
    - **Location** - *LP-001*
    - **Movement type code** - *CONSOLIDATE*

1. Select **OK**.
1. An informational message is displayed with the movement work created. Make note of the **Movement work** ID.

### View Movement Work

1. Go to **Warehouse management > Work > Work details**.
1. Filter or search the work grid to view the work created using the **Work ID** from consolidate inventory.
    - In this scenario, the consolidate inventory location used was one of the existing locations with inventory. Only one Work ID was created.

> [!NOTE]
> The system will create one work ID for each move that needs to be completed. If you enter one of the locations already containing inventory, then only one work ID will be created. If you enter a new location, then two will be created.
