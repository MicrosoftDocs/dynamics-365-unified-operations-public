---
title: Confirm and transfer
description: Learn how to use the Confirm and transfer feature, which lets users ship loads out of the warehouse before they complete all the work associated with those loads.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form:  WHSLoadTemplate,WHSWorkTemplateTable,WHSLoadPlanningWorkbench, WHSOutboundLoadPlanningWorkbench
ms.topic: how-to
ms.date: 09/24/2025
ms.custom: 
  - bap-template
---

# Confirm and transfer

[!include [banner](../includes/banner.md)]

The *Confirm and transfer* feature lets workers ship loads out of the warehouse before they complete all the work that's associated with those loads. This functionality supports scenarios where the full load doesn't fit onto a single truck, or where some of the load should leave the warehouse before the rest of the load is ready for shipment. In these scenarios, the remaining products can be transferred to a new load and therefore to a new truck. Because you can use this feature with loads that are otherwise intended to require full-load shipment, it provides extra flexibility so that transport managers can solve nonstandard or unforeseen scenarios.

You can choose what the system should do when confirming a load where not all load lines are fully picked.

You can set the system to either ask the worker what to do, or run batch jobs to automatically do the following actions:

- Split the load (add the unfulfilled quantity to a new load)
- Cancel the unfulfilled quantity

## Splitting the load

You can select the default split method for loads in the load template details and in the single load details. Systems set up to support load splitting handle scenarios where planned and partially loaded loads need to change because of new or changing circumstances.

The client includes logic that enables a partially loaded load to be closed and confirmed as shipped. If this rollover is required and the setup allows for it, all remaining shipments and load lines (including full or partial line quantities) roll over to a newly created load and shipment. New shipments and loads are automatically created based on the initial criteria for shipment and load creation, and their main attributes remain unchanged. You can also automatically cancel remaining quantities if a work order isn't yet created and you want to cancel these quantities.

When you split a load, the *Confirm and transfer* feature performs the following actions:

- Creates new loads and shipments as required. Each load or shipment has most of the same attributes as the original load or shipment. The exception is the load status, which is recalculated based on the work status.
- Informs you when a new load is created. It also notifies you about the ID of the new load.
- Updates the load lines, work headers, and work lines that were split with the new load and shipment information.
- Maintains the shipment and updates only the load references if a whole shipment is being split. Creates a new shipment if the shipment must be split.

You can split only loads that meet all the following criteria:

- One or more load lines have picked quantities.
- The load status is less than loaded.
- There's no load line data. (This data is created through license plate consolidation on the staging location, and the *Confirm and transfer* feature doesn't support license plate consolidation.)
- No inventory is currently awaiting packing at a packing location. (To be able to split loads with the *Confirm and transfer* feature for inventory that you picked to the pack station but didn't yet pack and move to staging locations, follow the configuration steps detailed in [Packing work for packing outbound containers and processing shipments](dynamics365/supply-chain/warehousing/packing-work)).

## Cancelling the load

When you cancel remaining quantities, the process removes any load line quantities that aren't picked and that don't have noncanceled work associated with them from the load. If any work is in process, you can only split the load. You can't cancel remaining quantities.

> [!NOTE]
> Use the *Confirm and transfer* feature in situations where you usually plan and create loads ahead of time, but exceptions sometimes occur in which the load doesn't fit the available transport (such as a truck).

## Set up confirm and transfer

You must enable *Confirm and transfer* functionality for every load template where you want to use it. Depending on your requirements, you might also want to prepare your work templates to support the feature. This section describes how to set up the feature and also describes the settings you need if you're planning to work through the example scenario that is provided later in this article.

### Prepare your load templates

1. Go to **Warehouse management \> Setup \> Load \> Load templates**.
1. Do one of the following steps:
    - To edit an existing template, select **Edit** on the Action Pane.
    - To create a new template, select **New** on the Action Pane.

1. Set up your new or selected template as usual, and then select the **Allow load split during ship confirm** check box for each template where you want to enable this feature. Every load that you create by using that template inherits this functionality. (If you're planning to work through the scenario provided later in this article, and are working with the *USMF* demo data, select this check box for the *20' Container* load template.)
1. On the Action Pane, select **Save**.
1. For each template that you save with the **Allow load split during ship confirm** checkbox selected, set **Load split shipment confirmation policy** to one of the following values to control what the system should do when confirming a load where not all load lines are fully picked:

    - *Manual selection* – Display a dialog that asks the worker to choose whether to add the remaining quantities to a new load or cancel the incomplete quantities. A batch job can't perform this action.
    - *Split quantity to a new load* – Automatically add the unfulfilled quantity to a new load. A batch job can perform this action.
    - *Cancel unfulfilled quantity* – Automatically cancel the remaining quantity. A batch job can perform this action.

    (If you're planning to work through the scenario provided later in this article, and are working with the *USMF* demo data, then set **Load split shipment confirmation policy** to *Manual selection* for the *20' Container* load template.)

### Prepare your work templates

This setup isn't required in all situations. The example that is shown here ensures that work can be broken by shipment to support the example scenario that is provided later in this article. You can also use other methods to achieve this result.

1. Go to **Warehouse management \> Setup \> Work \> Work templates**.
1. In the grid in the upper part of the page, select an existing work template where you want to set up the *Confirm and transfer* feature. (If you plan to work through the scenario provided later in this article, and you're working with the *USMF* demo data, select the *51 Pick to stage* work template.) Alternatively, create a new work template.
1. On the Action Pane, select **Edit query** to open the **Sales** dialog box.
1. In the **Sales** dialog box, on the **Sorting** tab, select **Add** to add a row to the grid.
1. In the new row, set the following values:

    - **Table:** *Temporary work transactions*
    - **Derived table:** *Temporary work transactions*
    - **Field:** *Shipment ID*
    - **Search direction:** *Ascending*

1. Select **OK** to save your settings and close the **Sales** dialog box.
1. If you receive a message that states that grouping is reset, select **Yes** to continue.
1. In the grid in the upper part of the **Work templates** page, select the template that you just edited, and then, on the Action Pane, select **Work header breaks**.
1. On the Action Pane, select **Edit** to put the page into edit mode.
1. In the grid, set the following values:

    - **Table name:** *Temporary work transactions*
    - **Field name:** *Shipment ID*
    - **Group by this field:** Select this check box.

1. On the Action Pane, select **Save**.
1. Close the page.

## Scenario

This scenario shows an example where the picking process isn't yet completed, but the items that you picked so far must be loaded onto a truck and shipped anyway. Therefore, you can split the unpicked load lines onto a new load. All the data relationships automatically update.

> [!NOTE]
> The specific values that are described in this scenario are based on the *USMF* [demo data](../../fin-ops-core/dev-itpro/get-started/demo-data.md). Use this demo data while you're demonstrating or learning how to use the feature. If you don't use the *USMF* demo data, substitute your own values as required.

### Step 1: Create a load that has multiple load lines

Before you can use this functionality, you must have a load that contains multiple load lines. You must also make sure that the pick locations have enough inventory for all the items on the sales orders that you create. Review the setup of the location directive (**Warehouse management \> Setup \> Location directives**), and make a note of the picking locations that are used for sales order picking. If you must adjust the inventory, create manual movements, use replenishment, or use any other flow, as required.

To create a qualifying load, first create three sales orders by following these steps.

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. On the Action Pane, select **New** to open the **Create sales order** dialog box.
1. In the **Create sales order** dialog box, set the following values (at a minimum):

    - On the **Customer** FastTab, set the **Customer account** field to *US-004* (*Cave Wholesales*).
    - On the **General** FastTab, set the **Warehouse** field to *51*.

1. Select **OK** to create the sales order and close the **Create sales order** dialog box.
1. Your new sales order opens. In the **Sales order lines** grid, add a line that has the following values:

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

Mobile device tasks require worker input, such as the work ID or license plate ID. In the fields, this information typically appears for warehouse workers as bar codes on documentation, packaging, or racking. To complete the mobile device steps for scenarios, make sure that you identify the work IDs for the transactions, and the license plate IDs for the item and location in the transactions.

1. Sign in to the mobile device by using a user ID and password for warehouse *51*.
1. Select **Outbound**.
1. Select **Sales Picking**.
1. Enter the work ID or the license plate ID. Enter the work ID for the first sales order, then select **Enter**.
1. In the **Loc** field, enter the location that is shown to confirm the picking location. Then select **Enter**.
1. In the **LP** field, enter the license plate ID. The license plate ID must match the item, warehouse, and location of the item that you're picking from the selected location. When you're done, select **Enter**.
1. In the **Item** field, enter the item number to confirm the item that you're picking, then select **Enter**.
1. In the **Qty** field, enter the quantity of the item that you're picking, then select **Enter**.
1. In the **Target LP** field, enter a target license plate ID. Target license plates are user-defined. Be sure to enter a license plate ID that you can remember. We recommend that you use the current date plus a two-digit sequence (YYMMDD\#\#) as the format, such as *19112301*. When you're done, select **Enter**.
1. Review the information that is shown. This information is the *Pick* information that now becomes the *Put* data for the put transaction. When you're done, select **Enter**.

    - You receive a **Work Completed** message.

1. Repeat steps 4 through 10 for the work ID of the second sales order.

The next step is to load the two picked license plates to the truck.

1. Sign in to the mobile device by using a user ID and password for warehouse *51*.
1. Select **Outbound**.
1. Select **Sales Loading**.
1. Enter the target license plate ID that you created for the first work ID in the previous procedure. Then select **Enter** to put the target license plate into the *STAGE* location.
1. Enter the target license plate ID again, then select **Enter** to put the license plate into the *BAYDOOR* location.
1. Repeat steps 4 through 5 for the target license plate ID that you created for the second work ID.

The two work IDs are now closed (loaded).

### Step 3: Confirm the outbound shipment

In this step, you confirm the two sales orders and the work that you completed for the load to ship the picked items. You also create a new load for the unpicked items. You can confirm the outbound shipment from the **Outbound load planning workbench**, **All loads**, or **Load details** page.

> [!NOTE]
> If you're running Supply Chain Management version 10.0.41 or older, you can only split loads from the **Load details** page.

1. Go to **Warehouse management \> Loads \> Outbound load planning workbench**.
1. In the **Loads** section, in the grid, select the row for the load ID that you created.
1. Select the load ID link to open the **Load details** page.
1. On the Action Pane, on the **Ship and receive** tab, in the **Confirm** group, select **Outbound shipment** to initiate the confirmation.
1. Because the **Load split shipment confirmation policy** for the load template used to create this load is set to *Manual selection*, the **Ship confirm** dialog is shown. In the **Load split method during ship confirm** field, select *Split quantity to new load*.
1. Select **OK**.

    You might receive a *Processing operation* message. You might also receive informational messages that indicate that the shipment for your load is confirmed, and that a new load is created from the split quantity.

1. Refresh the **Outbound load planning workbench** page to see the newly created load.

You can confirm that transaction relations are updated in the following ways:

- The remaining (unprocessed) shipment and shipment lines are updated with the new load ID.
- The sales order is linked to the new load ID.
- The original load doesn't include the remaining load lines.
- The remaining work is updated with the new load ID.
- The wave remains the same.
- The status of the new load is correctly updated. (If the work status is *In process*, the load status is also *In process*.)

## Confirm and transfer and Partial shipment of transport load features

The *Confirm and Transfer* and ([Partial Shipment of a Transport Load]dynamics365/supply-chain/warehousing/partial-shipping-of-transport-loads?branch=main)) features both focus on flexibility in different aspects of the warehousing process. The *Partial shipment of transport load* feature enables flexibility in planning and loading, whereas the *Confirm and Transfer* feature enables flexibility in ship confirming a load. You can use these features alone or together.

Both features allow for more adaptable handling of transport loads, accommodating partial shipments and incomplete work scenarios. For example, you can plan loads without considering specific containers or trucks. After releasing these loads to the warehouse, workers can use mobile devices to assign loads in real-time as it makes sense, loading inventory from the same or different loads onto the same truck. This flexibility allows for partial shipments based on real-time loading decisions. Once a truck is full, workers can use the *Confirm and Transfer* feature to close and complete an incomplete load and optionally split or cancel remaining quantities. This way, warehouse workers can make real-time decisions on load assignments and shipment confirmations, optimizing the use of transport capacity, and warehouse operations can proceed without delays.

## Notes and tips

- In Supply Chain Management version 10.0.42 and later, you can use a batch job to split loads where the **Allow load split during ship confirm** option is set to *Yes* and **Load split shipment confirmation policy** is set to *Split quantity to a new load* or *Cancel unfulfilled quantity*.
- You can change the load shipment confirmation policy for an individual load after you create it but before the loading process starts. To do so, open its **Load details** page, set **Allow load split during ship confirm** to *Yes* and then select the desired value in the **Load split shipment confirmation policy** field.
- The **Split quantity to new load** option also works when some of the remaining work headers have a status of *In process*. Therefore, you can still use the functionality even if workers are already running the pick orders.
- If you select **Cancel unfulfilled quantity** while there's remaining work that has a status of *Open* or *In progress*, you receive the following error message: "Unable to cancel remaining qty for load. Work exists for load."
- If you select **Cancel unfulfilled quantity** when there's no remaining work but there are unreleased load lines on the load, you receive the following error message: "The shipment for load couldn't be confirmed because the quantity for item exceeds the percentage that is defined for under delivery." To avoid this error, you can set the **Under delivery** percentage on the unreleased load line to *100*. Unreleased lines aren't moved to a new load, but the current load is confirmed with under delivery. In this case, you can't rerelease the original order, so you have to handle it in some other way.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
