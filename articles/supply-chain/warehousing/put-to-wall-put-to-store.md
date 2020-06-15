# Put to Wall - Put to Store

## About

With this feature you can handle scenarios where consolidation of product is required to a prepack staging area based on configurable criteria. Companies shipping to stores or handling small items will benefit from this functionality due to decreased picking time as it allows for picking to a single target license plate and it can leverage greater number of put positions than cluster picking.

This workflow directs picked product to a Sorting location for distribution into various types of Containers. Generally, each Sorting Location includes multiple Sort Positions. Each sort position is assigned according to the criteria set by business process, typically final destination, shipment, or load. Once product arrives, it is distributed to each Sort Position by quantity associated to the order, destination, shipment, or load.  When a container is full or complete, it is moved to a Staging Location or a Shipping Location for further handling depending on business process.

This warehousing functionality is also called Put-to-light, Break opens, etc.

## Enable the Outbound sorting feature

Before you can use the **Put to Wall - Put to Store** functionality, the *Outbound Sorting* feature must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - *Warehouse management*
- **Feature name** - *Outbound sorting*

The **Outbound sorting** feature can be used in conjunction with another feature if enabled, **Organization wide wave step code**. You must also enable this feature if you will use predefined codes setup in Wave step codes. The feature is listed listed as:

- **Module** - *Warehouse management*
- **Feature name** - *Organization wide wave step code*

## Setup

For this demo, standard Contoso data is used with **Warehouse** *62*, with some additions noted below.

### Location type

1. Go to **Warehouse management > Setup > Warehouse > Location types**.
1. Select **New** from the Toolbar to create a new location type for Sorting. Enter the following:
    - **Location type** – *SORT*
    - *Description* – *Sort*

1. Select **Save**.

### Warehouse management parameters

1. Go to **Warehouse management > Setup > Warehouse management parameters**.
1. Expand the **General** tab.
1. Expand the **Location types** section. Enter the following:
    - **Sorting location type** - *SORT*

1. Select **Save**.

### Location profile

1. Go to **Warehouse management > Setup > Warehouse > Location profiles**.
1. Select **New** from the Toolbar to create a new **Location profile** for the Sorting location.
1. In the Header of **Location profiles**, enter the following:
    - **Location profile ID** – *Sort*
    - **Name** – *Sort*

1. In the **General** FastTab, enter the following:
    - **Location format** – *PACK*
    - **Location type** – *SORT*
    - **Use license plate tracking** – *Yes*
    - **Allow mixed items** – *Yes*
    - **Allow mixed inventory statuses** – *Yes*

1. Select **Save**.

### Locations

1. Go to **Warehouse management > Setup > Warehouse > Locations**.
1. Unselect **Generate check digits for location** then select  **New** from the Toolbar. Enter the following:
    - **Warehouse** – *62*
    - **Location** – *Sort*
    - **Location profile ID** – *Sort*

1. Select **Save**.

### Packing profiles

1. Go to **Warehouse management > Setup > Packing > Packing profiles**.
1. Select **New** from the Toolbar and enter the following:
    - **Packing profile ID** – *Sort*
    - **Description** – *Sort*
    - **Container packing policy** – *Leave blank*
    - **Container ID mode** – *Auto*
    - **Container type** - *PALLET 48X48*
    - **Autocreate container at container close** - *Leave blank*

1. Select **Save**.

### Wave step codes

If you enable the **Organization-wide Wave Step Code** feature, setup the following code.

1. Go to **Warehouse management > Setup > Waves > Wave step codes**.
1. Select **New** from the Toolbar and enter the following:
    - **Wave step code** - *Sort*
    - **Wave step description** - *Sort*
    - **Wave step type** - *Sort template*

1. Select **Save**.

### Outbound sorting template

The Sorting template controls if sort positions will be created, what criteria will be used, and other attributes of the sorting process.

1. Go to **Warehouse management > Setup > Packing > Outbound sorting template**.
1. Select **New** in the Toolbar to create a new sorting template.
1. In the header of the template, enter the following:
    - **Outbound sorting template ID** – *Wave Sort*
    - **Description** – *Wave sort*
    - **Sort template type** – *Wave demand*
        - The process for which the sorting template is used.
            - **Wave demand**
                - *Put to wall*. Used for processing inventory directly out of the wave, bypassing the pack station. The **sorting** wave process method must be included in the *wave template* for this type to be used.
            - **Container**
                - *Pallet building after packing*. Used for processing containers that are closed at the pack station and need to be sorted onto pallets.
    - **Warehouse** - *62*
    - **Location** – *Sort*

1. In the **General** FastTab enter the following:
    - **Sort verification** – *Position scan*
        - Verification that is required when sorting
          - **None**
          - **License plate scan**
          - **Position scan**
    - **Create work on position close** – *Yes*
        - When enabled work will be created when the position closed to move inventory to the final shipping location.
        - When disabled, inventory will be immediately picked to the order at the time of position close.
    - **Position assignment** - *Manual*
        - Type of position assignment.
            - **Manual** - The user must always indicate which position the inventory should be sorted.
            - **Automatic** - The system will automatically guide the inventory to a position when possible, based on the sort template breaks.
    - **Assign sort position criteria** – *Only use empty position*
        - Controls if inventory already present on sort positions will be taken into account when assigning a position for the demand.
          - **Only use empty position** - Will take into account positions that already have inventory associated.
          - **Assume position empty** - Will disregard any inventory already on the position while assigning and use all available positions.
    - **Wave step code** – *Sort* 
        - If **Organization-wide Wave Step Code** is enabled the wave step code *Sort* must also be setup in Wave step codes.
    - **Auto close sort position** – *Yes*
        - When enabled the sort position will automatically be closed when all work coming to the position has been completed.
    - **Number of sort positions** – *3*
        - Maximum number of sort positions that the system will create.
    - **Sort position prefix** – *SP-*
        - Prefix the system will assign before the position number.
    - **Auto pack sort position** – *Yes*
      - When enabled the inventory on the sort position will be packed into a container when the position is closed.
    - **Packing profile ID** – *Sort*
        - Packing profile that will be used when the sort position is being packed into a container.

1. In the Toolbar, select **Edit query** to specify the criteria used for this sorting template.
1. Select the **Sorting** tab.
1. Select *New* to add a new line, enter the following:
    - **Table** – *Load details*
    - **Derived table** – *Load details*
    - **Field** – *Shipment ID*
    - **Search direction** – *Ascending*

1. Select **OK**.
1. If you receive a message **Grouping will be reset, continue?**, select **Yes**.
1. This will enable the **Outbound sorting template breaks** button in the Toolbar.
1. Select the **Outbound sorting template breaks** button in the Toolbar to open the new form.
1. Select the **Group by field** box to group by Shipment ID.
    - This will create one sort position per shipment that is container in the wave.

1. Select **OK**.

### Wave process methods

1. Go to **Warehouse management > Setup > Waves > Wave process methods**.
1. Select **Regenerate methods** in the Toolbar.
1. This will add the **Method name** - *sorting* to the list of available methods. It will have a **Wave template type** - *Shipping* selected.

### Wave templates

Edit the wave template to use for wave demand sorting.

1. Go to **Warehouse management > Setup > Waves > Wave templates**.
1. Select **Wave template type** - *Shipping*.
1. Select the existing template **62 Shipping default** template.
1. Select **Edit** from the Toolbar.
1. In the **General** FastTab, make the following changes:
    - Change **Process wave at release to warehouse** to *No*
    - Change **Assign to open waves** to *Yes*

1. In the **Methods** FastTab **Remaining Methods** grid, move **sorting** to the **Selected Methods** grid by:
    - Select **sorting** in the **Remaining Methods** grid
    - Select the arrow box (**->**) to move sorting into the **Selected Methods** grid
    - Select **sorting** in the **Selected Methods** grid
    - **Wave step code** - *Sort*

1. Select **Save**.

### Mobile device menu items

1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu items**.
1. Select **New** from the Toolbar and enter the following:
    - In the header enter:
        - **Menu item name** – *Sort*
        - **Title** – *Sort*
        - **Mode** – *Indirect*
        - **Use existing work** – *No*

1. On GeneralFastTab enter the following:
    - **Activity code** – *Outbound sorting*
    - **Use process guide** - *Yes* (default)
    - **Outbound sorting template ID** – *Wave Sort*

1. Select **Save**.

### Mobile device menu

1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu**.
1. Select **Outbound** from the list of menus.
1. Select **Edit** from the Toolbar.
1. On the **Available Menus And Menu Items** grid, scroll until you find the menu item **Sort** you just created.
1. Select **Sort**.
1. Select the arrow box (**->**) to move **Sort** into the **Menu Structure** grid to add the menu item to the Outbound menu.

1. Select **Save**.

### Location directives

Location directives must be created to guide the work created after the sorting is completed.

1. Go to **Warehouse management > Setup > Location directives**.
1. Select **Work order type** - *Sorted inventory picking*.
1. Select **New** from the Toolbar.
1. In the header enter the following:
    - **Sequence** – *1*
    - **Name** – *Put to Baydoor*

1. On the **Location directives** FastTab, enter the following:
    - **Work type** – *Put*
    - **Site** – *6*
    - **Warehouse** – *62*
    - **Directive code** - *blank*
    - **Multiple SKU** - *No*

1. Select **Save** to enable the **Lines** FastTab.
1. On the **Lines** FastTab Select **New** in the Toolbar, then enter the following:
    - **Sequence number** – *1*
    - **From quantity** – *0*
    - **To quantity** – *1000000*
    - Accept the defaults for the remaining fields.

1. Select **Save** to enable the **Location Directive Actions** FastTab.
1. On the **Location Directive Actions** FastTab select **New** and enter the following:
    - **Sequence number** – *1*
    - **Name** – *Baydoor*
    - Accept the defaults for the remaining fields.

1. Select **Save** to enable **Edit query** on the **Location Directive Actions** FastTab.
1. Select **Edit query** on the **Location Directive Actions** FastTab.
1. On the query form select the **Range** tab and edit the **Location** field **Criteria** to *Baydoor*.
1. Select **OK** to confirm the edit.

### Work classes

1. Go to **Warehouse management > Setup > Work > Work classes**
1. Select **New** in the Toolbar and enter the following in the header:
    - **Work class ID** – *Sorting*
    - **Description** – *Sorting*
    - **Work order type** – *Sorted inventory picking*

1. Select **Save**.

### Work templates

1. Go to **Warehouse management > Work > Work templates**.
1. Select **Work order type** - *Sales orders*.
1. Select the **62 Pick to pack** work template in the grid.
1. Select **Work header breaks** in the Toolbar.
    - Select **Edit** in the Toolbar.
    - Uncheck the box for **Group by this field** on the line where the **Field name** is *Shipment ID*.
    - Select **Save** and close the **Work header breaks** form.

1. Select **Work order type** - *Sorted inventory picking*.
1. Select **New** to create a new work template.
1. In the **Overview** section enter the following:
    - **Work template** – *Sorted picking*
    - **Work template description** – *Sorted picking*
    - Accept the defaults for the remaining fields.

1. Select **Save** to enable the **Work Template Details** section.

1. In the **Work Template Details** section you will create two lines.
1. Select **New** in the **Work Template Details** Toolbar and enter the following for line 1.
    - **Work type** - *Pick*
    - **Mandatory** - *Yes* (selected)
    - **Work class ID** - *Sorting*

1. Select **New** in the **Work Template Details** Toolbar and enter the following for line 2.
    - **Work type** - *Put*
    - **Mandatory** - *Yes* (selected)
    - **Work class ID** - *Sorting*

1. Select **Save**.

## Scenario

This scenario will simulate a storyline where the warehouse is storing small items in locations and has to pack them into boxes before shipping, where Packing station functionality is not really suitable. Workers are picking orders for multiple customers and different addresses at the same time to increase the picking speed. After the picking has been finished, the workers arrive to the sorting location where the picked items can be sorted to the correct box, based on required criteria. In this example, *Shipment ID* will be used to determine that, as each shipment has a different address. After all items from the Load are packed and sorted by Shipment, the boxes will be moved to the staging area and eventually loaded to truck.

Prior to starting with the demo, ensure that all standard warehouse functionality is set up correctly for your warehouse. Standard Contoso **Warehouse 62** is used for this purpose. Standard configurations have not been altered, besides what is described in the setup.

### Create demand

Before the functionality can be demonstrated, some demand must be created.

Due to the nature of the scenario, you will create three different Sales orders for three different customers to simulate different delivery addresses. This will create three different Shipments.

Before creating Sales orders and Shipments, ensure there is enough inventory on the pick locations for all the items on the orders. Review the Location Directive setting to be sure what picking locations are used for sales order picking. You can create manual movements, use replenishment, or any other flow if needed to adjust the inventory. Reserve the inventory.

1. Go to **Sales and Marketing > Sales orders > All sales orders**.
1. Select **New** to create a new Sales Order for Order 1.
1. On the **Create sales order** FlyOut, enter the following:
    - **Customer** - *US-001*
    - **Warehouse** - *62*

1. Select **OK**.
1. A new line is added to the **Sales order lines** FastTab, enter the following:
    - **Item number** - *A0001*
    - **Quantity** - *5*

1. Select **Add line** from the Toolbar to add a second line, enter the following:
    - **Item number** - *A0002*
    - **Quantity** - *10*

1. Reserve inventory, for each sales line on the order. Repeat the steps below for each sales line.
1. On the **Sales order lines** Toolbar select **Inventory** then select **Reservation** from the menu.
1. On the **Reservation** form select **Reserve lot**, then close the form.
1. Select **Save**.

1. Select **New** to create a new Sales Order for Order 2.
1. On the **Create sales order** FlyOut, enter the following:
    - **Customer** - *US-004*
    - **Warehouse** - *62*

1. Select **OK**.
1. A new line is added to the **Sales order lines** FastTab, enter the following:
    - **Item number** - *A0001*
    - **Quantity** - *7*

1. Select **Add line** from the Toolbar to add a second line, enter the following:
    - **Item number** - *A0002*
    - **Quantity** - *3*

1. Reserve inventory, for each sales line on the order. Repeat the steps below for each sales line.
1. On the **Sales order lines** Toolbar select **Inventory** then select **Reservation** from the menu.
1. On the **Reservation** form select **Reserve lot**, then close the form.
1. Select **Save**.

1. Select **New** to create a new Sales Order for Order 3.
1. On the **Create sales order** FlyOut, enter the following:
    - **Customer** - *US-007*
    - **Warehouse** - *62*

1. Select **OK**.
1. A new line is added to the **Sales order lines** FastTab, enter the following:
    - **Item number** - *A0001*
    - **Quantity** - *8*

1. Reserve inventory, for each sales line on the order. Repeat the steps below for each sales line.
1. On the **Sales order lines** Toolbar select **Inventory** then select **Reservation** from the menu.
1. On the **Reservation** form select **Reserve lot**, then close the form.
1. Select **Save**.

Release each sales order to warehouse to create a Shipment. There should be three different shipments created. All three shipments will be added to one new wave.

1. In the **All sales orders** Action Pane, select the **Warehouse** tab to reveal the **Release to warehouse** button.
1. In the list page, focus on Sales order 1, then select **Release to warehouse**.
1. An informational message will appear with the *Wave ID* and *Shipment ID* created.
1. Repeat this for Sales orders 2 & 3.
    - Note that the wave message will indicate that shipment has been added to the wave created when releasing Sales order 1.

1. Go to **Warehouse management > Outbound waves > Shipment waves > All waves**.
1. In the list page, select the **Wave ID** created from the release of the sales orders to open the Wave details.
1. On the **Waves** form **Wave lines* FastTab the 3 shipments created will be displayed.

1. Work needs to be created to bring the item from the picking location to the sorting location. In the Action Pane select **Process**.
    - During Wave processing, the sorting method will use the sorting template to assign the inventory to sort positions.

1. When the Wave has finished processing an informational message will be displayed indicating that the Wave has been posted and that Work has been created.
    - Select **Work** from the Action Pane **Related information** group to view the work created. Note the **Work ID**.

1. Go to **Warehouse management > Packing and containerization > Outbound sorting position assignments**.
1. In the left column you can view the **Outbound sorting position** created for each shipment.
    - Expand the **Sort position criteria** FastTab to see the Shipment ID for that position.

One Work ID has been created to bring inventory from the picking locations to the sorting location. In order to complete the work you will need the **Work ID** created from processing the wave.

### Sales order picking to Sort location

1. Logon to the mobile app with a worker in *Warehouse 62*'
1. Select **Outbound** from the menu.
1. Select **Sales Picking** from the menu.
1. Select the **ID* field.
1. Enter the *Work ID* from processing the wave.
1. Confirm your entry.
1. Next you will be asked to enter a **Target LP** (Target License Plate).
    - You will note that line 1 from sales order 1 is what is to be picked and added to the Target License Plate.
    - Item number, Quantity, Item description and Pick location are displayed.

1. Enter a *License plate number* in the **Target LP** field.
    - You will be picking all lines created from the processed wave onto the same *Target license plate*. After confirming, you will be presented with a series of Pick screens, pointing you to the picking location and the Item and Quantity to be picked. The final screen will be the Work to *Put* the picked items into the **Sort** location.
1. Confirm your License plate entry.
1. Confirm your first Work pick.
1. The next picking work will be displayed, confirm the pick.
    - The remaining work will be displayed to the user on the mobile app. Item, quantity and picking location information is displayed. Confirm the pick work once the picked item is added to the License Plate.

1. Continue confirming the remaining picking work.
1. The final step will be to complete the Put work. Confirm the put away to  the Sort location.
1. A work completed message will be displayed.
1. Exit Sales Picking on the mobile app.

### Sorting / Put-to-wall

Now that all inventory has been put to Sorting location, it needs to be sorted to the correct sort position.

1. Logon to the mobile app and go to the **Outbound** menu.
1. Select **Sort** from the menu to initiate sorting of the items.
1. Enter the Target License Plate of the picked Sales order work in the **LP/CON** field.
1. Confirm the license plate number entered.
1. Enter the **Item number** to sort first.
1. The system determines the first sort position to be displayed. Confirm the **Sort Position**.
1. The user will be prompted to assign a license plate to the sort position. Select the **LP** field and enter a license plate number, and confirm the license plate.
    - Because the sort position is related to the *Shipment ID*, you will be sorting the picked items into a license plate that will be specific to the outbound shipment and sales order.

1. On next screen, instructions on what to sort are presented.
    - The system will display the **ItemId**, **Qty**, **Sort position Id** as well as the to and from license plate ID's.
    - This information instructs the user to sort the specified item and quantities from the picking license plate into the sorting license plate.

1. Confirm the Sort position.
1. When you have completed the sorting of the items in the sort position, the system will direct you to the next sort position.
1. Repeat this process for all picked lines on the Work order. This should also be done if there are multiple pick lines with the same item number.
1. As this is repeated for all items, the system evaluates the criteria from the next scanned item (work line) and determines to which sorting position it should be put. The user is automatically directed to *Put* the item to the correct Sorting position, and depending on the confirmation setup, to confirm this by entering the Position number or License plate ID.
    - If automatic sorting is enabled, manual override is not available.

1. Once finished, open **Outbound sorting position assignments** form to review the status of the positions.
    - If positions are closed automatically, select **Show closed** to display the closed positions.
    - Note that **Sort position transactions** are shown. Item and quantity processed through the position are displayed.

1. During setup of the **Outbound sorting template**, **Auto close sort position** was configured to be *Yes* so that the position will be Closed automatically once the last expected inventory is put to it. The sort positions are in **Closed** status and Work has been created to move the sorted inventory to *Baydoor* location.
1. Complete the Sorted inventory picking work to move the inventory to the shipping location. Ship confirm when ready.

> [!NOTE]
> For Sorted inventory picking work to be processed correctly, a **Mobile Device Menu Item** with a **Work class ID** with a **Work order type** of *Sorted inventory picking* should be used for the movement and loading process.

### Manually Close Position - Optional

If sort positions should be closed manually, the **Outbound sorting template** configuration for **Auto close sort position** was set to *No*, closing must be done before inventory can be moved to the Baydoor area. Closing of Positions can occur in few different ways:

1. Via the Mobile device
    - The user can scan one of the items already on the Position and select the **Close** button. This will close the position.
    - As the user scans an already sorted container, an error message will be shown, but the user can still proceed with closing the position.
1. Using the **Outbound sorting position assignments** form.
    - The user can select the *Outbound sorting position* record, then select **Close position** from the Toolbar.

## Tips

- Items cannot be moved between positions once assigned to one. The system will evaluate how many of each items should go to a certain position.
- Sort template can be configured to create Container automatically on Position Close. This will create standard Container ID structure, based on the Packing profile specified.

> [!CAUTION]
> Once movement work has been created from Sorting location, the work should not be cancelled. If so, the Position and Containers within will be deleted from the system and unable for further processing. The inventory will also be removed.
