# Outbound sorting

With this functionality, several industries will experience easier handling of small containers and will enable the warehouse workers to better plan and organize pallet capacity within the truck.

With outbound sorting you now can sort packed containers to the correct pallet after a packing station, and to build a packing hierarchy.

This functionality allows for the building of pallets from containers packed through the <!-- HHM: Link should not be to Blue Horseshoe site. Either remove link or link to the Docs location. [Packing](https://bluehorseshoe.sharepoint.com/SitePages/Packing.aspx) --> packing functionality. The container is not sent to the final shipping location as it would be in the original Packing flow. Instead, this functionality allows the user to close the container and move it to a Sort type location. They can then sort containers onto positions, each position has a license plate. Once the containers have been sorted, work can be created to send the whole LP to the final shipping dock or stage locations based on Location Directives/customer requirements. The closing of the sort position can also immediately move the inventory to the final shipping location and pick it to the order.

## Enable the Outbound sorting feature

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - *Warehouse management*
- **Feature name** - *Outbound sorting*

## Setup

For this scenario, standard Contoso demo data is used with Warehouse 62 and some additional setups as noted below.

### Location type

1. Go to **Warehouse management > Setup > Warehouse > Location types**
1. Select **New** from the Action Pane
1. Enter the following to create new location type:
    - **Location type** - *SORT*
    - **Description** - *Sort*
1. Close *Location types* form

### Warehouse management parameters

1. Go to **Warehouse management > Setup > Warehouse management parameters**
1. Select **General** group and expand the **Location types** FastTab.
1. Enter the following:
    - **Sorting location type** - *SORT*
1. Close the *Warehouse management parameters* form.

### Location profiles

1. Go to **Warehouse management > Setup -> Warehouse -> Location profiles**
1. Select **New** from the Action Pane
1. Enter the following in the header:
    - **Location profile ID** – *SORTING*
    - **Name** – *Sorting*
1. In the **General** FastTab, enter the following:
    - **Location format** – *ASRB* (Aisle-Rack-Shelf-Bin)
    - **Location type** – *SORT*
    - **Use license plate tracking** – *Yes*
    - **Allow mixed items** – *Yes*
        - **Allow mixed inventory batches** is automatically changed to *Yes* and cannot be independently changed.
    - **Allow mixed inventory statuses** – *Yes*
1. This profile will be used in a new parameter under the Advanced Warehouse parameters form​​.

### Locations

1. Go to **Warehouse management > Setup > Warehouse > Locations**
1. Unselect **Generate check digits for location** in the header
1. Select **New** from the Action Pane to create a new *Location*. Enter the following:
    - **Warehouse** – *62*
    - **Location** – *SORT*
    - **Location profile ID** – *SORTING*
1. Select **Save** and close *Locations*

### Outbound sorting template

The Outbound sorting template determines if work will be created out of Sort location and how sorting will take place, either manual or automatic.

#### For Pallet building after packing station

1. Go to **Warehouse Management > Setup > Packing > Outbound sorting template**
1. Select **New** in the Action Pane
1. In the **header** of the new template, enter the following:
    - **Outbound sorting template ID** – *AutoWork*
    - **Description** – *Auto Work Creation*
    - **Outbound sorting template type** – *Container*
    - **Warehouse** - *62*
    - **Location** – *SORT*
1. In the **General** FastTab, enter the following:
    - **Sort verification** – *Position scan*
        - Verification that is required when sorting
            - None
            - License plat scan
            - Position scan
    - **Create work on position close** – *Yes*
        - When enabled work will be created when the position is closed to move inventory to the final shipping location. When disabled, inventory will be immediately picked to the order at the time of position close.
    - **Position assignment** - *Automatic*
        - Type of position assignment. When 'Manual' the user must always indicate which position the inventory should be sorted to. When 'Automatic' the system will automatically guide the inventory to a position when possible, based on the sort template breaks.
        - Select **Save** to enable *Edit query*
1. In the Action Pane, select **Edit Query** to specify the criteria used for this Outbound sort template.
    - Select the **Sorting** tab
    - Select **Add** a new line with the following setup:
        - **Table** – *Shipments*
        - **Derived table** – *Shipments*
        - **Field** – *Carrier service*
            - You may get a message: *Field Carrier service is not an index field. Do you want to add sorting on this?* Select **Yes**
        - **Search direction** – *Ascending*
        - Select **OK**
            - If you get the message: *Grouping will be reset, continue?* Select **Yes**
        - This will enable the *Outbound sorting template breaks* button in the Action Pane
    - Select **Outbound sorting template breaks**
        - The **Outbound sorting criteria** FlyOut opens
            - **Reference table name** - *Shipments*
            - **Reference field name** - *Carrier service*
            - Select the **Group by field** to group shipments by Carrier service
        - Select **OK**

### Container packing policies

1. Go to **Warehouse management > Setup > Containers > Container packing policies**
1. Select **New** in the Action Pane
1. In the **Header** enter the following:
    - **Container packing policy** – *Sort*
    - **Description** – *Sort*
1. In the **Overview** FastTab, enter the following:
    - **Warehouse** – *62*
    - **Default location for sorting** – *SORT*
    - **Weight unit** – *kg*
    - **Container closing policy** – *Automatic release*
    - **Container release policy** – *Assign container to outbound sorting position*
1. Select **Save**

### Packing profiles

1. Go to **Warehouse management > Setup > Packing > Packing profiles**
1. and create a new Packing profile to be used with sorting functionality.
1. In the Action Pane select **New**
1. In the new line created, enter the following:
    - **Packing profile ID** – *Sort*
    - **Description** – *Sort*
    - **Container packing policy** - *Sort*
    - **Container ID mode** – *Auto*
    - **Container type** – *Box-Large*
    - **Auto create container at container close** – *No* (unselected)
    - Select **Save**

### Mobile device menu items

1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu items**
1. Select **New** from the Action Pane
1. In the **Header**, enter the following:
    - **Menu item name** – *Pallet build*
    - **Title** – *Pallet build*
    - **Mode** – *Indirect*
    - **Use existing work** – *No*
1. In **General** FastTab, enter the following:
    - **Activity code** – *Outbound sorting*
        - When selected the *Outbound sorting template ID* field is displayed
    - **Use process guide** - *Yes*
        - When *Outbound sorting* is selected this is automatically set to *Yes*
    - **Outbound sorting template ID** – *AutoWork*
    - Select **Save**

### Mobile device menu

Add the *Mobile device menu item* for *Pallet build* to the Outbound menu of the mobile device.

1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu**
1. Add the **Pallet build** menu item that you just created to a *Mobile device menu*
1. Select the **Outbound** menu
1. Select **Edit** from the Action Pane
1. Scroll in the **AVAILABLE MENUS AND MENU ITEMS** until you find *Pallet build*
1. Select **Pallet build**, the arrow pointing to the **MENU STRUCTURE** list will be enabled
1. Select the ***arrow*** button to move the *Pallet build* menu item into the *Outbound* menu structure
1. Select *Pallet build* from the **MENU STRUCTURE** list then select the *UP* or *DOWN* arrows to move the menu item into the desired position on the mobile device menu.

### Location directives

*Location directives* are rules tha help identify pick and put locations for inventory movement. Create a rule to manage the sorting work.

#### Single sku directive

1. Go to **Warehouse management > Setup > Location directives**
1. On the left pane, change **Work order type** to *Sorted inventory picking*
1. In the Action Pane, select **New**
1. In the **Header** enter the following:
    - **Sequence** – *1*
    - **Name** – *Baydoor*
1. In the **Location directives** FastTab, enter the following:
    - **Work type** – *Put*
    - **Site** – *6*
    - **Warehouse** – *62*
    - **Multiple SKU** - *No*
    - Select **Save** to enable the *Lines* FastTab
1. In the **Lines** FastTab, select **New** in the Action Pane and enter the following on the new line:
    - **Sequence** – *1*
    - **From** – *0*
    - **To** – *1,000,000*
    - Accept the defaults for the remaining fields
    - Select **Save** to enable the *Location Directive Actions* FastTab
1. In the **Location directive actions** FastTab, select **New** in the Action Pane and enter the following on the new line:
    - **Sequence** – *1*
    - **Name** – *Baydoor*
    - Accept the defaults for the remaining fields
    - Select **Save**
1. In the **Location directive actions** FastTab Action Pane, select *Edit query*
    - On the **Range** tab, find in the grid the row where **Field** = *Location* and enter the following:
        - **Criteria** - *Baydoor*
        - Select **OK**

#### Multiple sku directive

1. Go to **Warehouse management > Setup > Location directives**
1. On the left pane, change **Work order type** to *Sorted inventory picking*
1. In the Action Pane, select **New**
1. In the **Header** enter the following:
    - **Sequence** – *2*
    - **Name** – *Baydoor Multi*
1. In the **Location directives** FastTab, enter the following:
    - **Work type** – *Put*
    - **Site** – *6*
    - **Warehouse** – *62*
    - **Multiple SKU** - *Yes*
    - Select **Save** to enable the *Lines* FastTab
1. In the **Lines** FastTab, select **New** in the Action Pane and enter the following on the new line:
    - **Sequence** – *1*
    - **From** – *0*
    - **To** – *1,000,000*
    - Accept the defaults for the remaining fields
    - Select **Save** to enable the *Location Directive Actions* FastTab
1. In the **Location directive actions** FastTab, select **New** in the Action Pane and enter the following on the new line:
    - **Sequence** – *1*
    - **Name** – *Baydoor Multi*
    - Accept the defaults for the remaining fields
    - Select **Save**
1. In the **Location directive actions** FastTab Action Pane, select *Edit query*
    - On the **Range** tab, find in the grid the row where **Field** = *Location* and enter the following:
        - **Criteria** - *Baydoor*
        - Select **OK**

### Work classes

1. Go to **Warehouse management > Setup > Work > Work classes**
1. Select **New** from the Action Pane
and create new Work class for Sorting:
    - **Work class ID** – *Sort*
    - **Description** – *Sort*
    - **Work order type** – *Sorted inventory picking*
1. Select **Save**

### Work templates

1. Go to **Warehouse management > Setup > Work > Work templates**
1. change the **Work order type** to *Sorted inventory picking* 1. Select **New** from the Action Pane to create a new work template
1. In the **Overview** tab, enter the following:
    - **Sequence** – *1*
    - **Work template** – *Sort*
    - **Work template description** – *Sort*
    - Select **Save** to enable the *Work Template Details*
1. In **Work Template Details** select **New** to add ***Line 1***
1. Enter the following on *Line 1*:
    - **Work type** - *Pick*
    - **Work class ID** - *SORT*
1. In **Work Template Details** select **New** to add ***Line 2***
1. Enter the following on *Line 2*:
    - **Work type** - *Put*
    - **Work class ID** - *SORT*
1. Select **Save**

## Scenario

This scenario will simulate a situation where the packed containers should be automatically sorted to different positions (pallets) after the packing station, based on the shipping carrier service. After all items from the Load are packed and sorted by address, the pallets will be moved to the baydoor.

### Create a new sales order

1. Go to **Sales and marketing > Sales orders > All sales orders**
1. Select **New** from the Action Pane
1. On the **Create sales order FlyOut, enter the following:
    - **Customer account** = *US-005*
    - **Warehouse** = *62*
    - Select **OK** to close the form and create a new sales order
1. Your new sales order opens. It should include a new, empty line in the **Sales order lines** table.
    - Shipping carrier = Air cargo
    - Carrier service = Air

Add a line for item A0001, quantity 2. Reserve the order line and release to warehouse.

Complete the created picking work using the mobile device to the pack station.

Create a second sales order:

- Customer = US-006
- Warehouse = 62

Add a line for item A0001, quantity 1. Specify Mode of delivery = Flowe-STD

Add a second line for item A0002, quantity 1. Specify Mode of delivery = Air C-Air

Reserve both lines and release to warehouse.

### Picking

Complete the created work using the mobile device to the pack station

### Packing

Open the pack form, and specify:

- Warehouse – 62
- Location – Pack
- Packing profile ID – Sort

Enter the target LP used when picking the first sales order. Create a new container, accept the defaults.

Pack quantity 1 of A0001 into the container. Close it, using the system weight.

 The container will be moved to the &#39;SORT&#39; location and is ready for sorting

Create a second container, pack the remaining 1 of A0001 into it. Close it, using the system weight.

Enter the target LP used when picking the second sales order. Create a new container, accept the defaults.

Pack quantity 1 of A0001 into the container. Close it, using the system weight.

Create a second container, pack quantity 1 of A0002 into the container. Close it, using the system weight.

### Sorting

Open the Pallet build menu item on the mobile device.

Enter the first container ID from the first sales order. Since no sort positions currently exist, the user must specify one. Specify SP01.

Because there is no license plate currently associated with SP01, the user must specify one. Enter PLP01

Sort position validation is enabled, so the user is required to enter the sort position ID again.

Navigate to _Warehouse management_ _-_ _Packing and containerization_ _-_ _Outbound sorting position assignments._

This form will show all of the sort positions that are currently active, the LP associated with each, and what containers are in the sort position. Observe that one sort position currently exists, it is using a criteria of Shipment – Carrier service = Air.

The container that has been sorted is shown in Sort position transactions grid.

On the mobile device, scan the second container ID associated with the first order. Because the sorting template is setup to sort automatically, and there is already a sport position that exists with matching criteria, the user is automatically directed to the correct sort position. They only need to scan the position ID to confirm they&#39;re putting the inventory to the right place.

Scan the container containing A0001 from the second order. Because the carrier service is different, the user is prompted to enter and new sort position (use SP02) and assign a license plate to that position (PLP02).

Scan the container containing A0002 from the second order. Because the carrier service matches the first sort position, the user will be directed to put the container on SP01.

Once all inventory has been sorted, the position needs to be closed for work to be created.

On the mobile device, scan the pallet ID PLP02. The user will be asked if they want to close the position. Click OK and the position will be closed, and sorted inventory picking work will be created to take the inventory to the Baydoor.

From the outbound sorting position assignments form, select SP01, and click Close from the action bar. This will perform the same action that was performed on the mobile device: Close the position and create sorted inventory picking work.

Complete the sorted inventory picking work normally. Once completed the inventory will be picked to the sales order. All other warehouse processes apply at this point.
