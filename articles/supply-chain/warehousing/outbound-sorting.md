---
# required metadata

title: Outbound sorting
description: Outbound sorting makes it easier to handle small containers and will enable warehouse workers to better plan and organize pallet capacity within the truck.
author: Mirzaab
manager: tfehr
ms.date: 06/10/2020
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
ms.search.validFrom: 2020-06-10
ms.dyn365.ops.version: Release 10.0.9
---

# Outbound sorting

[!include [banner](../includes/banner.md)]

This functionality makes it easier to handle small containers and will enable warehouse workers to better plan and organize pallet capacity within the truck.

With outbound sorting, you can sort packed containers to the correct pallet after a packing station and build a packing hierarchy.

This functionality lets you build pallets from containers packed through the packing functionality. The container is not sent to the final shipping location as it would be in the original packing flow. Instead, this functionality allows workers to close the container and move it to a sort type location. They can then sort containers onto positions, each position has a license plate. Once the containers have been sorted, work can be created to send the whole license plate to the final shipping dock or stage locations based on location directives of your own requirements. The closing of the sort position can also immediately move the inventory to the final shipping location and pick it to the order.

## Enable the Outbound sorting feature

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - *Warehouse management*
- **Feature name** - *Outbound sorting*

## Setup

For this scenario, you must use standard **USMF** demo data with Warehouse 62 and make the additional set up steps noted below.

### Set up a wave template

This setting automatically processes the Wave and creates work when a line is released to the warehouse.

1. Go to **Warehouse management > Setup > Waves > Wave templates**.
1. In the template list, select **Warehouse 62**.
1. Ensure that in the **General** FastTab, **Process wave at release to warehouse** is set to **Yes**.

### Set up a worker

The packing station is seen as a location. When the warehouse workers are logging in at the packing station, they will only see and operate on shipments and containers that are planned at the specific packing location. The user signing into Dynamics 365 must be set up as a **Worker** in Warehouse management. If the user's name doesn't appear in the list of work users, use the following procedure to add them.

>[!NOTE]
>These steps assume that the user already exists in the system and has been associated as an employee or worker in the Human Resources module.

1. Go to **Warehouse management > Setup > Worker**.
1. Select **New**.
1. Open the **Worker** drop-down list to open the list of employees and select the target user.
1. Select the **Select** button.
1. Select **Save** on the Action Pane.
1. On the **Users** Toolbar, select **New** to create a mobile device account and make the following settings for it:
    - **User ID** - Enter a unique ID
    - **User name** - Enter a name for the ID
    - **Default warehouse** - *62*
    - **Menu name** - *Main*
1. Select **Save** on the Action Pane.

1. The **Set password** dialog box opens, which lets you create a simple password for the user to log in to the mobile app.
    - **Password** - Enter a simple password
    - **Confirm password** - Enter the same password again

1. Select **Set password**, a notification is sent to the Action center stating that the password has been set for user that your created.

### Create a location type

1. Go to **Warehouse management > Setup > Warehouse > Location types**.
1. Select **New** on the Action Pane.
1. Enter the following to create new location type:
    - **Location type** - *SORT*
    - **Description** - *Sort*
1. Select **Save** on the Action Pane.

### Set up warehouse management parameters

1. Go to **Warehouse management > Setup > Warehouse management parameters**.
1. Select **General** tab and expand the **Location types** FastTab.
1. Set **Sorting location type** to *SORT*.
1. Select **Save** on the Action Pane.

### Set up a location profile

1. Go to **Warehouse management > Setup > Warehouse > Location profiles**.
1. Select **New** on the Action Pane.
1. Enter the following in the header:
    - **Location profile ID** – *Sorting*
    - **Name** – *Sorting*

1. On the **General** FastTab, make the following settings:
    - **Location format** – *ASRB* (Aisle-Rack-Shelf-Bin)
    - **Location type** – *SORT*
    - **Use license plate tracking** – *Yes*
    - **Allow mixed items** – *Yes* (**Allow mixed inventory batches** - is automatically changed to *Yes* and can't be changed independently.)

1. Select **Save**.

### Set up a location

1. Go to **Warehouse management > Setup > Warehouse > Locations**.
1. Unselect **Generate check digits for location** in the header.
1. Select **New** from the Action Pane to create a new *Location*. Enter the following:
    - **Warehouse** – *62*
    - **Location** – *SORT*
    - **Location profile ID** – *SORTING*

1. Select **Save**.

### Set up an outbound sorting template

The outbound sorting template determines if work will be created out of the sort location and how sorting will take place, either manually or automatically.

For this scenario, you will create an outbound sorting template for pallet building after the packing station.

1. Go to **Warehouse Management > Setup > Packing > Outbound sorting template**.
1. Select **New** on the Action Pane.
1. In the header of the new template, enter the following:
    - **Outbound sorting template ID** – *AutoWork*
    - **Description** – *Auto Work Creation*
    - **Outbound sorting template type** – *Container*
    - **Warehouse** - *62*
    - **Location** – *SORT*
1. On the **General** FastTab, enter the following:
    - **Sort verification** – *Position scan*
    - **Create work on position close** – *Yes*  
        When this is enabled, work will be created when the position is closed to move inventory to the final shipping location. When disabled, inventory will be immediately picked to the order at the time of position close.
    - **Position assignment** - *Automatic*  
        When set to *Manual*, the user must always indicate which position the inventory should be sorted to. When set to *Automatic*, the system will automatically guide the inventory to a position when possible, based on the sort template breaks.

1. Select **Save** to enable **Edit query**.
1. On the Action Pane, select **Edit Query** to open the query editor. Go to the **Sorting** tab and add a new line with the following settings:
    - **Table** – *Shipments*
    - **Derived table** – *Shipments*
    - **Field** – *Carrier service*  
        Select **Yes** if you see the message: "Field Carrier service is not an index field. Do you want to add sorting on this?"
    - **Search direction** – *Ascending*

1. Select **OK**.
    - Select **Yes** if you see the message: "Grouping will be reset, continue?"
    - This will enable the **Outbound sorting template breaks** button on the Action Pane.

1. Select **Outbound sorting template breaks** on the Action Pane. The **Outbound sorting criteria** dialog box opens. Make the following selection:
    - **Reference table name** - *Shipments*
    - **Reference field name** - *Carrier service*
    - Select the **Group by field** check box to group shipments by Carrier service.

1. Select **OK** to save you settings and close the dialog box.

### Set up container packing policies

1. Go to **Warehouse management > Setup > Containers > Container packing policies**.
1. Select **New** on the Action Pane.
1. In the header enter the following:
    - **Container packing policy** – *Sort*
    - **Description** – *Sort*

1. On the **Overview** FastTab, enter the following:
    - **Warehouse** – *62*
    - **Default location for sorting** – *SORT*
    - **Weight unit** – *kg*
    - **Container closing policy** – *Automatic release*
    - **Container release policy** – *Assign container to outbound sorting position*

1. Select **Save**.

### Set up packing profiles

Create a new packing profile to be used with sorting functionality.

1. Go to **Warehouse management > Setup > Packing > Packing profiles**.
1. On the Action Pane select **New**.
1. In the new line created, enter the following:
    - **Packing profile ID** – *Sort*
    - **Description** – *Sort*
    - **Container packing policy** - *Sort*
    - **Container ID mode** – *Auto*
    - **Container type** – *Box-Large*
    - **Auto create container at container close** – *No* (unselected)

1. Select **Save**.

### Work classes

Set up a work class to be used with sorting.

1. Go to **Warehouse management > Setup > Work > Work classes**.
1. Select **New** from the Action Pane.
and create new Work class for Sorting:
    - **Work class ID** – *Sort*
    - **Description** – *Sort*
    - **Work order type** – *Sorted inventory picking*

1. Select **Save**.

### Set up mobile device menu items

#### Set up a new pallet menu item

Create a mobile device menu item to build pallets during sorting.

1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu items**.
1. Select **New** from the Action Pane.
1. In the header, enter the following:
    - **Menu item name** – *Pallet build*
    - **Title** – *Pallet build*
    - **Mode** – *Indirect*
    - **Use existing work** – *No*

1. On the **General** FastTab, enter the following:
    - **Activity code** – *Outbound sorting*  
        When selected, the **Outbound sorting template ID** field is displayed.
    - **Use process guide** - *Yes*  
        When **Activity code** is set to *Outbound sorting*, this is automatically set to *Yes*.
    - **Outbound sorting template ID** – *AutoWork*

1. Select **Save**.

#### Set up a new loading menu item

This menu item allows users to move the sorted inventory items to the shipping location.

1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu items**.
1. Select **New** from the Action Pane.
1. In the header, enter the following:
    - **Menu item name** – *Load from Sorting*
    - **Title** – *Load from Sorting*
    - **Mode** – *Work*
    - **Use existing work** – *Yes*

1. On the **General** FastTab, set **Directed by** to *User directed*.

1. On the **Work classes** Toolbar, select **New** and enter the following:
    - **Work class ID** - *SORT*
    - **Work order type** - *Sorted inventory picking*

1. Select **Save**.

### Set up the mobile device menu

Now you must add the new menu items to the mobile device menu. Do the following:

1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu**.
1. Select the **Outbound** menu.
1. Select **Edit** from the Action Pane.
1. Locate and select **Pallet build** in the **Available menus and menu items** column.
1. Select the right-arrow button ( **→** ) to move **Pallet build** to the **Menu structure** column.
1. Use the up and down arrows to place the **Pallet build** item at the desired position on the mobile device menu.
1. Select **Save**.
1. Repeat this procedure to add **Load from Sorting** to the **Outbound** menu.

### Set up location directives

*Location directives* are rules that help identify pick and put locations for inventory movement. Create a rule to manage the sorting work.

#### Set up a single-SKU directive

1. Go to **Warehouse management > Setup > Location directives**.
1. In the directives list, change **Work order type** to *Sorted inventory picking*.
1. On the Action Pane, select **New**.
1. In the header enter the following:
    - **Sequence** – *1*
    - **Name** – *Baydoor*

1. On the **Location directives** FastTab, enter the following:
    - **Work type** – *Put*
    - **Site** – *6*
    - **Warehouse** – *62*
    - **Multiple SKU** - *No*

1. Select **Save** to enable the *Lines* Toolbar.
1. On the **Lines** Toolbar, select **New** on the Action Pane and enter the following on the new line:
    - **Sequence** – *1*
    - **From** – *0*
    - **To** – *1,000,000*
    - Accept the defaults for the remaining fields.

1. Select **Save** to enable the *Location Directive Actions* Toolbar.
1. On the **Location directive actions** Toolbar, select **New** on the Action Pane and enter the following on the new line:
    - **Sequence** – *1*
    - **Name** – *Baydoor*
    - Accept the defaults for the remaining fields.

1. Select **Save**
1. On the **Location directive actions** FastTab, select **Edit query**.
1. The query editor opens. On the **Range** tab, find the row where **Field** = *Location* and set its **Criteria** to *Baydoor*.
1. Select **OK** to save your setting and close the query editor.

#### Set up a multiple-SKU directive

1. Go to **Warehouse management > Setup > Location directives**
1. In the directives list, change **Work order type** to *Sorted inventory picking*.
1. On the Action Pane, select **New**.
1. In the header enter the following:
    - **Sequence** – *2*
    - **Name** – *Baydoor Multi*

1. On the **Location directives** FastTab, enter the following:
    - **Work type** – *Put*
    - **Site** – *6*
    - **Warehouse** – *62*
    - **Multiple SKU** - *Yes*

1. Select **Save** to enable the **Lines** Toolbar.
1. On the **Lines** Toolbar, select **New** on the Action Pane and enter the following on the new line:
    - **Sequence** – *1*
    - **From** – *0*
    - **To** – *1,000,000*
    - Accept the defaults for the remaining fields.

1. Select **Save** to enable the **Location Directive Actions** Toolbar.
1. On the **Location directive actions** Toolbar, select **New** on the Action Pane and enter the following on the new line:
    - **Sequence** – *1*
    - **Name** – *Baydoor Multi*
    - Accept the defaults for the remaining fields.

1. Select **Save**
1. On the **Location directive actions** Toolbar, select **Edit query**.
1. The query editor opens. On the **Range** tab, find the row where **Field** = *Location* and set its **Criteria** to *Baydoor*.
1. Select **OK** to save your setting and close the query editor.

### Set up work templates

1. Go to **Warehouse management > Setup > Work > Work templates**
1. Change the **Work order type** to *Sorted inventory picking*.
1. Select **New** from the Action Pane to create a new work template
1. On the **Overview** tab, enter the following:
    - **Sequence** – *1*
    - **Work template** – *Sort*
    - **Work template description** – *Sort*

1. Select **Save** to enable the *Work Template Details*
1. In **Work Template Details** select **New** to add a new line and enter the following for it:
    - **Work type** - *Pick*
    - **Work class ID** - *SORT*

1. In **Work Template Details** select **New** to a second new line and enter the following for it:
    - **Work type** - *Put*
    - **Work class ID** - *SORT*

1. Select **Save**.

## Scenario

This scenario will simulate a situation where the packed containers should be automatically sorted to different positions (pallets) after the packing station, based on the shipping carrier service. After all items from the load are packed and sorted by address, the pallets will be moved to the baydoor.

### Create sales orders and picking work

#### Create sales order 1

1. Go to **Sales and marketing > Sales orders > All sales orders**
1. Select **New** on the Action Pane.
1. The **Create sales order** dialog box opens. Enter the following:
    - **Customer account** = *US-005*
    - **Warehouse** = *62*

1. Select **OK** to close the dialog box.
1. Your new sales order opens.
1. Select the **Header** section tab and then expand the **Delivery** FastTab. Enter the following in the **Transportation** section:
    - **Shipping carrier** - *Air cargo*
    - **Carrier service** - *Air*

1. Select the **Lines** section tab.
1. If a new line is not automatically opened, select **Add line** on the **Sales order lines** Toolbar. Enter the following values for the new line:
    - **Item number** - *A0001*
    - **Quantity** - *2*

1. With the new order line still selected, open the **Inventory** menu the **Sales order lines** Toolbar and then select **Reservation** from the menu.
1. The **Reservation** page opens. Select **Reserve lot** to reserve your selected line's full quantity in the warehouse.

1. Close the **Reservation** page to return to your sales order.
1. On the Action Pane, open the **Warehouse** tab and, from the **Actions** group, Select **Release to warehouse**.
1. An informational message displays with the shipment and wave for this order. Note the **Wave ID** and **Shipment ID** numbers.  

#### Sales order 2

1. Go to **Sales and marketing > Sales orders > All sales orders**.
1. Select **New** from the Action Pane.
1. On the **Create sales order dialog box, enter the following:
    - **Customer account** = *US-006*
    - **Warehouse** = *62*

1. Select **OK** to close the dialog box.
1. Your new sales order opens. It should include a new, empty line in the **Sales order lines** table. Enter the following values for this first order line:
    - **Item** - *A0001*
    - **Quantity** - *1*

1. Expand the **Line details** FastTab and open its **Delivery** tab. Then set **Mode of delivery** to *Flowe-STD*.

1. On the **Sales order lines** Toolbar, select **Add line** and enter the following values for the second order line:
    - **Item** - *A0002*
    - **Quantity** - *1*

1. On the **Line details** FastTab select the **Delivery** tab and change the **Mode of delivery** to *Air C-Air*.

1. On the **Sales order lines** FastTab, select the first order line.
1. Open the **Inventory** menu on the **Sales order lines** Toolbar and then select **Reservation** from the menu.
1. The **Reservation** page opens. Select **Reserve lot** to reserve your selected line's full quantity in the warehouse.

1. Close the **Reservation** page to return to your sales order.
1. Select the second order line on the **Sales order lines** FastTab
1. Open the **Inventory** menu on the **Sales order lines** Toolbar and then select **Reservation** from the menu.
1. The **Reservation** page opens. Select **Reserve lot** to reserve your selected line's full quantity in the warehouse.

1. Close the **Reservation** page to return to your sales order.
1. On the Action Pane, open the **Warehouse** tab and, from the **Actions** group, select **Release to warehouse**.
1. An informational message displays with the shipment and wave for this order.Note that two **Wave ID** numbers and two **Shipment ID** numbers are created, one for each Mode of delivery for the sales order lines.

#### Get the work IDs from work details

1. Go to **Warehouse management > Work > Work details**. Here you can see the work IDs that have been created form sales orders.
1. Using the wave IDs and shipment IDs from the sales orders you created find, and make note of the **Work ID** for each Wave/Shipment. You will use these work IDs in the following steps. Note that two Work IDs were created for the second sales order. Picking different items from different locations will generate two work IDs.

### Pick items for the sales orders

Complete the created work using the mobile device to the pack station.

1. Log in to **Warehouse** *62* on the mobile app with the **User ID** you created for this scenario (or an existing demo data user).
1. Select **Outbound** from the **Main Menu**.
1. Select **Sales Picking** from the **Outbound** menu.
1. In the **ID** field, enter the work ID created for sales order 1.

1. Select **OK**
1. Enter a **Target LP** (license plate) created for sales order 1 on the **Sales orders - Pick** screen. Note that the picking location (*bulk-001*), item (*A0001*), and quantity (*2 pcs*) are displayed.

1. Select **OK**. Confirm the information shown on the  **Sales orders - Put** screen. The picked items should be going into **Loc** - *Pack*.

1. Select **OK**
1. A **Work Completed** message is displayed on the *Scan a work ID / license plat ID* screen indicating that the *Work ID* from Sales Order 1 has been completed.

1. Pick the second sales order.

1. In the **ID** field, enter the work ID created for sales order 2, with **Line 1** - *Item A0001*.
1. Select **OK**.
1. Enter a **Target LP** (license plate) on the **Sales orders - Pick** screen. Note that the picking location (*bulk-001*), item (*A0001*) and quantity (*1 pcs*) are displayed.

1. Select **OK**. Confirm the information shown on the **Sales orders - Put** screen. The picked item should be going into **Loc** - *Pack*.

1. Select **OK**
1. A **Work Completed** message is displayed on the **Scan a work ID / license plat ID** screen indicating that the work ID from sales order 2, line 1 has been completed.
1. In the **ID** field, enter the work ID  created for sales order 2, with **Line 2** - *Item A0002*.
1. Select **OK**.
1. Enter a **Target LP** (license plate) on the **Sales orders - Pick** screen. Note that the picking location (*bulk-002*), item (*A0001*) and quantity (*1 pcs*) are displayed.

1. Select **OK**. Confirm the information shown on the **Sales orders - Put** screen. The picked item should be going into **Loc** - *Pack*.

1. Select **OK**
1. A **Work Completed** message is displayed on the **Scan a work ID / license plat ID** screen indicating that the work ID from sales order 2, line 2 has been completed.

### Pack sales orders into containers

#### Pack sales order 1 into containers

1. Go to **Warehouse management > Packing and containerization > Pack**.
1. The **Select packing station** dialog box opens. The **Worker** field should default to the worker's name you set up earlier. Enter the following to view and operate on shipments and containers that are planned at the specific packing location:
    - **Site** - *6*
    - **Warehouse** – *62*
    - **Location** – *Pack*
    - **Packing profile ID** – *Sort*

1. Select **OK** to close the dialog box.
1. The **Pack** page opens. In the **License plate or shipment** field, enter the target license plate for first sales order. Hit the *Tab* or *Enter* key on your keyboard to exit the field.
1. On the Action Pane, select **New container**.
1. Leave all settings at their defaults and select **OK**. Make note of the **Container ID**.
1. On the **Item packing** FastTab, enter the following:
    - **Quantity** - *1*
    - **Identifier** - *Item* - *A0001*

1. On the Action Pane, select **Close container**.
1. The **Close container** dialog box opens. Select **Get system weight** to have the system update the **GROSS WEIGHT** field.
1. Select **OK**. The container will be moved to the **SORT** location and is ready for sorting.
1. Create a second container to add the second item from the sales order 1 license plate to a new container.
1. On the Action Pane, select **New container**.
1. Accept the Defaults and select **OK**. Make note of the **Container ID**.
1. On the **Item packing** FastTab, enter the following:
    - **Quantity** - *1*
    - **Identifier** - *Item* - *A0001*

1. On the Action Pane, select **Close container**.
1. The **Close container** dialog box opens. Select **Get system weight** to have the system update the **GROSS WEIGHT** field.
1. Select **OK**. The container will be moved to the **SORT** location and is ready for sorting.

#### Pack sales order 2 into containers

1. You should still be on the **Pack** page.
1. In the **License plate or shipment** field, enter the target license plate for Line 1 of the second sales order. Hit the *Tab* or *Enter* key on your keyboard to exit the field.
1. On the Action Pane, select **New container**.
1. Accept the Defaults and select **OK**. Make note of the **Container ID**.
1. On the **Item packing** FastTab, enter the following:

    - **Quantity** - *1*
    - **Identifier** - *Item* - *A0001*

1. On the Action Pane, select **Close container**.
1. The **Close container** dialog box opens. Select **Get system weight** to have the system update the **GROSS WEIGHT** field.
1. Select **OK**. The container will be moved to the **SORT** location and is ready for sorting.
1. In the **License plate or shipment** field, enter the target license plate for Line 2 of the second sales order. Hit the *Tab* or *Enter* key on your keyboard to exit the field.
1. On the Action Pane, select **New container**.
1. Accept the Defaults and select **OK**. Make note of the *Container ID*
1. On the **Item packing** FastTab, enter the following:

    - **Quantity** - *1*
    - **Identifier field** - *Item* - *A0002*

1. On the Action Pane, select **Close container**.
1. The **Close container** dialog box opens. Select **Get system weight** to have the system update the **GROSS WEIGHT** field.
1. Select **OK**. The container will be moved to the **SORT** location and is ready for sorting.

To view the container details, go to **Warehouse management > Packing and containerization > Containers** and search for the container IDs created during packing.

### Sort the containers

> [!CAUTION]
> When you access the **Pallet build** menu item on the mobile app to perform outbound sorting, you will see a button option labeled **Full**. *Do not use the **Full** button to sort or close the position*.
>
> The **Full** button is provided by default and can't be disabled or removed from the form. It isn't used for the outbound sorting feature.

#### Sort the first container

1. Log in to **Warehouse** *62* on the mobile app with the **User ID** you created for this scenario (or an existing demo data user).
1. Select **Outbound** from the **Main Menu**.
1. Select **Pallet build** from the **Outbound** menu.
1. In the **LP/Con** field, enter the first container ID associated with the sales order 1.
1. Select **OK**.
1. Because no sort positions currently exist, you must specify one. In the **Sort position ID** field, enter *SP01*.
1. Because there is no license plate currently associated with **Sort position** *SP01*, you must specify one. In the **LP** field, enter *PLP01*.
1. Select **OK**
1. Sort position validation is enabled, so you must enter the **Sort position ID** again. Enter *SP01* in the **Sort Position ID** field
1. Select **OK**.
1. A *Work completed* message is displayed.

> [!TIP]
> Go to **Warehouse management > Packing and containerization > Outbound sorting position assignments** to view the sorting position and license plate in the position.
>
> This page shows all the sort positions that are currently active. The **Sort position transactions** field shows the license plate associated with each, and which containers are in the sort position. Note that one sort position currently exists, and on the **Sort position criteria** FastTab, it shows a criteria of **Shipment – Carrier service - Air**.

#### Sort the remaining containers

1. Go to the mobile app.
1. Log in to **Warehouse** *62* on the mobile app with the **User ID** you created for this scenario (or an existing demo data user).
1. Select **Outbound** from the **Main Menu**.
1. Select **Pallet build** from the **Outbound** menu.
1. In the **LP/Con** field, enter the second container ID associated with the sales order 1.
1. Select **OK**. Because the sorting template is setup to sort automatically, and there is already a sort position that exists with matching criteria, you are automatically directed to the correct sort position.
1. Select **OK**.
1. Confirm the **Sort Position ID** by entering the sort position *SP01* to show that the inventory is in right place.
1. Select **OK**.
1. Work is completed on the second container from sales order 1.
1. Sort the remaining containers from sales order 2.
1. In the **LP/Con** field, enter the **Container ID** containing *Item A0001* from the second order. Because the carrier service is different, you are prompted to enter and new sort position (use *SP02*) and assign a license plate to that position (*PLP02*).
1. Select **OK**.
1. Confirm the sort position by entering *SP02* in the **Sort Position ID** field.
1. Select **OK**.
1. Work is completed on the container.
1. Enter the container ID for the remaining container from sales 2, which has *Item A0002* in the **LP/Con** field. Because the carrier service is the same as Sales Order 1, the system displays the sort position that exists with matching criteria.
1. Select **OK**.
1. Confirm the sort position by entering *SP01* in the **Sort Position ID** field.
1. Select **OK**.
1. Work is completed on the container.

### Close the Outbound Sorting positions

Once all inventory has been sorted, the position needs to be closed for work to be created. Sorted inventory picking work will be created to take the inventory to the baydoor.

#### Close position from the mobile device

1. Log in to **Warehouse** *62* on the mobile app with the **User ID** you created for this scenario (or an existing demo data user).
1. Select **Outbound** from the **Main Menu**.
1. Select **Pallet build** from the **Outbound** menu.
1. Enter a container ID (that was sorted onto the *SP01* position) in the **LP/Con** field.
1. Select **OK**.
1. The following message displays: "The container is already sorted to position SP01. Close the position?" Select **Close**.
1. Work is completed.

#### Close position from outbound sorting position assignments

1. Go to **Warehouse management > Packing and containerization > Outbound sorting position assignments**.
1. In the left side column, select **SP02**. This is the outbound sorting position row that you will close.
1. On the Action Pane, select **Close position**. The sorting record is closed and is no longer displayed.
1. Select the **Show closed** box to show all closed position records.

### Sorted inventory picking

Complete the sorted inventory picking work. Once completed, the inventory will be picked to the sales order. All other warehouse processes apply at this point.

1. Log in to **Warehouse** *62* on the mobile app with the **User ID** you created for this scenario (or an existing demo data user).
1. Select **Outbound** from the **Main Menu**
1. Select **Load from Sorting** from the **Outbound** menu
1. Enter the **Target license plate ID** from the first sort position *SP01*. Set **ID** to *PLP01*.
1. Select **OK**.
1. The **Sorted inventory picking: Pick** screen displays the pick work to be performed. Pick from the *SORT* location, target license plate *PLP01* with *Multiple* items and a quantity of *3*.
1. Select **OK**.
1. The **Sorted inventory picking: Put** screen displays the put work to be performed. Put to the *Baydoor* location, target license plate *PLP01* with *Multiple* items and a quantity of *3*
1. Select **OK**.
1. Work is completed.
1. Enter the **Target license plate ID** from the second sort position *SP02*. Set **ID** to *PLP02*.
1. Select **OK**
1. The **Sorted inventory picking: Pick** screen displays the pick work to be performed. Pick from the *SORT* location, target license plate *PLP02* with *Multiple* items and a quantity of *1*.
1. Select **OK**.
1. The **Sorted inventory picking: Put** screen displays the put work to be performed. Put to the *Baydoor* location, target license plate *PLP02* with *Multiple* items and a quantity of *1*.
1. Select **OK**
1. Work is completed

All other warehouse processes apply from this point forward.
