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
1. If the two configurations above were already enabled, go to the instructions below for the **Dimensions** FastTab.
1. If the two configurations above were not already enabled, you must run the Warehouse location status consistency check after enabling.
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

10. On the **Location profiles** page, **Location Profile ID** *FLOOR-05*, expand the **Dimensions** FastTab, and enter the following:
    - **Volume utilization percentage** - *100*
    - **Volumetric method used for inventory location** - *Use location volume*
    - **Actual location height** - *10*
    - **Actual location width** - *10*
    - **Actual location depth** - *10*
    - **Maximum weight** - *100*

1. Select **Save**.

## Scenario

Open the mobile device, log in to warehouse 51, and navigate to **Inventory > Adjust In**. (no menu item)

Enter Loc = LP-001, make up a new LP (system generated), and Item = M9201. Enter 10 ea as the quantity and confirm the adjustment.

Using the same menu item, enter Loc = LP-002, make up a new LP (system generated), and Item = M9201. Enter 15 ea as the quantity and confirm the adjustment.

Navigate to **Warehouse management > Periodic tasks > Item Consolidation**. Enter warehouse *51*.

You will see two records displayed, one for each location that you adjusted item M9201 into. The Utilization percentage column shows the volumetric usage of each location.

To consolidate inventory, select all the locations you want to consolidate, and click on **Consolidate Inventory** in the action bar. Enter the location to consolidate into, and the movement type code to use. (no movement type)

The system will create one work ID for each move that needs to be completed. If you enter one of the locations already containing inventory, then only one work ID will be created. If you enter a new location, then two will be created.
