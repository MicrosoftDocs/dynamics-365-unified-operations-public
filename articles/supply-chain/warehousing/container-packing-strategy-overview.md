---
title: Container packing strategy overview
description: This topic presents a difference between container packing strategies. 
author: GalynaFedorova
ms.date: 06/11/2021
ms.topic: article
ms.search.form: WHSWaveTemplateTable, InventLocationIdLookup, WHSContainerType, WHSContainerGroup, WHSContainerizationTable, WHSContainerizationBreak, WHSCreateContainerBreak, WHSContainerStructure, WHSContainerTable
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: v-gfedorova
ms.search.validFrom: 2021-06-11
ms.dyn365.ops.version: 10.0.19
---

# Container packing strategy overview

A *container packing strategy* is a strategy that you can use to define item allocations across the containers. This topic explains the difference between the *Pack into all open containers* and *Pack into current container only* strategies.  

The *Pack into all open containers* strategy indicates that the system must check all open containers that have already been created during the containerization cycle to make sure that the items will fit in any of them. During packing, the system checks each item to see whether it will fit into any of the already created containers. If the item won't fit into an existing container, the system creates a new container and continues until it completes packing the entire order. For example, suppose there are *n* ordered items that require containerization. In the worst case, each time the system processes an item that doesn't fit into any existing container, the system will perform (((n-1) × (n+1)) / 2) checks in total to evaluate whether it fits into the existing containers.

The *Pack into current container only* strategy indicates that the system must check the most recently created container to make sure that the item will fit into that container. During packing, the system checks each item to see whether it will fit in the most recently created container. If the item won't fit into that container, the system creates a new container and continues until it completes packing the entire order. For example, suppose there are *n* ordered items that require containerization. In the worst case, the system will perform (n-1) checks in total to evaluate whether it fits into the containers.

## Example of the container packing strategy flow

For this example, suppose you are setting up items for the containerization with the following physical dimensions:

| Item | Physical dimensions (Width, Depth, Height)  | Weight  |
|---|---|---|
| HDMI Cable 6' | 1 x 1 x 1 | 1 |
| HDMI Cable 12' | 2 x 1 x 1 |1 |
| HDMI Cable 18' | 3 x 1 x 1 |2 |

You are setting up a box that will be used for packaging with the following physical dimensions:

| Container |Physical dimensions (Length, Width, Height) | Weight  | Volume|
|---|---|---|---|
| Medium Box | 6 x 3 x 2 | 10 | 100 |

You are setting up an order that contains the following products and quantities:

| Sales order line | Quantity  |
|---|---|
| HDMI Cable 12' | 9 |
| HDMI Cable 18' | 8 |
| HDMI Cable 6' | 13 |

The following table summarizes how containerization works when you use *Pack into all open containers* and when you use *Pack into current container only*.

| Pack into all open containers | Pack into current container |
|---|----|
| HDMI Cable 12': <ul><li>Create new container CONT0001.</li> <li>Place 9 ea into container CONT0001</li></ul>|HDMI Cable 12':<ul><li>Create a new container CONT0001.</li> <li>Place 9 ea into container CONT0001.</li></ul>|
|HDMI Cable 18': <ul><li> Check if item can fit container CONT0001.</li><li>Create new container CONT0002.</li> <li>Place 5 ea into container CONT0002.</li><li>Create new container CONT0003.</li> <li>Place 3 ea into container CONT0003.</li></ul> |HDMI Cable 18': <ul><li> Check if item can fit container CONT0001.</li><li>Create new container CONT0002.</li> <li>Place 5 ea into container CONT0002.</li><li>Create new container CONT0003.</li> <li>Place 3 ea into container CONT0003.</li></ul>|
|HDMI Cable 6': <ul><li> Check if item can fit container CONT0001.</li><li>Place 1 ea into container CONT0001.</li><li>Check if item can fit container CONT0002.</li><li>Check if item can fit container CONT0003.</li><li>Place 4 ea into container CONT0003.</li><li>Create new container CONT0004.</li><li>Place 8 ea into container CONT0004.</li></ul> |HDMI Cable 6':<ul><li> Check if item can fit container CONT0003.</li><li>Place 4 ea into container CONT0003.</li><li>Create new container CONT0004.</li><li>Place 9 ea into container CONT0004.</li></ul> |

## Example scenario: Pack single orders per container

This section presents a scenario where the system is set to  consolidation of multiple orders into one shipment, so we will containerize from the sales order to ensure that each single order, which contains multiple products, is packed in its own container.

This functionality lets you handle scenarios where you must pack only one sales order into each container, thereby making it possible for the distribution center to cross dock full containers between retail stores. In addition to the retail scenarios (order per retail store, shipping to a distribution center for cross docking) this technique is also commonly used in lean supply chains (sales order per just-in-time production line).

This scenario illustrates how you could containerize using the *Pack into current container only* strategy to decrease the number of containers that are evaluated during packing.

### Prerequisites

#### Enable the Consolidate shipments feature on your system

This scenario makes use of the *Consolidate shipments* feature, which you must enable using [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) if it isn't already available on your system.

#### Make demo data available

This scenario references values and records that are included in the standard demo data that is provided for Microsoft Dynamics 365 Supply Chain Management. If you want to use the values that are provided here as you do the exercises, be sure to work in an environment where the demo data is installed, and set the legal entity to **USMF** before you begin.

### Inspect or create container types

To inspect your container types, and create new ones if needed, follow these steps:

1. Go to **Warehouse management** \> **Setup** \> **Containers** \> **Container types**.
1. Make sure that each of the following container types is available in your demo data. Edit or create container types as needed.
    - Container type 1:
        - **Container type code:** *Box-Large*
        - **Description:** *Large Box*
        - **Maximum net weight:** *100*
        - **Volume:** *400*
        - **Length:** *4*
        - **Width:** *10*
        - **Height:** *10*
    - Container type 2:
        - **Container type code:** *Box-Medium*
        - **Description:** *Medium Box*
        - **Maximum net weight:** *50*
        - **Volume:** *200*
        - **Length:** *2*
        - **Width:** *10*
        - **Height:** *10*
    - Container type 3:
        - **Container type code:** *Box-Small*
        - **Description:** *Small Box*
        - **Maximum net weight:** *20*
        - **Volume:** *100*
        - **Length:** *1*
        - **Width:** *10*
        - **Height:** *10*

### Inspect or create container groups

To inspect your container groups, and create new ones if needed, follow these steps:

1. Go to **Warehouse management** \> **Setup** \> **Containers** \> **Container groups**.
1. Make sure that the following container group is available in your demo data. Select **New** to create it if needed.
    - **Container group ID:** *Boxes*
    - **Description:** *Box sizes*
1. On the **Details** FastTab for the *Boxes* container group, make sure the following lines exist. Select **New** to add them if needed.
    - **Line 1:**
        - **Sequence number:** *1*
        - **Container type:** *Box-Large*
        - **Container utilization percentage:** *100*
    - **Line 2:**
        - **Sequence number:** *2*
        - **Container type:** *Box-Medium*
        - **Container utilization percentage:** *100*
    - **Line 3:**
        - **Sequence number:** *3*
        - **Container type:** *Box-Small*
        - **Container utilization percentage:** *100*

### Create a new container build template

Create a new container build template by following these steps:

1. Go to **Warehouse management** \> **Setup** \> **Containers** \> **Container build template**.
1. Select **New** to create a new container build template with the following settings:
    - **Sequence number:** *1*
    - **Container template ID:** *Box*
    - **Container group ID:** *Boxes*
    - **Base query types:** *Sales allocation line*
    - **Wave step code:** *234*
    - **Allow split picks:** *Yes*
    - **Container packing strategy:** *Pack into current container only*
    - **Pack by directive unit:** *No*
1. With the new row still selected, on the Action Pane, select **Edit query**.
1. A standard query-editor dialog opens. On the **Sorting** tab, select **Add** to add a row that has the following settings:
    - **Table:** *Temporary work transactions*
    - **Derived table:** *Temporary work transactions*
    - **Field:** *Order number*
    - **Search direction:** *Ascending*
    > [!IMPORTANT]
    > To avoid cycling over all the other open containers, and to speed up the process by checking one container at a time, use the *Pack into current container only* strategy in addition to sorting by order number, which will work like a work break on a work template.  
1. Select **OK** to close the query-editor dialog.
1. With the new row still selected, on the Action Pane, select **Container mixing constraints**. This will let you add a constraint that will place items from single order into single container. Items from another order should be placed into another container. Select **New** to create a mixing constraint with the following settings:
    - **Table:** *Sales orders*
    - **Field select:** *SalesId* (will show as *Sales order* on the grid)
1. Select **OK** to add the constraint.
1. Close the page.

### Set up a wave template for containerization

Set up a wave template by following these steps:

1. Go to **Warehouse management \> Setup \> Waves \> Wave templates**.
1. In the list pane, set the **Wave template type** to *Shipping*.
1. Select template **63 Containerization** in the list.
1. On the Action Pane, select **Edit**.
1. On the **Methods** FastTab, in the **Selected methods** column, find the following line:
    - **Method name:** *containerization*
    - **Name:** *Containerization*
1. Set the **Wave step code** field for this line to *234*.

### Set up a work template

To set up a work template, follow these steps:

1. Go to **Warehouse management \> Setup \> Work \> Work templates**.
1. Set **Work order type** to *Sales orders*.
1. In the **Overview** grid, find and select the work template that should be used with this function. For this scenario, select the *63 Pick to container* template.
1. On the Action Pane, select **Edit query**.
1. A standard query-editor dialog opens. On the **Sorting** tab, add the following lines:
    - **Line 1:**
        - **Table:** *Temporary work transactions*
        - **Derived table:** *Temporary work transactions*
        - **Field:** *Shipment ID*
        - **Search direction:** *Ascending*
    - **Line 2:**
        - **Table:** *Temporary work transactions*
        - **Derived table:** *Temporary work transactions*
        - **Field:** *Order number*
        - **Search direction:** *Ascending*
    - **Line 3:**
        - **Table:** *Temporary work transactions*
        - **Derived table:** *Temporary work transactions*
        - **Field:** *Container ID*
        - **Search direction:** *Ascending*
1. Select **OK** to close the query-editor dialog.
1. You receive the following message: "Grouping will be reset, continue?" Select **Yes** to continue.
1. With the *63 Pick to container* template still selected, on the Action Pane, select **Work header breaks**. This will let you make settings to break the work so that each container within the order is linked to one work order.
1. Select the **Group by this field** check box for each row shown on the **Work header breaks** page (*Shipment ID*, *Order number*, *Container ID*.
1. Close the page.

### Set up shipment consolidation policies

To set up a shipment consolidation policy, follow these steps:

1. Go to **Warehouse management \> Setup \> Release to warehouse \> Shipment consolidation policies**.
1. On the list pane, set **Policy type** to *Sales orders*.
1. Select the *Default* policy on the list pane.
1. On the Action Pane, select **Edit**.
1. On the **Consolidation fields** FastTab, in the **Selected fields** list, select the row where the **Field name** field is set to *Order number*.
1. Select the **Remove** button ![Left arrow](media/backward-button.png) to move the field to the **Remaining fields** list.
1. On the Action Pane, select **Save**.

### Set up physical dimensions for the product

Set up physical dimensions for the products we will use in the scenario by doing the following:

1. Go to **Product information management \> Products \> Released products**.
1. Select the product with **Item number** *A0001*.
1. On the Action Pane, open the **Manage inventory** tab and, from the **Warehouse** group, select **Physical dimensions**.
1. The **Physical dimensions** page opens. You should see the following line on the grid:
    - **Unit:** *pcs*
    - **Gross weight:** *3.00*
    - **Width:** *2.00*
    - **Depth:** *2.00*
    - **Height:** *4.00*
    - **Volume:** *16.00*
1. Close the page.
1. Select the product with **Item number** *A0002*.
1. On the Action Pane, open the **Manage inventory** tab and, from the **Warehouse** group, select **Physical dimensions**.
1. The **Physical dimensions** page opens. You should see the following line on the grid:
    - **Unit:** *pcs*
    - **Gross weight:** *4.00*
    - **Width:** *3.00*
    - **Depth:** *1.00*
    - **Height:** *3.00*
    - **Volume:** *9.00*

### Create sales order 1

Create a sales order by doing the following:

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. On the Action Pane, select **New** to open a dialog box for creating a new sales order.
1. In the dialog box, set the following values:
    - **Customer account:** *US-001*
    - **Warehouse:** *63*
1. Select **OK** to create the sales order and close the dialog box.
1. The new sales order opens. On the **Sales order lines** FastTab, add the following sales lines:
    - **Line 1:**
        - **Item number:***A0001*
        - **Quantity:** *2*
    - **Line 2:**
        - **Item number:***A0002*
        - **Quantity:** *2*
1. Select the first line and select **Inventory \> Reservation** on the toolbar. On the **Reservation** page, select **Reserve lot**. Then close the page.
1. Repeat the previous step for the second line.
1. Close the page.

### Create sales order 2

Create a second sales order by doing the following:

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. On the Action Pane, select **New** to open a dialog box for creating a new sales order.
1. In the dialog box, set the following values:
    - **Customer account:** *US-001*
    - **Warehouse:** *63*
1. Select **OK** to create the sales order and close the dialog box.
1. The new sales order opens. On the **Sales order lines** FastTab, add the following sales lines:
    - **Line 1:**
        - **Item number:***A0001*
        - **Quantity:** *4*
    - **Line 2:**
        - **Item number:***A0002*
        - **Quantity:** *4*
1. Select the first line and select **Inventory \> Reservation** on the toolbar. On the **Reservation** page, select **Reserve lot**. Then close the page.
1. Repeat the previous step for the second line.
1. Close the page.

### Create the load

Follow these steps to create a load for each order that you created for this scenario and then release it to the warehouse.

1. Go to **Warehouse management \> Loads \> Load planning workbench**.
1. On the **Sales lines** tab, find and select all the sales order lines from the sales orders that you created for this scenario.
1. On the Action Pane, open the **Supply and demand** tab and, from the **Add** group, select **To new load**. This will add the selected order lines to a new Load.
1. The **Load template assignment** dialog opens. In the **Load template ID** field, select a load template, such as *40' Container*.
1. Select **OK** to close the dialog.
1. In the **Loads** section, find and select the load that you just created.
1. Select **Release \> Release to warehouse**.
1. The **Release to warehouse** dialog opens. Select **OK** to release the selected load to the warehouse.

### Verify the shipments and containers

The following procedure lets you verify the shipments that have been created. Use it to review the order that you created for this scenario to make sure that you've obtained the expected results.

1. Go to **Warehouse management \> Shipments \> All shipments**.
1. Find and select the shipment that was created for the load you just released.
1. On the Action Pane, open the **Transportation** tab and select **View containers**. Confirm that the items from sales orders were containerized into the two different containers.
