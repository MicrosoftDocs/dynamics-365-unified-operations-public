---
# required metadata

title: Confirm and transfer
description: This article explains how to use the Confirm and transfer feature, which lets users ship loads out of the warehouse before they complete all the work that is associated with those loads.
author: Mirzaab
ms.date: 07/01/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  WHSLoadTemplate,WHSWorkTemplateTable,WHSLoadPlanningWorkbench
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2020-07-01
ms.dyn365.ops.version: 10.0.8
---

# Confirm and transfer

[!include [banner](../includes/banner.md)]

The *Confirm and transfer* feature lets users ship loads out of the warehouse before they complete all the work that is associated with those loads. When a shipment is received that includes load lines that weren't fully picked, the confirming user is prompted either to split the remaining quantities onto a new load or to cancel the incomplete quantities.

Systems that are set up to allow load splitting support scenarios where planned and partially loaded loads must be adapted because of new or changing circumstances.

The client includes logic that enables a partially loaded load to be closed and confirmed as shipped. All remaining shipments and load lines (including full or partial line quantities) are then rolled over to a newly created load and shipment, if this rollover is required and the setup allows for it. New shipments and loads are automatically created based on the initial criteria for shipment and load creation, and their main attributes remain unchanged. There is also an option to automatically cancel remaining quantities if a work order hasn't yet been created and the user deems this cancellation necessary.

This functionality supports scenarios where the full load doesn't fit onto a single truck, or where some of the load should leave the warehouse before the rest of the load is ready for shipment. In these scenarios, the remaining products can be transferred to a new load and therefore to a new truck. Because this feature can be used with loads that are otherwise intended to require full-load shipment, it provides extra flexibility so that transport managers can solve nonstandard or unforeseen scenarios.

When a load is split, the *Confirm and transfer* feature performs the following actions:

- New loads and shipments are created as they are required. Each load or shipment will have most of the same attributes as the original load or shipment. The exception is the load status, which will be recalculated based on the work status.
- The user is informed that a new load has been created. The user is also notified about the ID of the new load.
- The load lines, work headers, and work lines that were split are updated with the new load and shipment information.
- If a whole shipment is being split, the shipment is maintained, and only the load references are updated. If the shipment must be split, a new shipment is created.

When remaining quantities are canceled, any load line quantities that haven't been picked and that don't have non-canceled work associated with them are removed from the load. If any work is in process, the user can only split the load. Remaining quantities can't be canceled.

You can split only loads that meet all the following criteria:

- One or more load lines have picked quantities.
- The load status is less than loaded.
- There is no load line data. (This data is created through license plate consolidation on the staging location, and the Confirm and transfer feature doesn't support license plate consolidation.)
- No inventory is currently awaiting packing at a packing location. (The *Confirm and transfer* feature doesn't support inventory that has been picked to the pack station but hasn't yet been packed unless containers that are packed are placed at staging locations with loading work created.)

> [!NOTE]
> This functionality differs from the transport load functionality, which should be used in warehouses that can never plan and create loads before picking, but that instead load the available transportation space after picking is completed.
>
> Use the *Confirm and transfer* feature in situations where loads are usually planned and created ahead of time, but where exceptions sometimes occur in which the load doesn't fit the available transport (such as a truck).

## Turn the confirm and transfer feature on or off

To use the functionality described in this article, the *Confirm and transfer* feature must be turned on for your system. As of Supply Chain Management 10.0.25, this feature is mandatory and can't be turned off. If you're running a version older than 10.0.25, then admins can turn this functionality on or off by searching for the *Confirm and transfer* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

## Set up confirm and transfer

To use the *Confirm and transfer* feature, you must turn it on in every relevant load template. In addition, depending on your requirements, you might want to prepare your work templates to support the feature. If you want to work through the example scenario that is provided later in this article, set up your system as described in this section. (That scenario is based on **USMF** demo data.)

### Prepare your load templates

1. Go to **Warehouse management \> Setup \> Load \> Load templates**.
1. On the Action Pane, select **Edit** to put the page into edit mode.
1. Select the **Allow load split during ship confirm** check box for each existing template where you want to turn on the feature. Alternatively, select **New** to create a new template, and configure it as you require. Every load that you create by using that template will inherit this functionality. (If you're working with the **USMF** demo data, turn on the feature for the **20' Container** load template.)

### Prepare your work templates

This setup isn't required in all situations. The example that is shown here ensures that work can be broken by shipment to support the example scenario that is provided later in this article. There are also other ways to achieve this result.

1. Go to **Warehouse management \> Setup \> Work \> Work templates**.
1. In the grid in the upper part of the page, select an existing work template where you want to set up the *Confirm and transfer* feature. (If you're working with the **USMF** demo data, select the **51 Pick to stage** work template.) Alternatively, create a new work template.
1. On the Action Pane, select **Edit query** to open the **Sales** dialog box.
1. In the **Sales** dialog box, on the **Sorting** tab, select **Add** to add a row to the grid.
1. In the new row, set the following values:

    - **Table:** *Temporary work transactions*
    - **Derived table:** *Temporary work transactions*
    - **Field:** *Shipment ID*
    - **Search direction:** *Ascending*

1. Select **OK** to save your settings and close the **Sales** dialog box.
1. If you receive a message that states that grouping will be reset, select **Yes** to continue.
1. In the grid in the upper part of the **Work templates** page, select the template that you just edited, and then, on the Action Pane, select **Work header breaks**.
1. On the Action Pane, select **Edit** to put the page into edit mode.
1. In the grid, set the following values:

    - **Table name:** *Temporary work transactions*
    - **Field name:** *Shipment ID*
    - **Group by this field:** Select this check box.

1. On the Action Pane, select **Save**.
1. Close the page.

## Scenario

This scenario shows an example where the picking process isn't yet completed, but the items that have been picked so far must be loaded onto a truck and shipped anyway. Therefore, the user can split the unpicked load lines onto a new load. All the data relationships will then automatically be updated.

> [!NOTE]
> The specific values that are described in this scenario are based on the **USMF** demo data. We recommend that you use this demo data while you're demonstrating or learning how to use the feature. If you aren't using the **USMF** demo data, substitute your own values as required.

### Step 1: Create a load that has multiple load lines

Before you can use this functionality, you must have a load that contains multiple load lines. You must also make sure that the pick locations have enough inventory for all the items on the sales orders that you will create. Review the setup of the location directive (**Warehouse management \> Setup \> Location directives**), and make a note of the picking locations that are used for sales order picking. If you must adjust the inventory, create manual movements, use replenishment, or use any other flow, as required.

To create a qualifying load, first create three sales orders by following these steps.

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. On the Action Pane, select **New** to open the **Create sales order** dialog box.
1. In the **Create sales order** dialog box, set the following values (at a minimum):

    - On the **Customer** FastTab, set the **Customer account** field to *US-004* (*Cave Wholesales*).
    - On the **General** FastTab, set the **Warehouse** field to *51*.

1. Select **OK** to create the sales order and close the **Create sales order** dialog box.
1. Your new sales order is opened. In the **Sales order lines** grid, add a line that has the following values:

    - **Item number:** *M9200*
    - **Quantity:** *40*
    - **Unit:** *ea*

1. On the **Inventory** menu above the grid, select **Reservation**.
1. On the Action Pane, select **Reserve lot** to open the **Reservation** page.
1. Reserve the inventory on the sales line, and then close the **Reservation** page.
1. Repeat steps 1 through 4 to add a second sales order for the same customer and warehouse.
1. Add two sales lines that have the following values. After you add each line, reserve inventory for it as described in steps 6 through 8.

    - **Line 1:** Set the **Item number** field to *M9200*, the **Quantity** field to *30*, and the **Unit** field to *ea*.
    - **Line 2:** Set the **Item number** field to *M9201*, the **Quantity** field to *20*, and the **Unit** field to *ea*.

1. Repeat steps 1 through 4 to add a third sales order for the same customer and warehouse.
1. Add two sales lines that have the following values. After you add each line, reserve inventory for it as described in steps 6 through 8.

    - **Line 1:** Set the **Item number** field to *M9201*, the **Quantity** field to *20*, and the **Unit** field to *ea*.
    - **Line 2:** Set the **Item number** field to *M9202*, the **Quantity** field to *60*, and the **Unit** field to *ea*.

#### Load planning workbench

The load planning workbench will use the load template ID to build the shipments and release the sales order lines to the warehouse.

1. Go to **Warehouse management \> Loads \> Load planning workbench**.
1. In the **Warehouse** field, select *51*.

    You will now build the load for the sales orders that you just created.

1. On the **Sales lines** tab, in the grid, select the sales lines for the new sales orders.
1. On the Action Pane, on the **Supply and demand** tab, in the **Add** group, select **To new load**.
1. In the **Load template assignment** dialog box, in the **Load template ID** field, select *20' Container*.
1. Select **OK**.
1. In the **Loads** section of the **Load planning workbench** page, in the grid, find the newly created load ID for warehouse *51*. Scroll right until you see the **Allow load split during ship confirm** column. The check box should be selected for your load.
1. Select the load.
1. On the **Release** menu above the grid, select **Release to warehouse** to create work.
1. In the **Release load to warehouse** dialog box, verify that the **Records to include** FastTab shows your load ID.
1. Select **OK**.

    You might receive a "Processing operation" message while the system creates the shipments and work.

1. In the **Loads** section of the **Load planning workbench** page, your load should now have a load status of *Waved*. Select the load, and then, on the **Related information** menu above the grid, select **Wave details** to view the shipment IDs that were created. When you've finished, close the **Waves** page.
1. In the **Loads** section of the **Load planning workbench** page, select the load, and then, on the **Related information** menu above the grid, select **Work details** to view the work that was created for the sales orders.
1. Make a note of the work IDs that were created. You might have to scroll right to see the sales order number and shipment ID that are associated with the work ID.

### Step 2: Set up the execution flow for mobile devices

Mobile device tasks will require user input of information, such as the work ID or license plate ID. In the fields, this information is typically provided for warehouse users in the form of bar codes that are found on documentation, packaging, or racking. To complete the mobile device steps for scenarios, make sure that you've identified the work IDs for the transactions, and the license plate IDs for the item and location in the transactions.

1. Sign in to the mobile device by using a user ID and password for warehouse *51*.
1. Select **Outbound**.
1. Select **Sales Picking**.
1. You have the option to enter the work ID or the license plate ID. Enter the work ID for the first sales order, and then select **Enter**.
1. In the **Loc** field, enter the location that is shown to confirm the picking location. Then select **Enter**.
1. In the **LP** field, enter the license plate ID. The license plate ID must be a match for the item, warehouse, and location of the item that is being picked from the selected location. When you've finished, select **Enter**.
1. In the **Item** field, enter the item number to confirm the item that is being picked, and then select **Enter**.
1. In the **Qty** field, enter the quantity of the item that is being picked, and then select **Enter**.
1. In the **Target LP** field, enter a target license plate ID. Target license plates are user-defined. Be sure to enter a license plate ID that you will remember. We recommend that you use the current date plus a two-digit sequence (YYMMDD\#\#) as the format, such as *19112301*. When you've finished, select **Enter**.
1. Review information that is shown. This information is the *Pick* information that will now become the *Put* data for the put transaction. When you've finished, select **Enter**.

    - You receive a **Work Completed** message.

1. Repeat steps 4 through 10 for the work ID of the second sales order.

The next step is to load the two picked license plates to the truck.

1. Sign in to the mobile device by using a user ID and password for warehouse *51*.
1. Select **Outbound**.
1. Select **Sales Loading**.
1. Enter the user-defined target license plate ID that you created for the first work ID in the previous procedure. Then select **Enter** to put the target license plate into the **STAGE** location.
1. Enter the target license plate ID again, and then select **Enter** to put the license plate into the **BAYDOOR** location.
1. Repeat steps 4 through 5 for the target license plate ID that you created for the second work ID.

The two work IDs will now be closed (loaded).

### Step 3: Confirm the outbound shipment

In this step, you will confirm the two sales orders and work that have been completed for the load to ship the picked items of the load and create a new load for the unpicked items. Outbound shipment confirmation must be done on the **Load details** page.

1. Go to **Warehouse management \> Loads \> Load planning workbench**.
1. In the **Loads** section, in the grid, select the row for the load ID that you created.
1. Select the load ID link to open the **Load details** page.
1. On the **Load details** page, on the Action Pane, on the **Ship and receive** tab, in the **Confirm** group, select **Outbound shipment** to initiate the confirmation.
1. In the **Ship confirm** dialog box, in the **Load split method during ship confirm** field, select *Split quantity to new load*.
1. Select **OK**.

    You might receive a "Processing operation" message.

    You receive informational messages that indicate that the shipment for your load has been confirmed, and that a new load has been created from the split quantity.

Refresh the **Load planning workbench** page to see the newly created load.

You can also confirm that transaction relations have been updated in the following ways:

- The remaining (unprocessed) shipment and shipment lines are updated with the new load ID.
- The sales order is linked to the new load ID.
- The original load doesn't include the remaining load lines.
- The remaining work has been updated with the new load ID.
- The wave remains the same.
- The status of the new load is correctly updated. (If the work status is _In process_, the load status should also be _In process_.)

## Notes and tips

- You can also turn on the **Allow load split during ship confirm** parameter after the load has been created with the **Load template** parameter turned off but before the loading process has started. Go to the desired load, and then, in the header view, turn on the parameter.
- The **Split quantity to new load** option also works when some of the remaining work headers have a status of *In process*. Therefore, you can still use the functionality even if workers are already running the pick orders.
- If you select **Cancel unfulfilled quantity** while there is remaining work that has a status of *Open* or *In progress*, you receive the following error message: "Unable to cancel remaining qty for load. Work exists for load."
- If you select **Cancel unfulfilled quantity** when there is no remaining work but there are unreleased load lines on the load, you receive the following error message: "The shipment for load could not be confirmed because the quantity for item exceeds the percentage that is defined for under delivery." To avoid the error, you can set the **Under delivery** percentage on the unreleased load line to 100 percent. Unreleased lines won't be moved to a new load, but the current load will be confirmed with under-delivery. In this case, you won't be able to re-release the original order. Therefore, so you will have to handle it in some other way.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]