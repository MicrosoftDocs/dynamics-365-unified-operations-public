# System Directed Work Sequencing

System directed work sequencing setup offers the ability to sort and filter which work orders will the system present to the user for execution. This functionality solves scenarios where additional criteria is required to drive warehouse picking process, e.g. by the time of shipping, picking zone, Location profile, or even based on a combination of different criteria.

This functionality extends the current system directed picking with new System directed query order where the user can set up a sequence and a query or multiple queries which will evaluate all created work orders. It will therefore capture and present only the work orders that meet the specified criteria of the mobile device menu item setup.

Warehouse picking processes can therefore be further optimized as this feature identifies work orders that match the defined criteria and assigns those to the correct mobile device menu item, and consequently presents them to a worker based on a specific skillset, picking equipment, or any other requirement.

*NOTE*: If different criteria is needed, multiple mobile device menu items will have to be used.

## Enable the Organization-wide system directed work sequencing feature

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - *Warehouse management*
- **Feature name** - *Organization-wide system directed work sequencing*

## Setup

- **Warehouse used**: *51*
- **Data**: *Default Contoso data*

> [!IMPORTANT]
>Before releasing the orders to warehouse, ensure there is enough inventory on the pick locations for all the items on the orders.
>
>Default Contoso data should support this scenario. If you are not using demo date, review the Location Directive setting to be sure what picking locations are used for sales order picking. You can create manual movements, use replenishment, or any other flow if needed to adjust the inventory.

### Mobile device menu item

1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu items**

1. Select **Sales Picking – System** from the list of mobile device menu items.
    - Menu item is already created and can be used for this purpose. Confirm the following settings:
        - - **General** FastTab:
            - **Directed by** - *System directed*

        - **Work classes** FastTab:
            | Work class ID | Work order type |
            |---|---|---|
            | Sales | Sales orders |
            | SO Pick | Sales orders |

1. In the **Action pane**, select **System directed work sequence queries**.
1. Select **Edit**
1. **Delete** the existing line.
    - In the message box select **Yes**

1. In the Action Pane, select **New** to create a new line.
    - Enter the following values
        - **Sequence number** - *1*
        - **Description field** - *Work quantity less than 20 and Descending*

1. Select **Save**
1. In the Action Pane, select **Edit Query**.
1. Select the **Joins** tab.
1. Expand the joins hierarchy to reveal the **Work lines** table.
1. Select the **Work lines** table join.
1. In the header select **Add table join**.
1. In the list displayed, scroll until the following row is displayed, then select the row:
    - **Join mode** - *n:1*
    - **Relation** - *Locations (Location)*

1. In the header choose the **Select** button.
1. Locations is added to the table join.
1. Select the **Sorting** tab.
1. Select **Add**
1. On the new line, enter the following:
    - **Table** - *Work lines*
    - **Derived table** - *Work lines*
    - **Field** - *Work quantity*
        - In the message box select **Yes** to add sorting to this field.

    - **Search direction** - *Descending*

1. Select the **Range** tab.
    - If only specific Work criteria should be included in the sequencing, you can specify that on the Range.
    - In this example, we will want to include only Work with less than 20 eaches (lowest unit of measure).
1. Select **Add** in the header.
    - Note that there are already some lines included which should not be removed.
1. On the new line, enter the following:
    - **Table** - *Work lines*
    - **Derived table** - *Work lines*
    - **Field** - *Inventory work quantity*
    - **Criteria** - *<20*
        - (less than 20)

1. Select **Add** in the header.
1. On the new line, enter the following:
    - **Table** - *Work lines*
    - **Derived table** - *Work lines*
    - **Field** - *Work type*
    - **Criteria** - *Pick*

1. Select **Add** in the header.
1. On the new line, enter the following:
    - **Table** - *Locations*
    - **Derived table** - *Locations*
    - **Field** - *Location profile ID*
    - **Criteria** - *!STAGE*
        - Important: be sure to include the exclamation mark ( **!** ) in front of STAGE.

1. Select **OK** to save and close the query.
1. Select **Save**.
1. **Close** the page to return to the **Mobile device menu items** page.

>[!NOTE]
>This is now the criteria based on which the mobile device menu item will be fed the eligible work. If more Query criteria lines are used, the system will first use the Query line with lowest sequence number.
>
>Therefore, all eligible Work for Sequence number 1 will first be fed to the user, and after that all Work for Sequence number 2 will be presented to the user. Hence if certain Range and Sorting need to be used in tandem, they should be specified on the same System directed work sequence query.
>
>Note that this setup will capture any work that has at least one line with less than 20 ea. Hence, if the same Work has another line with exactly 20 ea or more than 20 ea, it will also be valid, as long as at least one line has less than 20 ea.

### Location directives

Default Contoso Data will not require editing of the location directive action query. When applying this feature in a non-Contoso environment, ensure that the Location Directives will capture the items on the Sales orders by creating a new location directive. To verify the settings in the demo environment, do the following:

1. Go to **Warehouse management** > **Setup** > **Location directives**.
1. Select **Work order type** - *Sales orders*.
1. Select the following **Location directive**:
    - **Name** - *51 Pick*

1. In the **Location Directive Actions** FastTab, select the line for the **Pick** action.
1. Select **Edit query** on the Location Directive Actions Toolbar.
1. Review the **Range** query.
    - Find the line with **Field** - *Location*
    - Ensure that **Criteria** has no restrictions (blank).

## Scenario

### Create sales order picking work

Before system directed picking is executed, some outbound work should be created. Based on the specified System directed work sequence queries, create 4 different **Sales Orders**, with the below specifications.

You will reserve inventory quantities for a specific sales order. This means that reserved inventory cannot be withdrawn from the warehouse for other orders unless the inventory reservation, or part of the inventory reservation, is canceled.

You will release the sales order to the warehouse to create the work.

#### Sales order 1

1. Go to **Sales and marketing > Sales orders > All sales orders**
1. In the Action Pane, select **New** to create **Sales Order 1**.
1. In the **Create sales order** dialog box, select the following:
    - In the Customer section:
        - **Customer account** - *US-004*
    - In the **General** section
        - **Warehouse** - *51*
    - Select **OK** to close the dialog box.
        - Make note of the Sales order number.

1. Add a new line to the sales order and reserve the inventory, enter, and select the following:
    - **Item number** - *M9200*
    - **Quantity** - *20*
    - Select **Inventory** on the FastTab **Toolbar**  then select **Reservation** from the list.
        - On the **Reservation** form, select **Reserve lot** to reserve the inventory.
        - **Close** the **Reservation** form.

1. On the Action Pane, select the **Warehouse** tab and then *Release to warehouse* to create work for the warehouse.
1. Informational messages are displayed with the *Wave ID* and *Shipment ID*(s) created for the sales order.

#### Sales order 2

1. In the Action Pane, select **New** to create **Sales Order 2**.
1. In the **Create sales order** dialog box, enter the following:
    - **Customer account** - *US-007*
    - **Warehouse** - *51*
    - Select **OK** to close the dialog box.
        - Make note of the Sales order number.

1. Add a line to sales order 2, enter the following:
    - **Item number** - *M9200*
    - **Quantity** - *5*

1. Select **Add line** to add a second line and enter the following:
    - **Item number** - *M9201*
    - **Quantity** - *1*

1. Reserve inventory for both lines.
1. Release the order to the warehouse.

#### Sales order 3

1. In the Action Pane, select **New** to create **Sales Order 3**.
1. In the **Create sales order** dialog box, enter the following:
    - **Customer account** - *US-009*
    - **Warehouse** - *51*
    - Select **OK** to close the dialog box.
        - Make note of the Sales order number.

1. Add a line to sales order 3, enter the following:
    - **Item number** - *M9200*
    - **Quantity** - *7*

1. Select **Add line** to add a second line and enter the following:
    - **Item number** - *M9202*
    - **Quantity** - *8*

1. Reserve inventory for both lines.
1. Release the order to the warehouse.

#### Sales order 4

1. In the Action Pane, select **New** to create **Sales Order 4**.
1. In the **Create sales order** dialog box, enter the following:
    - **Customer account** - *US-010*
    - **Warehouse** - *51*
    - Select **OK** to close the dialog box.
        - Make note of the Sales order number.

1. Add a line to sales order 4, enter the following:
    - **Item number** - *M9200*
    - **Quantity** - *25*

1. Select **Add line** to add a second line and enter the following:
    - **Item number** - *M9202*
    - **Quantity** - *10*

1. Reserve inventory for both lines.
1. Release the order to the warehouse.

### Get  Work ID's for the created work

1. Go to **Warehouse management > Work > Work details**.
1. Filter for **Warehouse** - *51*.

Four different Work IDs should have been created. Make note of the work ID for each sales order.

| Sales Order ID | Work ID | Work quantity |
| --- | --- | --- |
| Sales Order 1 | Work ID 1 | 20 ea |
| Sales Order 2 | Work ID 2 | 6 ea (sum of both lines) |
| Sales Order 3 | Work ID 3 | 15 ea (sum of both lines) |
| Sales Order 4 | Work ID 4 | 35 ea (sum of both lines) |

Before executing the flow on the mobile device, ensure that only the created work is in Open status for Warehouse 51 and Work order type Sales order. If not, the results of the test may vary as the System direct picking will include all eligible work.

1. Navigate to **Warehouse management** > **Work** > **Outbound** > **Open sales work**
1. In the **Open sales work** grid filter on **Warehouse** for warehouse **51**
1. Confirm that the only work displayed are the 4 **Work ID**'s created in the steps above.
1. **Close** **Work** form

### Mobile device flow execution

Based on the setup, the system will feed the user *Work*, sorted from highest Work line quantity to lowest, but less than 20 each on a single line.

Remember that this setup will capture any work that has at least one line with less than 20 ea. Hence, if the Work has another line with exactly 20 ea or more than 20 ea, it will also be valid.

#### Mobile app

1. Log on to the warehousing app with a user in **Warehouse** - *51*.
1. Go to **Outbound > Sales Picking - System**.
    - After selecting the menu, the user will be presented with the Pick step of the **Work ID** - *4*.
        - This is due to the System Directed Query Order setup, where we have specified that Work should be sequenced based on Work line Quantity - Descending.
    - Complete the necessary Pick and Put to Close the Work ID.
    - Next, **Work ID** - *3* is presented to the worker. One of its work lines is next in the sequence based on Work line Quantity. Complete the Pick and Put to Close the Work ID.
    - Next, **Work ID** - *2* is presented to the worker. This work's pick line is next in the sequence based on our setup. Complete the Pick and Put to Close the Work ID.
    - No work should be presented to the user after this completion. **Work ID** - *1* is not eligible for this mobile device menu item, because it has been specified on the Query that only Work headers with Work lines less than 20 should be considered.

## Tips

The **System directed work sequence queries is inclusive**, which is important to know with certain setups. For example, if the user wishes for a certain menu item to process only work with work unit in eaches and it specifies that on the Range, all Work with at least one Work line with Work unit eaches will be fed to the user. This will therefore also include all Work with other Work units besides *eaches* (box or pallet) and it will not exclude those. It will exclude only Work where no Work lines have Work Unit set as each.

- Hence, in the example from this scenario, the Work ID 4 was also captured by the query. It was created with 2 lines, one for 25 ea and another one for 10 ea. The Work was still be assigned to the user because at least one Work line had less than 20 ea. This can be prevented with Work breaks, depending on the scenario.
