---
# required metadata

title: Outbound sorting
description: This article provides information about outbound sorting. This functionality makes it easier to handle small containers, and helps warehouse workers better plan and organize pallet capacity in the truck.
author: Mirzaab
ms.date: 07/15/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
ms.search.form:  WHSPack, WHSOutboundSortTemplate, WHSOutboundSortPositionAssignments, WHSLocationType, WHSLoactionProfile
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2020-07-15
ms.dyn365.ops.version: 10.0.9
---

# Outbound sorting

[!include [banner](../includes/banner.md)]

This functionality makes it easier to handle small containers and helps warehouse workers better plan and organize pallet capacity in the truck. When you use outbound sorting, you can sort packed containers to the correct pallet after they have been at a packing station. You can also build a packing hierarchy.

This functionality lets you build pallets from containers that are packed through the packing functionality. The container isn't sent to the final shipping location as it is in the original packing flow. Instead, workers can close the container and move it to a sort type location. They can then sort containers to positions, each of which has a license plate (LP). After the containers have been sorted, work can be created to send the whole LP to the final shipping dock or stage locations, based on location directives or your own requirements. Additionally, the action of closing of the sort position can immediately move the inventory to the final shipping location and pick it to the order.

## Turn on the Outbound sorting feature

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.32, this feature is mandatory and can't be turned off. If you are running a version older than 10.0.32, then admins can turn this functionality on or off by searching for the *Outbound sorting* feature in the [**Feature management** workspace](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Setup

For this scenario, you must use standard **USMF** demo data and warehouse *62*. You must also complete the setup that is described in the following subsections.

### Set up a wave template

This setup automatically processes the wave and creates work when a line is released to the warehouse.

1. Go to **Warehouse management \> Setup \> Waves \> Wave templates**.
1. In the template list, select **Warehouse 62**.
1. On the **General** FastTab, make sure that the **Process wave at release to warehouse** option is set to *Yes*.

### Set up a worker

The packing station is considered a location. Warehouse workers who sign in at the packing station see and work on only shipments and containers that are planned at that specific packing location. A user who signs in to Microsoft Dynamics 365 must be set up as a worker in Warehouse management. If the user's name doesn't appear in the list of work users, use the following procedure to add it.

> [!NOTE]
> These steps assume that the user already exists in the system and has been associated as an employee or worker in the **Human Resources** module.

1. Go to **Warehouse management \> Setup \> Worker**.
1. Select **New**.
1. In the **Worker** field, select the target user in the list of employees.
1. Select **Select**.
1. On the Action Pane, select **Save**.
1. On the **Users** FastTab, select **New** to create a mobile device account, and set the following values for it:

    - **User ID:** Enter a unique ID.
    - **User name:** Enter a name for the ID.
    - **Default warehouse:** *62*
    - **Menu name:** *Main*

1. On the Action Pane, select **Save**.
1. The **Set password** dialog box appears, where you can create a simple password that the user can use to sign in to the mobile app. Set the following values:

    - **Password:** Enter a simple password.
    - **Confirm password:** Enter the same password again.

1. Select **Set password**.

    A notification in the Action Center informs you that the password has been set for the user that you created.

### Create a location type

1. Go to **Warehouse management \> Setup \> Warehouse \> Location types**.
1. On the Action Pane, select **New** to create a location type, and set the following values for it:

    - **Location type:** *SORT*
    - **Description:** *Sort*

1. On the Action Pane, select **Save**.

### Set up Warehouse management parameters

1. Go to **Warehouse management \> Setup \> Warehouse management parameters**.
1. On the **General** tab, on the **Location types** FastTab, set the **Sorting location type** field to *SORT*.
1. On the Action Pane, select **Save**.

### Set up a location profile

1. Go to **Warehouse management \> Setup \> Warehouse \> Location profiles**.
1. On the Action Pane, select **New**.
1. In the header, set the following values:

    - **Location profile ID:** *Sorting*
    - **Name:** *Sorting*

1. On the **General** FastTab, set the following values:

    - **Location format:** *ASRB* (Aisle-Rack-Shelf-Bin)
    - **Location type:** *SORT*
    - **Use license plate tracking:** *Yes*
    - **Allow mixed items:** *Yes* (When you set this option to *Yes*, the **Allow mixed inventory batches** option is automatically set to *Yes* and can't be changed independently.)

1. Select **Save**.

### Set up a location

1. Go to **Warehouse management \> Setup \> Warehouse \> Locations**.
1. In the header, clear the **Generate check digits for location** check box.
1. On the Action Pane, select **New** to create a location, and set the following values for it:

    - **Warehouse:** *62*
    - **Location:** *SORT*
    - **Location profile ID:** *SORTING*

1. Select **Save**.

### Set up an outbound sorting template

The outbound sorting template determines whether work is created out of the sort location, and whether sorting is done manually or automatically.

For this scenario, you will create an outbound sorting template to build pallets after the packing station.

1. Go to **Warehouse Management \> Setup \> Packing \> Outbound sorting template**.
1. On the Action Pane, select **New**.
1. In the header of the new template, set the following values:

    - **Outbound sorting template ID:** *AutoWork*
    - **Description:** *Auto Work Creation*
    - **Outbound sorting template type:** *Container*

1. Use the **Warehouse selection** FastTab to specify the warehouse and location where the outbound sorting template will apply.

    - **Warehouse selection** – Select one of the following values:

        - *All* – Use the outbound sorting template for all warehouses.
        - *Warehouse group* – Use the outbound sorting template for all warehouses in the warehouse group that's selected in the **Warehouse group** field.
        - *Warehouse* – Use the outbound sorting template only for the specific warehouse that's selected in the **Warehouse** field.

    - **Warehouse** and **Location** – If the **Warehouse selection** field is set to *Warehouse*, select the warehouse and the location where the outbound sorting template applies.
    - **Warehouse group** – If the **Warehouse selection** field is set to *Warehouse group*, select the warehouse group where the outbound sorting template applies. For more information about how to set up warehouse groups, see [Warehouse groups](warehouse-groups.md).

   For this scenario, set the following values:
    - **Warehouse selection:** *Warehouse*
    - **Warehouse:** *62*
    - **Location:** *SORT*

1. On the **General** FastTab, set the following values:

    - **Sort verification:** *Position scan*
    - **Create work on position close:** *Yes*

        If this option is set to *Yes*, when the position is closed, work will be created to move inventory to the final shipping location. If it's set to *No*, inventory will immediately be picked to the order when the position is closed.

    - **Position assignment:** *Automatic*

        If this field is set to *Manual*, the user must always indicate which position the inventory should be sorted to. If it's set to *Automatic*, the system will automatically guide the inventory to a position whenever it can, based on the sort template breaks.

1. Select **Save** to make the **Edit query** button on the Action Pane available.
1. On the Action Pane, select **Edit Query**.
1. In the query editor, on the **Sorting** tab, add a line that has the following values:

    - **Table:** *Shipments*
    - **Derived table:** *Shipments*
    - **Field:** *Carrier service*

        When you select this value, you might receive the following message: "Field Carrier service is not an index field. Do you want to add sorting on this?" Select **Yes**.

    - **Search direction:** *Ascending*

1. Select **OK**.
1. You might receive the following message: "Grouping will be reset, continue?" Select **Yes**.

    The **Outbound sorting template breaks** button on the Action Pane becomes available.

1. On the Action Pane, select **Outbound sorting template breaks**.
1. In the **Outbound sorting criteria** dialog box, set the following values:

    - **Reference table name:** *Shipments*
    - **Reference field name:** *Carrier service*
    - **Group by field:** Select this check box to group shipments by carrier service.

1. Select **OK** to save your settings and close the dialog box.

### Set up container packing policies

1. Go to **Warehouse management \> Setup \> Containers \> Container packing policies**.
1. On the Action Pane, select **New**.
1. In the header of the new policy, set the following values:

    - **Container packing policy:** *Sort*
    - **Description:** *Sort*

1. On the **Overview** FastTab, set the following values:

    - **Warehouse:** *62*
    - **Default location for sorting:** *SORT*
    - **Weight unit:** *kg*
    - **Container closing policy:** *Automatic release*
    - **Container release policy:** *Assign container to outbound sorting position*

1. Select **Save**.

### Set up packing profiles

Create a new packing profile that will be used together with the sorting functionality.

1. Go to **Warehouse management \> Setup \> Packing \> Packing profiles**.
1. On the Action Pane, select **New** to create a line, and set the following values for it:

    - **Packing profile ID:** *Sort*
    - **Description:** *Sort*
    - **Container packing policy:** *Sort*
    - **Container ID mode:** *Auto*
    - **Container type:** *Box-Large*
    - **Auto create container at container close:** Cleared (= *No*)

1. Select **Save**.

### Set up work classes

Set up a work class that will be used together with sorting.

1. Go to **Warehouse management \> Setup \> Work \> Work classes**.
1. On the Action Pane, select **New** to create a work class for sorting, and set the following values for it:

    - **Work class ID:** *Sort*
    - **Description:** *Sort*
    - **Work order type:** *Sorted inventory picking*

1. Select **Save**.

### Set up mobile device menu items

#### Set up a new pallet menu item

Create a mobile device menu item to build pallets during sorting.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. On the Action Pane, select **New**.
1. In the header, set the following values:

    - **Menu item name:** *Pallet build*
    - **Title:** *Pallet build*
    - **Mode:** *Indirect*
    - **Use existing work:** *No*

1. On the **General** FastTab, set the following values:

    - **Activity code:** *Outbound sorting*

        When this field is set to *Outbound sorting*, the **Outbound sorting template ID** field is shown.

    - **Use process guide:** *Yes*

        When the **Activity code** field is set to *Outbound sorting*, this option is automatically set to *Yes*.

    - **Outbound sorting template ID:** *AutoWork*

1. Select **Save**.

#### Set up a new loading menu item

Next, create a menu item that lets users move the sorted inventory items to the shipping location.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. On the Action Pane, select **New**.
1. In the header, set the following values:

    - **Menu item name:** *Load from Sorting*
    - **Title:** *Load from Sorting*
    - **Mode:** *Work*
    - **Use existing work:** *Yes*

1. On the **General** FastTab, set the **Directed by** field to *User directed*.
1. On the **Work classes** FastTab, select **New**, and then set the following values:

    - **Work class ID:** *SORT*
    - **Work order type:** *Sorted inventory picking*

1. Select **Save**.

### Set up the mobile device menu

You must now add the new menu items to the mobile device menu.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu**.
1. Select the **Outbound** menu.
1. On the Action Pane, select **Edit**.
1. In the **Available menus and menu items** column, find and select **Pallet build**.
1. Select the right arrow button to move **Pallet build** to the **Menu structure** column.
1. Use the up arrow and down arrow buttons to put the **Pallet build** menu item in the desired position on the mobile device menu.
1. Select **Save**.
1. Repeat this procedure to add the **Load from Sorting** menu item to the **Outbound** menu.

### Set up location directives

*Location directives* are rules that help identify pick and put locations for inventory movement. You must now create a rule to manage the sorting work.

#### Set up a single-SKU directive

1. Go to **Warehouse management \> Setup \> Location directives**.
1. In the left pane, change the value of the **Work order type** field to *Sorted inventory picking*.
1. On the Action Pane, select **New**.
1. In the header, set the following values:

    - **Sequence:** *1*
    - **Name:** *Baydoor*

1. On the **Location directives** FastTab, set the following values:

    - **Work type:** *Put*
    - **Site:** *6*
    - **Warehouse:** *62*
    - **Multiple SKU:** *No*

1. Select **Save** to make the toolbar on the **Lines** FastTab available.
1. On the **Lines** FastTab, select **New**, and then set the following values on the new line. Accept the default values for all the other fields.

    - **Sequence:** *1*
    - **From:** *0*
    - **To:** *1,000,000*

1. Select **Save** to make the toolbar on the **Location Directive Actions** FastTab available.
1. On the **Location Directive Actions** FastTab, select **New**, and then set the following values on the new line. Accept the default values for all the other fields.

    - **Sequence:** *1*
    - **Name:** *Baydoor*

1. Select **Save**.
1. On the **Location Directive Actions** FastTab, select **Edit query**.
1. In the query editor, on the **Range** tab, find the row where the **Field** field is set to *Location*. Set the **Criteria** field for this row to *Baydoor*.
1. Select **OK** to save your settings and close the query editor.

#### Set up a multiple-SKU directive

1. Go to **Warehouse management \> Setup \> Location directives**.
1. In the left pane, change the value of the **Work order type** field to *Sorted inventory picking*.
1. On the Action Pane, select **New**.
1. In the header, set the following values:

    - **Sequence:** *2*
    - **Name:** *Baydoor Multi*

1. On the **Location directives** FastTab, set the following values:

    - **Work type:** *Put*
    - **Site:** *6*
    - **Warehouse:** *62*
    - **Multiple SKU:** *Yes*

1. Select **Save** to make the toolbar on the **Lines** FastTab available.
1. On the **Lines** FastTab, select **New**, and then set the following values on the new line. Accept the default values for all the other fields.

    - **Sequence:** *1*
    - **From:** *0*
    - **To:** *1,000,000*

1. Select **Save** to make the toolbar on the **Location Directive Actions** FastTab available.
1. On the **Location Directive Actions** FastTab, select **New**, and then set the following values on the new line. Accept the default values for all the other fields.

    - **Sequence:** *1*
    - **Name:** *Baydoor Multi*

1. Select **Save**.
1. On the **Location Directive Actions** FastTab, select **Edit query**.
1. In the query editor, on the **Range** tab, find the row where the **Field** field is set to *Location*. Set the **Criteria** field for this row to *Baydoor*.
1. Select **OK** to save your settings and close the query editor.

### Set up work templates

1. Go to **Warehouse management \> Setup \> Work \> Work templates**.
1. Change the value of the **Work order type** field to *Sorted inventory picking*.
1. On the Action Pane, select **New** to create a work template.
1. On the **Overview** tab, set the following values:

    - **Sequence:** *1*
    - **Work template:** *Sort*
    - **Work template description:** *Sort*

1. Select **Save** to make the **Work Template Details** FastTab available.
1. On the **Work Template Details** FastTab, select **New** to add a line, and then set the following values for it:

    - **Work type:** *Pick*
    - **Work class ID:** *SORT*

1. Select **New** again to add a second line, and then set the following values for it:

    - **Work type:** *Put*
    - **Work class ID:** *SORT*

1. Select **Save**.

## Scenario

This scenario simulates a situation where packed containers should automatically be sorted to different positions (pallets) after the packing station, depending on the shipping carrier service. After all items from the load are packed and sorted by address, the pallets will be moved to the bay door.

### Create sales orders and picking work

#### Create sales order 1

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. On the Action Pane, select **New**.
1. In the **Create sales order** dialog box, set the following values:

    - **Customer account:** *US-005*
    - **Warehouse:** *62*

1. Select **OK** to close the dialog box.

    The new sales order is opened.

1. Switch to the **Header** view.
1. On the **Delivery** FastTab, in the **Transportation** section, set the following values:

    - **Shipping carrier:** *Air cargo*
    - **Carrier service:** *Air*

1. Switch to the **Lines** view.
1. If a new, empty line isn't automatically added to the grid on the **Sales order lines** FastTab, select **Add line** to add one.
1. On the new order line, set the following values:

    - **Item number:** *A0001*
    - **Quantity:** *2*

1. While the new order line is still selected on the **Sales order lines** FastTab, on the **Inventory** menu above the grid, select **Reservation**.
1. On the **Reservation** page, select **Reserve lot** to reserve the full quantity of the selected line in the warehouse.
1. Close the **Reservation** page to return to the sales order.
1. On the Action Pane, on the **Warehouse** tab, in the **Actions** group, select **Release to warehouse**.
1. You receive an informational message that shows the shipment and wave for this order. Make a note of the wave ID and shipment ID numbers.

#### Sales order 2

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. On the Action Pane, select **New**.
1. In the **Create sales order** dialog box, set the following values:

    - **Customer account:** *US-006*
    - **Warehouse:** *62*

1. Select **OK** to close the dialog box.
1. The new sales order is opened. It should include a new, empty line in the grid on the **Sales order lines** FastTab. Set the following values on this order line:

    - **Item:** *A0001*
    - **Quantity:** *1*

1. On the **Line details** FastTab, on the **Delivery** tab, set the **Mode of delivery** field to *Flowe-STD*.
1. On the **Sales order lines** FastTab, select **Add line**, and then set the following values on the second order line:

    - **Item:** *A0002*
    - **Quantity:** *1*

1. On the **Line details** FastTab, on the **Delivery** tab, change the value of the **Mode of delivery** field to *Air C-Air*.
1. On the **Sales order lines** FastTab, select the first order line. Then, on the **Inventory** menu above the grid, select **Reservation**.
1. On the **Reservation** page, select **Reserve lot** to reserve the full quantity of the selected line in the warehouse.
1. Close the **Reservation** page to return to the sales order.
1. On the **Sales order lines** FastTab, select the second order line. Then, on the **Inventory** menu above the grid, select **Reservation**.
1. On the **Reservation** page, select **Reserve lot** to reserve the full quantity of the selected line in the warehouse.
1. Close the **Reservation** page to return to the sales order.
1. On the Action Pane, on the **Warehouse** tab, in the **Actions** group, select **Release to warehouse**.
1. You receive an informational message that shows the shipment and wave for this order. Notice that two wave ID numbers and two shipment ID numbers have been created, one for each mode of delivery for the sales order lines.

#### Get the work IDs from the work details

1. Go to **Warehouse management \> Work \> Work details**.
1. The page shows the work IDs that have been created from sales orders. Use the wave IDs and shipment IDs from the sales orders that you created to find the work ID for each wave and shipment. Make a note of those work IDs, because you will need them in the next steps. Notice that two work IDs were created for the second sales order. If different items are picked from different locations, separate word IDs are generated.

### Pick items for the sales orders

Complete the created work by using the mobile device to move the items to the pack station.

1. On the mobile device, sign in to warehouse *62* by using the user ID that you created for this scenario (or the user ID of an existing demo data user).
1. On the main menu, select **Outbound**.
1. On the **Outbound** menu, select **Sales Picking**.
1. In the **ID** field, enter the work ID that was created for sales order 1.
1. Select **OK**.
1. On the **Sales orders - Pick** page, enter a target LP that was created for sales order 1. Notice that the picking location (*bulk-001*), item (*A0001*), and quantity (*2 pcs*) are shown.
1. Select **OK**.
1. Review the information on the **Sales orders - Put** page. The **Loc** field should indicate that the picked items are going to the *Pack* location.
1. Select **OK**.

    On the **Scan a work ID / license plate ID** page, you receive a "Work Completed" message, which indicates that the work ID from sales order 1 has been completed.

    You will now pick sales order 2.

1. In the **ID** field, enter the work ID that was created for sales order 2, where line 1 has item *A0001*.
1. Select **OK**.
1. On the **Sales orders - Pick** page, enter a target LP. Notice that the picking location (*bulk-001*), item (*A0001*), and quantity (*1 pcs*) are shown.
1. Select **OK**.
1. Review the information on the **Sales orders - Put** page. The **Loc** field should indicate that the picked items are going to the *Pack* location.
1. Select **OK**.

    On the **Scan a work ID / license plate ID** page, you receive a "Work Completed" message. This message indicates that the work ID from line 1 of sales order 2 has been completed.

1. In the **ID** field, enter the work ID that was created for sales order 2, where line 2 has item *A0002*.
1. Select **OK**.
1. On the **Sales orders - Pick** page, enter a target LP. Notice that the picking location (*bulk-002*), item (*A0001*), and quantity (*1 pcs*) are shown.
1. Select **OK**.
1. Review the information on the **Sales orders - Put** page. The **Loc** field should indicate that the picked items are going to the *Pack* location.
1. Select **OK**.

    On the **Scan a work ID / license plate ID** page, you receive a "Work Completed" message. This message indicates that the work ID from line 2 of sales order 2 has been completed.

### Pack sales orders into containers

#### Pack sales order 1 into containers

1. Go to **Warehouse management \> Packing and containerization \> Pack**.

    The **Select packing station** dialog box appears. By default, the **Worker** field should be set to the name of the worker that you set up earlier.

1. Set the following values to view and work on shipments and containers that are planned at the specific packing location:

    - **Site:** *6*
    - **Warehouse:** *62*
    - **Location:** *Pack*
    - **Packing profile ID:** *Sort*

1. Select **OK** to close the dialog box.
1. On the **Pack** page, in the **License plate or shipment** field, enter the target LP for sales order 1. Then select the **Tab** or **Enter** key on your keyboard to move out of the field.
1. On the Action Pane, select **New container**.
1. Accept all the default settings, and select **OK**. Make a note of the container ID.
1. On the **Item packing** FastTab, set the following values:

    - **Quantity:** *1*
    - **Identifier:** Item *A0001*

1. On the Action Pane, select **Close container**.
1. In the **Close container** dialog box, select **Get system weight** to have the system update the **Gross weight** field.
1. Select **OK**. The container is moved to the *SORT* location and is ready for sorting.
1. Create a second container to add the second item from the LP for sales order 1 to a new container.
1. On the Action Pane, select **New container**.
1. Accept all the default settings, and select **OK**. Make a note of the container ID.
1. On the **Item packing** FastTab, set the following values:

    - **Quantity:** *1*
    - **Identifier:** Item *A0001*

1. On the Action Pane, select **Close container**.
1. In the **Close container** dialog box, select **Get system weight** to have the system update the **Gross weight** field.
1. Select **OK**. The container is moved to the *SORT* location and is ready for sorting.

#### Pack sales order 2 into containers

1. On the **Pack** page, in the **License plate or shipment** field, enter the target LP for line 1 of sales order 2. Then select the **Tab** or **Enter** key on your keyboard to move out of the field.
1. On the Action Pane, select **New container**.
1. Accept all the default settings, and select **OK**. Make a note of the container ID.
1. On the **Item packing** FastTab, set the following values:

    - **Quantity:** *1*
    - **Identifier:** Item *A0001*

1. On the Action Pane, select **Close container**.
1. In the **Close container** dialog box, select **Get system weight** to have the system update the **Gross weight** field.
1. Select **OK**. The container is moved to the *SORT* location and is ready for sorting.
1. In the **License plate or shipment** field, enter the target LP for line 2 of the sales order 2. Then select the **Tab** or **Enter** key on your keyboard to move out of the field.
1. On the Action Pane, select **New container**.
1. Accept all the default settings, and select **OK**. Make a note of the container ID.
1. On the **Item packing** FastTab, set the following values:

    - **Quantity:** *1*
    - **Identifier field:** Item *A0002*

1. On the Action Pane, select **Close container**.
1. In the **Close container** dialog box, select **Get system weight** to have the system update the **Gross weight** field.
1. Select **OK**. The container is moved to the *SORT* location and is ready for sorting.

To view the container details, go to **Warehouse management \> Packing and containerization \> Containers**, and search for the container IDs that were created during packing.

### Sort the containers

> [!IMPORTANT]
> When you access the **Pallet build** menu item on the mobile app to do outbound sorting, you will see a button that is labeled **Full**. *Don't use the **Full** button to sort or close the position.*
>
> The **Full** button is provided by default and can't be disabled or removed from the page. It isn't used for the *Outbound sorting* feature.

#### Sort the first container

1. On the mobile device, sign in to warehouse *62* by using the user ID that you created for this scenario (or the user ID of an existing demo data user).
1. On the main menu, select **Outbound**.
1. On the **Outbound** menu, select **Pallet build**.
1. In the **LP/Con** field, enter the first container ID that is associated with sales order 1.
1. Select **OK**.
1. Because no sort positions currently exist, you must specify one. In the **Sort position ID** field, enter *SP01*.
1. Because no LP is currently associated with sort position *SP01*, you must specify one. In the **LP** field, enter *PLP01*.
1. Select **OK**.
1. Because sort position validation is turned on, you must enter the sort position ID again. In the **Sort Position ID** field, enter *SP01*.
1. Select **OK**.

    You receive a "Work completed" message.

> [!TIP]
> To view the sort position and the LP in it, go to **Warehouse management \> Packing and containerization \> Outbound sorting position assignments**.
>
> The **Outbound sorting position assignments** page shows all the sort positions that are currently active. The **Sort position transactions** field shows the LP that is associated with each sort position, and the containers that are in the sort position. Notice that one sort position currently exists, and that the **Sort position criteria** FastTab shows a criterion of **Shipment – Carrier service - Air**.

#### Sort the remaining containers

1. On the mobile device, sign in to warehouse *62* by using the user ID that you created for this scenario (or the user ID of an existing demo data user).
1. On the main menu, select **Outbound**.
1. On the **Outbound** menu, select **Pallet build**.
1. In the **LP/Con** field, enter the second container ID that is associated with sales order 1.
1. Select **OK**. Because the sorting template is set up to sort automatically, and a sort position that has matching criteria already exists, you're automatically directed to the correct sort position.
1. Select **OK**.
1. Confirm the sort position ID to indicate that the inventory is in the correct place. In the **Sort Position ID** field, enter *SP01*.
1. Select **OK**.

    Work is completed on the second container from sales order 1. You will now sort the remaining containers from sales order 2.

1. In the **LP/Con** field, enter the container ID of the container from sales order 2 that holds item *A0001*. Because the carrier service differs, you're prompted to enter a new sort position and assign an LP to that position. Use sort position *SP02* and LP *PLP02*.
1. Select **OK**.
1. Confirm the sort position by entering *SP02* in the **Sort Position ID** field.
1. Select **OK**.

    Work is completed on the container.

1. In the **LP/Con** field, enter the container ID for the remaining container from sales order 2 that holds item *A0002*. Because the carrier service is the same as the carrier service for sales order 1, the system shows the existing sort position that has matching criteria.
1. Select **OK**.
1. Confirm the sort position by entering *SP01* in the **Sort Position ID** field.
1. Select **OK**.

    Work is completed on the container.

### Close the outbound sorting positions

When all inventory has been sorted, the position must be closed before work can be created. Sorted inventory picking work will be created to take the inventory to the bay door.

#### Close a position from the mobile device

1. On the mobile device, sign in to warehouse *62* by using the user ID that you created for this scenario (or the user ID of an existing demo data user).
1. On the main menu, select **Outbound**.
1. On the **Outbound** menu, select **Pallet build**.
1. In the **LP/Con** field, enter a container ID that was sorted to sort position *SP01*.
1. Select **OK**.
1. You receive the following message: "The container is already sorted to position SP01. Close the position?" Select **Close**.

    Work is completed.

#### Close a position from outbound sorting position assignments

1. Go to **Warehouse management \> Packing and containerization \> Outbound sorting position assignments**.
1. In the left column, select **SP02**. This outbound sorting position row is the one that you will close.
1. On the Action Pane, select **Close position**. The sorting position record is closed and is no longer shown.

    > [!TIP]
    > To show all closed position records, select the **Show closed** check box.

### Sorted inventory picking

You must complete the sorted inventory picking work. When it's completed, the inventory will be picked to the sales order. At that point, all other warehouse processes apply.

1. On the mobile device, sign in to warehouse *62* by using the user ID that you created for this scenario (or the user ID of an existing demo data user).
1. On the main menu, select **Outbound**.
1. On the **Outbound** menu, select **Load from Sorting**.
1. Enter the target LP ID from the first sort position, *SP01*. Set the **ID** field to *PLP01*.
1. Select **OK**.
1. The **Sorted inventory picking: Pick** page shows the pick work that must be done. Pick from the *SORT* location and target LP *PLP01*, which has multiple items and a quantity of *3*.
1. Select **OK**.
1. The **Sorted inventory picking: Put** page shows the put work that must be done. Put to the *Baydoor* location and target LP *PLP01*, which has multiple items and a quantity of *3*.
1. Select **OK**.

    Work is completed.

1. Enter the target license plate ID from the second sort position, *SP02*. Set the **ID** field to *PLP02*.
1. Select **OK**.
1. The **Sorted inventory picking: Pick** page shows the pick work that must be done. Pick from the *SORT* location and target LP *PLP02*, which has multiple items and a quantity of *1*.
1. Select **OK**.
1. The **Sorted inventory picking: Put** page shows the put work that must be done. Put to the *Baydoor* location and target LP *PLP02*, which has multiple items and a quantity of *1*.
1. Select **OK**.

    Work is completed.

From this point forward, all other warehouse processes apply.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]