---
# required metadata

title: Confirm and transfer
description: Learn how to use the confirm-and-transfer feature, which allows users to ship loads out of the warehouse before completing all work associated with them.
author: mirzaab
manager: AnnBe
ms.date: 01/28/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2020-02-01
ms.dyn365.ops.version: Release 10.0.8
---

# Confirm and transfer

The confirm-and-transfer feature allows users to ship loads out of the warehouse before completing all work associated with them. On receiving a shipment that includes load lines that weren't fully picked, the confirming user will be prompted to choose either to split the remaining quantities onto a new load or to cancel the incomplete quantities.

Systems set to allow load splitting support scenarios where planned and partially loaded loads must be adapted as a result of new or changing circumstances.

The client includes logic that allows a partially loaded load to be closed and confirmed as shipped. If necessary, and if allowed by the setup, all remaining shipments and load lines (including full or partial line quantities) will be rolled over to a newly created load and shipment. New shipments and loads are automatically created based on the initial shipment/load creation criteria and will keep their main attributes unchanged. There is also an option to auto-cancel the remaining quantities if a work order hasn't been created yet and the user deems it necessary.

This functionality supports scenarios where the full load doesn't fit onto a single truck or where some of the load should leave the warehouse before the remainder is ready for shipping. The remaining products can therefore be transferred to a new load and consequently to a new truck. This feature can be used with loads that are otherwise intended to require full-load shipping, so it provides extra flexibility that lets transport managers solve nonstandard or unforeseen scenarios.

When splitting a load, the confirm-and-transfer feature takes the following actions:

- Create new loads and shipments as required. Each of these loads/shipments will have the same attributes as the original load/shipment, except for the load status, which will be recalculated based on the work status.
- Inform the user that a new load has been created along with the new load ID.
- Update the load lines, work headers, and work lines that were split with the new load and shipment information.
- If an entire shipment is being split, then the shipment will be maintained and only the load references will be updated. If the shipment needs to be split, then a new shipment will be created.

When canceling, any load line quantities that haven't been picked, and which don't have non-canceled work associated with them, will be removed from the load. If there is in-process work, then the user will only be able to split, not cancel.

You can only split loads that meet all of the following criteria:

- One or more load lines have picked quantities.
- The load status is less than loaded.
- There are no Load Line data (these are created as a result of License Plate consolidation on the staging location, which isn't supported by confirm and transfer).
- No inventory is currently at a packing location awaiting packing (inventory picked to the pack station, but not yet packed, isn't supported by confirm and transfer).

> [!NOTE]
> This functionality is different from the transport-load feature, which should be used in warehouses that are never able to plan and create loads prior to picking, but instead load the available transportation space after picking is completed.
>
> Use the confirm-and-transfer feature in situations where loads are normally planned and created ahead of time, but where exceptions sometimes occur in which the load doesn't fit the available transport (such as a truck).

## Enable confirm and transfer

Before you begin trying to set up or use this feature, you must make sure it's available on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the feature status and enable it if needed. Here, the feature is listed listed as:

- **Module**: Warehouse management
- **Feature name**: Confirm and transfer

## Set up confirm and transfer

To use confirm-and-transfer feature, you must enable it on each of your relevant load templates. In addition, you might choose to prepare your work templates to support the feature, depending on your requirements. If you'd like to work through the example scenario (based on **USMF** legal-entity demo data) provided later in this topic, then set up your system as described in this section.

### Prepare your load templates

1. Go to **Warehouse management** > **Setup** > **Loads** > **Load templates**.
1. Select **Edit** on the action pane to put the page into edit mode.
1. Select the **Allow load split during ship confirm** check box for each listed template where you'd like to enable this feature (or select **Add** to create a new template and configure it as needed). Every load that you create using this template will now inherit this functionality (If you're working with the **USMF** legal-entity demo data, then enable this feature for the **20' Container** load template.)

### Prepare your work templates

This setup isn't required in all situations. The example shown here ensures that work can be broken by shipment, which will support the example scenario provided later in this topic. There are also other ways to accomplish this.

1. Go to **Warehouse management** > **Setup** > **Work** > **Work templates**.
1. Find or create a work template where you want to set up the confirm-and-transfer feature (If you're working with the **USMF** legal-entity demo data, then edit the **51 Pick to stage** work template.)
1. Select **Edit query** on the action pane to open the **Sales** flyout.
1. Open the **Sorting** tab on the flyout.
1. Select **Add** to add a new row to the table and then make the following settings for the new row:
    - **Table**: Temporary work transactions
    - **Derived table**: Temporary work transactions
    - **Field**: Shipment ID
    - **Search direction**: Ascending
1. Select **OK** to save your settings and close the flyout.
1. You may see an alert telling you that grouping will be reset. Select **Yes** to continue.
1. In the **Work templates** table, select the template that you just edited and then select **Work header breaks** on the action pane.
1. Select **Edit** on the action pane to put the page into edit mode.
1. Make the following settings in the table:
    - **Table name**: Temporary work transactions
    - **Field name**: Shipment ID
    - **Group by this field**: (Selected)
1. Select **Save** on the action pane.
1. **Close** the form.

## Scenario

This scenario illustrates an example where the picking process isn't finished yet, but the items picked so far need to be loaded onto a truck and shipped anyway. The user will therefore be able to _**split**_ the unpicked load lines into a new load with all data relationships updated automatically.

> [!NOTE]
> The specific values suggested in this scenario are based on the **USMF** legal-entity demo data. We recommend you use this demo data while demonstrating or learning the feature. If you aren't using the **USMF** demo data, then substitute your own values as needed.

### Step 1: Create a load with multiple load lines

Before you can use this functionality, you must have a load with multiple load lines. Also, ensure you have enough inventory in the pick locations for all of the items in the sales orders you will create. Review the **Location directive** setting (**Warehouse management** > **Setup** > **Location directives**) and take note of the picking locations are used for sales order picking. If you need to adjust the inventory, create manual movements, use replenishment, or any other flow as needed.

To create a qualifying load first create three sales orders:

1. Go to **Sales and Marketing** > **Sales orders** > **All sales orders**.

1. Select **New** on the action pane to open the **Create sales order** flyout.

1. In the flyout, make the following settings (at minimum):

    - In the **Customer** FastTab, select **US-004**, - **Cave Wholesales**.
    - In the **General** FastTab, set the **Warehouse** to *51*.

1. Select **OK** to create the sales order and close the flyout.

1. Your new sales order now opens. In the **Sales order** lines table, add a line with the following values:

    - **Item number** *M9200*, **Quantity** *40*, **Unit**: *ea*
1. In the **Sales order lines** FastTab, select **Inventory**, then select **Reservation** from the menu.
1. Select **Reserve lot** from the Action pane to open the **Reservation** form and reserve the inventory on the sales line.
1. Close the **Reservation** form.

1. Repeat **steps 1 - 4** to add a second sales order for the same **Customer** and **Warehouse**, but this time with the following order lines:

    - Line 1: **Item number** *M9200*, **Quantity** *30*, **Unit** *ea*
    - Line 1: Reserve the inventory for the sales line (**steps 6 - 8**).
        - Select **Add line** to add an additional line
    - Line 2: **Item number** *M9201*, **Quantity** *20*, **Unit** *ea*
    - Line 2: Reserve the inventory for the sales line (**steps 6 - 8**).

1. Repeat this procedure to add a third sales order for the same **Customer** and **Warehouse**, but this time with the following order lines:
    - Line 1: **Item number** *M9201*, **Quantity** *20*, **Unit** *ea*
    - Line 1: Reserve the inventory for the sales line (**steps 6 - 8**).
        - Select **Add line** to add an additional line
    - Line 2: **Item number** *M9202*, **Quantity** *60*, **Unit** *ea*
    - Line 2: Reserve the inventory for the sales line (**steps 6 - 8**).

### Load Planning Workbench

The load planning workbench will utilize the **Load template ID** to build the shipments and release the sales order lines to the warehouse.

1. Go to **Warehouse management** > **Loads** > **Load planning workbench**
1. Select warehouse **51** in the **Warehouse field**.
1. Select **Sales lines** tab. Now you will build the load for the sales orders you just created.
1. In the **Sales lines** grid, select the sales lines for the sales orders you just created.
1. On the Action Pane, select **Supply and demand**.
1. Select **To new load**.
1. In the **Load template assignment** FlyOut, select **20' Container** from **Load template ID**
1. In the **Loads** section of the **Load planning workbench**, find your newly created **Load ID** for warehouse **51**. Scroll right until you see the column **Allow load split during ship confirm**. Your load will be checked.
1. Select the load.
1. Select **Release** from the **Loads** action pane, then select **Release to warehouse** to create work.
1. In the **Release load to warehouse** FlyOut, validate that your **Load ID** is displayed in the **Records to include** FastTab.Expand the section if necessary.
1. Select **OK**.
1. A **Processing operation** popup may display while the system creates the shipments and work.
1. In the **Loads** section your load will now have a **Load status** of **Waved**. Select your load then select **Related information** from the **Loads** action pane.
1. There are several menu options to choose from, select **Wave details** to view the **Shipment ID**'s created.
1. Select **Work details** to view the work created for the sales orders.
1. Make note of the **Work ID**'s created, you may need to scroll right to identify the sales **Order number** and **Shipment ID** associated with the work ID.

### Step 2: Set up the execution flow for mobile devices

Mobile device tasks will require user input of information, such as **Work ID** or **License Plate**. In the field, this information is typically provided for warehouse users in the form of barcodes found on documentation, packaging or racking. To complete the mobile device steps of scenarios, ensure that you have identified the work ID's for the transactions and the license plate ID's for the item and location in the transactions.

1. Log in to the mobile device with a **User ID** and **Password** for warehouse **51**.
1. Select the **Outbound** menu item.
1. Select **Sales Picking** menu item.
1. You have the option to enter the **Work ID** or **License Plate ID**, enter the **work ID** for the first **Sales order**, select **Enter**.
1. Enter the displayed location in the **LOC** field to confirm the picking location, select **Enter**.
1. Enter the **License plate ID** in the **LP** field. License plate ID must match to the Item, Warehouse and Location of the item being picked from the selected location, select **Enter**.
1. Enter the **Item number** in the **ITEM** field to confirm the item being picked, select **Enter**.
1. Enter the quantity of the item being picked in the **QTY** field, select **Enter**.
1. Enter a **Target License plate ID** in the **Target LP** field. Target LP's are user defined, enter a LP ID you will remember, suggest a format of current date plus a 2 digit sequence (example: YYMMDD##, 19112301), select **Enter**.
1. Review information displayed, this is the **Pick** information that will now become the **Put** data for the put transaction, select **Enter**.
1. **Work Completed**
1. Repeat **Steps 4 - 10** for the **Work ID** of the second **Sales order**.

Next step is to load the two picked license plates to the truck.

1. Log in to the mobile device with a **User ID** and **Password** for warehouse **51**.
1. Select the **Outbound** menu item.
1. Select **Sales Loading** menu item.
1. Enter the user defined **Target License plate ID** created in **Step 9** above, select **Enter** to **Put** the target LP into the **STAGE** location.
1. Enter the target license plate ID again and select **Enter** to **Put** the LP into the **BAYDOOR** location.
1. Repeat for the **Target License plate ID** created for the second work ID.

These two Work IDs will now be closed (loaded).

### Step 3: Confirm the outbound shipment

In this step you will confirm the two Sales orders/Work that have been completed for the load to **ship** the picked items of the load and create a new load for the unpicked items. **Outbound shipment confirmation** must be done on the **Load details** form.

1. Go to **Warehouse management** > **Loads** > **Load planning workbench**.
1. In the **Load planning workbench** form, select the **Load ID** you created from the grid in the **Loads** section.
1. Select the **Load ID** ***hyperlink*** to open **Load Details**.
1. On the **Load details** Action Pane, select **Ship and receive** tab and then select **Outbound shipment** from the **Confirm** section to initiate the confirmation.
1. On the **Ship confirm** FlyOut, in the **Load split method during ship confirm** field, select **Split quantity to new load**.
1. Select **OK**. A processing operation message may appear.
1. Informational messages are displayed indicating that the **shipment** for your load has been confirmed, and, a new **Load** has been created from the split quantity.

On the main screen, the user is presented with the newly created Load after a refresh.

You can also confirm that transaction relations have been updated accordingly.

- The remaining (unprocessed) Shipment and Shipment lines are updated with the new Load ID.
- Sales order is linked to the new Load ID.
- Original Load does not include the remaining Load lines.
- Remaining Work has been updated with the new Load ID.
- The Wave remains the same.
- Status of the new Load is also correctly updated (if work is _In process_, Load status will also be _In process_)

## Notes and tips

- You can also enable **Allow load split during ship confirm** after the load has been created with the **Load template** parameter turned off, but before the loading process has started. To do so, navigate to the desired load and on the header view enable the parameter.
- The **Split quantity to new load** option also works when some of the remaining work headers have a status of **In process**, which means that you can still use the functionality even if workers are already executing the pick orders.
- If you select **Cancel unfulfilled quantity** while there is remaining work with a status of **Open** or **In progress**, you will get the following error: *Unable to cancel remaining qty for load. Work exists for load*.
- If you select **Cancel unfulfilled quantity** when there is no work remaining (but unreleased load lines are on the load), you will get the following error: *The shipment for load could not be confirmed because the quantity for item exceeds the percentage that is defined for under delivery.* You can avoid this by setting the **Under delivery** percentage on the unreleased load line to 100%. This won't move unreleased lines to a new load, but will confirm the current load with under delivery. You won't be able to re-release the original order in this case, so you'll have to handle it in some other way.
