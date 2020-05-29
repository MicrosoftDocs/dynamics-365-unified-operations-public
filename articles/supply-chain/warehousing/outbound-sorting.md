# Outbound sorting

With this functionality, several industries will experience easier handling of small containers and will enable the warehouse workers to better plan and organize pallet capacity within the truck.

With outbound sorting you now can sort packed containers to the correct pallet after a packing station, and to build a packing hierarchy.

This functionality allows for the building of pallets from containers packed through the packing functionality. The container is not sent to the final shipping location as it would be in the original Packing flow. Instead, this functionality allows the user to close the container and move it to a Sort type location. They can then sort containers onto positions, each position has a license plate. Once the containers have been sorted, work can be created to send the whole LP to the final shipping dock or stage locations based on Location Directives/customer requirements. The closing of the sort position can also immediately move the inventory to the final shipping location and pick it to the order.

## Enable the Outbound sorting feature

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - *Warehouse management*
- **Feature name** - *Outbound sorting*

## Setup

For this scenario, standard Contoso demo data is used with Warehouse 62 and additional setups as noted below.

### Wave Template

This setting automatically processes the Wave and creates work when a line is released to the warehouse.

1. Go to **Warehouse management > Setup > Waves > Wave templates**
1. In the left pane, select the Shipping template for *Warehouse 62*
1. Ensure that in the ***General*** FastTab, **Process wave at release to warehouse** is set to *Yes*

### Worker

The packing station is seen as a location. When the warehouse workers are logging in at the packing station, they will only see and operate on shipments and containers that are planned at the specific packing location. The *User* logging into D365 must be setup as a **Worker** in *Warehouse management*. If the Login User's name does not appear in the list of Work users, follow the steps below to add them.

>[!NOTE]
>These steps assume that the Login user is already a User in the system and has been associated as an employee or worker in the Human Resources module.

1. Go to **Warehouse management > Setup > Worker**
1. Select **New**
1. In the header **Worker** field, select the dropdown to open the list of employees and select the user name
1. Tap or click the **Select** button
1. Select **Save**
1. In the **Users** FastTab, select **New** to create a mobile device login, enter the following:
    - **User ID** - Enter a unique ID
    - **User name** - Enter a name for the ID
    - **Default warehouse** - *62*
    - **Menu name** - *Main*
    - Select **Save**

1. The **Set password** FlyOut opens, create a simple password for the User ID to login to the mobile app.
    - **Password** - Simple password
    - **Confirm password** - Enter password again

1. Select **Set password**, a message is sent to the *Action center* that the password has been set for user that your created

### Location type

1. Go to **Warehouse management > Setup > Warehouse > Location types**
1. Select **New** from the Action Pane
1. Enter the following to create new location type:
    - **Location type** - *SORT*
    - **Description** - *Sort*
    - Select **Save**

1. Close *Location types* form

### Warehouse management parameters

1. Go to **Warehouse management > Setup > Warehouse management parameters**
1. Select **General** group and expand the **Location types** FastTab.
1. Enter the following:
    - **Sorting location type** - *SORT*
    - Select **Save**

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
    - Select **Save**

### Locations

1. Go to **Warehouse management > Setup > Warehouse > Locations**
1. Unselect **Generate check digits for location** in the header
1. Select **New** from the Action Pane to create a new *Location*. Enter the following:
    - **Warehouse** – *62*
    - **Location** – *SORT*
    - **Location profile ID** – *SORTING*
    - Select **Save**

1. Close *Locations*

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
            - License plate scan
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

Create a new Packing profile to be used with sorting functionality.

1. Go to **Warehouse management > Setup > Packing > Packing profiles**
1. In the Action Pane select **New**
1. In the new line created, enter the following:
    - **Packing profile ID** – *Sort*
    - **Description** – *Sort*
    - **Container packing policy** - *Sort*
    - **Container ID mode** – *Auto*
    - **Container type** – *Box-Large*
    - **Auto create container at container close** – *No* (unselected)

1. Select **Save**

### Mobile device menu items

#### Create a new pallet menu item

Create a mobile device menu item to build pallets during sorting.

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

1. Select **Save**

#### Create a new loading menu item

This menu item allows users to move the sorted inventory items to the shipping location.

1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu items**
1. Select **New** from the Action Pane
1. In the **Header**, enter the following:
    - **Menu item name** – *Load from Sorting*
    - **Title** – *Load from Sorting*
    - **Mode** – *Work*
    - **Use existing work** – *Yes*

1. In the **General** FastTab, enter the following:
    - **Directed by** – *User directed*

1. In the **Work classes** FastTab
1. Select **New** and enter the following:
    - **Work class ID** - *SORT*
    - **Work order type** - *Sorted inventory picking*

1. Select **Save**

### Mobile device menu

Add the *Mobile device menu item* for *Pallet build* to the Outbound menu of the mobile device.

1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu**
1. Add the **Pallet build** menu item that you just created to a *Mobile device menu*
1. Select the **Outbound** menu
    - Select **Edit** from the Action Pane
    - Scroll in the **AVAILABLE MENUS AND MENU ITEMS** until you find *Pallet build*
    - Select **Pallet build**, the arrow pointing to the **MENU STRUCTURE** list will be enabled
    - Select the ***arrow*** button to move the *Pallet build* menu item into the *Outbound* menu structure
    - Select *Pallet build* from the **MENU STRUCTURE** list then select the *UP* or *DOWN* arrows to move the menu item into the desired position on the mobile device menu.

1. Select **Save**

### Location directives

*Location directives* are rules tha help identify pick and put locations for inventory movement. Create a rule to manage the sorting work.

#### Create a Single sku directive

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

1. Select **Save** to enable the *Lines* FastTab
1. In the **Lines** FastTab, select **New** in the Action Pane and enter the following on the new line:
    - **Sequence** – *1*
    - **From** – *0*
    - **To** – *1,000,000*
    - Accept the defaults for the remaining fields

1. Select **Save** to enable the *Location Directive Actions* FastTab
1. In the **Location directive actions** FastTab, select **New** in the Action Pane and enter the following on the new line:
    - **Sequence** – *1*
    - **Name** – *Baydoor*
    - Accept the defaults for the remaining fields

1. Select **Save**
1. In the **Location directive actions** FastTab Action Pane, select *Edit query*
    - On the **Range** tab, find in the grid the row where **Field** = *Location* and enter the following:
        - **Criteria** - *Baydoor*
    - Select **OK**

#### Create a Multiple sku directive

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

1. Select **Save** to enable the *Lines* FastTab
1. In the **Lines** FastTab, select **New** in the Action Pane and enter the following on the new line:
    - **Sequence** – *1*
    - **From** – *0*
    - **To** – *1,000,000*
    - Accept the defaults for the remaining fields

1. Select **Save** to enable the *Location Directive Actions* FastTab
1. In the **Location directive actions** FastTab, select **New** in the Action Pane and enter the following on the new line:
    - **Sequence** – *1*
    - **Name** – *Baydoor Multi*
    - Accept the defaults for the remaining fields

1. Select **Save**
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

1. Select **Save** to enable the *Work Template Details*
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

### Create sales orders and picking work

#### Sales order 1

1. Go to **Sales and marketing > Sales orders > All sales orders**
1. Select **New** from the Action Pane
1. On the **Create sales order** FlyOut, enter the following:
    - **Customer account** = *US-005*
    - **Warehouse** = *62*

1. Select **OK** to close the form and create a new sales order
1. Your new sales order opens. It should include a new, empty line in the **Sales order lines** table.
1. Select the **Header** section tab and expand the **Delivery** FastTab. Enter the following in the **Transportation** group:
    - **Shipping carrier** - *Air cargo*
    - **Carrier service** - *Air*

1. Select the **Lines** section tab.
1. If a new line is not automatically opened, select *Add line* in the **Sales order lines** FastTab to add a line with the following values:
    - **Item** - *A0001*
    - **Quantity** - *2*

1. Focus on the order line, in the **Sales order lines** FastTab
1. Select **Inventory** then select **Reservation** from the list
1. The **Reservation** page opens
    - Select **Reserve lot** to reserve your selected line's full quantity in the warehouse.

1. Close the **Reservation** page to return to your sales order.
1. In the Action Pane, select the **Warehouse** tab.
1. Select **Release to warehouse** from the *Actions* group.
1. An informational message displays with the shipment and wave for this order. Note the ***Wave ID*** number and the ***Shipment ID*** numbers.  

#### Sales order 2

1. Go to **Sales and marketing > Sales orders > All sales orders**
1. Select **New** from the Action Pane
1. On the **Create sales order FlyOut, enter the following:
    - **Customer account** = *US-006*
    - **Warehouse** = *62*

1. Select **OK** to close the form and create a new sales order
1. Your new sales order opens. It should include a new, empty line in the **Sales order lines** table. Enter the following values:
    - **Item** - *A0001*
    - **Quantity** - *1*

1. Expand the ***Line details*** FastTab
1. Select the **Delivery** tab
    - In the *MISC. DELIVERY INFO* GROUP, change the **Mode of delivery** to *Flowe-STD*

1. In the **Sales order lines** FastTab Action Pane, select **Add line** and enter the following in the new line:
    - **Item** - *A0002*
    - **Quantity** - *1*

1. In the **Line details** FastTab select the **Delivery** tab
    - In the *MISC. DELIVERY INFO* GROUP, change the **Mode of delivery** to *Air C-Air*

1. Focus on the first order line, in the **Sales order lines** FastTab
1. Select **Inventory** then select *Reservation* from the list
1. The **Reservation** page opens
    - Select **Reserve lot** to reserve your selected line's full quantity in the warehouse.

1. Close the **Reservation** page to return to your sales order.
1. Focus on the second order line, in the **Sales order lines** FastTab
1. Select **Inventory** then select *Reservation* from the list
1. The **Reservation** page opens
    - Select **Reserve lot** to reserve your selected line's full quantity in the warehouse.

1. Close the **Reservation** page to return to your sales order.
1. In the Action Pane, select the **Warehouse** tab.
1. Select **Release to warehouse** from the *Actions* group.
1. An informational message displays with the shipment and wave for this order.
    - Note that two ***Wave ID*** numbers and two ***Shipment ID*** numbers are created, one for each *Mode of delivery* on the lines of the sales order.

#### Get the Work ID's from Work Details

1. Go to **Warehouse management > Work > Work details**
1. **Work ID**'s are created from the Sales Orders
1. Using the *Wave ID*'s and *Shipment ID*'s from the sales orders you created, find and make note of the **Work ID** for each *Wave/Shipment*. You will use these *Work ID's* in the following steps.
    - Note that two *Work ID*'s are also created for the second sales order. Picking different items from different locations will generate two Work ID's.

### Picking

Complete the created work using the mobile device to the pack station

1. Login to **Warehouse** *62* on the Mobile app with the **User ID** created in the *Worker* setup, or use an existing demo data user
1. Select **Outbound** from the *Main Menu*
1. Select **Sales Picking** from the *Outbound* menu
    - In the **ID** field, enter the *Work ID* created on *Sales Order 1*

1. Select **OK**
    - Enter a **Target LP** (License Plate) created for *Sales Order 1* on the *Sales orders - Pick* screen
        - Note that the picking location (**Loc** - *bulk-001*), Item (*A0001*) and Qty (*2 pcs*) are displayed.

1. Select **OK**
    - Confirm the *Sales orders - Put* screen information
        - The picked items should be going into **Loc** - *Pack*

1. Select **OK**
1. A **Work Completed** message is displayed on the *Scan a work ID / license plat ID* screen indicating that the *Work ID* from Sales Order 1 has been completed.

1. Pick the second sales order
    - In the **ID** field, enter the *Work ID* created for Sales Order 2, ***Line 1*** - *Item A0001*
1. Select **OK**
    - Enter a **Target LP** (License Plate) on the *Sales orders - Pick* screen
        - Note that the picking location (**Loc** - *bulk-001*), Item (*A0001*) and Qty (*1 pcs*) are displayed.

1. Select **OK**
    - Confirm the *Sales orders - Put* screen information, the picked item should be going into **Loc** - *Pack*

1. Select **OK**
1. A **Work Completed** message is displayed on the *Scan a work ID / license plat ID* screen indicating that the *Work ID* from Sales Order 2, line 1 has been completed.
    - In the **ID** field, enter the *Work ID* created for Sales Order 2, ***Line 2*** - *Item A0002*
1. Select **OK**
    - Enter a **Target LP** (License Plate) on the *Sales orders - Pick* screen
        - Note that the picking location (**Loc** - *bulk-002*), Item (*A0001*) and Qty (*1 pcs*) are displayed.

1. Select **OK**
    - Confirm the *Sales orders - Put* screen information, the picked item should be going into **Loc** - *Pack*

1. Select **OK**
1. A **Work Completed** message is displayed on the *Scan a work ID / license plat ID* screen indicating that the *Work ID* from Sales Order 2, line 2 has been completed.

### Packing

#### Pack Sales Order 1 into Containers

1. Go to **Warehouse management > Packing and containerization > Pack**
1. On the **Select packing station** FlyOut, the **Worker** field should default to the User login worker name, enter the following to see and operate on shipments and containers that are planned at the specific packing location:
    - **Site** - *6*
    - **Warehouse** – *62*
    - **Location** – *Pack*
    - **Packing profile ID** – *Sort*

1. Select **OK** to close the FlyOut
1. In the **License plate or shipment** field, enter the *Target LP* for 1st Sales Order
    - Select the *Tab* or *Enter* keys to exit the field.
1. In the Action Pane, select **New container**
1. Accept the Defaults and select **OK**
    - Make note of the *Container ID*
1. In the **Item packing** FastTab, *PACK ITEM* group, enter the following:
    - **Quantity** - *1*
    - **Identifier field** - *Item* - *A0001*

1. In the Action Pane, select **Close container**
1. The **Close container** FlyOut opens.
    - Select **Get system weight** to have the system update the *GROSS WEIGHT* field
1. Select **OK**
    - The container will be moved to the **SORT** location and is ready for sorting
1. Create a second container to add the second item from the sales order 1 license plate to a new container
1. In the Action Pane, select **New container**
1. Accept the Defaults and select **OK**
    - Make note of the *Container ID*
1. In the **Item packing** FastTab, *PACK ITEM* group, enter the following:

    - **Quantity** - *1*
    - **Identifier field** - *Item* - *A0001*

1. In the Action Pane, select **Close container**
1. The **Close container** FlyOut opens.
    - Select **Get system weight** to have the system update the *GROSS WEIGHT* field
1. Select **OK**
    - The container will be moved to the **SORT** location and is ready for sorting

#### Pack Sales Order 2 into Containers

1. In the **License plate or shipment** field, enter the *Target LP* for Line 1 of Sales Order 2. Select the *Tab* or *Enter* keys to exit the field.
1. In the Action Pane, select **New container**
1. Accept the Defaults and select **OK**
    - Make note of the *Container ID*
1. In the **Item packing** FastTab, *PACK ITEM* group, enter the following:

    - **Quantity** - *1*
    - **Identifier field** - *Item* - *A0001*

1. In the Action Pane, select **Close container**
1. The **Close container** FlyOut opens.
    - Select **Get system weight** to have the system update the *GROSS WEIGHT* field
1. Select **OK**
    - The container will be moved to the **SORT** location and is ready for sorting
1. In the **License plate or shipment** field, enter the *Target LP* for Line 2 of Sales Order 2. Select the *Tab* or *Enter* keys to exit the field.
1. In the Action Pane, select **New container**
1. Accept the Defaults and select **OK**
    - Make note of the *Container ID*
1. In the **Item packing** FastTab, *PACK ITEM* group, enter the following:

    - **Quantity** - *1*
    - **Identifier field** - *Item* - *A0002*

1. In the Action Pane, select **Close container**
1. The **Close container** FlyOut opens.
    - Select **Get system weight** to have the system update the *GROSS WEIGHT* field
1. Select **OK**
    - The container will be moved to the **SORT** location and is ready for sorting

To view the *Container* details, go to **Warehouse management > Packing and containerization > Containers** and search for the *Container ID*'s created during packing.

### Sorting

#### Sort the first container

1. Login to **Warehouse** *62* on the Mobile app with the **User ID** created in the *Worker* setup, or an existing demo data user
1. Select **Outbound** from the *Main Menu*
1. Select **Pallet build** from the *Outbound* menu
    - Enter the first *Container ID* from the  Sales order 1 in the **LP/Con** field
1. Select **OK**
1. Since no sort positions currently exist, the user must specify one.
    - In the **Sort position ID** field, enter *SP01*.
1. Because there is no license plate currently associated with **Sort position** *SP01*, the user must specify one.
    - In the **LP** field, enter *PLP01*
1. Select **OK**
1. Sort position validation is enabled, so the user is required to enter the **Sort position ID** again
    - Enter *SP01* in the **Sort Position ID** field
1. Select **OK**
1. A message is displayed that *Work completed*

>[!TIP]
>Go to **Warehouse management > Packing and containerization > Outbound sorting position assignments** to view the sorting position and license plate in the position.
>
>This form will show all of the sort positions that are currently active. **Sort position transactions** show the license plate associated with each, and what containers are in the sort position. Note that one sort position currently exists and in the **Sort position criteria** FastTab , it shows using a criteria of **Shipment – Carrier service - Air**

#### Sort the remaining containers

1. Go to the mobile app
1. Login to **Warehouse** *62* on the Mobile app with the **User ID** created in the *Worker* setup, or an existing demo data user
1. Select **Outbound** from the *Main Menu*
1. Select **Pallet build** from the *Outbound* menu
    - Enter the second container ID associated with the Sales order 1 in the **LP/Con** field
1. Select **OK**
    - Because the sorting template is setup to sort automatically, and there is already a sort position that exists with matching criteria, the user is automatically directed to the correct sort position.
1. Select **OK**
    - Confirm the **Sort Position ID** by entering the sort position *SP01* to show that the inventory is in right place.
1. Select **OK**
1. Work is completed on the second container from *Sales order 1*
1. Sort the remaining containers from *Sales order 2*
1. In the **LP/Con** field enter the **Container ID** containing *Item A0001* from the second order.
    - Because the carrier service is different, the user is prompted to enter and new sort position (use *SP02*) and assign a license plate to that position (*PLP02*).
1. Select **OK**
    - Confirm the sort position, in the **Sort Position ID** field enter *SP02*
1. Select **OK**
1. Work is completed on the container
1. Enter the *Container ID* for the remaining container from Sales Order 2 that has *Item A0002* into the **LP/Con** Field
    - Because the carrier service is the same as Sales Order 1, the system displays the sort position that exists with matching criteria.
1. Select **OK**
    - Confirm the sort position, in the **Sort Position ID** field enter *SP01*
1. Select **OK**
1. Work is completed on the container

### Close the Outbound Sorting positions

Once all inventory has been sorted, the position needs to be closed for work to be created. Sorted inventory picking work will be created to take the inventory to the Baydoor.

#### Close position from the mobile device

1. Login to **Warehouse** *62* on the Mobile app with the **User ID** created in the *Worker* setup, or an existing demo data user
1. Select **Outbound** from the *Main Menu*
1. Select **Pallet build** from the *Outbound* menu
    - Enter a *Container ID* (that was sorted onto the *SP01* position) in the **LP/Con** field
1. Select **OK**
1. A message displays "The container is already sorted to position SP01. Close the position?"
    - Select **Close**
1. Work is completed

#### Close position from Outbound sorting position assignments

1. Go to **Warehouse management > Packing and containerization > Outbound sorting position assignments**
1. In the left side column, select the row of the *Outbound sorting position* to close
    - Select **Outbound sorting position** - *SP02*
1. In the Action Pane, select **Close position**
    - The sorting record is closed and is no longer displayed
    - Select the **Show closed** box to show all closed position records

### Sorted inventory picking

Complete the sorted inventory picking work. Once completed the inventory will be picked to the sales order. All other warehouse processes apply at this point.

1. Login to **Warehouse** *62* on the Mobile app with the **User ID** created in the *Worker* setup, or an existing demo data user
1. Select **Outbound** from the *Main Menu*
1. Select **Load from Sorting** from the *Outbound* menu
1. Enter the **Target licence plate ID** from the first sort position *SP01*
    - **ID** - *PLP01*

1. Select **OK**
1. The *Sorted inventory picking: Pick* screen displays the pick work to be performed
    -Picking from the *SORT* location, Target LP *PLP01* with *Multiple* items and a quantity of *3*

1. Select **OK**
1. The *Sorted inventory picking: Put* screen displays the put work to be performed
    - Put to the *Baydoor* location, Target LP *PLP01* with *Multiple* items and a quantity of *3*

1. Select **OK**
1. Work is completed
1. Enter the **Target licence plate ID** from the second sort position *SP02*
    - **ID** - *PLP02*

1. Select **OK**
1. The *Sorted inventory picking: Pick* screen displays the pick work to be performed
    -Picking from the *SORT* location, Target LP *PLP02* with *Multiple* items and a quantity of *1*

1. Select **OK**
1. The *Sorted inventory picking: Put* screen displays the put work to be performed
    - Put to the *Baydoor* location, Target LP *PLP02* with *Multiple* items and a quantity of *1*

1. Select **OK**
1. Work is completed

All other warehouse processes apply from this point forward.
