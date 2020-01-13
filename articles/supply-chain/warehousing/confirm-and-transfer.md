# Confirm and Transfer

# Released in version 10.0.1

# About

The confirm and transfer features allows users to ship loads out of the warehouse prior to all work associated with the load being completed. When ship confirming, if all of the load lines are not fully picked, then the user will be prompted to either split off the remaining quantities onto a new load or cancel the quantities that have not been completed.

With the setup to allow splitting of loads you can handle scenarios where already planned and partially loaded Loads need to be adapted due to new or changing circumstances.

New logic has been added to the client to allow a Load that is partially loaded to be closed and ship confirmed. If necessary, and if allowed by the setup, all remaining shipments and load lines, this includes full or partial line quantities, will be rolled over to newly created load and shipment. New shipment and load are automatically created based on initial Shipment/Load creation criteria and will keep the main attributes unchanged. Further, there is also an option to auto cancel the remaining quantities if work order has not been created yet and if deemed necessary by the user.

This functionality supports the scenario in which all product cannot fit onto a truck or where some of the load should leave the warehouse before the remainder is ready for shipping. The left-over product can therefore be transferred to a new load and consequently to a new truck. This feature can be used with loads that are otherwise intended to allow only full load shipping and therefore gives more flexibility to transport managers for solving nonstandard or unforeseen scenarios.

Please note that this functionality is not the same as transport load feature as transport load feature should be used in warehouses that never are able to plan and create load prior to picking but do loading of the available transportation space after picking is completed.

Confirm and transfer feature is used where loads are planned and created but where sometimes exceptions occur where load does not fit the available transport e.g. truck.



When splitting, using Confirm and Transfer feature,  a new load and shipment(s) will be created with all of the same attributes as the current load/shipment, with the exception of the load status, which will be recalculated based on the work status. The user will receive a message that a new load has been created along with the new load ID. Load lines, work headers, and work lines that were split will be updated with the new load and shipment information. If an entire shipment is being split, then the shipment will be maintained and only the load references will be updated. If the shipment needs to be split, then a new shipment will be created.

When canceling, any load line quantities that have not been picked, and do not have non-canceled work associated with them will be removed from the load. If there is in process work, then the user will only be able to split, not cancel.

A load will be eligible to be split if any load lines have picked quantities, the load status is less than loaded, there are no LoadLineWorkLineDetails (created as a result of LP consolidation on the staging location, this action is not supported by confirm and transfer), and there is no inventory currently on a packing location awaiting packing (Inventory picked to the pack station, but not yet packed is not supported by confirm and transfer).



# Setup

## Load templates

Navigate to _Advanced warehouse management_ _-_ _Setup - Loads - Load templates_. Select the template to be used with this functionality and enable the _Allow Load Split During Ship Confirm_ parameter.

For this demo, I have enabled this on the standard Contoso _20&#39; Container_ Load template. If preferred, create a new Template with desired configuration.

Every Load that will have been created with this Load Template will now inherit the _Allow Load Split During Ship Confirm_ functionality.

There are two options available to the user when this functionality is used:

- --Split quantity to new load
- --Cancel unfulfilled quantity

In this demo, I will show the _Split quantity to new load_. No additional setup is needed for the other option, as it is a user decision at execution.

## Work templates

Navigate to Warehouse management _-_ Setup _-_  Work _-_  Work templates and find the Work template that will be used with this function. For this demo, standard Contoso Work template **51 Pick to stage** was used.

The following setup is not required, but it ensures that Work will be broken by Shipment, to easier simulate the demo scenario. This can also be achieved differently.

Select the correct Work template, click on _Edit query_ and navigate to _Sorting_tab. Add a new line with the following criteria:

- --Table – _Temporary work transactions_
- --Derived table – _Temporary work transactions_
- --Field – _Shipment ID_
- --Search direction – _Ascending_

After saving, select the _Work header breaks_ blue ribbon button and _Group by_ Shipment ID. Save selection and close the form.

# Demo

This demo will simulate a scenario where picking process has not been fully completed and where the already picked items should be loaded to a truck and shipped regardless of the status of the remaining items. The user will be able to _split_ the unpicked Load lines to a new Load and all data relationship will be updated accordingly.

## Create Load with multiple Load lines

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

## Mobile device flow execution

Enter mobile device and select the menu where the new Sales order picking mobile device menu is located.

Select the _Sales Pick_ menu item and initiate the pick. After selecting the menu and entering the first Work ID, the user will be presented with the Pick step. Complete the pick until the Put to Stage step for Work ID 1 and repeat the same for Work ID 2.

Next, load the two picked pallets to the truck. Select the _Sales Loading_ menu item to start the loading process. After selecting the menu and entering the first Work ID, the user will be presented with the Pick step. Complete the loading of Work ID 1 and repeat the same for Work ID 2.

These two Work IDs will now be closed (loaded).

## Confirm outbound shipment

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

# Appendix

- --_Allow Load Split During Ship Confirm_ can also be enabled after the Load has been created with the Load template parameter turned off, but before the loading process has started. Simply navigate to the desired Load and on the header view enable the parameter.
- --_Split quantity to new load_ option is working also if some of the remaining Work headers are _In process_ status, hence the functionality can be used even if workers are already executing the pick orders.
- --If _Cancel unfulfilled quantity_ is selected when there is remaining Work in _Open_ or _In progress_ status, the user will be presented with an error _&#39;Unable to cancel remaining qty for Load. Work_ exists for load&#39;
- --If Cancel unfulfilled quantity is selected when there is no Work remaining (but unreleased Load lines are on the Load), the user will be presented with an error _&#39;The shipment for load could not be confirmed because the quantity for item exceeds the percentage that is defined for under delivery._
  - This can be avoided if _Under delivery_ percentage on the unreleased Load line is adjusted to 100%. This will not move unreleased to a new Load, but with confirm the current Load with under delivery. The origin order cannot be re-released in this case and will have to be handled otherwise.
