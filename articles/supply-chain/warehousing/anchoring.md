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
ms.author: v-gfedorova
ms.search.validFrom: 2021-07-29
ms.dyn365.ops.version: 10.0.21
---

# Anchoring

[!include [banner](../includes/banner.md)]

This topic provides details about the anchoring process. It describes the configuration that is required and the logic that is executed when a warehouse worker changes either the staging or loading location.

The anchoring feature lets you override the staging or loading location so that all open puts will be directed to the new staging or loading location.

This feature can help workers be more efficient while shipping goods. Here are some examples:

- A worker who must put items for order 1 in a staging location by dock 1 isn't able to do so because a previous load hasn't cleared the location. Instead of waiting for the dock 1 staging location to become available, the worker can decide to use the staging location for dock 2. In this case, the worker overrides the suggested staging location. The put location for all remaining items for the work is then updated to the dock 2 staging location.

- A worker who must perform multiple picks for the same delivery can be sure that all put items are assembled to the same place so it takes less time to load them into the truck.

Anchoring is configured for mobile device menu items using the **Anchor** field. If **Anchor** is set to *Yes*, then you can choose to anchor by shipment or by load. If **Anchor by** is set to *Shipment*, then the subsequent open puts will be changed to the new location for that shipment. If **Anchor by** is set to *Load*, then the subsequent open puts will be changed to the new location for that load.

> [!IMPORTANT]
> The location for the subsequent open puts will be changed only on the work lines generated from the same work template line. In other words, the system will anchor the put lines that originate from the same work template line.

This topic provides a scenario to illustrate how anchoring works. During the scenario, you will create a set of sales orders and release them to the warehouse. You will then override the suggested staging location and review that all the remaining put-away work is directed to the new location.

## Scenario prerequisite: Make demo data available

The scenario in this topic references values and records that are included in the standard demo data that is provided for Microsoft Dynamics 365 Supply Chain Management. If you want to use the values that are provided here as you do the exercises, be sure to work in an environment where the demo data is installed, and set the legal entity to *USMF* before you begin.

## Scenario setup

Before you work through the example scenario, you must enable anchoring for the relevant mobile device menu item.

### Set up a mobile device menu item to allow anchoring

Use the following procedure to enable anchoring for a mobile device menu item.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. In the list pane, select the record that is named *Sales Picking*. If no existing record has this name, create it. Confirm or set the following values for the record: 

    - **Menu item name:** *Sales Picking*
    - **Title:** *Sales Picking*
    - **Mode:** *Work*
    - **Use existing work:** *Yes*
    - **Directed by:** *User directed*
    - **Anchoring:** *Yes*
      By setting this parameter, the system will anchor multiple work order lines together during sales picking.
    - **Anchor by:** *Load*
      By setting this parameter, the system will anchor by load.
    - **Override target license plate:** *Yes*
    - **Override license plate during put:** *Yes*
    - **Keep work locked by user:** *Yes*
    - **Allow over pick:** *Yes*

### Set up a work template to allow staging

Use the following procedure to configure a work template to enable staging. This configuration will show the scenario when a worker put items for the order in a staging location. 

1. Go to **Warehouse management \> Setup \> Work \> Work templates**.
1. In the **Work order type** field, select *Sales orders*.
1. In the grid, select the **61 SO Stage** work template.
1. In the **Work Template Details** section, make sure that the following lines exist and are configured as shown: 

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

1. On the **Range** tab, make sure that the following line is configured:
    - **Table:** *Temporary work transactions*
    - **Derived Table:** *Temporary work transactions*
    - **Field:** *Warehouse*
    - **Criteria:** *61*

1. On the **Sorting** tab, make sure that the following line is configured:
    - **Table:** *Temporary work transactions*
    - **Derived Table:** *Temporary work transactions*
    - **Field:** *Shipment ID*
    - **Search direction:** *Ascending*

1. Select **OK** to apply your settings and close the query editor. Accept the changes if prompted.
1. On the Action Pane, select **Work header breaks**.
1. On the line where the **Field name** field is set to *Shipment ID*, make sure that the **Group by this field** check box is marked.

### Create demand

Before you can try the anchoring functionality, you must create some demand. For this scenario, you will create three sales orders for the same customer.

Before you create sales orders and shipments, make sure that the pick locations have enough inventory for all the items in the orders. Review the location directive settings to confirm the picking locations that are used for sales order picking. If you must adjust the inventory, you can create manual movements, use replenishment, or use any other flow.

For this scenario the following inventory is available: 
   - *A0001* for *100* ea in the location *06A01R2S1B*
   - *A0002* for *100* ea in the location *06A01R3S1B*

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. Select **New** to create a sales order for order 1.
1. In the **Create sales order** dialog, set the following values:

    - **Customer:** *US-001*
    - **Warehouse:** *61*

1. Select **OK**.
1. A new line is added to the **Sales order lines** FastTab. Set the following values for it:

    - **Item number:** *A0001*
    - **Quantity:** *1*

1. Select **Add line** from the toolbar to add a second line, and set the following values:

    - **Item number:** *A0002*
    - **Quantity:** *1*

1. Repeat the following steps for each sales line on the order to reserve inventory for it:

    1. On the **Sales order lines** FastTab, on the **Inventory** menu, select **Reservation**.
    1. On the **Reservation** page, select **Reserve lot**, and then close the page.
    1. Select **Save**.

1. Select **New** to create a sales order for order 2.
1. In the **Create sales order** dialog, set the following values:

    - **Customer:** *US-001*
    - **Warehouse:** *61*

1. Select **OK**.
1. A new line is added to the **Sales order lines** FastTab. Set the following values:

    - **Item number:** *A0001*
    - **Quantity:** *2*

1. Select **Add line** to add a second line, and set the following values:

    - **Item number:** *A0002*
    - **Quantity:** *2*

1. Repeat the following steps for each sales line on the order to reserve inventory for it:

    1. On the **Sales order lines** FastTab, on the **Inventory** menu, select **Reservation**.
    1. On the **Reservation** page, select **Reserve lot**, and then close the page.
    1. Select **Save**.

1. Select **New** to create a sales order for order 3.
1. In the **Create sales order** dialog, set the following values:

    - **Customer:** *US-001*
    - **Warehouse:** *61*

1. Select **OK**.
1. A new line is added to the **Sales order lines** FastTab. Set the following values:

    - **Item number:** *A0001*
    - **Quantity:** *3*

1. Select **Add line** to add a second line, and set the following values:

    - **Item number:** *A0002*
    - **Quantity:** *3*

1. Repeat the following steps for each sales line on the order to reserve inventory for it:

    1. On the **Sales order lines** FastTab, on the **Inventory** menu, select **Reservation**.
    1. On the **Reservation** page, select **Reserve lot**, and then close the page.
    1. Select **Save**.

## Use the load planning workbench to create a load and release it to the warehouse

Follow these steps to create a load for the orders that you created for this scenario and then release it to the warehouse.

1. Go to **Warehouse management \> Loads \> Load planning workbench**.
1. On the **Sales lines** tab, find and select all the sales order lines for sales order 1 and sales order 2.
1. On the Action Pane, on the **Supply and demand** tab, from the **Add** group, select **To new load**.
1. In the **Load template assignment** dialog, in the **Load template ID** field, select a load template, such as *Stnd Load Template*. 
1. Select **OK** to close the dialog.
1. In the **Loads** section, find and select the load that you created.
1. On the toolbar, select **Release \> Release to warehouse**.
1. In the **Release load to warehouse** dialog, select **OK** to release the selected load to the warehouse.
1. Go to **Warehouse management \> Work \> All work** to view the work that was created. Make a note of the **Work ID** value, because you will need it in the next procedure. <!-- KFM: For me, no work was ever created. Are we missing a step? Also, might we select the load and then use the **Related information > Work** toolbar button instead of opening **All work**? -->

Two work IDs were created for each shipment to bring inventory from the picking locations to the staging location and from the staging location to the baydoor.

### Sales order picking to the staging location for the first shipment
<!-- KFM: I could not continue because I have no work. Stopped review here. -->
1. Sign in to the Warehouse Management mobile app as a worker in warehouse *61*.
1. On the main menu, select **Outbound**.
1. On the **Outbound** menu, select **Sales Picking**.
1. Select the **ID** field, and then enter the work ID for the first shipment.
1. Confirm your entry.
1. In the **LP** field, enter a license plate number for the first item.
1. Confirm your entry.
1. In the **Target LP** field, enter a license plate number.
   You will pick all lines that were created from the processed wave onto the same target license plate.
1. Confirm your entry.
1. In the **LP** field, enter a license plate number for the second item.
1. Confirm your entry.
1. The last step is to complete the put work.
1. Select **Override Loc** to override suggested staging location.
1. In the **Work exceptions** field, set *Staging lane changed*.
1. In the **Location** field, enter a new staging location *STAGE03* (or any other stage location available that is different from the stage location initially suggested by the system).
1. Confirm your entry.
    You receive a "Work completed" message.
1. Go to **Warehouse management \> Work \> All work**.
1. Select Work ID for the first shipment. Verify that the staging location was updated by the location defined in the mobile device.
1. Select Work ID for the second shipment. Verify that the staging location was updated to new staging location due to the anchoring setup.

> [!IMPORTANT]
> Location for all the remaining open put work lines that have the same staging location and generated from the same work template line will be updated to the new location.

## Use the load planning workbench to add new sales order to the existing load

Follow these steps to add an order to the load and then release it to the warehouse.

1. Go to **Warehouse management \> Loads \> Load planning workbench**.
1. On the **Sales lines** tab, find and select all the sales order lines for sales order 3.
1. On the Action Pane, on the **Supply and demand** tab, from the **Add** group, select **To existing load** to add the selected order lines to an existing Load.
1. Select **OK** to close the dialog.
1. In the **Loads** section, find and select the load from the previous steps.
1. Select **Release \> Release to warehouse** to release the selected load to the warehouse.
1. Go to **Warehouse management \> Work \> All work** to view the work that was created. Make a note of the **Work ID** value, because you will need it in the next procedure.

### Sales order picking to the staging location for the third shipment

1. Sign in to the mobile app as a worker in warehouse *61*.
1. On the main menu, select **Outbound**.
1. On the **Outbound** menu, select **Sales Picking**.
1. Select the **ID** field, and then enter the work ID for the third shipment.
1. Confirm your entry.
1. In the **LP** field, enter a license plate number for the first item.
1. Confirm your entry.
1. In the **Target LP** field, enter a license plate number.
1. Confirm your entry.
1. In the **LP** field, enter a license plate number for the second item.
1. Confirm your entry.
1. The last step is to complete the put work.
1. Select **Override Loc** to override suggested staging location.
1. In the **Work exceptions** field, set *Staging lane changed*.
1. In the **Location** field, enter a new staging location *STAGE04* (or any other stage location available that is different from the stage location initially suggested by the system).
1. Confirm your entry.
    You receive a "Work completed" message.
1. Go to **Warehouse management \> Work \> All work**.
1. Select Work ID for the first shipment. Verify that staging location was not updated to new staging location because the remaining open put line does not correspond to the work template line of the completed put line.
1. Select Work ID for the second shipment. Verify that staging location was not updated to new staging location because the staging location does not correspond to the staging location of the completed put line. In other words, completed put work line and the remaining open work line have different staging locations and in this case, only lines that have the same staging locations are updated.
1. Select Work ID for the third shipment. Verify that staging location was updated to the new staging location.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]