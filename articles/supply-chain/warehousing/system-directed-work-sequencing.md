---
title: System-directed work sequencing
description: Learn bout system-directed work sequencing. This functionality lets you sort and filter the work orders that the system presents to users for execution.
author: Mirzaab
ms.author: mirzaab
ms.topic: article
ms.date: 07/03/2020
ms.custom:
ms.reviewer: kamaybac
ms.search.form:  WHSRFSystemDirectedWorkSequenceQuery, WHSLocDirTable
---

# System-directed work sequencing

[!include [banner](../includes/banner.md)]

System-directed work sequencing lets you sort and filter the work orders that the system presents to users for execution. It's helpful in scenarios where additional criteria (such as the time of shipping, the picking zone, the location profile, or a combination of various criteria) are required to drive the warehouse picking process.

This functionality extends the current system-directed picking functionality by adding a system-directed query order, where you can set up a sequence and one or more queries that evaluate all work orders that are created. The system captures and presents only work orders that meet the criteria that you specify in the setup of the mobile device menu item.

Therefore, this functionality allows for further optimization of warehouse picking processes as it identifies work orders that match the specified criteria, assigns them to the correct mobile device menu item, and then presents them to a worker, based on a specific skill set, picking equipment, or other requirement.

> [!NOTE]
> If you need different criteria, use multiple mobile device menu items.

## Setup

### Make demo data available

To work through the scenario by using the values that are presented in this article, you must work on a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. Additionally, you must select the **USMF** legal entity. The scenario uses warehouse *51* from the demo data.

> [!IMPORTANT]
> Before you release the orders to the warehouse, make sure that the pick locations have enough inventory for all the items on the orders.
>
> Default USMF data should support this scenario. If you aren't using demo data, review the **Location directive** setting to learn which picking locations are used for sales order picking. If you must adjust the inventory, you can create manual movements, use replenishment, or use any other flow.

### Set up a mobile device menu item

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. In the list of mobile device menu items, select **Sales Picking – System**. The required menu item should already exist.
1. Confirm the following settings:

    - On the **General** FastTab, set the **Directed by** field to *System directed*.
    - On the **Work classes** FastTab, confirm the following settings:

        | Work class ID | Work order type |
        |---|---|
        | Sales | Sales orders |
        | SO Pick | Sales orders |

1. On the Action Pane, select **System directed work sequence queries**.
1. Select **Edit**.
1. Delete the existing line, and then confirm the action by selecting **Yes**.
1. On the Action Pane, select **New** to create a line.
1. On the new line, set the following values:

    - **Sequence number:** *1*
    - **Description field:** *Work quantity less than 20 and Descending*

1. Select **Save**.
1. On the Action Pane, select **Edit Query**.
1. On the **Joins** tab, expand the join hierarchy to show the **Work lines** table.
1. Select the **Work lines** table join.
1. Select **Add table join**.
1. In the list that appears, find and select the row that has the following settings:

    - **Join mode:** *n:1*
    - **Relation:** *Locations (Location)*

1. Select **Select**.

    The system adds locations to the table join.

1. On the **Sorting** tab, select **Add** to add a line.
1. On the new line, set the following values:

    - **Table:** *Work lines*
    - **Derived table:** *Work lines*
    - **Field:** *Work quantity* (In the message box that appears, select **Yes** to add sorting to this field.)
    - **Search direction:** *Descending*

1. Select the **Range** tab.

    If you want to include only specific work criteria in the sequencing, specify them on the **Range** tab. In this example, you want to include only work where the quantity is less than 20 ea (the lowest unit of measure).

    Notice that some lines are already included. Don't remove those lines.

1. Select **Add** to add a line.
1. On the new line, set the following values:

    - **Table:** *Work lines*
    - **Derived table:** *Work lines*
    - **Field:** *Inventory work quantity*
    - **Criteria:** *\<20* (less than 20)

1. Select **Add** to add another line.
1. On the new line, set the following values:

    - **Table:** *Work lines*
    - **Derived table:** *Work lines*
    - **Field:** *Work type*
    - **Criteria:** *Pick*

1. Select **Add** to add another line.
1. On the new line, set the following values:

    - **Table:** *Locations*
    - **Derived table:** *Locations*
    - **Field:** *Location profile ID*
    - **Criteria:** *!STAGE*

        > [!IMPORTANT]
        > Be sure to include the exclamation point (*!*) in front of *STAGE*.

1. Select **OK** to save and close the query.
1. Select **Save**.
1. Close the page to return to the **Mobile device menu items** page.

> [!NOTE]
> This setup defines the criteria that the system uses to feed eligible work to the mobile device menu item. If you add more criteria lines to the query, the system uses the query line with the lowest sequence number first. In other words, the user sees all eligible work for sequence number 1 first, then all work for sequence number 2. Therefore, if a specific range and sorting must be used together, specify them in the same system-directed work sequence query.
>
> This setup captures any work that has at least one line where the quantity is less than 20 ea. Therefore, if the work has a line where the quantity is exactly 20 ea or more than 20 ea, it's valid, provided that it also has at least one line where the quantity is less than 20 ea.

### Location directives

If you use default Contoso data, you don't need to change the query for the location directive action. However, to make sure that the location directives capture the items on the sales orders when you apply the feature in a non-Contoso environment, create a new location directive. To verify the settings in the demo environment, follow these steps.

1. Go to **Warehouse management** \> **Setup** \> **Location directives**.
1. In the **Work order type** field, select *Sales orders*.
1. Select the location directive named *51 Pick*.
1. On the **Location Directive Actions** FastTab, select the line for the **Pick** action.
1. Select **Edit query** above the grid.
1. Review the **Range** query.

    1. Find the line where the **Field** field is set to *Location*.
    1. Make sure that the **Criteria** field is blank (that is, there are no restrictions).

## Scenario

### Create sales order picking work

Before you run system-directed picking, create some outbound work. For this scenario, create four sales orders that are based on the specified system-directed work sequence queries.

You reserve inventory quantities for each sales order. Therefore, you can't withdraw reserved inventory from the warehouse for other orders unless you cancel the inventory reservation, or part of the inventory reservation.

You then release each sales order to the warehouse to create the outbound work.

#### Sales order 1

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. On the Action Pane, select **New** to create sales order 1.
1. In the **Create sales order** dialog box, set the following values:

    - In the **Customer** section, set the **Customer account** field to *US-004*.
    - In the **General** section, set the **Warehouse** field to *51*.

1. Select **OK** to close the dialog box. Make a note of the sales order number.
1. Add a line to the new sales order, and set the following values:

    - **Item number:** *M9200*
    - **Quantity:** *20*

1. On the **Inventory** menu above the grid, select **Reservation**.
1. On the **Reservation** page, select **Reserve lot** to reserve the inventory.
1. Close the **Reservation** page.
1. On the Action Pane, on the **Warehouse** tab, select **Release to warehouse** to create work for the warehouse.

    You receive informational messages that show the wave ID and shipment IDs that were created for the sales order.

#### Sales order 2

1. On the Action Pane, select **New** to create sales order 2.
1. In the **Create sales order** dialog box, set the following values:

    - **Customer account:** *US-007*
    - **Warehouse:** *51*

1. Select **OK** to close the dialog box. Make a note of the sales order number.
1. Add a line to the new sales order, and set the following values:

    - **Item number:** *M9200*
    - **Quantity:** *5*

1. Select **Add line** to add a second line, and set the following values:

    - **Item number:** *M9201*
    - **Quantity:** *1*

1. Reserve inventory for both lines.
1. Release the order to the warehouse.

#### Sales order 3

1. On the Action Pane, select **New** to create sales order 3.
1. In the **Create sales order** dialog box, set the following values:

    - **Customer account:** *US-009*
    - **Warehouse:** *51*

1. Select **OK** to close the dialog box. Make a note of the sales order number.
1. Add a line to the new sales order, and set the following values:

    - **Item number:** *M9200*
    - **Quantity:** *7*

1. Select **Add line** to add a second line, and set the following values:

    - **Item number:** *M9202*
    - **Quantity:** *8*

1. Reserve inventory for both lines.
1. Release the order to the warehouse.

#### Sales order 4

1. On the Action Pane, select **New** to create sales order 4.
1. In the **Create sales order** dialog box, set the following values:

    - **Customer account:** *US-010*
    - **Warehouse:** *51*

1. Select **OK** to close the dialog box. Make a note of the sales order number.
1. Add a line to the new sales order, and set the following values:

    - **Item number:** *M9200*
    - **Quantity:** *25*

1. Select **Add line** to add a second line, and set the following values:

    - **Item number:** *M9202*
    - **Quantity:** *10*

1. Reserve inventory for both lines.
1. Release the order to the warehouse.

### Get work IDs for the work that you created

1. Go to **Warehouse management \> Work \> Work details**.
1. Filter on the **Warehouse** field so that only work for warehouse *51* is shown.
1. Four work IDs are created. Make a note of the work ID for each sales order.

    | Sales order ID | Work ID | Work quantity |
    |---|---|---|
    | Sales Order 1 | Work ID 1 | 20 ea |
    | Sales Order 2 | Work ID 2 | 6 ea (sum of both lines) |
    | Sales Order 3 | Work ID 3 | 15 ea (sum of both lines) |
    | Sales Order 4 | Work ID 4 | 35 ea (sum of both lines) |

Before you run the flow on the mobile device, make sure that only the work that you just created is in *Open* status for warehouse *51* and the *Sales order* work order type. Otherwise, the results of the test might vary, because the system-direct picking includes all eligible work.

1. Go to **Warehouse management \> Work \> Outbound \> Open sales work**.
1. In the **Open sales work** grid, filter on the **Warehouse** field so that only work for warehouse *51* is shown.
1. Confirm that only the four work IDs that you created earlier are shown.
1. Close the **Work** page.

### Mobile device flow execution

Based on the setup, the system feeds the user work sorted from the highest work line quantity to the lowest. The quantity on every line is less than 20.

Remember that this setup captures any work that has at least one line where the quantity is less than 20. Therefore, if the work has another line where the quantity is exactly 20 or more than 20, it's also valid.

#### Mobile app

1. Sign in to the warehousing app as a user in warehouse *51*.
1. Go to **Outbound \> Sales Picking - System**.

    The pick step for work ID *4* is presented. This work ID is presented first because of the setup of the system-directed query order, where you specified that work is sequenced based on descending work line quantity.

1. Complete the required pick and put to close the work ID.

    Next, work ID *3* is presented. One of its work lines is next in the sequence, based on the work line quantity.

1. Complete the pick and put to close the work ID.

    Next, work ID *2* is presented. This work's pick line is next in the sequence.

1. Complete the pick and put to close the work ID.

    No further work is presented to you. Work ID *1* isn't eligible for this mobile device menu item, because the query specifies that work headers are considered only if the quantity on the work lines is less than 20.

## Tips

The system-directed work sequence queries are *inclusive*. Remember this fact for some setups. For example, you want a specific menu item to process only work where the work unit is *ea*, and you specify that restriction on the **Range** tab of the query. In this case, the worker receives all work where at least one work line has the work unit set to *ea*. Therefore, this work might also include work where work lines have a work unit other than *ea* (such as *box* or *pallet*). The query excludes only work where no work line has the work unit set to *ea*.

Therefore, in the example from this scenario, the query also captured work ID *4*. When you created it, you added two lines: one for 25 ea and another for 10 ea. The work was still presented to the user, because at least one work line has a quantity of less than 20 ea.

Depending on the scenario, you can prevent this behavior by using work breaks.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
