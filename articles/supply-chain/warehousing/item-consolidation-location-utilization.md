# Item consolidation - location utilization

## About Item consolidation - location utilization

The new location utilization form serves as a tool to warehouse managers to easily view and filter the volumetric utilization of location across the warehouse. If deemed necessary, the user can select locations and create inventory movement work straight from the form in order to consolidate items, better utilizing warehouse space.

## About Warehouse location status

The location status feature adds four new fields to the Locations form to track additional information about the current state of the location:

- **Item number**
  - Item that is currently in the location. If the location contains multiple items, this field will be blank.

- **Last activity date and time**
  - Timestamp of the last warehouse transaction that was performed against the location

- **Aging date**
  - Date the inventory in the location was brought into the warehouse.
  - Calculated based on the license plate aging date. Accurate for license plate tracked locations. Not guaranteed to be accurate for non license plate tracked locations.

- **Location status**
  - Four options:
    - **Undetermined**: Location profile does not track status. Current status unknown
    - **Empty**: No inventory currently in the location
    - **Picking**: Outbound transactions have been performed against the location after it was last empty
    - **Storage**: Only inbound transactions have been performed since the location was last empty

These fields allow warehouse managers to get a better overview of the status of the locations in the warehouse and enable more advanced reporting and filtering.

## Enable the features

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable it if needed. You must enable the *Warehouse location status* feature before you can enable the *Item consolidation location utilization* feature. Enable the Warehouse location status feature, it is listed as:

- **Module** - *Warehouse management*
- **Feature name** - *Warehouse location status*

Next, enable the Item consolidation location utilization feature, it is listed as:

- **Module** - *Warehouse management*
- **Feature name** - *Item consolidation location utilization*

## Setup

### Released product

1. Go to **Product information management > Products > Released products**.
1. Select **Item number** - *M9201* and open the details page.
1. In the Action Pane, select the **Manage inventory** tab.
1. In the **Warehouse** section select **Physical dimensions**.
1. Select **New** in the Action Pane of the Physical dimensions page.
1. A new line is added to the grid. **Item number** field is pre-populated.
1. In the **Unit** field, select *ea*. The rest of the fields on the line will auto populate.
1. Select **Save** and close the page.

### Location profile

1. Go to **Warehouse management > Setup >  Warehouse > Location profiles**.
1. Select **FLOOR-05** from the list of location profiles.
1. Select **Edit** in the Action Pane.
1. In the **General** FastTab, ensure that the following have been enabled:
    - **Enable item in location** - *Yes*
    - **Enable location status** - *Yes*

1. Select **Save**.

> [!IMPORTANT]
> If the two configurations above were already enabled, go to the instructions below for the **Dimensions** FastTab.
>
> If the two configurations above were not already enabled, you must run a **Consistency check** for the **Warehouse module** after enabling.

1. To run the consistency check, go to **System administration > Periodic tasks > Database > Consistency check**.
1. In the **Consistency check** dialog box, select the following:
    - **Module** - *Warehouse management*
    - **Check/Fix** - *Check*
    - **From date** - leave blank
    - Select the **check box** for *Warehouse location status consistency check*
    - Select **OK**

> [!TIP]
>When the check process is completed you will receive an notification. Open the Action Center to view the message. Select **Message details** button to view the details.
>
>If the message for Warehouse location consistency check indicates **Incorrect location status information found for location XXXX in warehouse XX.** you must run the consistency check again with **Check/Fix** set to *Fix error*. Check messages for 0 errors found.

1. Finish setting up the location profile. Go to **Warehouse management > Setup >  Warehouse > Location profiles**.
1. Select **FLOOR-05** from the list of location profiles.
1. Select **Edit** in the Action Pane.
1. Expand the **Dimensions** FastTab, and enter the following:
    - **Volume utilization percentage** - *100*
    - **Volumetric method used for inventory location** - *Use location volume*
    - **Actual location height** - *10*
    - **Actual location width** - *10*
    - **Actual location depth** - *10*
    - **Maximum weight** - *100*

1. Select **Save**.

### Mobile Device Menu Items

1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu items**.
1. Select **New** in the Action Pane, and create a new menu item to be used for sorting.
1. In the Header, enter the following:
    - **Menu item name** – *Adjust In*
    - **Title** – *Adjust In*
    - **Mode** – *Work*
    - **Use existing work** – *No*

1. In **General** FastTab, select the following:
    - **Work creation process** – *Adjustment in*
    - **Inventory adjustment types** - *Adjust in*

1. Select **Save**.

### Mobile device menu

1. Go to **Warehouse management >  Setup > Mobile device > Mobile device menu**.
1. Select **Inventory** from the list of menus.
1. Select **Edit** on the Action Pane.
1. In the **Available Menus And Menu Items** scroll until you find the menu item **Adjust In**.
1. Select **Adjust In** in the list then select the arrow button **(→)** to move the menu item into the **Menu Structure** list and add the newly created menu item to the desired menu.
1. Select **Save**.

### Movement types

1. Go to **Warehouse management > Setup > Inventory > Movement types**.
1. Select **New** from the Action Pane and enter the following:
    - **Movement type code** - *CONSOLIDATE*
    - **Description** - *Consolidate locations*
    - **Work class ID** - *InvMov*
  
1. Select **Save**.

## Scenario

The following scenario utilizes the Warehousing Mobile Device to perform a task, along with D365 Supply Chain Management functions. The mobile device will be used to make an inventory *adjustment in* to two locations in the warehouse.

### Add inventory to locations

1. Login to the mobile device with a user setup for Warehouse **51**.
1. Go to **Inventory > Adjust In**.
1. Enter the first location adjustment.
1. On the **Adjustment in** task, select the location to make the inventory adjustment, enter the following:
    - **LOC** - *LP-001*

1. Confirm the location.
1. Create a license plate ID for the item that will be added to the location, enter the following:
    - **LP** - *LP00101*

1. Confirm the license plate.
1. Enter the item to be added to the license plate, enter the following:
    - **ITEM** - *M9201*

1. Confirm the item.
1. Enter the quantity of the item to be added, enter the following:
    - **QTY** - *10*

1. Confirm the quantity.
1. A **Work Completed** message is displayed.
1. Enter the second location adjustment.
1. On the **Adjustment in** task, select the location to make the inventory adjustment, enter the following:
    - **LOC** - *LP-002*

1. Confirm the location.
1. Create a license plate ID for the item that will be added to the location, enter the following:
    - **LP** - *LP00201*

1. Confirm the license plate.
1. Enter the item to be added to the license plate, enter the following:
    - **ITEM** - *M9201*

1. Confirm the item.
1. Enter the quantity of the item to be added, enter the following:
    - **QTY** - *15*

1. Confirm the quantity.
1. A **Work Completed** message is displayed.
1. Select the menu button ( **≡** ), then select **Cancel** to exit the adjustment task.

### Consolidate locations

1. Go to **Warehouse management > Periodic tasks > Item Consolidation**.
1. In the header, select a warehouse to perform the consolidation. Enter the following:
    - **Warehouse** - *51*

1. Records will be displayed, one for each location that the Item M9201 was adjusted. The Utilization percentage column shows the volumetric usage of each location.
1. To consolidate inventory, select all the locations to be consolidated, and select **Consolidate Inventory** in the Action Pane.
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
