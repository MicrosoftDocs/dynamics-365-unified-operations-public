---
# required metadata

title: Pick line grouping
description: This topic provides an overview of pick line grouping.
author: Mirzaab
manager: tfehr
ms.date: 12/15/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSRFMenuItem,WHSWorkTemplateTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations, Supply Chain Management
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

Pick line grouping allows multiple work lines that have the same item and location to be combined into a single pick presented to the user on the mobile device. This allows for warehouse workers to be given the most efficient instructions possible, while still maintaining required work line separation within the system (for different containers, orders, etc).

## Enable the Pick line grouping feature

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - *Warehouse management*
- **Feature name** - *Pick line grouping*

## Set up pick line grouping

### Create a mobile device menu item

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. Select **New** in the Action Pane.
1. In the **Menu item name** field enter *Sales group line picking*.
1. In the **Title** field enter *Sales group line picking*.
    1. This is what will be displayed on the mobile device menu.
1. In the **Mode** field select *Work*.
1. Set the **Use existing work** option to *Yes*.
1. In the **General** FastTab set the following values:

    - In the **Directed by** field select *User directed*.
    - Set the **Generate license plate** option to *Yes*.
    - Set the **Group pick** option to *Yes*.
    - Accept the default values for the remaining options.

1. In the **Work classes** FastTab, follow these steps to configure the valid work classes for the mobile device menu item:

    - In the menu bar select **New**.
    - In the **Work class ID** field, you can select Sales or SO Pick, depending on the warehouse that you will use. For this scenario select *SO Pick*.
    - The **Work order type** field will default to *Sales orders*.

### Set up a mobile device menu

1. Add the menu item that you just created to the **Outbound** menu.
1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu**.
1. Select **Edit** in the Action Pane.
1. A list of existing menus will be in the pane on the left. There are two grid boxes in the **Mobile device menus** FastTab; **Available menus and menu items** and **Menu structure**.
1. Select **Outbound** from the list of menus.
1. In the list **Available menus and menu items** scroll until you find the menu item just created, **Sales group line picking**.
1. Select *Sales group line picking* in the list.
1. There are two arrow buttons between the grid boxes, the arrow pointing to **Menu structure** will be activated when you make the selection in the prior step.
1. Select the activated arrow button to move the menu item into the *menu structure* grid.
1. Use the Up and Down arrows to move the menu item into the desired position within the menu structure.
1. Select **Save** in the Action Pane.

### Set up a work template

1. Go to **Warehouse management \> Setup \> Work \> Work templates**.
1. In the **Work order type** field, select *Sales orders*.
1. In the **Overview** grid find the work template that should be used with this function. For this scenario, select the **51 Pick to stage** template.
1. In the Action Pane, select **Edit query**.
1. Select the **Sorting** tab, then select **Add** from the menu bar, and then set the following values:

    - In the **Table** field, select **Temporary work transactions**.
    - In the **Derived table** field, select **Temporary work transactions**.
    - In the **Field** field, select **Item number**.
    - In the **Search direction** field, select **Ascending**.

1. Select **OK** to close the window and save your selection.

1. A message **Grouping will be reset, continue?** will display, select **Yes** to continue.

> [!NOTE]
> For the pick line grouping functionality to work, the work lines must be sorted by item ID. If lines that have the same items aren't sequenced one after another, they won't be grouped.

## Example

### Create picking work

Before you can set up pick line grouping, you must create some eligible outbound work.

1. Go to **Sales and Marketing \> Sales orders \> All sales orders**.
1. Select **New** to create a sales order.
1. In the **Customer account** field, select **US-004**.
1. On the **General** FastTab, in the **Warehouse** field, select **51**. Then select **OK**.
1. In the **Sales order lines** FastTab, add the following six lines:

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

1. Before you release the orders to the warehouse, you must make sure that the pick locations have enough inventory for all the items on all the orders. Review the **Location directive** setting to determine which picking locations are used for sales order picking. If you are using the Contoso demo data environment for warehouse **51**, confirm that there is inventory available.
1. Reserve the inventory for each line.
1. With the line to be reserved selected in the grid of the **Sales order lines** FastTab, select **Inventory** from the menu bar, then select **Reservation** from the list.
1. On the **Reservation** page Action Pane, select **Reserve lot** to apply the reservation then close the page window.
1. Repeat for the remaining lines.
1. Release the sales order to the warehouse.
1. Select **Warehouse** from the Action Pane, then select **Release to warehouse**.
1. A message bar will be displayed with 3 lines indicating that a shipment and a wave have been created and that the wave has been submitted to run in a batch. When the wave and all downstream jobs have completed, a work ID that has six lines will be created. The lines will be sorted by item number.
1. Go to **Warehouse management \> Work \> All work** to view the created work. Make note of the created **Work ID** to be used in the next step.

### Initiate picking from the mobile device

1. Login to the mobile device with a user setup for warehouse 51.
1. On the mobile device, select the menu that includes the new mobile device menu item. In this scenario select **Outbound**.
1. Select the **Sales group line picking** menu item, to initiate the pick.
1. Enter the **Work ID** noted in the previous step.

> [!IMPORTANT]
> After you select the menu and enter the work ID, you see the pick step where all pick lines for item M9200 are grouped. You receive an instruction to pick 7 each of item M9200. On the mobile device the pick work for the three pick work lines has been aggregated into one picking step for the user.

1. Confirm the pick step.
1. Go to the work page of the work ID, notice that all three pick lines for item M9200 were closed simultaneously.
1. Go back to the mobile device and continue picking, work line 4 is presented for item M9201. Since there was only one work line on the order, there is nothing to consolidate.
1. Confirm the pick step.
1. The last pick step on the mobile device aggregates the last two pick lines from the work order.
1. Complete the pick step for 9 each of item M9202.
1. Confirm the put step and any additional pick/put pairs to complete the work.

> [!IMPORTANT]
>
> - Work lines can be grouped only if they are in sequence.
> - The following functionality isn't supported:
>
>   - Catch-weight items. If there are any catch-weight items on the work, you receive an error message before you start to pick.
>   - Piece picking.
>   - Work lines that have unfinished replenishment work.
>   - Over-picking.
>   - Short picking with item reallocation
