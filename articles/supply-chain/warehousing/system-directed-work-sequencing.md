# System Directed Work Sequencing

System directed work sequencing setup offers the ability to sort and filter which work orders will the system present to the user for execution. This functionality solves scenarios where additional criteria is required to drive warehouse picking process, e.g. by the time of shipping, picking zone, Location profile, or even based on a combination of different criteria.

This functionality extends the current system directed picking with new System directed query order where the user can set up a sequence and a query or multiple queries which will evaluate all created work orders. It will therefore capture and present only the work orders that meet the specified criteria of the mobile device menu item setup.

Warehouse picking processes can therefore be further optimized as this feature identifies work orders that match the defined criteria and assigns those to the correct mobile device menu item, and consequently presents them to a worker based on a specific skillset, picking equipment, or any other requirement.

_NOTE_: If different criteria is needed, multiple mobile device menu items will have to be used.

## Enable the Organization-wide system directed work sequencing feature

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - *Warehouse management* 
- **Feature name** - *Organization-wide system directed work sequencing*

## Setup

**Warehouse used:** 51

**Data:** Default Contoso data

## Mobile device menu item

1. Go to __Warehouse management__ > __Setup__ > __Mobile device__ > __Mobile device menu items__

1. Select **Sales Picking – System**
    1. Item is already created and can be used for this purpose.
        - **Directed by** is set to __System directed__
        - **Work classes**
            - **Work class ID** Sales, **Work order type** Sales orders
            - **Work class ID** SO Pick, **Work order type** Sales orders

1. Select **System directed work sequence queries** button in the **Action pane**.
1. Delete the existing line
    1. In the message window select **Yes**

1. Select **New** to create a new line
    1. Set the following values
        - In **Sequence number** field, select __1__
        - In **Description field** field, enter __Work quantity less than 20 and Descending__
1. Select **Save**

1. Select **Edit Query** button in **Action Pane**
1. Select **Sorting** tab
    1. Select **Add**
    1. On the grid line in the **Sorting** tab, specify the following data:

    - In the **Table** field, select __Work lines__
    - In the **Derived table** field, select __Work lines__
    - In the **Field** field, select __Work quantity__
        - In the message window select **Yes** to add sorting to this field
    - In the **Search direction** field, select __Descending__

1. Select **Range** tab
    1. If only specific _**Work**_ criteria should be included in the sequencing, you can specify that on the Range. 
    1. In this example, we will want to include only Work with less than 20 eaches (lowest unit of measure).

    1. Select **Add**

        1. Note that there are already some lines included which should not be removed.

1. On the new grid line in the **Range** tab, specify the following data:

    - In the **Table** field, select __Work lines__
    - In the **Derived table** field, select __Work lines__
    - In the **Field** field, select **Inventory work quantity**
    - In the **Criteria** field, enter \<20
        - (less than 20)

1. Select **OK**
1. Select **Save** on the **System Directed Work Sequence Queries | SALES PICKING - SYSTEM : SYSTEM DIRECTED** form
1. **Close** the form to return to the **Mobile device menu items** form


This is now the criteria based on which the mobile device menu item will be fed the eligible work. If more Query criteria lines are used, the system will first use the Query line with lowest sequence number.

Therefore, all eligible Work for Sequence number 1 will first be fed to the user, and after that all Work for Sequence number 2 will be presented to the user. Hence if certain Range and Sorting need to be used in tandem, they should be specified on the same System directed work sequence query.

Note that this setup will capture any work that has at least one line with less than 20 ea. Hence, if the same Work has another line with exactly 20 ea or more than 20 ea, it will also be valid, as long as at least one line has less than 20 ea.

## Location directives

Default Contoso Data will not require editing of the location directive action query. When applying this feature in a non-Contoso environment, ensure that the Location Directives will capture the items on the Sales orders by creating a new location directive. Select **Edit  query** the Location Directive Actions sequence for **Pick** and ensure there is no restriction for the **Location** criteria in the query. Save the change.

1. Go to **Warehouse management** > **Setup** > **Location directives**
1. Select **Work order type** **Sales orders**
1. Select the **Sequence number** and **Name** of the location directive.
1. In the **Location Directive Actions** pane, select the **Sequence number** line for the **Pick** action.
1. Select **Edit query**
1. Review the **Range** query and ensure that the **Location** **Criteria** has no restrictions.

## Scenario

### Create picking work

Before system directed picking is executed, some outbound work should be created. Based on the specified System directed work sequence queries, create 4 different **Sales Orders**, with the below specifications.

1. Navigate to **Sales and marketing** > **Sales orders** > **All sales orders**
1. Create _**Sales Order 1**_
    1. Select **New** to create a new sales order.
    1. In **Customer account** select **US-004** -- **Cave Wholesales**
    1. Expand the **General** section
    1. In the **Warehouse** field, select **51**
    1. Select **OK**
    1. Make note of the Sales order number for **Cave Wholesales**
    1. Add a new line to the sales order
        1. In the **Item number** field select **M9200**
        1. In the **Quantity** field enter **20**
    1. Select **Save**
1. Create _**Sales order 2**_
    1. Select **New** to create a new sales order.
    1. In **Customer account** select **US-007** -- **Desert Wholesales**
    1. Expand the **General** section
    1. In the **Warehouse** field, select **51**
    1. Select **OK**
    1. Make note of the Sales order number for **Desert Wholesales**
    1. Add a new line to the sales order
        1. In the **Item number** field select **M9200**
        1. In **Quantity** field enter **5**
    1. Select **Add line**
        1. In the **Item number** field select **M9201**
        1. In **Quantity** field enter **1**
    1. Select **Save**
1. Create _**Sales order 3**_
    1. Select **New** to create a new sales order.
    1. In **Customer account** select **US-009** -- **Owl Wholesales**
    1. Expand the **General** section
    1. In the **Warehouse** field, select **51**
    1. Select **OK**
    1. Make note of the Sales order number for **Owl Wholesales**
    1. Add a new line to the sales order
        1. In the **Item number** field select **M9200**
        1. In **Quantity** field enter **7**
    1. Select **Add line**
        1. In the **Item number** field select **M9202**
        1. In **Quantity** field enter **8**
    1. Select **Save**
1. Create _**Sales order 4**_
    1. Select **New** to create a new sales order.
    1. In **Customer account** select **US-010** -- **Sunset Wholesales**
    1. Expand the **General** section
    1. In the **Warehouse** field, select **51**
    1. Select **OK**
    1. Make note of the Sales order number for **Sunset Wholesales**
    1. Add a new line to the sales order
        1. In the **Item number** field select **M9200**
        1. In **Quantity** field enter **25**
    1. Select **Add line**
        1. In the **Item number** field select **M9202**
        1. In **Quantity** field enter **10**
    1. Select **Save**

## Reserve Inventory and Release to Warehouse

Before releasing the orders to warehouse, ensure there is enough inventory on the pick locations for all the items on the orders.

Default Contoso data should support this scenario but review the Location Directive setting to be sure what picking locations are used for sales order picking. You can create manual movements, use replenishment, or any other flow if needed to adjust the inventory.

### Reserve inventory

You can reserve inventory quantities for a specific sales order. This means that reserved inventory cannot be withdrawn from the warehouse for other orders unless the inventory reservation, or part of the inventory reservation, is canceled. 

To reserve inventory:

1. Select **Sales Order 1** and open to display the **Sales order details** form
1. In the **Sales order lines** section focus on the order line
1. On the section's **Action pane** select **Inventory** and select **Reservation** from the list
1. In the **Reservation** header the sales line order quantity is displayed in the **On order** field. In the **Detailed availability by dimension** section, enter the value from the **On order** field in the header into the **Reservation** field
1. Press **Tab** to move off of the **Reservation** field
1. The form updates, **Reserved physical** field is updated and **Lock reservations** fast tab is updated
1. **Close** the **Reservation** form
1. Repeat the steps above for each line on the remaining Sales Orders

    _**Option**_: After reserving inventory for each Sales Order, follow the steps for releasing to warehouse before moving to the next sales order.

### Release to Warehouse

Sales orders must be released to the warehouse in order for work to be created. Work in the warehouse defines the instructions to the warehouse worker of what tasks to perform. 

To release the sales order to the warehouse and create work:

1. Select **Sales Order 1** and open to display the **Sales order details** form
1. In the Action pane select the **Warehouse** tab then select **Release to warehouse** initiate the release process
1. When the release to warehouse process completes 4 **informational messages** are displayed: the number of **shipments** that have been created,  **Wave** number that has been created for the **shipment**, the **Work build ID** number, and, the **Wave** that is posted.
1. In the **Sales order lines** section select **Warehouse** from the Action pane then select **Work details** from the list
1. The **Work** form opens
1. On the **Overview** tab in the grid field **Work ID** the Work ID number is displayed.
1. Make note of the **Work ID** for **Sales Order 1**
1. **Close** the **Work** form
1. Repeat the steps above for each of the remaining 3 Sales Orders

Four different Work IDs should have been created.

1. Sales Order 1 / Work ID 1 – 20 ea
2. Sales Order 2 / Work ID 2 – 6 ea (sum of both lines)
3. Sales Order 3 / Work ID 3 – 15 ea (sum of both lines)
4. Sales ORder 4 / Work ID 4 – 35 ea (sum of both lines)

## Mobile device flow execution

Before executing the flow on the mobile device, ensure that only the created work is in Open status for Warehouse 51 and Work order type Sales order. If not, the results of the test may vary as the System direct picking will include all eligible work.

1. Navigate to **Warehouse management** > **Work** > **Outbound** > **Open sales work**
1. In the **Open sales work** grid filter on **Warehouse** for warehouse **51**
1. Confirm that the only work displayed are the 4 **Work ID**'s created in the steps above.
1. **Close** **Work** form

Enter mobile device and select the menu where the System Directed Query Order is located **Outbound** > **Sales picking – System**. Based on our setup, the system will feed the user Work, sorted from highest Work line quantity to lowest, but less than 20 each on a single line.

Remember that this setup will capture any work that has at least one line with less than 20 ea. Hence, if the Work has another line with exactly 20 ea or more than 20 ea, it will also be valid.

Select the _Sales Picking – System_ menu and initiate the pick. After selecting the menu, the user will be presented with the Pick step of the Work ID 4. This is due to the System Directed Query Order setup, where we have specified that Work should be sequenced based on Work line Quantity - Descending.

Complete the necessary Pick and Put to Close the Work ID.

Next, Work ID 3 is presented to the worker. One of it&#39;s work lines is next in the sequence based on Work line Quantity. Complete the Pick and Put to Close the Work ID.

Next, Work ID 2 is presented to the worker. This work&#39;s pick line is next in the sequence based on our setup. Complete the Pick and Put to Close the Work ID.

No work should be presented to the user after this completion. Work ID 1 is not eligible for this mobile device menu item, because it has been specified on the Query that only Work headers with Work lines less than 20 should be considered.

## Tips <!--HHM: in line comments in code -->

The **System directed work sequence queries is**  **inclusive** , which is important to know with certain setups. For example, if the user wishes for a certain menu item to process only work with work unit in eaches and it specifies that on the Range, all Work with at least one Work line with Work unit eaches will be fed to the user. This will therefore also include all Work with other Work units besides _eaches_ (box or pallet) and it will not exclude those. It will exclude only Work where no Work lines have Work Unit set as each.

- --Hence, in the example from this demo, the Work ID 4 was also captured by the query. It was created with 2 lines, one for 25 ea and another one for 10 ea. The Work was still be assigned to the user because at least one Work line had less than 20 ea. This can be prevented with Work breaks, depending on the scenario.
