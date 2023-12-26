---
title: Container packing strategies
description: This article describes the differences between container packing strategies and provides examples.
author: GalynaFedorova
ms.date: 08/09/2022
ms.topic: article
ms.search.form: WHSWaveTemplateTable, InventLocationIdLookup, WHSContainerType, WHSContainerGroup, WHSContainerizationTable, WHSContainerizationBreak, WHSCreateContainerBreak, WHSContainerStructure, WHSContainerTable
audience: Application User
ms.reviewer: kamaybac
ms.collection: get-started
ms.search.region: Global
ms.author: gfedorova
ms.search.validFrom: 2021-06-11
ms.dyn365.ops.version: 10.0.19
---

# Container packing strategies

[!include [banner](../includes/banner.md)]

A *container packing strategy* is a strategy that you can use to define item allocations across containers. This article explains the differences between the *Pack into all open containers* and *Pack into current container only* strategies.

- **Pack into all open containers** – The system must check all open containers that have already been created during the containerization cycle, to make sure that the item will fit into one of them. During packing, the system checks each item to determine whether it will fit into any of the previously created containers. If the item won't fit into an existing container, the system creates a new container and continues until it has finished packing the whole order.

    For example, *n* ordered items require containerization. In the worst case, every time that the system processes an item that doesn't fit into any existing container, it will do a total of (\[(*n* – 1) × (*n* + 1)\] ÷ 2) checks to evaluate whether the item fits into the existing containers.

- **Pack into current container only** – The system must check only the most recently created container to make sure that the item will fit into it. During packing, the system checks each item to determine whether it will fit into the most recently created container. If the item won't fit into that container, the system creates a new container and continues until it has finished packing the whole order.

    For example, *n* ordered items require containerization. In the worst case, the system will do a total of (*n* – 1) checks to evaluate whether the item fits into the containers.

## Example of the flow for container packing strategies

You set up the following items for containerization.

| Item | Physical dimensions (width × depth × height) | Weight |
|---|---|---|
| HDMI Cable 6' | 1 × 1 × 1 | 1 |
| HDMI Cable 12' | 2 × 1 × 1 | 1 |
| HDMI Cable 18' | 3 × 1 × 1 | 2 |

You also set up the following box that will be used for packaging.

| Container | Physical dimensions (length × width × height) | Weight | Volume |
|---|---|---|---|
| Medium Box | 6 × 3 × 2 | 10 | 100 |

Finally, you set up an order that has the following products and quantities.

| Sales order line | Quantity |
|---|---|
| HDMI Cable 12' | 9 |
| HDMI Cable 18' | 8 |
| HDMI Cable 6' | 13 |

The following table summarizes how containerization works when you use the *Pack into all open containers* strategy and when you use the *Pack into current container only* strategy.

| Pack into all open containers | Pack into current container |
|---|---|
| <p>HDMI Cable 12':</p><ol><li>Create a new container, CONT0001.</li><li>Put 9 ea into container CONT0001.</li></ol> | <p>HDMI Cable 12':</p><ol><li>Create a new container, CONT0001.</li><li>Put 9 ea into container CONT0001.</li></ol> |
| <p>HDMI Cable 18':</p><ol><li>Check whether the item can fit into container CONT0001.</li><li>Create a new container, CONT0002.</li><li>Put 5 ea into container CONT0002.</li><li>Create a new container, CONT0003.</li><li>Put 3 ea into container CONT0003.</li></ol> | <p>HDMI Cable 18':</p><ol><li>Check whether the item can fit into container CONT0001.</li><li>Create a new container, CONT0002.</li><li>Put 5 ea into container CONT0002.</li><li>Create a new container, CONT0003.</li><li>Put 3 ea into container CONT0003.</li></ol> |
| <p>HDMI Cable 6':</p><ol><li>Check whether the item can fit into container CONT0001.</li><li>Put 1 ea into container CONT0001.</li><li>Check whether the item can fit into container CONT0002.</li><li>Check whether the item can fit into container CONT0003.</li><li>Put 4 ea into container CONT0003.</li><li>Create a new container, CONT0004.</li><li>Put 8 ea into container CONT0004.</li></ol> | <p>HDMI Cable 6':</p><ol><li>Check whether the item can fit into container CONT0003.</li><li>Put 4 ea into container CONT0003.</li><li>Create a new container, CONT0004.</li><li>Put 9 ea into container CONT0004.</li></ol> |

## Example scenario: Pack single orders per container

This section presents a scenario where the system is set up to consolidate multiple orders into one shipment. Therefore, containerization will be done from the sales order to ensure that every order that contains multiple products is packed into its own container.

This functionality lets you handle scenarios where you must pack only one sales order into each container, so that the distribution center can cross-dock full containers between retail stores. In addition to the retail scenarios (order per retail store and shipping to a distribution center for cross-docking) this technique is also commonly used in lean supply chains (sales order per just-in-time production line).

This scenario shows how you can decrease the number of containers that are evaluated during packing by using the *Pack into current container only* strategy for containerization.

### Prerequisites

#### Turn on the Consolidate shipments feature in your system

This scenario uses the *Consolidate shipments* feature. As of Supply Chain Management version 10.0.29, the feature is mandatory and can't be turned off. If you're running a version older than 10.0.29, then admins can turn this functionality on or off by searching for the *Consolidate shipments* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

#### Make demo data available

This scenario references values and records that are included in the standard demo data that is provided for Microsoft Dynamics 365 Supply Chain Management. If you want to use the values that are provided here as you do the exercises, be sure to work in an environment where the demo data is installed, and set the legal entity to **USMF** before you begin.

### Inspect or create container types

To inspect your container types, or to create new container types if they are required, follow these steps.

1. Go to **Warehouse management** \> **Setup** \> **Containers** \> **Container types**.
1. Make sure that each of the following container types is available in your demo data. Edit or create container types as required.

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

To inspect your container groups, or to create new container groups if they are required, follow these steps.

1. Go to **Warehouse management** \> **Setup** \> **Containers** \> **Container groups**.
1. Make sure that the following container group is available in your demo data. If it isn't available, select **New** to create it.

    - **Container group ID:** *Boxes*
    - **Description:** *Box sizes*

1. On the **Details** FastTab for the *Boxes* container group, make sure that the following lines exist. If they don't, select **New** to add them.

    - Line 1:

        - **Sequence number:** *1*
        - **Container type:** *Box-Large*
        - **Container utilization percentage:** *100*

    - Line 2:

        - **Sequence number:** *2*
        - **Container type:** *Box-Medium*
        - **Container utilization percentage:** *100*

    - Line 3:

        - **Sequence number:** *3*
        - **Container type:** *Box-Small*
        - **Container utilization percentage:** *100*

### Create a new container build template

To create a new container build template, follow these steps.

1. Go to **Warehouse management** \> **Setup** \> **Containers** \> **Container build template**.
1. Select **New** to create a container build template that has the following settings:

    - **Sequence number:** *1*
    - **Container template ID:** *Box*
    - **Container group ID:** *Boxes*
    - **Base query types:** *Sales allocation line*
    - **Wave step code:** *234*
    - **Allow split picks:** *Yes*
    - **Container packing strategy:** *Pack into current container only*
    - **Pack by directive unit:** *No*

1. While the row for the new template is still selected, select **Edit query** on the Action Pane.
1. A standard query editor dialog box appears. On the **Sorting** tab, select **Add** to add a row that has the following settings:

    - **Table:** *Temporary work transactions*
    - **Derived table:** *Temporary work transactions*
    - **Field:** *Order number*
    - **Search direction:** *Ascending*

    > [!IMPORTANT]
    > To avoid cycling over all the other open containers, and to speed up the process by checking one container at a time, use the *Pack into current container only* strategy in addition to sorting by order number. This combination will work like a work break on a work template.

1. Select **OK** to close the query editor dialog box.
1. While the row for the new template is still selected, select **Container mixing constraints** on the Action Pane.

    You will now add a constraint that puts items from a single order into a single container. Items from any other order will be put into a separate container.

1. Select **New** to create a mixing constraint that has the following settings:

    - **Table:** *Sales orders*
    - **Field select:** *SalesId* (The field will appear as *Sales order* in the grid.)

1. Select **OK** to add the constraint.
1. Close the page.

### Set up a wave template for containerization

To set up a wave template, follow these steps.

1. Go to **Warehouse management \> Setup \> Waves \> Wave templates**.
1. In the list pane, set the **Wave template type** field to *Shipping*.
1. Select the **63 Containerization** template in the list.
1. On the Action Pane, select **Edit**.
1. On the **Methods** FastTab, in the **Selected methods** column, find the following line:

    - **Method name:** *containerization*
    - **Name:** *Containerization*

1. Set the **Wave step code** field for the line to *234*.

### Set up a work template

To set up a work template, follow these steps.

1. Go to **Warehouse management \> Setup \> Work \> Work templates**.
1. Set the **Work order type** field to *Sales orders*.
1. In the **Overview** grid, find and select the work template that should be used for packing single orders per container. For this scenario, select the **63 Pick to container** template.
1. On the Action Pane, select **Edit query**.
1. A standard query editor dialog box appears. On the **Sorting** tab, add the following lines:

    - Line 1:

        - **Table:** *Temporary work transactions*
        - **Derived table:** *Temporary work transactions*
        - **Field:** *Shipment ID*
        - **Search direction:** *Ascending*

    - Line 2:

        - **Table:** *Temporary work transactions*
        - **Derived table:** *Temporary work transactions*
        - **Field:** *Order number*
        - **Search direction:** *Ascending*

    - Line 3:

        - **Table:** *Temporary work transactions*
        - **Derived table:** *Temporary work transactions*
        - **Field:** *Container ID*
        - **Search direction:** *Ascending*

1. Select **OK** to close the query editor dialog box.
1. You receive the following message: "Grouping will be reset, continue?" Select **Yes** to continue.
1. While the **63 Pick to container** template is still selected, select **Work header breaks** on the Action Pane.

    You will now apply settings to break the work so that each container in the order is linked to one work order.

1. Select the **Group by this field** checkbox for each row on the **Work header breaks** page (**Shipment ID**, **Order number**, and **Container ID**).
1. Close the page.

### Set up shipment consolidation policies

To set up a shipment consolidation policy, follow these steps.

1. Go to **Warehouse management \> Setup \> Release to warehouse \> Shipment consolidation policies**.
1. In the list pane, set the **Policy type** field to *Sales orders*.
1. Select the **Default** policy in the list.
1. On the Action Pane, select **Edit**.
1. On the **Consolidation fields** FastTab, in the **Selected fields** list, select the row where the **Field name** field is set to *Order number*.
1. Select the **Remove** button ![Left arrow.](media/backward-button.png) to move the field to the **Remaining fields** list.
1. On the Action Pane, select **Save**.

### Set up physical dimensions for the product

To set up physical dimensions for the products that will be used in this scenario, follow these steps.

1. Go to **Product information management \> Products \> Released products**.
1. Select the product where the **Item number** field is set to *A0001*.
1. On the Action Pane, on the **Manage inventory** tab, in the **Warehouse** group, select **Physical dimensions**.
1. On the **Physical dimensions** page, you should see the following line in the grid:

    - **Unit:** *pcs*
    - **Gross weight:** *3.00*
    - **Width:** *2.00*
    - **Depth:** *2.00*
    - **Height:** *4.00*
    - **Volume:** *16.00*

1. Close the page.
1. Select the product where the **Item number** field is set to *A0002*.
1. On the Action Pane, on the **Manage inventory** tab, in the **Warehouse** group, select **Physical dimensions**.
1. On the **Physical dimensions** page, you should see the following line in the grid:

    - **Unit:** *pcs*
    - **Gross weight:** *4.00*
    - **Width:** *3.00*
    - **Depth:** *1.00*
    - **Height:** *3.00*
    - **Volume:** *9.00*

### Create sales order 1

To create a sales order, follow these steps.

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. On the Action Pane, select **New**.
1. A dialog box for creating a new sales order appears. Set the following values:

    - **Customer account:** *US-001*
    - **Warehouse:** *63*

1. Select **OK** to create the sales order and close the dialog box.
1. The new sales order is opened. On the **Sales order lines** FastTab, add the following sales lines:

    - Line 1:

        - **Item number:** *A0001*
        - **Quantity:** *2*

    - Line 2:

        - **Item number:** *A0002*
        - **Quantity:** *2*

1. Select the first line, and then select **Inventory \> Reservation**.
1. On the **Reservation** page, select **Reserve lot**. Then close the page.
1. Repeat the previous two steps for the second line.
1. Close the page.

### Create sales order 2

To create a second sales order, follow these steps.

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. On the Action Pane, select **New**.
1. A dialog box for creating a new sales order appears. Set the following values:

    - **Customer account:** *US-001*
    - **Warehouse:** *63*

1. Select **OK** to create the sales order and close the dialog box.
1. The new sales order is opened. On the **Sales order lines** FastTab, add the following sales lines:

    - Line 1:

        - **Item number:** *A0001*
        - **Quantity:** *4*

    - Line 2:

        - **Item number:** *A0002*
        - **Quantity:** *4*

1. Select the first line, and then select **Inventory \> Reservation**.
1. On the **Reservation** page, select **Reserve lot**. Then close the page.
1. Repeat the previous two steps for the second line.
1. Close the page.

### Create the load

To create a load for each order that you created for this scenario and then release it to the warehouse, follow these steps.

1. Go to **Warehouse management \> Loads \> Load planning workbench**.
1. On the **Sales lines** tab, find and select all the sales order lines from the sales orders that you created for this scenario.
1. On the Action Pane, on the **Supply and demand** tab, in the **Add** group, select **To new load**. The selected order lines are added to a new load.
1. In the **Load template assignment** dialog box, in the **Load template ID** field, select a load template, such as *40' Container*.
1. Select **OK** to close the dialog box.
1. In the **Loads** section, find and select the load that you just created.
1. Select **Release \> Release to warehouse**.
1. In the **Release to warehouse** dialog box, select **OK** to release the selected load to the warehouse.

### Verify the shipments and containers

The following procedure lets you verify the shipments that have been created. Use it to review the order that you created for this scenario, to make sure that you've obtained the expected results.

1. Go to **Warehouse management \> Shipments \> All shipments**.
1. Find and select the shipment that was created for the load that you just released.
1. On the Action Pane, on the **Transportation** tab, select **View containers**.
1. Confirm that the items from the sales orders were containerized into two different containers.

## Additional resources

- [Containerization](wave-containerization.md)
