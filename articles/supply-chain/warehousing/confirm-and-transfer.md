# Confirm and Transfer

The confirm-and-transfer feature allows users to ship loads out of the warehouse before completing all work associated with them. On receiving a shipment that includes load lines that weren't fully picked, the confirming user will be prompted to choose either to split the remaining quantities onto a new load or to cancel the incomplete quantities.

Systems set to allow load splitting support scenarios where planned and partially loaded loads must be adapted as a result of new or changing circumstances.

The client includes logic that allows a partially loaded load to be closed and confirmed as shipped. If necessary, and if allowed by the setup, all remaining shipments and load lines (including full or partial line quantities) will be rolled over to a newly created load and shipment. New shipments and loads are automatically created based on the initial shipment/load creation criteria and will keep their main attributes unchanged. There is also an option to auto-cancel the remaining quantities if a work order hasn't been created yet and the user deems it necessary.

This functionality supports scenarios where the full load doesn't fit onto a single truck or where some of the load should leave the warehouse before the remainder is ready for shipping. The remaining products can therefore be transferred to a new load and consequently to a new truck. This feature can be used with loads that are otherwise intended to require full-load shipping, so it provides extra flexibility that lets transport managers solve nonstandard or unforeseen scenarios.

When splitting a load, the confirm-and-transfer feature does the following:

- Create new loads and shipments as required. Each of these loads/shipments will have the same attributes as the original load/shipment, except for the load status, which will be recalculated based on the work status.
- Inform the user that a new load has been created along with the new load ID.
- Update the load lines, work headers, and work lines that were split with the new load and shipment information.
- If an entire shipment is being split, then the shipment will be maintained and only the load references will be updated. If the shipment needs to be split, then a new shipment will be created.

When canceling, any load line quantities that haven't been picked, and which don't have non-canceled work associated with them, will be removed from the load. If there is in-process work, then the user will only be able to split, not cancel.

You can only split loads that meet all of the following criteria:

- One or more load lines have picked quantities
- The load status is less than loaded
- There are no LoadLineWorkLineDetails (these are created as a result of LP consolidation on the staging location, which isn't supported by confirm and transfer)
- No inventory is currently at a packing location awaiting packing (inventory picked to the pack station, but not yet packed, isn't supported by confirm and transfer)

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
1. Make the following settings in the table:
    - **Table name**: Temporary work transactions
    - **Field name**: Shipment ID
    - **Group by this field**: (Selected)
1. Select **Save** on the action pane.

## Example scenario

This scenario illustrates an example where the picking process isn't finished yet, but the already picked items need to be loaded onto a truck and shipped anyway. The user will therefore be able to _split_ the unpicked load lines into a new load with all data relationships updated automatically.

### Step 1: create a load with multiple load lines

Before the functionality can be demonstrated, Load must be created with multiple Load lines.

Navigate to _Sales and Marketing - Sales orders - All sales order_. Click New to create a new Sales Order. Enter desired customer. In the _General_ section specify Warehouse 51.

1. Sales order 1: Add a new line to the sales order, item M9200, quantity 40 ea.
2. Sales order 2: Add a new line to the sales order, item M9200, quantity 30 ea. Add a second line for item M9201, quantity 20 ea
3. Sales order 3: Add a new line to the sales order, item M9201, quantity 20 ea. Add a second line for item M9202, quantity 60 ea

Before creating a new Load, ensure there is enough inventory on the pick locations for all the items on the orders. Review the Location Directive setting to be sure what picking locations are used for sales order picking. You can create manual movements, use replenishment, or any other flow if needed to adjust the inventory. Reserve the inventory.

Navigate to _Warehouse management - Loads - Load planning workbench_ and open the _Load planning workbench_ where new Load will be created with the desired Load template.

Select the _Sales lines_ from the previously created Sales orders and _Add them to a new Load._ On the _Load template assignment_ form, select the Load template from the setup.

New Load is now created.

On the _Loads_ section on the LPW, navigate to _Release_ and _Release to warehouse_ newly created Load. This will create Work orders for the added Load lines.

### Step 2: Set up the execution flow for mobile devices

Enter mobile device and select the menu where the new Sales order picking mobile device menu is located.

Select the _Sales Pick_ menu item and initiate the pick. After selecting the menu and entering the first Work ID, the user will be presented with the Pick step. Complete the pick until the Put to Stage step for Work ID 1 and repeat the same for Work ID 2.

Next, load the two picked pallets to the truck. Select the _Sales Loading_ menu item to start the loading process. After selecting the menu and entering the first Work ID, the user will be presented with the Pick step. Complete the loading of Work ID 1 and repeat the same for Work ID 2.

These two Work IDs will now be closed (loaded).

### Step 3: Confirm the outbound shipment

Navigate to _Sales and Warehouse management - Loads - Load planning workbench_ and select the click on the Load you have created with this demo to view the load details.

On the top ribbon, select _Ship and receive_ and under _Confirm_ section, press _Outbound Shipment_ to initiate the confirmation.

New _Ship confirm_ form will be presented to the user indicating that _Ship confirm will split Load_, where the user has the option to continue or cancel.

For the purpose of this demo, select option _Split quantity to new load_ and press _OK._

The system will show a message to the user &quot;The shipment for load %1 has been confirmed&quot;.On the main screen, the user is presented with the newly created Load after a refresh.

You can also confirm that transaction relations have been updated accordingly.

- --The remaining (unprocessed) Shipment and Shipment lines are updated with the new Load ID.
- --Sales order is linked to the new Load ID.
- --Original Load does not include the remaining Load lines.
- --Remaining Work has been updated with the new Load ID.
- --The Wave remains the same.
- --Status of the new Load is also correctly updated (if work is _In process_, Load status will also be _In process_)

## Notes and tips

- --_Allow Load Split During Ship Confirm_ can also be enabled after the Load has been created with the Load template parameter turned off, but before the loading process has started. Simply navigate to the desired Load and on the header view enable the parameter.
- --_Split quantity to new load_ option is working also if some of the remaining Work headers are _In process_ status, hence the functionality can be used even if workers are already executing the pick orders.
- --If _Cancel unfulfilled quantity_ is selected when there is remaining Work in _Open_ or _In progress_ status, the user will be presented with an error _&#39;Unable to cancel remaining qty for Load. Work_ exists for load&#39;
- --If Cancel unfulfilled quantity is selected when there is no Work remaining (but unreleased Load lines are on the Load), the user will be presented with an error _&#39;The shipment for load could not be confirmed because the quantity for item exceeds the percentage that is defined for under delivery._
  - This can be avoided if _Under delivery_ percentage on the unreleased Load line is adjusted to 100%. This will not move unreleased to a new Load, but with confirm the current Load with under delivery. The origin order cannot be re-released in this case and will have to be handled otherwise.
