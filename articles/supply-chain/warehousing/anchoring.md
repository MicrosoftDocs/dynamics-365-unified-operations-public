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

This topic provides details about the anchoring process. It describes the configuration that is required and the logic that is executed when warehouse worker changes either the staging or loading location.

The Anchor feature lets you override the staging or loading location so that all open puts will be directed to the new staging or loading location. 

This feature can help workers be more efficient while shipping the goods. Here are some examples:

- A worker who must put items for order 1 in a staging location by Dock 1 can’t, because a previous load hasn’t cleared the location. Instead of waiting for the Dock 1 staging location to become available, the worker can decide to use the staging location for Dock 2. In this case, the worker overrides the suggested staging location. The put location for all remaining items for the work order is then updated to the Dock 2 staging location. 

- A worker who must perform multiple picks for the same delivery can be sure that all put items are assembled to the same place so it takes less time to load them into the truck. 

Anchoring is configured on the mobile device menu items by defining the **Anchor** field. If the Anchor field is selected, then you can anchor by shipment or by load. If anchoring is by shipment, then the subsequent open puts will be changed to the new location for that shipment. If anchoring is by load, then the subsequent open puts will be changed to the new location for that load.

> [!IMPORTANT]
> Location on the subsequent open puts will be changed only on the work lines generated from the same work template line that allows better support multi-stage works. In other words, the system will anchor the put lines that originate from the same work template line.

During the scenario, you will create set of sales orders and release to the warehouse. You will then override the suggested staging location and review that all the remaining put-away works are directed to the new location.

## Scenario prerequisite: Make demo data available

The scenario in this topic references values and records that are included in the standard demo data that is provided for Microsoft Dynamics 365 Supply Chain Management. If you want to use the values that are provided here as you do the exercises, be sure to work in an environment where the demo data is installed, and set the legal entity to *USMF* before you begin.

## Scenario setup

Before you work through the example scenario, you must enable anchoring for the relevant mobile device menu item.

### Set up a mobile device menu item to allow anchoring

Here is the general procedure for configuring a mobile device menu item to enable anchoring. 

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. In the list pane, select the record that is named *Sales Picking*. If no existing record has this name, create it. Confirm or set the following values for the record:

    - **Menu item name:** *Sales Picking*
    - **Title:** *Sales Picking*
    - **Mode:** *Work*
    - **Use existing work:** *Yes*
    - **Directed by:** *User directed*
    - **Override license plate during put:** *Yes*
    - **Override target license plate:** *Yes*
    - **Keep work locked by user:** *Yes*
    - **Allow over pick:** *Yes*
    - **Anchoring:** *Yes*
    - **Anchor by:** *Load*

### Set up a work template to allow staging

Here is the general procedure for configuring a work template to enable staging.

1. Go to **Warehouse management \> Work \> Work templates**.
1. In the **Work order type** field, select *Sales orders*.
1. In the grid, select the **61 SO Stage** work template.
1. In the **Work Template Details** section, make sure that the following lines are configured:

   - Line 1:
   
     - **Work type:** *Pick*
     - **Mandatory:** Selected (= *Yes*)
     - **Work class ID:** *SO Pick*

   - Line 2:
   
     - **Work type:** *Put*
     - **Mandatory:** Selected (= *Yes*)
     - **Work class ID:** *SO Pick*
     - **Directive code:** *Stage*

   - Line 3:

     - **Work type:** *Pick*
     - **Mandatory:** Selected (= *Yes*)
     - **Work class ID:** *SO Load*
     - **Stop work:** *Yes*

   - Line 4:

     - **Work type:** *Put*
     - **Mandatory:** Selected (= *Yes*)
     - **Work class ID:** *SO Load*
     - **Directive code:** *Baydoor*

1. Select **Edit query** to open the query editor.

1. On the **Range** tab, make sure that the following line is configured:

    - Line 1:

        - **Table:** *Temporary work transactions*
        - **Derived Table:** *Temporary work transactions*
        - **Field:** *Warehouse*
        - **Criteria:** *61*

1. On the **Sorting** tab, make sure that the following line is configured:

    - Line 1:

        - **Table:** *Temporary work transactions*
        - **Derived Table:** *Temporary work transactions*
        - **Field:** *Shipment ID*
        - **Search direction:** *Ascending*

1. Close the query editor.
1. On the Action Pane, select **Work header breaks**.
1. On the line where the **Field name** field is set to *Shipment ID*, make sure that the **Group by this field** check box is marked.

### Create demand

Before the functionality can be demonstrated, you must create some demand. For this scenario, you will create three sales orders for the same customer.

Before you create sales orders and shipments, make sure that the pick locations have enough inventory for all the items on the orders. Review the location directive settings to confirm the picking locations that are used for sales order picking. If you must adjust the inventory, you can create manual movements, use replenishment, or use any other flow. Then reserve the inventory.

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. Select **New** to create a sales order for order 1.
1. In the **Create sales order** dialog box, set the following values:

    - **Customer:** *US-001*
    - **Warehouse:** *61*

1. Select **OK**.
1. A new line is added to the **Sales order lines** FastTab. Set the following values:

    - **Item number:** *A0001*
    - **Quantity:** *1*

1. Select **Add line** to add a second line, and set the following values:

    - **Item number:** *A0002*
    - **Quantity:** *1*

1. Repeat the following steps for each sales line on the order to reserve inventory for it:

    1. On the **Sales order lines** FastTab, on the **Inventory** menu, select **Reservation**.
    1. On the **Reservation** page, select **Reserve lot**, and then close the page.
    1. Select **Save**.

1. Select **New** to create a sales order for order 2.
1. In the **Create sales order** dialog box, set the following values:

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
1. In the **Create sales order** dialog box, set the following values:

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

## Use the load planning workbench to create load and release load to the warehouse

Follow these steps to create a load for orders that you created for this scenario and then release it to the warehouse.

1. Go to **Warehouse management \> Loads \> Load planning workbench**.
1. On the **Sales lines** tab, find and select all the sales order lines for sales order 1 and sales order 2.
1. On the Action Pane, on the **Supply and demand** tab, select **Add \> To new load** to add the selected order lines to a new Load.
1. In the **Load template assignment** dialog box, in the **Load template ID** field, select a load template, such as *Stnd Load Template*.
1. Select **OK** to close the dialog box. 
1. In the **Loads** section, find and select the load that you created.
1. Select **Release \> Release to warehouse** to release the selected load to the warehouse.
1. Go to **Warehouse management \> Work \> All work** to view the works that were created. Make a note of the **Work ID** value, because you will need it in the next procedure.
   
   Two work IDs have been created for each shipment to bring inventory from the picking locations to the staging location and from the staging location to the baydoor.

### Sales order picking to the staging location

1. Sign in to the mobile app as a worker in warehouse *61*.
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
1. In the **Location** field, enter a new staging location *STAGE03*.
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
1. On the Action Pane, on the **Supply and demand** tab, select **Add \> To existing load** to add the selected order lines to an existing Load.
1. Select **OK** to close the dialog box. 
1. In the **Loads** section, find and select the load from the previous steps.
1. Select **Release \> Release to warehouse** to release the selected load to the warehouse.
1. Go to **Warehouse management \> Work \> All work** to view the work that was created. Make a note of the **Work ID** value, because you will need it in the next procedure.

### Sales order picking to the staging location

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
1. In the **Location** field, enter a new staging location *STAGE04*.
1. Confirm your entry. 
    You receive a "Work completed" message.
1. Go to **Warehouse management \> Work \> All work**.
1. Select Work ID for the first shipment. Verify that staging location was not updated to new staging location because the remaining open put line does not correspond to the work template line of the completed put line.
1. Select Work ID for the second shipment. Verify that staging location was not updated to new staging location because the staging location does not correspond to the staging location of the completed put line.
1. Select Work ID for the third shipment. Verify that staging location was updated to the new staging location.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]