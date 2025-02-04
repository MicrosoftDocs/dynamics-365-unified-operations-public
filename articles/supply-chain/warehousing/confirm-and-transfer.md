---
title: Confirm and transfer
description: Learn how to use the Confirm and transfer feature, which lets users ship loads out of the warehouse before they complete all the work associated with those loads.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form:  WHSLoadTemplate,WHSWorkTemplateTable,WHSLoadPlanningWorkbench, WHSOutboundLoadPlanningWorkbench
ms.topic: how-to
ms.date: 09/16/2024
ms.custom: 
  - bap-template
---

# Confirm and transfer

[!include [banner](../includes/banner.md)]

The *Confirm and transfer* feature lets workers ship loads out of the warehouse before they complete all the work that is associated with those loads. It's possible to select the default split method to be used on the loads from the load template details and from the single load details.

You can choose what the system should do when confirming a load where not all load lines were fully picked. You can set the system to automatically split the load (add the unfulfilled quantity to a new load), automatically cancel the unfulfilled quantity, or ask the worker what to do. The automatic options can be used in batch jobs, while the manual option requires worker input.

Systems that are set up to allow load splitting support scenarios where planned and partially loaded loads must be adapted because of new or changing circumstances.

The client includes logic that enables a partially loaded load to be closed and confirmed as shipped. All remaining shipments and load lines (including full or partial line quantities) are then rolled over to a newly created load and shipment, if this rollover is required and the setup allows for it. New shipments and loads are automatically created based on the initial criteria for shipment and load creation, and their main attributes remain unchanged. There's also an option to automatically cancel remaining quantities if a work order hasn't yet been created and the user deems this cancellation necessary.

This functionality supports scenarios where the full load doesn't fit onto a single truck, or where some of the load should leave the warehouse before the rest of the load is ready for shipment. In these scenarios, the remaining products can be transferred to a new load and therefore to a new truck. Because this feature can be used with loads that are otherwise intended to require full-load shipment, it provides extra flexibility so that transport managers can solve nonstandard or unforeseen scenarios.

When a load is split, the *Confirm and transfer* feature performs the following actions:

- New loads and shipments are created as required. Each load or shipment has most of the same attributes as the original load or shipment. The exception is the load status, which is recalculated based on the work status.
- The user is informed when a new load is created. The user is also notified about the ID of the new load.
- The load lines, work headers, and work lines that were split are updated with the new load and shipment information.
- If a whole shipment is being split, the shipment is maintained, and only the load references are updated. If the shipment must be split, a new shipment is created.

When remaining quantities are canceled, any load line quantities that haven't been picked and that don't have noncanceled work associated with them are removed from the load. If any work is in process, the user can only split the load. Remaining quantities can't be canceled.

You can split only loads that meet all the following criteria:

- One or more load lines have picked quantities.
- The load status is less than loaded.
- There's no load line data. (This data is created through license plate consolidation on the staging location, and the Confirm and transfer feature doesn't support license plate consolidation.)
- No inventory is currently awaiting packing at a packing location. (The *Confirm and transfer* feature doesn't support inventory that has been picked to the pack station but hasn't yet been packed unless containers that are packed are placed at staging locations with loading work created.)

> [!NOTE]
> This functionality differs from the transport load functionality, which should be used in warehouses that can never plan and create loads before picking, but that instead load the available transportation space after picking is completed.
>
> Use the *Confirm and transfer* feature in situations where loads are usually planned and created ahead of time, but where exceptions sometimes occur in which the load doesn't fit the available transport (such as a truck).

## Set up confirm and transfer

You must enable *Confirm and transfer* functionality for every each load template where you want to use it. Depending on your requirements, you might also want to prepare your work templates to support the feature. This section describes how to set up the feature and also describes the settings you'll need if you're planing to work through the example scenario that is provided later in this article.

### Prepare your load templates

1. Go to **Warehouse management \> Setup \> Load \> Load templates**.
1. Do one of the following steps:
    - To edit an existing template, select **Edit** on the Action Pane.
    - To create a new template, select **New** on the Action Pane.

1. Set up your new or selected template as usual, and then select the **Allow load split during ship confirm** check box for each template where you want to enable this feature. Every load that you create by using that template inherits this functionality. (If you're planning to work through the scenario provided later in this article, and are working with the *USMF* demo data, select this check box for the *20' Container* load template.)
1. On the Action Pane, select **Save**.
1. For each template that was saved with the **Allow load split during ship confirm** checkbox selected, set **Load split shipment confirmation policy** to one of the following values to control what the system should do when confirming a load where not all load lines were fully picked:

    - *Manual selection* – Display a dialog that asks the worker to choose whether to add the remaining quantities to a new load or cancel the incomplete quantities. This action can't be performed by a batch job.
    - *Split quantity to a new load* – Automatically add the unfulfilled quantity to a new load. This action can be performed by a batch job.
    - *Cancel unfulfilled quantity* – Automatically cancel the remaining quantity. This action can be performed by a batch job.

    (If you're planning to work through the scenario provided later in this article, and are working with the *USMF* demo data, then set **Load split shipment confirmation policy** to *Manual selection* for the *20' Container* load template.)

### Prepare your work templates

This setup isn't required in all situations. The example that is shown here ensures that work can be broken by shipment to support the example scenario that is provided later in this article. There are also other ways to achieve this result.

1. Go to **Warehouse management \> Setup \> Work \> Work templates**.
1. In the grid in the upper part of the page, select an existing work template where you want to set up the *Confirm and transfer* feature. (If you're planning to work through the scenario provided later in this article, and are working with the *USMF* demo data, select the *51 Pick to stage* work template.) Alternatively, create a new work template.
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
> The specific values that are described in this scenario are based on the *USMF* [demo data](../../fin-ops-core/dev-itpro/get-started/demo-data.md). We recommend that you use this demo data while you're demonstrating or learning how to use the feature. If you aren't using the *USMF* demo data, substitute your own values as required.

### Step 1: Create a load that has multiple load lines

Before you can use this functionality, you must have a load that contains multiple load lines. You must also make sure that the pick locations have enough inventory for all the items on the sales orders that you'll create. Review the setup of the location directive (**Warehouse management \> Setup \> Location directives**), and make a note of the picking locations that are used for sales order picking. If you must adjust the inventory, create manual movements, use replenishment, or use any other flow, as required.

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

#### Outbound load planning workbench

The outbound load planning workbench uses the load template ID to build the shipments and release the sales order lines to the warehouse.

1. Go to **Warehouse management \> Loads \> Outbound load planning workbench**.
1. In the **Warehouse** field, select *51*.

    You'll now build the load for the sales orders that you created.

1. On the **Sales lines** tab, in the grid, select the sales lines for the new sales orders.
1. On the Action Pane, on the **Supply and demand** tab, in the **Add** group, select **To new load**.
1. In the **Load template assignment** dialog box, in the **Load template ID** field, select *20' Container*.
1. Select **OK**.
1. In the **Loads** section of the **Outbound load planning workbench** page, in the grid, find the newly created load ID for warehouse *51*. Scroll right until you see the **Allow load split during ship confirm** column. The check box should be selected for your load.

    > [!NOTE]
    > The default setting for **Allow load split during ship confirm** comes from the load template used to create the load. The **Load split shipment confirmation policy** setting is also inherited from the template but isn't shown on the **Outbound load planning workbench** page. To change the policy for a load, open its **Load details** page (for example, by selecting its **Load ID** in the grid here).

1. Select the load.
1. On the **Release** menu above the grid, select **Release to warehouse** to create work.
1. In the **Release load to warehouse** dialog box, verify that the **Records to include** FastTab shows your load ID.
1. Select **OK**.

    You might receive a "Processing operation" message while the system creates the shipments and work.

1. In the **Loads** section of the **Outbound load planning workbench** page, your load should now have a load status of *Waved*. Select the load, and then, on the **Related information** menu above the grid, select **Wave details** to view the shipment IDs that were created. When you're done, close the **Waves** page.
1. In the **Loads** section of the **Outbound load planning workbench** page, select the load, and then, on the **Related information** menu above the grid, select **Work details** to view the work that was created for the sales orders.
1. Make a note of the work IDs that were created. You might have to scroll right to see the sales order number and shipment ID that are associated with the work ID.

### Step 2: Set up the execution flow for mobile devices

Mobile device tasks require worker input, such as the work ID or license plate ID. In the fields, this information is typically provided for warehouse workers in the form of bar codes that are found on documentation, packaging, or racking. To complete the mobile device steps for scenarios, make sure that you've identified the work IDs for the transactions, and the license plate IDs for the item and location in the transactions.

1. Sign in to the mobile device by using a user ID and password for warehouse *51*.
1. Select **Outbound**.
1. Select **Sales Picking**.
1. You have the option to enter the work ID or the license plate ID. Enter the work ID for the first sales order, and then select **Enter**.
1. In the **Loc** field, enter the location that is shown to confirm the picking location. Then select **Enter**.
1. In the **LP** field, enter the license plate ID. The license plate ID must be a match for the item, warehouse, and location of the item that is being picked from the selected location. When you're done, select **Enter**.
1. In the **Item** field, enter the item number to confirm the item that is being picked, and then select **Enter**.
1. In the **Qty** field, enter the quantity of the item that is being picked, and then select **Enter**.
1. In the **Target LP** field, enter a target license plate ID. Target license plates are user-defined. Be sure to enter a license plate ID that you can remember. We recommend that you use the current date plus a two-digit sequence (YYMMDD\#\#) as the format, such as *19112301*. When you're done, select **Enter**.
1. Review information that is shown. This information is the *Pick* information that will now become the *Put* data for the put transaction. When you're done, select **Enter**.

    - You receive a **Work Completed** message.

1. Repeat steps 4 through 10 for the work ID of the second sales order.

The next step is to load the two picked license plates to the truck.

1. Sign in to the mobile device by using a user ID and password for warehouse *51*.
1. Select **Outbound**.
1. Select **Sales Loading**.
1. Enter the target license plate ID that you created for the first work ID in the previous procedure. Then select **Enter** to put the target license plate into the **STAGE** location.
1. Enter the target license plate ID again, and then select **Enter** to put the license plate into the **BAYDOOR** location.
1. Repeat steps 4 through 5 for the target license plate ID that you created for the second work ID.

The two work IDs will now be closed (loaded).

### Step 3: Confirm the outbound shipment

In this step, you'll confirm the two sales orders and the work that was completed for the load to ship the picked items. You'll also create a new load for the unpicked items. Outbound shipment confirmation can be done from the **Outbound load planning workbench**, **All loads**, or **Load details** page.

> [!NOTE]
> If you are running Supply Chain Management version 10.0.41 or older, then you can only split loads from the **Load details** page.

1. Go to **Warehouse management \> Loads \> Outbound load planning workbench**.
1. In the **Loads** section, in the grid, select the row for the load ID that you created.
1. Select the load ID link to open the **Load details** page.
1. On the Action Pane, on the **Ship and receive** tab, in the **Confirm** group, select **Outbound shipment** to initiate the confirmation.
1. Because the **Load split shipment confirmation policy** for the load template used to create this load is set to *Manual selection*, the **Ship confirm** dialog is shown. In the **Load split method during ship confirm** field, select *Split quantity to new load*.
1. Select **OK**.

    You might receive a *Processing operation* message. You might also receive informational messages that indicate that the shipment for your load has been confirmed, and that a new load has been created from the split quantity.

1. Refresh the **Outbound load planning workbench** page to see the newly created load.

You can confirm that transaction relations have been updated in the following ways:

- The remaining (unprocessed) shipment and shipment lines are updated with the new load ID.
- The sales order is linked to the new load ID.
- The original load doesn't include the remaining load lines.
- The remaining work has been updated with the new load ID.
- The wave remains the same.
- The status of the new load is correctly updated. (If the work status is *In process*, the load status should also be *In process*.)

## Notes and tips

- In Supply Chain Management version 10.0.42 and later, you can use a batch job to split loads where the **Allow load split during ship confirm** option is set to *Yes* and **Load split shipment confirmation policy** is set to *Split quantity to a new load* or *Cancel unfulfilled quantity*.
- You can change the load shipment confirmation policy for an individual load after you've created it but before the loading process has started. To do so, open its **Load details** page, set **Allow load split during ship confirm** to *Yes* and then select the desired value in the **Load split shipment confirmation policy** field.
- The **Split quantity to new load** option also works when some of the remaining work headers have a status of *In process*. Therefore, you can still use the functionality even if workers are already running the pick orders.
- If you select **Cancel unfulfilled quantity** while there's remaining work that has a status of *Open* or *In progress*, you receive the following error message: "Unable to cancel remaining qty for load. Work exists for load."
- If you select **Cancel unfulfilled quantity** when there's no remaining work but there are unreleased load lines on the load, you receive the following error message: "The shipment for load couldn't be confirmed because the quantity for item exceeds the percentage that is defined for under delivery." To avoid this error, you can set the **Under delivery** percentage on the unreleased load line to *100*. Unreleased lines won't be moved to a new load, but the current load will be confirmed with under delivery. In this case, you won't be able to rerelease the original order, so you'll have to handle it in some other way.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
