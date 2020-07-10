---
# required metadata

title: Cluster position full
description: This feature offers an alternative to more rigid enforcement of work break rules when using cluster picking as it enables larger margin of error in volumetric constraints of containers or totes. 
author: Mirzaab
manager: tfehr
ms.date: 07/08/2020
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
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: Release 10.0.8
---

# Cluster position full

[!include [banner](../includes/banner.md)]

This feature offers an alternative to more rigid enforcement of work break rules when using cluster picking as it enables larger margin of error in volumetric constraints of containers or totes. It is a common scenario that not all items within the work order fit into a selected container. This leaves the warehouse worker who is cluster picking with little option for resolution, either changing the container size to a larger one or solving it differently with the supervisor.

This functionality introduces the ability to execute "full" option on one of the work units within a cluster. This was not an option with cluster picking in older version, but it was only available with normal order picking. However, this feature differs from standard full button flow as it cancels the remaining work. It does not suggest user to add another bin to same cluster and it does not create new work automatically.

## Set up

This section provides guidelines and an example of how to set up and use this feature.

### Enable sample data

To work through the [example scenario](#example-scenario) using the sample records and values specified here, you must be on a system with the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) installed, and you must select the **USMF** legal entity before you begin.

You can also use this example as guidance for how to use this feature when working on a production system, but then you must substitute your own values for each setting described here.

### Cluster profiles

Specify whether to automatically generate cluster IDs, the number of positions to use, when to break clusters, and how to sequence and verify the picking work.

1. Go to **Warehouse management > Setup > Mobile device > Cluster profiles**.
1. In the list select **Create Cluster**.
1. In the **General** FastTab ensure the following is setup:
    - **Generate cluster ID** - *Yes*
    - **Activate positions** - *Yes*
    - **Number of positions** - *2*
    - **Position name** - *Numeric*
    - **Break cluster at** - *Put*
    - **Sort verification type** - *Position scan*

1. The **Cluster sorting** FastTab should be empty, no lines.

### Work templates

Define how to create the picking work for cluster picking.

1. Go to **Warehouse management > Setup > Work > Work templates**.
1. In the **Overview** grid, **Work order type** of *Sales order*, ensure that the demo data work templates for warehouse 61 are set up. If they are not setup you will not be able to complete the scenario:
    - **61 SO Stage**
    - **61 SO Cluster pick**

### Location directives

Specify where to pick items from, and where to put them.

1. Go to **Warehouse management > Setup > Location directives**.
1. In the list header select the **Work order type** of **Sales orders**.
1. In the list of sales order directives, ensure the following demo data location directives are setup. If they are not setup you will not be able to complete the scenario:
    - **61 Cluster pick**
    - **61 SO Pick order**

### Mobile device menu items

Configure a mobile device menu item to use existing work that is directed by cluster picking.

The cluster picking mobile device menu item must have the **Allow splitting of work** parameter enabled. Add the **SO Pick** work class added.

1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu items**.
1. In the list select **Cluster Pick Create**.
1. Select **Edit** in the Action Pane.
1. In the **General** FastTab ensure the following has been setup:
    - **Directed by** - *Cluster picking*
    - **Generate license plate** - *Yes*
    - **Allow splitting of work** - *Yes*
        - Must be enabled
    - **Cluster profile ID** - *Create Cluster*
    - Accept all other defaults

1. In the **Work classes** FastTab, ensure the following has been setup:
    - **Work class ID** - *Sales* : **Work order type** - *Sales orders*
    - **Work class ID** - *SO Pick* : **Work order type** - *Sales orders*
        - Must be added

## Create picking work

Before cluster picking can be performed, some outbound work must be created. The previously created **Cluster profile** specifies *2* cluster positions, so at least two different **Work ID**'s must be created for sales order picking. For this scenario transactions will take place in Warehouse **61** and use items **L0101** and **T0100**. Demo data will have a sufficient level of on-hand inventory of these items. Ensure that you have sufficient inventory to complete the transactions.

### Sales order 1

1. Go to **Sales and Marketing > Sales orders > All sales orders**.
1. Select **New** to create sales order 1.
1. In the **Create sales order** dialog box enter the following:
    - **Customer account** - *US-010*
    - **Warehouse** - *61*
    - Select **OK**

1. A new line is added to the sales order, enter the following:
    - **Item number** - *T0100*
    - **Quantity** - *5*

1. In the **Line details** FastTab, **Delivery** tab, set the **Confirmed ship date** to be *Today*'s date.
1. In the **Sales order lines** FastTab, select **Add line** in the Toolbar.
1. A new line is added to the sales order, enter the following:
    - **Item number** - *L0101*
    - **Quantity** - *20*

1. In the **Line details** FastTab, **Delivery** tab, set the **Confirmed ship date** to be *Today*'s date.
1. Next reserve inventory for each of the lines just added. Follow the steps below for both lines:
    - Select the line to reserve inventory
    - In the **Sales order lines** Toolbar, select **Inventory** then select **Reservation** from menu list.
    - On the **Reservation** page select **Reserve lot** in the Toolbar to reserve the inventory. Then close the page.

1. Once inventory has been reserved the sales order must be released to the warehouse.
1. In the Action Pane, select the **Warehouse** tab then select **Release to warehouse**.
1. When the release completes, informational messages will be displayed the the wave and load ID's created.

### Sales order 2

1. Go to **Sales and Marketing > Sales orders > All sales orders**.
1. Select **New** to create sales order 2.
1. In the **Create sales order** dialog box enter the following:
    - **Customer account** - *US-011*
    - **Warehouse** - *61*
    - Select **OK**

1. A new line is added to the sales order, enter the following:
    - **Item number** - *L0101*
    - **Quantity** - *20*

1. In the **Line details** FastTab, **Delivery** tab, set the **Confirmed ship date** to be *Today*'s date.
1. In the **Sales order lines** FastTab, select **Add line** in the Toolbar.
1. A new line is added to the sales order, enter the following:
    - **Item number** - *T0100*
    - **Quantity** - *2*

1. In the **Line details** FastTab, **Delivery** tab, set the **Confirmed ship date** to be *Today*'s date.
1. Next reserve inventory for each of the lines just added. Follow the steps below for both lines:
    - Select the line to reserve inventory
    - In the **Sales order lines** Toolbar, select **Inventory** then select **Reservation** from menu list.
    - On the **Reservation** page select **Reserve lot** in the Toolbar to reserve the inventory. Then close the page.

1. Once inventory has been reserved the sales order must be released to the warehouse.
1. In the Action Pane, select the **Warehouse** tab then select **Release to warehouse**.
1. When the release completes, informational messages will be displayed the the wave and load ID's created.

### Get Work ID's and License plate numbers

Two different Work IDs should have been created, each with two pick lines.

1. Go to **Warehouse management > Work > Work details**.
1. In the **Overview** grid column **Order number**, search for the two sales orders just created and make a note of the corresponding **Work ID** for each sales order.
1. In the **Lines** section, make note of the location from which each item will be picked.

1. Go to **Inventory management > Inquiries and reports > On-hand list**.
1. Filter the on-hand list as follows:
    - **Item number**
        - **is one of** - *L0101* and *T100*
    - **Warehouse**
        - **begins with** - *61*

1. Make note of the **License plate** in the location from the work details **Lines**.

<a name="example-scenario"></a>

## Scenario

### Mobile device flow execution – Work confirmation setup for Product

1. Login to the mobile device as user in warehouse 61.
1. Enter mobile device menu item: **Outbound > Cluster pick create**.

**TASK: Assign work to Cluster** opens.

1. Enter the Work ID for Sales order 1 to assign it to the cluster Position 1.
1. Select **OK** (**✔**).
1. Enter the Work ID for Sales order 2 to assign it to the cluster Position 2.
1. Select **OK** (**✔**).

**TASK: Cluster Pick Create: Pick** - *Item L0101 2 PL* opens.

Because the Cluster profile set the number of positions as 2, the system will automatically direct the user to the first consolidate pick (2 Pallets (PL) of item L0101).

During the following steps, the user can select the **DETAILS** tab on the screen to view additional information pertaining to the task, such as picking location.

1. Enter **ITEM** - *L0101*.
    - This is to confirm the item number as configured on the **Mobile Device Menu Item** - **Work confirmation setup**.

1. Next enter the license plate number associated with the item in the location being picked. You will pick 2 pallets.
1. Enter in **LP** - *LP_PICK_01*.
1. Select **OK** (**✔**).

**TASK: Sort: Cluster Pick Create** opens.

Here you will sort the 2 picked pallets into a pick position. This could be a tote or container to separate the picked inventory by sales order.

1. View the details presented on screen for the **Item** (**L0101**) and **Quantity** (**20** ea) to be sorted into **Position 1** (Sales order 1).
1. Enter in **POSITION NA...** - *1*.
1. Select **OK** (**✔**).
1. View the details presented on screen for the **Item** (**L0101**) and **Quantity** (**20** ea) to be sorted into **Position 2** (Sales order 2).
1. Enter in **POSITION NA...** - *2*.
1. Select **OK** (**✔**).

**TASK: Cluster Pick Create: Pick** - *Item T0100 7 ea* opens.

In this scenario, Position 1 cannot accept the full quantity of items to be picked to fulfill sales order 1. A position must be marked as being full, in this scenario a partial pick of the second item will be performed. The second item to be picked will be partially picked for Position 1. New work will be created to pick the remaining quantity to fulfill the order.

1. Select the menu button (**≡**).
1. In the menu select the **Position full** button.
1. Next identify the position that is full, select *1*.
1. Select **OK** (**✔**).
1. Next enter the pick quantity that can still be picked into position 1, the system knows which item number is being picked.
1. Enter *2*.
1. Select **OK** (**✔**).
1. Next confirm the Item number to completed the pick of the remaining item into position 2.
1. Enter **ITEM** - *T0100*.
Select **OK** (**✔**).
1. Enter the license plate the item is being picked from, **LP** - *LPREPL04*.
1. Select **OK** (**✔**).
1. View the details presented on screen for the **Item** (**T0100**) and **Quantity** (*2* ea) to be sorted into **Position 2** (Sales order 2).
1. Enter in **POSITION NA...** - *2*.
1. Select **OK** (**✔**).
1. View the details presented on screen for the **Item** (**T0100**) and **Quantity** (*2* ea) to be sorted into **Position 1** (Sales order 1).
1. Enter in **POSITION NA...** - *1*.
1. Select **OK** (**✔**).

**TASK: Cluster Pick Create: Put** opens.

In this scenario, the cluster pick has completed and the user is directed to put away the picked items in position 1 and position 2 into the staging location STAGE01. Review the on screen information, a total quantity of 44 will be put to the staging location.

1. Select **OK** (**✔**).

A message **Cluster Completed** is displayed on the screen.

The **Sales Picking** menu item can now be used to pick the remaining quantity, and **Sales loading** menu item can be used to move the items from the staging location to the loading dock.
