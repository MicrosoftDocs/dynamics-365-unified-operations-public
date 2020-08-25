---
# required metadata

title: Cluster position full
description: This feature offers an alternative to more rigid enforcement of work break rules when using cluster picking as it enables larger margin of error in volumetric constraints of containers or totes. 
author: Mirzaab
manager: tfehr
ms.date: 08/25/2020
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

This feature offers an alternative to more rigid enforcement of work break rules when using cluster picking because it enables larger margin of error in volumetric constraints of containers or totes. It is a common scenario that not all items within a work order fit into a selected container. This leaves warehouse workers who are cluster picking with little option for resolution&mdash;they must either change the container size to a larger one or solve it differently with their supervisor.

This functionality introduces the ability to execute the *full* option on one of the work units within a cluster. This wasn't an option with cluster picking in older versions&mdash;it was only available with normal order picking. However, this feature differs from standard full-button flow as it cancels the remaining work. It doesn't suggest that the user add another bin to same cluster and it doesn't create new work automatically.

## Turn on the Cluster position full feature

Before you can use this feature, it must be turned on in your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Warehouse management*
- **Feature name:** *Cluster position full*

## Set up

This section provides guidelines and an example of how to set up and use this feature.

### Enable sample data

To work through the [example scenario](#example-scenario) using the sample records and values specified here, you must be on a system with the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) installed, and you must select the **USMF** legal entity before you begin.

You can also use this example as guidance for how to use this feature when working on a production system, but then you must substitute your own values for each setting described here.

### Cluster profiles

Specify whether to automatically generate cluster IDs, the number of positions to use, when to break clusters, and how to sequence and verify the picking work:

1. Go to **Warehouse management > Setup > Mobile device > Cluster profiles**.
1. On the list pane, select the *Create Cluster* record.
1. On the **General** FastTab, make the following settings:
    - **Generate cluster ID** - *Yes*
    - **Activate positions** - *Yes*
    - **Number of positions** - *2*
    - **Position name** - *Numeric*
    - **Break cluster at** - *Put*
    - **Sort verification type** - *Position scan*
1. The **Cluster sorting** FastTab should be empty (no lines).

### Work templates

Define how to create the picking work for cluster picking:

1. Go to **Warehouse management > Setup > Work > Work templates**.
1. At the top of the page, set **Work order type** to *Sales orders*.
1. Make sure that the following demo-data work templates are listed (if they aren't available, you won't be able to complete the scenario):
    - **61 SO Stage**
    - **61 SO Cluster pick**

### Location directives

Specify where to pick items from, and where to put them:

1. Go to **Warehouse management > Setup > Location directives**.
1. On the list pane, set the **Work order type** to *Sales orders*.
1. Make sure that the following demo-data sales order directives are listed (if they aren't available, you won't be able to complete the scenario):
    - **61 Cluster pick**
    - **61 SO Pick order**

### Mobile device menu items

Configure a mobile device menu item to use existing work that is directed by cluster picking. The cluster picking mobile device menu item must have the **Allow splitting of work** parameter enabled and the **SO Pick** work class added. Do the following:

1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu items**.
1. On the list pane, select the *Cluster Pick Create* record.
1. On the **General** FastTab, make the following settings:
    - **Directed by** - *Cluster picking*
    - **Generate license plate** - *Yes*
    - **Allow splitting of work** - *Yes*
    - **Cluster profile ID** - *Create Cluster*
    - Accept all other defaults

1. On the **Work classes** FastTab, add the following two lines (as needed):
    - Line 1 (usually present in demo data):
        - **Work class ID** - *Sales* 
        - **Work order type** - *Sales orders*
    - Line 2 (probably not present):
        - **Work class ID** - *SO Pick*
        - **Work order type** - *Sales orders*

## Create picking work

Before you can start cluster picking, you must create some outbound work. The previously created **Cluster profile** specifies two cluster positions, so at least two different work IDs must be created for sales order picking. For this scenario, transactions will take place in **Warehouse** *61* and use **Items** *L0101* and *T0100*. Demo data should have a sufficient level of on-hand inventory of these items. Ensure that you have sufficient inventory to complete the transactions.

### Create sales order 1

Do the following:

1. Go to **Sales and Marketing > Sales orders > All sales orders**.
1. Select **New** to create sales order 1.
1. In the **Create sales order** dialog box, enter the following:
    - **Customer account** - *US-010*
    - **Warehouse** - *61*
1. Select **OK**.
1. Your new sales order opens. On the **Sales order lines** FastTab, add a line with the following settings:
    - **Item number** - *T0100*
    - **Quantity** - *5*
1. On the **Line details** FastTab, open the **Delivery** tab and set the **Confirmed ship date** to today's date.
1. On the **Sales order lines** FastTab, add a second line with the following settings:
    - **Item number** - *L0101*
    - **Quantity** - *20*
1. On the **Line details** FastTab, open the **Delivery** tab and set the **Confirmed ship date** to today's date.
1. Reserve inventory for each of the lines you just added by doing the following for each line:
    - Select the line you need to reserve.
    - On the **Sales order lines** toolbar, select **Inventory > Reservation**.
    - The **Reservation** page opens. Select **Reserve lot** on the Action Pane to reserve the inventory. Then close the **Reservation** page.
1. On  the Action Pane, open the **Warehouse** tab and then select **Release to warehouse**.
1. When the release completes, informational messages will be displayed the the wave and load IDs created.

### Create sales order 2

Do the following:

1. Go to **Sales and Marketing > Sales orders > All sales orders**.
1. Select **New** to create sales order 2.
1. In the **Create sales order** dialog box enter the following:
    - **Customer account** - *US-011*
    - **Warehouse** - *61*
1. Select **OK**.
1. Your new sales order opens. On the **Sales order lines** FastTab, add a line with the following settings:
    - **Item number** - *L0101*
    - **Quantity** - *20*
1. On the **Line details** FastTab, open the **Delivery** tab and set the **Confirmed ship date** to today's date.
1. On the **Sales order lines** FastTab, add a second line with the following settings:
    - **Item number** - *T0100*
    - **Quantity** - *2*
1. On the **Line details** FastTab, open the **Delivery** tab and set the **Confirmed ship date** to today's date.
1. Reserve inventory for each of the lines you just added by doing the following for each line:
    - Select the line you need to reserve.
    - On the **Sales order lines** toolbar, select **Inventory > Reservation**.
    - The **Reservation** page opens. Select **Reserve lot** on the Action Pane to reserve the inventory. Then close the **Reservation** page.
1. On  the Action Pane, open the **Warehouse** tab and then select **Release to warehouse**.
1. When the release completes, informational messages will be displayed the the wave and load IDs created.

### Get work IDs and license plate numbers

Two different work IDs should have been created, each with two pick lines. Find their work IDs and license plate assignments by doing the following:

1. Go to **Warehouse management > Work > Work details**.
1. In the **Overview** grid, search the **Order number** column for the two sales orders you just created and make a note of the corresponding **Work ID** for each sales order.
1. On the **Lines** grid, make note of the location from which each item will be picked. (Select a row from the **Overview** grid to view related information on the **Lines** grid.)
1. Go to **Inventory management > Inquiries and reports > On-hand list**.
1. Select **Dimensions** on the Action Pane to open the **Dimension display** dialog box. Make sure the **License plate**, **Warehouse** and **Item number** check boxes are selected and then select **OK**.
1. Set the following on the **Filters** pane:
    - **Item number**
        - **is one of** - *L0101* and *T100*
    - **Warehouse**
        - **begins with** - *61*
1. Make note of the **License plate** values shown.

## <a name="example-scenario"></a>Example Scenario

### Mobile device flow execution – Work confirmation setup for product

1. Sign in to the warehouse app as user in warehouse 61.
1. Enter mobile device menu item: **Outbound > Cluster pick create**.
1. **TASK: Assign work to Cluster** opens.
1. Enter the Work ID for sales order 1 to assign it to cluster position 1.
1. Select **OK** (**✔**).
1. Enter the Work ID for sales order 2 to assign it to cluster position 2.
1. Select **OK** (**✔**).
1. **TASK: Cluster Pick Create: Pick** - *Item L0101 2 PL* opens.

Because the cluster profile set the number of positions as 2, the system will automatically direct you to the first consolidate pick (2 Pallets (PL) of item L0101).

During the following steps, you can select the **DETAILS** tab on the screen to view additional information pertaining to the task, such as picking location.

1. Set **ITEM** to *L0101*. This is to confirm the item number as configured on the **Mobile Device Menu Item** - **Work confirmation setup**.
1. Enter the license plate number associated with the item in the location being picked. You will pick 2 pallets.
1. Set **LP** to *LP_PICK_01*.
1. Select **OK** (**✔**).
1. **TASK: Sort: Cluster Pick Create** opens. Here you will sort the 2 picked pallets into a pick position. This could be a tote or container to separate the picked inventory by sales order.
1. View the details presented on screen for the **Item** (*L0101*) and **Quantity** (*20* ea) to be sorted into **Position 1** (sales order 1).
1. Set **POSITION NA...** to *1*.
1. Select **OK** (**✔**).
1. View the details presented on screen for the **Item** (*L0101*) and **Quantity** (*20* ea) to be sorted into **Position 2** (sales order 2).
1. Set **POSITION NA...** to *2*.
1. Select **OK** (**✔**).
1. **TASK: Cluster Pick Create: Pick** - *Item T0100 7 ea* opens.

In this scenario, position 1 can't accept the full quantity of items to be picked to fulfill sales order 1. A position must be marked as being full. In this scenario, you will do a partial pick of the second item. The second item to be picked will be partially picked for position 1. New work will be created to pick the remaining quantity to fulfill the order.

1. Select the menu button (**≡**).
1. In the menu, select **Position full**.
1. Identify the position that is full, select *1*.
1. Select **OK** (**✔**).
1. Enter the pick quantity that can still be picked into position 1. The system knows which item number is being picked.
1. Enter *2*.
1. Select **OK** (**✔**).
1. Confirm the item number to complete the pick of the remaining item into position 2.
1. Set **ITEM** to *T0100*.
Select **OK** (**✔**).
1. Enter the license plate the item is being picked from by setting **LP** to *LPREPL04*.
1. Select **OK** (**✔**).
1. View the details presented on screen for the **Item** (*T0100*) and **Quantity** (*2* ea) to be sorted into **Position 2** (sales order 2).
1. Set **POSITION NA...** to *2*.
1. Select **OK** (**✔**).
1. View the details presented on screen for the **Item** (*T0100*) and **Quantity** (*2* ea) to be sorted into **Position 1** (sales order 1).
1. Set **POSITION NA...** to *1*.
1. Select **OK** (**✔**).
1. **TASK: Cluster Pick Create: Put** opens.

In this scenario, the cluster pick has completed and the user is directed to put away the picked items from position 1 and position 2 into the staging location STAGE01. Review the on screen information, a total quantity of 44 will be put to the staging location. Then select **OK** (**✔**). The message **Cluster Completed** is displayed on the screen.

You can now use **Sales Picking** menu item to pick the remaining quantity, and the **Sales loading** menu item to move the items from the staging location to the loading dock.
