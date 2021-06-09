---
title: Container packing strategy overview
description: This topic presents a difference between container packing strategies. 
author: GalynaFedorova
ms.date: 06/01/2021
ms.topic: article
ms.search.form: WHSWaveTemplateTable, InventLocationIdLookup, WHSContainerType, WHSContainerGroup, WHSContainerizationTable, WHSContainerizationBreak, WHSCreateContainerBreak, WHSContainerStructure, WHSContainerTable
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: v-gfedorova
ms.search.validFrom: 2021-06-01
ms.dyn365.ops.version: 10.0.19
---

## Container packing strategy overview
Container packing strategy is the strategy that you can use to define items allocations across the containers. This topic explains the difference between *Pack into all open containers* and *Pack into current container only* strategies.  

*Pack into all open containers* strategy indicates that system must check all open containers that have been already created upon the containerization cycle to make sure that item will fit in any of them. During the packing, the system checks for the single item whether it fits in any already created containers, in case of fail the system creates a new container and continue until completes the entire packaging of the order. For example, there are n items ordered for which the containerization must be performed. In the worst case when each item doesn't fit in any existing containers, the system will perform ((n-1) × (n+1)) / 2 checks in total to evaluate whether it fits into the existing containers. 

*Pack into current container only* strategy indicates that system must check the most recently created container upon the containerization cycle to make sure that item will fit into found container. During the packing, the system checks for the single item whether it fits in the most recently created container, in case of fail the system creates a new container and continue until completes the entire packaging of the order. For example, there are n items ordered for which the containerization must be performed. In the worst case the system will perform n-1 checks in total to evaluate whether it fits into the containers. 

## Example of the container packing strategy flow
You are setting up the items for the containerization with the following physical dimensions:
 
| Item | Physical dimensions (Width, Depth, Height)  | Weight  |
|---|---|---|
| HDMI Cable 6′ | 1 x 1 x 1 | 1 |
| HDMI Cable 12′ | 2 x 1 x 1 |1 |
| HDMI Cable 18′ | 3 x 1 x 1 |2 |

You are setting up the box that will be used for the packaging with the following physical dimensions:

| Container |Physical dimensions (Length, Width, Height) | Weight  | Volume|
|---|---|---|---|
| Medium Box | 6 x 3 x 2 | 10 | 100 |

You are setting up the order that contains the following products and quantities:

| Sales order line | Quantity  | 
|---|---|
| HDMI Cable 12′ | 9 |
| HDMI Cable 18′ | 8 |
| HDMI Cable 6′ | 13 |

The following table summarizes how containerization works when you use *Pack into all open containers* and when you use *Pack into current container only*.

| Pack into all open containers | Pack into current container |
|---|----|
| HDMI Cable 12′: <ul><li>Create a new container CONT0001.</li> <li>Place 9 ea into CONT0001 container</li></ul>|HDMI Cable 12′:<ul><li>Create a new container CONT0001.</li> <li>Place 9 ea into CONT0001 container.</li></ul>|
|HDMI Cable 18′: <ul><li> Check if item can fit CONT0001 container.</li><li>Create a new container CONT0002 container.</li> <li>Place 5 ea into CONT0002 container.</li><li>Create a new container CONT0003 container.</li> <li>Place 3 ea into CONT0003 container.</li></ul> |HDMI Cable 18′: <ul><li> Check if item can fit CONT0001 container.</li><li>Create a new container CONT0002 container.</li> <li>Place 5 ea into CONT0002 container.</li><li>Create a new container CONT0003 container.</li> <li>Place 3 ea into CONT0003 container.</li></ul>|
|HDMI Cable 6′: <ul><li> Check if item can fit CONT0001 container.</li><li>Place 1 ea into CONT0001 container.</li><li>Check if item can fit CONT0002 container.</li><li>Check if item can fit CONT0003 container.</li><li>Place 4 ea into CONT0003 container.</li><li>Create a new container CONT0004.</li><li>Place 8 ea into CONT0004 container.</li></ul> |HDMI Cable 6′:<ul><li> Check if item can fit CONT0003 container.</li><li>Place 4 ea into CONT0003 container.</li><li>Create a new container CONT0004.</li><li>Place 9 ea into CONT0004 container.</li></ul> |
# Single order containing multiple products is packed into a single container 
[!include [banner](../includes/banner.md)]
This topic presents a scenario where consolidation of multiple orders into one shipment is in place, but containerization must be performed via sales order so that single order containing multiple products is packed in a single container. 
This functionality lets you handle scenarios where you must pack only one sales order into one container so that it would be possible for the distribution center to cross dock full containers between retail stores. In addition to the retail scenarios (order per retail store, shipping to a distribution center for cross docking), it is also commonly used lean supply chains (sales order per Just-in-time production line…).
The following scenario illustrates how you could use the containerization with *Pack into current container only* strategy to decrease the number of containers to be evaluated during packing.
## Make demo data available
The scenario in this topic references values and records that are included in the standard demo data that is provided for Microsoft Dynamics 365 Supply Chain Management. If you want to use the values that are provided here as you do the exercises, be sure to work in an environment where the demo data is installed, and set the legal entity to **USMF** before you begin.
## Create container types
To set up a container type, follow these steps:
1. Go to **Warehouse management** \> **Setup** \> **Containers** \> **Container type**.
1. Select **New** to create container types with the following settings:
    - Container type 1:
        - **Container type code** - *Box-Large*
        - **Description** - *Large Box*
        - **Maximum net weight** - *100*
        - **Volume** - *400*
        - **Length** - *4*
        - **Width** - *10*
        - **Height** - *10*
    - Container type 2:
        - **Container type code** - *Box-Medium*
        - **Description** - *Medium Box*
        - **Maximum net weight** - *50*
        - **Volume** - *200*
        - **Length** - *2*
        - **Width** - *10*
        - **Height** - *10*
    - Container type 3:
        - **Container type code** - *Box-Small*
        - **Description** - *Small Box*
        - **Maximum net weight** - *20*
        - **Volume** - *100*
        - **Length** - *1*
        - **Width** - *10*
        - **Height** - *10*
    
## Create container groups
To set up a container group, follow these steps:
1. Go to **Warehouse management** \> **Setup** \> **Containers** \> **Container groups**.
1. Select **New** to create container groups with the following settings:
    - **Container group ID** - *Boxes*
    - **Description** - *Box sizes*
1. On the **Details** FastTab, select **New** and add container types:
    - **Line 1:** In the **Sequence number** field, enter *1*. In the **Container type** field, select *Box-Large*. In the **Container utilization percentage** field, enter *100*.
    - **Line 2:** In the **Sequence number** field, enter *2*. In the **Container type** field, select *Box-Medium*. In the **Container utilization percentage** field, enter *100*.
    - **Line 3:** In the **Sequence number** field, enter *3*. In the **Container type** field, select *Box-Small*. In the **Container utilization percentage** field, enter *100*.
## Create container build templates
To set up a container build template, follow these steps:
1. Go to **Warehouse management** \> **Setup** \> **Containers** \> **Container build template**.
1. Select **New** to create a new container build template with the following settings: 
- **Sequence number** - *1*
- **Container template ID** - *Box*
- **Container group ID** - *Boxes*
- **Base query types** - *Sales allocation line*
- **Wave step code** - *234*
- **Allow split picks** - *Yes*
- **Container packing strategy** - *Pack into current container only*
- **Pack by directive unit** - *No*
1. On the Action Pane, select **Edit query**.
1. On the **Sorting** tab, select **Add** to add a row that has the following settings:
- **Table:** *Temporary work transactions*
- **Derived table:** *Temporary work transactions*
- **Field:** *Order number*
- **Search direction:** *Ascending*
> [!IMPORTANT]
> In order to avoid cycling over all the other open containers and speed up the process by checking one container at a time, use the *Pack into current container only* option in addition to sorting by order number that will work like a work break on work template.  
1. Close the page.
1. On the Action Pane, select **Container mixing constraints** to place items from single order into single container. Items from another order should be placed into another container. 
1. Select **New** to create mixing constraints with the following settings:
- **Table name:** *Sales orders*
- **Field name:** *Sales order*(SalesId)
## Create wave templates for containerization
To set up a wave template, follow these steps:
1. Go to **Warehouse management \> Setup \> Waves \> Wave templates**.
1. In the left pane, set the **Wave template type** field to *Shipping*.
1. Select template **63 Shipping** in the list.
1. On the Action Pane, select **Edit**.
1. On the **Methods** FastTab, in the **Selected methods** column, find the following line:
    - **Method name:** *containerization*
    - **Name:** *Containerization*
1. Set the **Wave step code** field for this line to *234*.
## Set up a work template
To set up a work template, follow these steps:
1. Go to **Warehouse management \> Setup \> Work \> Work templates**.
1. In the **Work order type** field, select *Sales orders*.
1. In the **Overview** grid, find and select the work template that should be used with this function. For this scenario, select the *63 Pick to container* template.
1. On the Action Pane, select **Edit query**.
1. In the query editor dialog box, on the **Sorting** tab, select **Add**, and then set the following values for the new row:
    - **Line 1:** In the **Table** field, select *Temporary work transactions*. In the **Derived table** field, select *Temporary work transactions*.In the **Field** column, select *Shipment ID*. In the **Search direction** column, select *Ascending*.
    - **Line 2:** In the **Table** field, select *Temporary work transactions*. In the **Derived table** field, select *Temporary work transactions*.In the **Field** column, select *Order number*. In the **Search direction** column, select *Ascending*.
    - **Line 3:** In the **Table** field, select *Temporary work transactions*. In the **Derived table** field, select *Temporary work transactions*.In the **Field** column, select *Container ID*. In the **Search direction** column, select *Ascending*.
1. On the Action Pane, select **Work header breaks** to break the work so that each container within the order is linked to one work order.
1. Set **Group by this field** to *Yes* for *Shipment ID*, *Order number*, *Container ID*.
1. Select **OK** to close the dialog box and save your selection.
1. You receive the following message: "Grouping will be reset, continue?" Select **Yes** to continue.
## Set up shipment consolidation policies
To set up a shipment consolidation policy, follow these steps:
1. Go to **Warehouse management \> Setup \> Release to warehouse \> Shipment consolidation policies**.
1. Set the **Policy type** field to *Sales orders*.
1. Select *Default* policy name.
1. On the Action Pane, select **Edit**.
1. On the **Consolidation fields** FastTab, in the **Selected fields** list, select the row where the **Field name** field is set to *Order number*.
1. Select the **Add** button ![Right arrow](media/forward-button.png) to move the field to the **Remaining fields** list.
1. On the Action Pane, select **Save**.
## Set up physical dimension in the product
Set up physical dimension for a product by doing the following:
1. Go to **Product information management \> Products \> Released products**.
1. Select the product with **Item number** *A0001*.
1. On the Action Pane, open the **Manage inventory** tab and, from the **Warehouse** group, select **Physical dimensions**.
1. The **Physical dimensions** page opens. Find the line in the grid with the following settings:
    - **Unit** - *pcs*
    - **Gross weight** - *3*
    - **Width** - *2*
    - **Depth** - *2*
    - **Height** - *4*
    - **Volume** - *16*
1. Close the page.
1. Select the product with **Item number** *A0002*.
1. On the Action Pane, open the **Manage inventory** tab and, from the **Warehouse** group, select **Physical dimensions**.
1. The **Physical dimensions** page opens. Find the line in the grid with the following settings:
    - **Unit** - *pcs*
    - **Gross weight** - *4*
    - **Width** - *3*
    - **Depth** - *1*
    - **Height** - *3*
    - **Volume** - *9*
## Create sales order 1
1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. On the Action Pane, select **New** to open a dialog box for creating a new sales order.
1. In the dialog box, set the following values:
    - **Customer account:** *US-001*
    - **Warehouse:** *63*
1. Select **OK** to create the sales order and close the dialog box.
1. The new sales order is opened. It includes a new, empty line on the **Sales order lines** FastTab. On this line, set the following values:
    - **Line 1:** In the **Item number** field, select *A0001*. In the **Quantity** field, select *2*. 
    - **Line 2:** In the **Item number** field, select *A0002*. In the **Quantity** field, select *2*. 
1. On the **Sales order lines** FastTab, select **Inventory \> Reservation**.
1. On the **Reservation** page, select **Reserve lot**.
1. Repeat reservation for the second line.
1. Close the page.
## Create sales order 2
1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. On the Action Pane, select **New** to open a dialog box for creating a new sales order.
1. In the dialog box, set the following values:
    - **Customer account:** *US-001*
    - **Warehouse:** *63*
1. Select **OK** to create the sales order and close the dialog box.
1. The new sales order is opened. It includes a new, empty line on the **Sales order lines** FastTab. On this line, set the following values:
    - **Line 1:** In the **Item number** field, select *A0001*. In the **Quantity** field, select *4*. 
    - **Line 2:** In the **Item number** field, select *A0002*. In the **Quantity** field, select *4*. 
1. On the **Sales order lines** FastTab, select **Inventory \> Reservation**.
1. On the **Reservation** page, select **Reserve lot**.
1. Repeat reservation for the second line.
1. Close the page.
## Create load
Follow these steps to create a load for each order  that you created for this scenario and then release it to the warehouse.
1. Go to **Warehouse management \> Loads \> Load planning workbench**.
1. On the **Sales lines** tab, find and select all the sales order lines from the order sets that you created for this scenario.
1. On the Action Pane, on the **Supply and demand** tab, select **Add \> To new load** to add the selected order lines to a new Load.
1. In the **Load template assignment** dialog box, in the **Load template ID** field, select a load template, such as *Stnd Load Template*.
1. Select **OK** to close the dialog box. 
1. In the **Loads** section, find and select the load that you just created.
1. Select **Release \> Release to warehouse** to release the selected load to the warehouse.
## Verify the shipments and containers
The following procedure lets you verify the shipments that have been created. Use it to review order set that you created for this scenario to make sure that you've obtained the expected results.
1. Go to **Warehouse management \> Shipments \> All shipments**.
1. Find and select the required shipment.
1. On the Action Pane, open the **Transportation** tab and select **View containers**. Confirm that the items from sales orders were containerized into the two different containers.
