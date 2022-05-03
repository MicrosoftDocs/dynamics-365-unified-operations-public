---
title: Anchoring
description: This topic explains how to enable and use anchoring.
author: GalynaFedorova
ms.date: 07/29/2021
ms.topic: article
ms.search.form: WHSRFMenuItem
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: gfedorova
ms.search.validFrom: 2021-07-29
ms.dyn365.ops.version: 10.0.21
---

# Anchoring

[!include [banner](../includes/banner.md)]

This topic provides details about the anchoring process. It describes the configuration that is required and the logic that is run when a warehouse worker changes either the staging location or the loading location.

The anchoring feature lets you override the staging or loading location. All open puts will then be directed to the new staging or loading location that you specify.

This feature can help workers be more efficient while they ship goods. Here are some examples:

- A worker who must put items for order 1 in a staging location by dock 1 can't complete this operation because a previous load hasn't cleared the location. Instead of waiting for the dock 1 staging location to become available, the worker decides to use the staging location for dock 2. Therefore, the worker overrides the suggested staging location. The put location for all remaining items for the work is then updated to the dock 2 staging location.
- A worker who must perform multiple picks for the same delivery can be sure that all put items are assembled in the same place. Therefore, less time is required to load the items into the truck.

You configure anchoring for mobile device menu items by using the **Anchor** option. If you set this option to *Yes*, you can use the **Anchor by** field to specify whether you want to anchor by shipment or load. If you set the **Anchor by** field to *Shipment*, subsequent open puts will be changed to the new location for that shipment. If you set it to *Load*, subsequent open puts will be changed to the new location for that load.

> [!IMPORTANT]
> The location for subsequent open puts will be changed only on the work lines that are generated from the same work template line. In other words, the system will anchor the put lines that originate from the same work template line.

This topic provides a scenario that shows how anchoring works. During the scenario, you will create a set of sales orders and release them to the warehouse. You will then override the suggested staging location and verify that all the remaining put-away work is directed to the new location.

## Scenario prerequisite: Make demo data available

The scenario in this topic references values and records that are included in the standard demo data that is provided for Microsoft Dynamics 365 Supply Chain Management. If you want to use the values that are provided here as you do the exercises, be sure to work in an environment where the demo data is installed, and set the legal entity to *USMF* before you begin.

## Scenario setup

Before you work through the example scenario, you must enable anchoring for the relevant mobile device menu item.

### Set up a mobile device menu item to enable anchoring

Follow these steps to enable anchoring for a mobile device menu item.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. In the list pane, select the record that is named *Sales Picking*. If no existing record has this name, create it. Confirm or set the following values for the record:

    - **Menu item name:** *Sales Picking*
    - **Title:** *Sales Picking*
    - **Mode:** *Work*
    - **Use existing work:** *Yes*
    - **Directed by:** *User directed*
    - **Anchoring:** *Yes*

        This setting causes the system to anchor multiple work order lines together during sales picking.

    - **Anchor by:** *Load*

        This setting causes the system to anchor by load.

    - **Override target license plate:** *Yes*
    - **Override license plate during put:** *Yes*
    - **Keep work locked by user:** *Yes*
    - **Allow over pick:** *Yes*

### Set up a work template to enable staging

Follow these steps to configure a work template to enable staging. This configuration will support the scenario where a worker puts items for an order in a staging location.

1. Go to **Warehouse management \> Setup \> Work \> Work templates**.
1. In the **Work order type** field, select *Sales orders*.
1. In the grid, select the **61 SO Stage** work template.
1. In the **Work Template Details** section, make sure that the following lines exist and are configured as shown here:

    - Line 1:

        - **Work type:** *Pick*
        - **Mandatory:** Selected (= *Yes*)
        - **Work class ID:** *SO Pick*

    - Line 2:

        - **Work type:** *Put*
        - **Mandatory:** Selected (= *Yes*)
        - **Directive code:** *Stage*
        - **Work class ID:** *SO Pick*

    - Line 3:

        - **Work type:** *Pick*
        - **Mandatory:** Selected (= *Yes*)
        - **Stop work:** *Yes*
        - **Work class ID:** *SO Load*

    - Line 4:

        - **Work type:** *Put*
        - **Mandatory:** Selected (= *Yes*)
        - **Directive code:** *Baydoor*
        - **Work class ID:** *SO Load*

1. On the Action Pane, select **Edit query** to open the query editor.
1. On the **Range** tab, make sure that the following line is present:

    - **Table:** *Temporary work transactions*
    - **Derived Table:** *Temporary work transactions*
    - **Field:** *Warehouse*
    - **Criteria:** *61*

1. On the **Sorting** tab, make sure that the following line is present:

    - **Table:** *Temporary work transactions*
    - **Derived Table:** *Temporary work transactions*
    - **Field:** *Shipment ID*
    - **Search direction:** *Ascending*

1. Select **OK** to apply your settings and close the query editor. Accept the changes if you're prompted.
1. On the Action Pane, select **Work header breaks**.
1. On the line where the **Field name** field is set to *Shipment ID*, make sure that the **Group by this field** checkbox is selected.

### Set up license plates, locations, and inventory

Before you create sales orders and shipments, you must ensure that the required locations, license plates, and inventory exist.

1. Go to **Warehouse management \> Setup \> Warehouse \> License plates**, and create two license plates:

    - MyLP1
    - MyLP2

1. Go to **Warehouse management \> Setup \> Warehouse \> Locations**, and create the following locations if they aren't already present.

    | Warehouse | Location   | Location profile ID | Zone ID   |
    |-----------|------------|---------------------|-----------|
    | 61        | 06A01R2S1B | PICK-06             | FLOOR     |
    | 61        | 06A01R3S1B | PICK-06             | FLOOR     |
    | 61        | STAGE01    | STAGE               | *(Blank)* |
    | 61        | STAGE02    | STAGE               | *(Blank)* |
    | 61        | STAGE03    | STAGE               | *(Blank)* |
    | 61        | STAGE04    | STAGE               | *(Blank)* |

1. Make sure that the following inventory is available. If you must adjust the inventory, you can create manual movements, use replenishment, or use any other flow.

    | Item number | Quantity | Warehouse | Location   | License plate |
    |-------------|----------|-----------|------------|---------------|
    | A0001       | 100      | 61        | 06A01R2S1B | MyLP1         |
    | A0002       | 100      | 61        | 06A01R3S1B | MyLP2         |

### Create demand

Before you can try the anchoring functionality, you must create some demand. For this scenario, you will create three sales orders for the same customer.

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. Select **New** to create the first sales order.
1. In the **Create sales order** dialog box, set the following values:

    - **Customer account:** *US-001*
    - **Warehouse:** *61*

1. Select **OK**.
1. The new sales order is opened. It includes a blank line on the **Sales order lines** FastTab. Set the following values for this line:

    - **Item number:** *A0001*
    - **Quantity:** *1*

1. On the toolbar, select **Add line** to add a second sales order line, and set the following values for it:

    - **Item number:** *A0002*
    - **Quantity:** *1*

1. Follow these steps for each sales line on the order to reserve inventory for it:

    1. On the **Sales order lines** FastTab, select a sales order line.
    1. On the toolbar, select **Inventory \> Reservation**.
    1. On the **Reservation** page, select **Reserve lot**, and then close the page.
    1. On the Action Pane, select **Save**.

1. Repeat steps 2 through 6 to create a second sales order. Set the following values for it:

    - In the **Create sales order** dialog box:

        - **Customer account:** *US-001*
        - **Warehouse:** *61*

    - On sales order line 1:

        - **Item number:** *A0001*
        - **Quantity:** *2*

    - On sales order line 2:

        - **Item number:** *A0002*
        - **Quantity:** *2*

1. Repeat step 7 to reserve each line on sales order 2.
1. Repeat steps 2 through 6 to create a third sales order. Set the following values for it:

    - In the **Create sales order** dialog box:

        - **Customer account:** *US-001*
        - **Warehouse:** *61*

    - On sales order line 1:

        - **Item number:** *A0001*
        - **Quantity:** *3*

    - On sales order line 2:

        - **Item number:** *A0002*
        - **Quantity:** *3*

1. Repeat step 7 to reserve each line on sales order 3.

### Use the load planning workbench to create a load and release it to the warehouse

Follow these steps to create a load for the orders that you created for this scenario and then release it to the warehouse.

1. Go to **Warehouse management \> Loads \> Load planning workbench**.
1. On the **Sales lines** tab, find and select all the sales order lines for sales order 1 and sales order 2.
1. On the Action Pane, on the **Supply and demand** tab, in the **Add** group, select **To new load**.
1. In the **Load template assignment** dialog box, in the **Load template ID** field, select a load template, such as *Stnd Load Template*.
1. Select **OK** to close the dialog box.
1. In the **Loads** section, find and select the load that you created.
1. On the toolbar, select **Release \> Release to warehouse**.
1. In the **Release load to warehouse** dialog box, select **OK** to release the selected load to the warehouse.
1. Go to **Warehouse management \> Work \> All work** to view the work that was created. You should find two new work IDs, one for each shipment. Each work ID has pick and put lines that bring inventory from the picking locations to the staging location and from the staging location to the baydoor. Make a note of the **Work ID** value for the first shipment, because you will need it in the next procedure.

### Sales order picking to the staging location for the first shipment

1. Sign in to the Warehouse Management mobile app as a worker in warehouse *61*. (In the standard demo data, you can sign in by using _61_ as the user ID and _1_ as the password.)
1. On the main menu, select **Outbound**.
1. On the **Outbound** menu, select **Sales Picking**.
1. Select the **ID** field, and then enter the work ID for the first shipment.
1. Confirm your entry.
1. In the **LP** field, enter a license plate number for the first item (*MyLP1*).
1. Confirm your entry.
1. In the **Target LP** field, enter any number (the targe license plate doesn't have to exist already).

    You will pick all lines that were created from the processed wave to the same target license plate.

1. Confirm your entry.
1. In the **LP** field, enter a license plate number for the second item (*MyLP2*).
1. Confirm your entry.

    Imagine that the worker has now collected the order, but when they get to the staging location that specified in the work, they find that the space is already occupied. However, the worker can see that another nearby location (*STAGE03*) is available. Therefore, they will request to change the staging location. Because the anchoring feature is enabled, the system will then automatically update the staging location for this and all related work.

1. Select **Override Loc** to override the suggested staging location.
1. In the **Work exceptions** field, specify *Staging lane changed*.
1. In the **Location** field, enter a new staging location (*STAGE03*).
1. Confirm your entry. You receive a "Work completed" message.
1. Go to **Warehouse management \> Work \> All work**.
1. Open the work ID for the first shipment. Verify that the staging location was updated to the new location (*STAGE03*) that was defined by using the mobile device.
1. Open the work ID for the second shipment. Verify that the staging location was updated to new staging location (*STAGE03*) because of the anchoring setup.

> [!NOTE]
> The location for all the remaining open put work lines that have the same staging location and that were generated from the same work template line will be updated to the new location.

### Use the load planning workbench to add the new sales order to the existing load

Follow these steps to add an order to the load and then release it to the warehouse.

1. Go to **Warehouse management \> Loads \> Load planning workbench**.
1. On the **Sales lines** tab, find and select all the sales order lines for sales order 3.
1. On the Action Pane, on the **Supply and demand** tab, in the **Add** group, select **To existing load** to add the selected order lines to an existing load.
1. Select **OK** to close the dialog box.
1. In the **Loads** section, find and select the load from the previous steps.
1. Select **Release \> Release to warehouse**.
1. In the **Release load to warehouse** dialog box, select **OK** to release the selected load to the warehouse.
1. Go to **Warehouse management \> Work \> All work** to view the work that was created. Make a note of the **Work ID** value, because you will need it in the next procedure.

### Sales order picking to the staging location for the third shipment

1. Sign in to the mobile app as a worker in warehouse *61*.
1. On the main menu, select **Outbound**.
1. On the **Outbound** menu, select **Sales Picking**.
1. Select the **ID** field, and then enter the work ID for the third shipment.
1. Confirm your entry.
1. In the **LP** field, enter a license plate number for the first item (*MyLP1*).
1. Confirm your entry.
1. In the **Target LP** field, enter any number (the targe license plate doesn't have to exist already).
1. Confirm your entry.
1. In the **LP** field, enter a license plate number for the second item (*MyLP2*).
1. Confirm your entry.

    As for the first load, imagine that the worker finds that the specified staging location isn't available. Therefore, they want to use a different staging location (*STAGE04*).

1. Select **Override Loc** to override the suggested staging location.
1. In the **Work exceptions** field, specify *Staging lane changed*.
1. In the **Location** field, enter a new staging location (*STAGE04*).
1. Confirm your entry. You receive a "Work completed" message.
1. Go to **Warehouse management \> Work \> All work**.
1. Open the work ID for the first shipment. Verify that the staging location wasn't updated to the new staging location (*STAGE04*) because the remaining open put line doesn't correspond to the work template line of the completed put line.
1. Open the work ID for the second shipment. Verify that the staging location wasn't updated to the new staging location (*STAGE04*) because the staging location doesn't correspond to the staging location of the completed put line. In other words, the completed put work line and the remaining open work line have different staging locations and, in this case, only lines that have the same staging locations are updated.
1. Open the work ID for the third shipment. Verify that the staging location was updated to the new staging location (*STAGE04*).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
