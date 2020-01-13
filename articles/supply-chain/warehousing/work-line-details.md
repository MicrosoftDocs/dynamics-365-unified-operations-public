# Work line details

# Released in version 10.0.0
#
# About

New Work lines form offers additional overview of work lines for warehouse management team. The user can switch between showing all work lines or only open work lines for a specific company. The form shows all important details that a supervisor would require to successfully manage and adjust workflow within the warehouse, namely work status, item number, location, work quantity, load id, shipment id, and others.

The user can change the location of any opened work line, which will override location directive setup,  to cancel any work line straight from the form or to adjust quantities. Further, there is also the ability to view transactions behind each work line straight from the form.

# Setup

Navigate to _Warehouse management_ - _Work_ - _Work line details_.

# Demo

## Create picking work

Before work is created, make sure that your warehouse setup will create work as expected.

Navigate to _Accounts receivable_ - _Sales orders_ - _ All sales order_. Click New to create a new sales order. Pick any customer. In the _General_ section specify Warehouse 51.

1. Sales order 1 (any customer): Add a new line to the sales order, item M9200, quantity 20 ea.
2. Sales order 2 (any customer): Add a new line to the sales order, item M9200, quantity 25 ea. Add a second line for item M9202, quantity 10 ea.

Before releasing the orders to warehouse, ensure there is enough inventory on the pick locations for all the items on the orders.

Default Contoso data should support this scenario but review the Location Directive setting to be sure what picking locations are used for sales order picking. You can create manual movements, use replenishment, or any other flow if needed to adjust the inventory.

Reserve the inventory and Release it to warehouse. Two different Work IDs should have been created.

## Change location

Navigate to _Warehouse management_ - _Work_ - _Work line details_ and open the form.

Select a work line and click on &#39;Change location&#39; in the action bar. Enter the new location that should be associated with the work line. If the location you selected has available inventory (for a pick) or if it matches the location type validation (for a put), the location on the work line will be updated.

## Cancel work line

Navigate to _Warehouse management_ - _Work_ - _Work line details_ and open the form.

Select a work line and click on &#39;Cancel work line&#39; in the action bar. Cancel full quantity for this example but be aware that you can also cancel only part of the quantity.

Note that the first Pick work line has been cancelled.

Let&#39;s continue with this example and cancel only a partial quantity of the second pick line. Select the second line on the Work line details form and press &#39;Cancel work line&#39;. In the new screen, specify qty 7ea.

Now, the new line will have qty 3, as we have cancelled 7ea (10ea - 7ea).

Note that only the Work created quantity field on the matching Load line will be changed as a result. The user must take other measures to remove the obsolete quantity from the load line, otherwise it won&#39;t be possible to be ship confirmed (unless under delivery is set up correctly).
