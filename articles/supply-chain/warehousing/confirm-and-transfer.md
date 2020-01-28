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
- There are no LoadLineWorkLineDetails (these are created as a result of LP consolidation on the staging location, which isn't supported by confirm and transfer).
- No inventory is currently at a packing location awaiting packing (inventory picked to the pack station, but not yet packed, isn't supported by confirm and transfer).

<!-- KFM: What kind of thing is "LoadLineWorkLineDetails"--can we make a real word or phrase out of this? Also, what is a "LP"? -->  

> [!NOTE]
> This functionality is different from the transport-load feature, which should be used in warehouses that are never able to plan and create loads prior to picking, but instead load the available transportation space after picking is completed.
> <!-- KFM: Let's add a link to the transport-load feature; is it this?: https://docs.microsoft.com/en-us/dynamics365/supply-chain/warehousing/partial-shipping-of-transport-loads -->  
> Use the confirm-and-transfer feature in situations where loads are normally planned and created ahead of time, but where exceptions sometimes occur in which the load doesn't fit the available transport (such as a truck).

## Enable confirm and transfer

Before you begin trying to set up or use this feature, you must make sure it's available on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the feature status and enable it if needed. Here, the feature is listed listed as:

- **Module**: Warehouse management
- **Feature name**: Confirm and transfer

<!-- KFM: Add this?: "If you don't see the feature listed here, then it may have become a standard part of the product since this documentation was written, in which case you can proceed with the remaining sections of this topic and all of the described features should be available to you." -->

## Set up confirm and transfer

To use confirm-and-transfer feature, you must enable it on each of your relevant load templates. In addition, you might choose to prepare your work templates to support the feature, depending on your requirements. If you'd like to work through the example scenario (based on **USMF** legal-entity demo data) provided later in this topic, then set up your system as described in this section.

### Prepare your load templates

1. Go to **Warehouse management** > **Setup** > **Loads** > **Load templates**.
1. Select **Edit** on the action pane to put the page into edit mode.
1. Select the **Allow load split during ship confirm** check box for each listed template where you'd like to enable this feature (or select **Add** to create a new template and configure it as needed). Every load that you create using this template will now inherit this functionality <!-- KFM: also existing loads, or just new ones? -->. <br>(If you're working with the **USMF** legal-entity demo data, then enable this feature for the **20' Container** load template.)

<!--
KFM: I'm not sure what to do with the following text. I think maybe it belongs in the intro or in the scenario:

    There are two options available to the user when this functionality is used:

    - --Split quantity to new load
    - --Cancel unfulfilled quantity

    In this demo, I will show the _Split quantity to new load_. No additional setup is needed for the other option, as it is a user decision at execution.
 -->

### Prepare your work templates

This setup isn't required in all situations. The example shown here ensures that work can be broken by shipment, which will support the example scenario provided later in this topic. There are also other ways to accomplish this.

1. Go to **Warehouse management** > **Setup** > **Work** > **Work templates**.
1. Find or create a work template where you want to set up the confirm-and-transfer feature.<br>(If you're working with the **USMF** legal-entity demo data, then edit the **51 Pick to stage** work template.)
1. Select **Edit query** on the action pane to open the **Sales** flyout.
1. Open the **Sorting** tab on the flyout.
1. Select **Add** to add a new row to the table and then make the following settings for the new row: <!-- KMF: what are we doing here? What do these settings do? Do we always want to do this? Do we have a link for more info? -->
    - **Table**: Temporary work transactions
    - **Derived table**: Temporary work transactions
    - **Field**: Shipment ID
    - **Search direction**: Ascending
1. Select **OK** to save your settings and close the flyout.
1. You may see an alert telling you that grouping will be reset. Select **Yes** to continue. <!-- KMF: I got this warning. Anything more to say here? -->
1. In the **Work templates** table, select the template that you just edited and then select **Work header breaks** on the action pane.
1. Select **Edit** on the action pane to put the page into edit mode.
1. Make the following settings in the table: <!-- KMF: what are we doing here? What do these settings do? Do we always want to do this? Do we have a link for more info? -->
    - **Table name**: Temporary work transactions
    - **Field name**: Shipment ID
    - **Group by this field**: (Selected)
1. Select **Save** on the action pane.

## Example scenario

This scenario illustrates an example where the picking process isn't finished yet, but the items picked so far need to be loaded onto a truck and shipped anyway. The user will therefore be able to _split_ the unpicked load lines into a new load with all data relationships updated automatically.

> [!NOTE]
> The specific values suggested in this scenario are based on the **USMF** legal-entity demo data. We recommend you use this demo data while demonstrating or learning the feature. If you aren't using the **USMF** demo data, then substitute your own values as needed.

### Step 1: Create a load with multiple load lines

Before you can use this functionality, you must have a load with multiple load lines. To create a qualifying load:

1. Go to **Sales and Marketing** > **Sales orders** > **All sales orders**.

1. Select **New** on the action pane to open the **Create sales order** flyout.

1. In the flyout, make the following settings (at minimum):

    - In the **Customer** FastTab, select an appropriate **Customer account**.
    - In the **General** FastTab, set the **Warehouse** to "51".

1. Select **OK** to create the sales order and close the flyout.

1. Your new sales order now opens. In the **Sales order** lines table, use the **Add line** button to add a line with the following values:

    - **Item number** "M9200", **Quantity** "40", **Unit**: "ea"

1. Repeat this procedure to add a second sales order for the same **Customer** and **Warehouse**, but this time with the following order lines:

    - Line 1: **Item number** "M9200", **Quantity** "30", **Unit** "ea"
    - LIne 2: **Item number** "M9201", **Quantity** "20", **Unit** "ea"

1. Repeat this procedure to add a third sales order for the same **Customer** and **Warehouse**, but this time with the following order lines:
    - Line 1: **Item number** "M9201", **Quantity** "20", **Unit** "ea"
    - Line 2: **Item number** "M9202", **Quantity** "60", **Unit** "ea"

    <!-- KMF: I was unable to confirm any of the steps after this point. -->

1. Make sure you have enough inventory in the pick locations for all of the items in the sales orders you just created. Review the **Location directive** setting and take note of the picking locations are used for sales order picking. If you need to adjust the inventory, create manual movements, use replenishment, or any other flow as needed.  <!-- KMF: How do I do these things? Where is the **location directive** setting? Do we have links for more info? -->

1. Reserve the inventory. <!-- KMF: How? Inventory > Reservation? Then what? Use all three SOs?  Do we have a link for more info? -->

1. Go to **Warehouse management** > **Loads** > **Load planning workbench** and open the workbench where the new load will be created with the desired load template. <!-- KMF: I only see one workbench. What load template do you mean? How do I know where my load will be created? -->

1. Select the load template from the setup. <!-- KMF: How do I choose a template? Which template should I choose? (Earlier, we prepare the **20' Container** load template.) What setup do you mean? -->

1. A new load is now created. <!-- KMF: How/when is it created? Does this happen automatically after choosing a load template in the last step? -->

1. In the **Loads** section of the **Load planning workbench**, go to **Release** and **Release to warehouse** for the newly created load. This will create work orders for the added load lines. <!-- KMF: This makes no sense to me. I suspect several steps are missing. -->

### Step 2: Set up the execution flow for mobile devices

<!-- KMF: I couldn't edit this section because none of it makes sense to me. I suspect many steps and/or links are missing. Please review and revise. -->

Enter mobile device and select the menu where the new Sales order picking mobile device menu is located.

Select the _Sales Pick_ menu item and initiate the pick. After selecting the menu and entering the first Work ID, the user will be presented with the Pick step. Complete the pick until the Put to Stage step for Work ID 1 and repeat the same for Work ID 2.

Next, load the two picked pallets to the truck. Select the _Sales Loading_ menu item to start the loading process. After selecting the menu and entering the first Work ID, the user will be presented with the Pick step. Complete the loading of Work ID 1 and repeat the same for Work ID 2.

These two Work IDs will now be closed (loaded).

### Step 3: Confirm the outbound shipment

1. Go to **Warehouse management** > **Loads** > **Load planning workbench** and select the load you just created to view its details.

1. On the action bar, open the **Ship and receive** tab and then select **Outbound shipment** from the **Confirm** section to initiate the confirmation.

<!-- KMF: I couldn't reproduce this procedure after this point, so I wasn't able to edit after here. -->

New _Ship confirm_ form will be presented to the user indicating that _Ship confirm will split Load_, where the user has the option to continue or cancel.

For the purpose of this demo, select option _Split quantity to new load_ and press _OK._

The system will show a message to the user &quot;The shipment for load %1 has been confirmed&quot;.On the main screen, the user is presented with the newly created Load after a refresh.

You can also confirm that transaction relations have been updated accordingly.

- The remaining (unprocessed) Shipment and Shipment lines are updated with the new Load ID.
- Sales order is linked to the new Load ID.
- Original Load does not include the remaining Load lines.
- Remaining Work has been updated with the new Load ID.
- The Wave remains the same.
- Status of the new Load is also correctly updated (if work is _In process_, Load status will also be _In process_)

## Notes and tips

- You can also enable **Allow load split during ship confirm** after the load has been created with the **Load template** parameter turned off, but before the loading process has started. To do so, navigate to the desired load and on the header view enable the parameter. <!-- KMF: Please clarify the last sentence here. -->
- The **Split quantity to new load** option also works when some of the remaining work headers have a status of **In process**, which means that you can still use the functionality even if workers are already executing the pick orders.
- If you select **Cancel unfulfilled quantity** while there is remaining work with a status of **Open** or **In progress**, you will get the following error: *Unable to cancel remaining qty for load. Work exists for load*.
- If you select **Cancel unfulfilled quantity** when there is no work remaining (but unreleased load lines are on the load), you will get the following error: *The shipment for load could not be confirmed because the quantity for item exceeds the percentage that is defined for under delivery.* You can avoid this by setting the **Under delivery** percentage on the unreleased load line to 100%. This won't move unreleased lines to a new load, but will confirm the current load with under delivery. You won't be able to re-release the original order in this case, so you'll have to handle it in some other way.
