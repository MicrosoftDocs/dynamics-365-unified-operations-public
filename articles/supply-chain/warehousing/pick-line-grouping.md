---
# required metadata

title: Pick line grouping
description: This article provides an overview of pick line grouping.
author: Mirzaab
ms.date: 12/15/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: WHSRFMenuItem,WHSWorkTemplateTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2019-12-31
ms.dyn365.ops.version: 10.0.1

---

# Pick line grouping

[!include [banner](../includes/banner.md)]

Pick line grouping enables multiple work lines that have the same item and location to be combined into a single pick that is presented to the user on the mobile device. Therefore, warehouse workers can receive the most efficient instructions, but required work line separation (for different containers, orders, and so on) can still be maintained in the system.

## Turn the pick line grouping feature on or off

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.32, it's turned on by default. As of Supply Chain Management version 10.0.36, the feature is mandatory and can't be turned off. If you're running a version older than 10.0.36, then admins can turn this functionality on or off by searching for the *Pick line grouping* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

## Set up pick line grouping

### Create a mobile device menu item

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. On the Action Pane, select **New**.
1. In the **Menu item name** field, enter *Sales group line picking*.
1. In the **Title** field, enter *Sales group line picking*. This title will be shown on the mobile device menu.
1. In the **Mode** field, select *Work*.
1. Set the **Use existing work** option to *Yes*.
1. On the **General** FastTab, set the following values:

    - In the **Directed by** field, select *User directed*.
    - Set the **Generate license plate** option to *Yes*.
    - Set the **Group pick** option to *Yes*.
    - Accept the default values for the remaining options.

1. Follow these steps to configure the valid work classes for the mobile device menu item:

    1. On the **Work classes** FastTab, elect **New**.
    2. In the **Work class ID** field, you can select either *Sales* or *SO Pick*, depending on the warehouse that you will use. For this scenario, select *SO Pick*.

        The **Work order type** field is automatically set to *Sales orders*.

### Set up a mobile device menu

Follow these steps to add the menu item that you just created to the **Outbound** menu.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu**.
1. On the Action Pane, select **Edit**.
1. The list pane shows all existing mobile device menus. Select *Outbound* in the list.
1. In the **Available menus and menu items** list, find and select the *Sales group line picking* menu item that you created.
1. Select the right arrow button to move the *Sales group line picking* menu item to the **Menu structure** list.
1. Use the up arrow and down arrow buttons to move the menu item into the desired position in the menu structure.
1. On the Action Pane, select **Save**.

### Set up a work template

1. Go to **Warehouse management \> Setup \> Work \> Work templates**.
1. In the **Work order type** field, select *Sales orders*.
1. In the **Overview** grid, find and select the work template that should be used with this function. For this scenario, select the *51 Pick to stage* template.
1. On the Action Pane, select **Edit query**.
1. In the query editor dialog box, on the **Sorting** tab, select **Add**, and then set the following values for the new row:

    - In the **Table** column, select *Temporary work transactions*.
    - In the **Derived table** column, select *Temporary work transactions*.
    - In the **Field** column, select *Item number*.
    - In the **Search direction** column, select *Ascending*.

1. Select **OK** to close the dialog box and save your selection.
1. You receive the following message: "Grouping will be reset, continue?" Select **Yes** to continue.

> [!IMPORTANT]
> For the pick line grouping functionality to work, the work lines must be sorted by item ID. If lines that have the same items aren't sequenced one after another, they won't be grouped.

## Example

### Create picking work

Before you can set up pick line grouping, you must create some eligible outbound work.

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. Select **New** to create a sales order.
1. In the **Customer account** field, select *US-004*.
1. On the **General** FastTab, in the **Warehouse** field, select *51*.
1. Select **OK**.
1. On the **Sales order lines** FastTab, add the following six lines:

    - **Line 1:** In the **Item number** field, select *M9200*. In the **Quantity** field, enter *3*.
    - **Line 2:** In the **Item number** field, select *M9201*. In the **Quantity** field, enter *3*.
    - **Line 3:** In the **Item number** field, select *M9202*. In the **Quantity** field, enter *2*.
    - **Line 4:** In the **Item number** field, select *M9200*. In the **Quantity** field, enter *1*.
    - **Line 5:** In the **Item number** field, select *M9200*. In the **Quantity** field, enter *3*.
    - **Line 6:** In the **Item number** field, select *M9202*. In the **Quantity** field, enter *7*.

    Here is a summary of the total quantities for each item:

    - **Item M9200:** *7* each
    - **Item M9201:** *3* each
    - **Item M9202:** *9* each

1. Before you release the orders to the warehouse, you must make sure that the pick locations have enough inventory for all the items on all the orders. Review the **Location directive** setting to determine which picking locations are used for sales order picking. If you're using the Contoso demo data environment for warehouse *51*, confirm that there is available inventory.

    You must now reserve the inventory for each line.

1. On the **Sales order lines** FastTab, select one of the lines that must be reserved.
1. On the **Inventory** menu above the grid, select **Reservation**.
1. On the **Reservation** page, on the Action Pane, select **Reserve lot** to apply the reservation. Then close the page.
1. Repeat steps 8 through 10 for the remaining lines that must be reserved.

    You must now release the sales order to the warehouse.

1. On the Action Pane, on the **Warehouse** tab, select **Release to warehouse**.

    You receive a message that states that a shipment and a wave have been created, and that the wave has been submitted to run in a batch.

    When the wave and all downstream jobs have been completed, a work ID is created for work that has six lines. The lines are sorted by item number.

1. Go to **Warehouse management \> Work \> All work** to view the work that was created. Make a note of the **Work ID** value, because you will need it in the next procedure.

### Initiate picking from the mobile device

1. Sign in to the mobile device as a user who is set up for warehouse *51*.
1. On the mobile device, select the menu that includes the new mobile device menu item. For this scenario, select **Outbound**.
1. Select the **Sales group line picking** menu item to initiate the pick.
1. Enter the **Work ID** value that you made a note of in the previous procedure.

    You should see a pick step where all pick lines for item *M9200* are grouped, and you should receive an instruction to pick *7* each of item *M9200*.

    > [!IMPORTANT]
    > On the mobile device, the pick work for the three pick work lines has been aggregated into one picking step for the user.

1. Confirm the pick step.
1. Go to the work page for the work ID, and notice that all three pick lines for item *M9200* were closed simultaneously.
1. Go back to the mobile device, and continue to pick. Work line 4 for item *M9201* should be presented. Because there was only one work line on the order, there is nothing to aggregate.
1. Confirm the pick step.
1. The last pick step on the mobile device aggregates the last two pick lines from the work order.
1. Complete the pick step for *9* each of item *M9202*.
1. Confirm the put step and any additional pick/put pairs to complete the work.

> [!IMPORTANT]
>
> - Work lines can be grouped only if they are in sequence.
> - The following functionality isn't supported:
>
>   - Catch-weight items
>
>    If there are any catch-weight items on the work, you receive an error message before you start to pick.
>
>   - Piece picking
>   - Work lines that have unfinished replenishment work
>   - Over-picking
>   - Short picking with item reallocation


[!INCLUDE[footer-include](../../includes/footer-banner.md)]