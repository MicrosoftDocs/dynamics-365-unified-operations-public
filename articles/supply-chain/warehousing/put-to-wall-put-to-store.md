---
# required metadata

title: Put to wall - put to store
description: This article provides information about the Put to wall - put to store functionality. This functionality lets you handle scenarios where you must consolidate a product to a prepack staging area, based on configurable criteria. It helps decrease picking time because it allows for picking to a single target license plate and can use more put positions than cluster picking.
author: Mirzaab
ms.date: 07/16/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
ms.search.form: WHSLocationType, WHSLocationProfile, WHSLocation, WHSPackProfile, WHSWaveStepCode, WHSOutboundSortTemplate, WHSPostMethod, WHSWaveTemplateTable, WHSLocDirTable, WHSWorkClass, WHSWorkTemplateTable
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2020-07-16
ms.dyn365.ops.version: 10.0.9
---

# Put to wall - put to store

[!include [banner](../includes/banner.md)]

The *Put to wall - put to store* functionality lets you handle scenarios where you must consolidate a product to a prepack staging area, based on configurable criteria. Because this functionality allows for picking to a single target license plate and can use more put positions than cluster picking, companies that ship to stores or handle small items will benefit from decreased picking time.

The workflow for this functionality directs picked product to a sorting location for distribution into various types of containers. Generally, each sorting location includes multiple sort positions. Each sort position is assigned according to the criteria that are set by the business process. Typical criteria are the final destination, shipment, or load. After a product arrives, it's distributed to each sort position, based on the quantity that is associated with the order, destination, shipment, or load. When a container is full or complete, it's moved to a staging location or a shipping location for further handling, depending on the business process.

This warehousing functionality is also referred to by other names, such as put-to-light and break opens.

## Turn on the Outbound sorting feature

To use the *Put to wall - put to store* functionality, two features must be turned on for your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of these features and turn them on if necessary. Both of the following features are required:

- *Outbound sorting* (As of Supply Chain Management version 10.0.32, this feature is mandatory and can't be turned off.)
- *Organization wide wave step code* (As of Supply Chain Management version 10.0.32, this feature is mandatory and can't be turned off.)

## Setup

For this demo, standard Contoso data and warehouse *62* are used. Some additions that are noted later are also used.

### Location type

1. Go to **Warehouse management \> Setup \> Warehouse \> Location types**.
1. On the Action Pane, select **New** to create a location type for sorting.
1. Set the following values:

    - **Location type:** *SORT*
    - **Description:** *Sort*

1. Select **Save**.

### Warehouse management parameters

1. Go to **Warehouse management \> Setup \> Warehouse management parameters**.
1. On the **General** tab, on the **Location types** FastTab, in the **Sorting location type** field, enter *SORT*.
1. Select **Save**.

### Location profile

1. Go to **Warehouse management \> Setup \> Warehouse \> Location profiles**.
1. On the Action Pane, select **New** to create a location profile for the sorting location.
1. In the header, set the following values:

    - **Location profile ID:** *Sort*
    - **Name:** *Sort*

1. On the **General** FastTab, set the following values:

    - **Location format:** *PACK*
    - **Location type:** *SORT*
    - **Use license plate tracking:** *Yes*
    - **Allow mixed items:** *Yes*
    - **Allow mixed inventory statuses:** *Yes*

1. Select **Save**.

### Locations

1. Go to **Warehouse management \> Setup \> Warehouse \> Locations**.
1. Clear the **Generate check digits for location** check box.
1. On the Action Pane, select **New**, and then set the following values:

    - **Warehouse:** *62*
    - **Location:** *Sort*
    - **Location profile ID:** *Sort*

1. Select **Save**.

### Packing profiles

1. Go to **Warehouse management \> Setup \> Packing \> Packing profiles**.
1. On the Action Pane, select **New**, and then set the following values:

    - **Packing profile ID:** *Sort*
    - **Description:** *Sort*
    - **Container packing policy:** Leave this field blank.
    - **Container ID mode:** *Auto*
    - **Container type:** *PALLET 48X48*
    - **Autocreate container at container close:** Leave this field blank.

1. Select **Save**.

### Wave step codes

If the *Organization wide wave step code* feature is turned on for your system, set up the following code.

1. Go to **Warehouse management \> Setup \> Waves \> Wave step codes**.
1. On the Action Pane, select **New**, and then set the following values:

    - **Wave step code:** *Sort*
    - **Wave step description:** *Sort*
    - **Wave step type:** *Sort template*

1. Select **Save**.

### Outbound sorting template

The sorting template controls whether sort positions are created, what criteria are used, and other attributes of the sorting process.

1. Go to **Warehouse management \> Setup \> Packing \> Outbound sorting template**.
1. On the Action Pane, select **New** to create a sorting template.
1. In the header of the new template, set the following values:

    - **Outbound sorting template ID:** *Wave Sort*
    - **Description:** *Wave sort*
    - **Sort template type:** *Wave demand*

        This field defines the process that the sorting template is used for. The following values are available:

        - **Wave demand** – The sorting template is used for the *Put to wall* process. This template type is used to bypass the pack station and process inventory directly out of the wave. You can use this type only if the **sorting** wave process method is included in the wave template.
        - **Container** – The sorting template is used for the *Pallet building after packing* process. This template type is used to process containers that are closed at the pack station and must be sorted onto pallets.

    - **Warehouse:** *62*
    - **Location:** *Sort*

1. On the **General** FastTab, set the following values:

    - **Sort verification:** *Position scan*

        This field defines the verification that is required during sorting. The following values are available:

        - None
        - License plate scan
        - Position scan

    - **Create work on position close:** *Yes*

        If this option is set to *Yes*, when the position is closed, work will be created to move inventory to the final shipping location. If it's set to *No*, inventory will immediately be picked to the order when the position is closed.

    - **Position assignment:** *Manual*

        This field defines the type of position assignment. The following values are available:

        - **Manual** – The user must always indicate which position the inventory should be sorted to.
        - **Automatic** – The system will automatically guide the inventory to a position whenever it can, based on the sort template breaks.

    - **Assign sort position criteria:** *Only use empty position*

        This field controls whether inventory that is already present on sort positions is taken into account when a position is assigned for the demand. The following values are available:

        - **Only use empty position** – Positions that already have inventory associated with them will be taken into account
        - **Assume position empty** – Any inventory that is already on the position will be disregarded during assignment. All available positions will be used.

    - **Wave step code:** *Sort*

        If the *Organization wide wave step code* feature is turned on, the *Sort* wave step code must also be set up in wave step codes.

    - **Auto close sort position:** *Yes*

        If this option is set to *Yes*, the sort position will automatically be closed when all work that comes to the position has been completed.

    - **Number of sort positions:** *3*

        This field defines the maximum number of sort positions that the system will create.

    - **Sort position prefix:** *SP-*

        This field defines the prefix that the system assigns before the position number.

    - **Auto pack sort position:** *Yes*

        If this option is set to *Yes*, the inventory on the sort position will be packed into a container when the position is closed.

    - **Packing profile ID:** *Sort*

        This field defines the packing profile that will be used when the sort position is packed into a container.

1. On the Action Pane, select **Edit query** to specify the criteria that are used for this sorting template.
1. In the query dialog box, on the **Sorting** tab, select **New** to add a line, and then set the following values:

    - **Table:** *Load details*
    - **Derived table:** *Load details*
    - **Field:** *Shipment ID*
    - **Search direction:** *Ascending*

1. Select **OK**.
1. You might receive the following message: "Grouping will be reset, continue?" Select **Yes**.

    The **Outbound sorting template breaks** button on the Action Pane becomes available.

1. On the Action Pane, select **Outbound sorting template breaks**.
1. Select the **Group by field** check box to group by shipment ID.

    This setting will create one sort position per shipment that is a container in the wave.

1. Select **OK**.

### Wave process methods

1. Go to **Warehouse management \> Setup \> Waves \> Wave process methods**.
1. On the Action Pane, select **Regenerate methods**.

    The **sorting** method is added to the list of available methods, and the *Shipping* wave template type is selected for it.

### Wave templates

Edit the wave template that is used for wave demand sorting.

1. Go to **Warehouse management \> Setup \> Waves \> Wave templates**.
1. In the **Wave template type** field, select *Shipping*.
1. Select the existing **62 Shipping default** template.
1. On the Action Pane, select **Edit**.
1. On the **General** FastTab, make the following changes:

    - Set the **Process wave at release to warehouse** option to *No*.
    - Set the **Assign to open waves** option to *Yes*.

1. On the **Methods** FastTab, set up the **sorting** method:

    1. In the **Remaining Methods** grid, select **sorting**.
    2. Select the right arrow button to move **sorting** to the **Selected Methods** grid.
    3. In the **Selected Methods** grid, select **sorting**.
    4. Set the **Wave step code** field to *Sort*.

1. Select **Save**.

### Mobile device menu items

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. On the Action Pane, select **New**.
1. In the header, set the following values:

    - **Menu item name:** *Sort*
    - **Title:** *Sort*
    - **Mode:** *Indirect*
    - **Use existing work:** *No*

1. On the **General** FastTab, set the following values:

    - **Activity code:** *Outbound sorting*
    - **Use process guide:** *Yes* (default value)
    - **Outbound sorting template ID:** *Wave Sort*

1. Select **Save**.

### Mobile device menu

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu**.
1. In the list of menus, select **Outbound**.
1. On the Action Pane, select **Edit**.
1. In the **Available Menus And Menu Items** grid, find and select the **Sort** menu item that you just created.
1. Select the right arrow button to move **Sort** to the **Menu Structure** grid. In this way, you add the menu item to the **Outbound** menu.
1. Select **Save**.

### Location directives

You must create location directives to guide the work that is created after the sorting is completed.

1. Go to **Warehouse management \> Setup \> Location directives**.
1. In the **Work order type** field, select *Sorted inventory picking*.
1. On the Action Pane, select **New**.
1. In the header, set the following values:

    - **Sequence:** *1*
    - **Name:** *Put to Baydoor*

1. On the **Location directives** FastTab, set the following values:

    - **Work type:** *Put*
    - **Site:** *6*
    - **Warehouse:** *62*
    - **Directive code:** Leave this field blank.
    - **Multiple SKU:** *No*

1. Select **Save** to make the **Lines** FastTab available.
1. On the **Lines** FastTab, select **New**, and then set the following values. Accept the default values for all the other fields.

    - **Sequence number:** *1*
    - **From quantity:** *0*
    - **To quantity:** *1000000*

1. Select **Save** to make the **Location Directive Actions** FastTab available.
1. On the **Location Directive Actions** FastTab, select **New**, and then set the following values. Accept the default values for all the other fields.

    - **Sequence number:** *1*
    - **Name:** *Baydoor*

1. Select **Save** to make the **Edit query** button on the **Location Directive Actions** FastTab available.
1. On the **Location Directive Actions** FastTab, select **Edit query**.
1. In the query dialog box, on the **Range** tab, find the row where the **Field** field is set to *Location*. Set the **Criteria** field for this row to *Baydoor*.
1. Select **OK** to confirm the edit.

### Work classes

1. Go to **Warehouse management \> Setup \> Work \> Work classes**.
1. On the Action Pane, select **New**.
1. In the header, set the following values:

    - **Work class ID:** *Sorting*
    - **Description:** *Sorting*
    - **Work order type:** *Sorted inventory picking*

1. Select **Save**.

### Work templates

1. Go to **Warehouse management \> Work \> Work templates**.
1. In the **Work order type** field, select *Sales orders*.
1. In the grid, select the **62 Pick to pack** work template.
1. On the Action Pane, select **Work header breaks**.
1. On the Action Pane, select **Edit**.
1. On the line where the **Field name** field is set to *Shipment ID*, clear the **Group by this field** check box.
1. Select **Save**, and then close the **Work header breaks** dialog box.
1. In the **Work order type** field, select *Sorted inventory picking*.
1. Select **New** to create a work template.
1. In the **Overview** section, set the following values. Accept the default values for all the other fields.

    - **Work template:** *Sorted picking*
    - **Work template description:** *Sorted picking*

1. Select **Save** to make the **Work Template Details** section available.
1. In the **Work Template Details** section, you will create two lines. Select **New**, and then set the following values for line 1:

    - **Work type:** *Pick*
    - **Mandatory:** Selected (= *Yes*)
    - **Work class ID:** *Sorting*

1. Select **New** again, and then set the following values for line 2:

    - **Work type:** *Put*
    - **Mandatory:** Selected (= *Yes*)
    - **Work class ID:** *Sorting*

1. Select **Save**.

## Example scenario

This scenario simulates a situation where the warehouse stores small items in locations and must pack them into boxes before they are shipped, and where packing station functionality isn't really suitable. Workers pick orders for multiple customers and different addresses at the same time to increase the picking speed. After picking has been completed, the workers arrive at the sorting location, where the picked items can be sorted to the correct box, based on required criteria. In this example, the shipment ID will be used to determine the correct box, because each shipment has a different address. After all items from the load are packed and sorted by shipment, the boxes will be moved to the staging area and eventually loaded onto a truck.

Before you start the scenario, make sure that all standard warehouse functionality is set up correctly for your warehouse. Standard Contoso warehouse *62* is used for this purpose. Standard configurations haven't been changed, besides what is described in the setup.

### Create demand

Before the functionality can be demonstrated, you must create some demand. For this scenario, you will create three sales orders for three different customers to simulate different delivery addresses. In this way, you will create three separate shipments.

Before you create sales orders and shipments, make sure that the pick locations have enough inventory for all the items on the orders. Review the location directive settings to confirm the picking locations that are used for sales order picking. If you must adjust the inventory, you can create manual movements, use replenishment, or use any other flow. Then reserve the inventory.

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. Select **New** to create a sales order for order 1.
1. In the **Create sales order** dialog box, set the following values:

    - **Customer:** *US-001*
    - **Warehouse:** *62*

1. Select **OK**.
1. A new line is added to the **Sales order lines** FastTab. Set the following values:

    - **Item number:** *A0001*
    - **Quantity:** *5*

1. Select **Add line** to add a second line, and set the following values:

    - **Item number:** *A0002*
    - **Quantity:** *10*

1. Repeat the following steps for each sales line on the order to reserve inventory for it:

    1. On the **Sales order lines** FastTab, on the **Inventory** menu, select **Reservation**.
    1. On the **Reservation** page, select **Reserve lot**, and then close the page.
    1. Select **Save**.

1. Select **New** to create a sales order for order 2.
1. In the **Create sales order** dialog box, set the following values:

    - **Customer:** *US-004*
    - **Warehouse:** *62*

1. Select **OK**.
1. A new line is added to the **Sales order lines** FastTab. Set the following values:

    - **Item number:** *A0001*
    - **Quantity:** *7*

1. Select **Add line** to add a second line, and set the following values:

    - **Item number:** *A0002*
    - **Quantity:** *3*

1. Repeat the following steps for each sales line on the order to reserve inventory for it:

    1. On the **Sales order lines** FastTab, on the **Inventory** menu, select **Reservation**.
    1. On the **Reservation** page, select **Reserve lot**, and then close the page.
    1. Select **Save**.

1. Select **New** to create a sales order for order 3.
1. In the **Create sales order** dialog box, set the following values:

    - **Customer:** *US-007*
    - **Warehouse:** *62*

1. Select **OK**.
1. A new line is added to the **Sales order lines** FastTab. Set the following values:

    - **Item number:** *A0001*
    - **Quantity:** *8*

1. Follow these steps to reserve inventory for the sales line:

    1. On the **Sales order lines** FastTab, on the **Inventory** menu, select **Reservation**.
    1. On the **Reservation** page, select **Reserve lot**, and then close the page.
    1. Select **Save**.

Complete the following procedure to release each sales order to the warehouse. Three different shipments will be created. You will then add all three shipments to one new wave.

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. In the grid, select the first sales order that you created.
1. On the Action Pane, on the **Warehouse** tab, select **Release to warehouse**.

    You receive an informational message that shows the wave ID and shipment ID that were created.

1. Repeat the previous steps to release sales orders 2 and 3 to the warehouse. Notice that the informational message that you receive indicates that a shipment has been added to the wave that was created when you released sales order 1.
1. Go to **Warehouse management \> Outbound waves \> Shipment waves \> All waves**.
1. Select the wave ID that was created from the release of the sales orders to open the **Waves** page. This page shows the wave details. The **Wave lines** FastTab shows the shipments that were created.

    You must now create work to bring items from the picking locations to the sorting location.

1. On the Action Pane, select **Process**.

    During wave processing, the sorting method will use the sorting template to assign the inventory to sort positions. When wave processing is completed, you receive an informational message that states that the wave has been posted and work has been created.

1. On the Action Pane, on the **Wave** tab, in the **Related information** group, select **Work** to view the work that was created. Make a note of the work ID.
1. Go to **Warehouse management \> Packing and containerization \> Outbound sorting position assignments**.
1. In the left column, you can view the outbound sorting position that was created for each shipment.
1. On the **Sort position criteria** FastTab, you can view the shipment ID for that position.

One work ID has been created to bring inventory from the picking locations to the sorting location. To complete the work, you will need the work ID that was created during wave processing.

### Sales order picking to the sorting location

1. Sign in to the mobile app as a worker in warehouse *62*.
1. On the main menu, select **Outbound**.
1. On the **Outbound** menu, select **Sales Picking**.
1. Select the **ID** field, and then enter the work ID from the wave processing.
1. Confirm your entry.

    Next, you're prompted to enter a target license plate (LP). Notice that line 1 from sales order 1 is what must be picked and added to the target license plate. The item number, quantity, item description, and pick location are shown.

1. In the **Target LP** field, enter a license plate number.

    You will pick all lines that were created from the processed wave onto the same target license plate.

1. Confirm your entry.

    The mobile app now presents a series of **Pick** pages that point you to the picking location, and to the item and quantity that must be picked. After the picked item is added to the license plate, you will confirm the pick work. The last page will be the work to put the picked items into the sorting location.

1. Confirm the first pick work.
1. The next pick work is shown. Confirm the pick.
1. Continue to confirm the remaining pick work.
1. The last step is to complete the put work. Confirm the put-away to the sorting location.

    You receive a "Work completed" message.

1. Exit **Sales Picking** on the mobile app.

### Sorting/put-to-wall

Now that all inventory has been put to the sorting location, it must be sorted to the correct sort position.

1. Sign in to the mobile app.
1. On the main menu, select **Outbound**.
1. On the **Outbound** menu, select **Sort** to start to sort the items.
1. In the **LP/CON** field, enter the target license plate of the picked sales order work.
1. Confirm your entry.
1. Enter the item number to sort first.
1. The system determines the first sort position that should be shown. Confirm the sort position.
1. You're prompted to assign a license plate to the sort position. Select the **LP** field, enter a license plate number, and then confirm your entry.

    Because the sort position is related to the shipment ID, you will sort the picked items into a license plate that is specific to the outbound shipment and sales order.

    The next page shows the item ID, quantity, sort position ID, and the "from" (picking) and "to" (sorting) license plate IDs. The information on this page instructs you to sort the specified item and quantities from the picking license plate into the sorting license plate.

1. Confirm the sort position.
1. Sort the items in the first sort position. When you've finished, the system directs you to the next sort position.
1. Repeat this process for all picked lines on the work order. You should also use this process when there are multiple pick lines that have the same item number.

    As you repeat this process for all items, the system evaluates the criteria from the next scanned item (work line) and determines which sorting position it should be put to. You're automatically directed to put the item to the correct sort position. Depending on the confirmation setup, you're also directed to confirm this action by entering the position number or license plate ID.

    > [!NOTE]
    > If automatic sorting is turned on, manual override isn't available.

1. When you've finished, in Microsoft Dynamics 365 Supply Chain Management, open the **Outbound sorting position assignments** page to review the status of the positions.

    - If positions are closed automatically, select **Show closed** to show the closed positions.
    - Notice that sort position transactions are shown. The item and quantity that were processed through the position are shown.

    When you set up the outbound sorting template, you set the **Auto close sort position** option to *Yes*. Therefore, the position is automatically closed after the last expected inventory is put to it. The sort positions are in **Closed** status, and work has been created to move the sorted inventory to *Baydoor* location.

1. Complete the sorted inventory picking work to move the inventory to the shipping location. When the inventory is ready, ship-confirm it.

> [!NOTE]
> For sorted inventory picking work to be processed correctly, a mobile device menu item that has a work class ID where the **Work order type** field is set to *Sorted inventory picking* should be used for the movement and loading process.

### Manually close a position (optional)

If sort positions should be closed manually, the **Auto close sort position** option for the outbound sorting template must be set to *No*, and closing must be done before inventory can be moved to the bay door area. Positions can be closed in various ways:

- Via the Warehouse Management mobile app:

    - The user can scan one of the items that are already on the position and then select **Close** to close the position.
    - If the user scans a container that has already been sorted container, an error message is shown. However, the user can still continue to close the position.

- From the Microsoft Dynamics 365 Supply Chain Management **Outbound sorting position assignments** page:

    - The user can select the outbound sorting position record and then select **Close position** on the Action Pane.

## Tips

- Items can't be moved between positions after they have been assigned to one. The system evaluates how many of each item should go to a specific position.
- Sorts template can be configured to automatically create containers when positions are closed. This approach will create standard container ID structure that is based on the specified packing profile.

> [!IMPORTANT]
> After movement work has been created from the sorting location, you must not cancel the work. Otherwise, the position and the containers in it will be deleted from the system and unavailable for further processing. The inventory will also be removed.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]