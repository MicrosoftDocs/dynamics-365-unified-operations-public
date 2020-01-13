# System Directed Work Sequencing

# Released in version 10.0.0

#

# About

System directed work sequencing setup offers the ability to sort and filter which work orders will the system present to the user for execution. This functionality solves scenarios where additional criteria is required to drive warehouse picking process, e.g. by the time of shipping, picking zone, Location profile, or even based on a combination of different criteria.

This functionality extends the current system directed picking with new System directed query order where the user can set up a sequence and a query or multiple queries which will evaluate all created work orders. It will therefore capture and present only the work orders that meet the specified criteria of the mobile device menu item setup.

Warehouse picking processes can therefore be further optimized as this feature identifies work orders that match the defined criteria and assigns those to the correct mobile device menu item, and consequently presents them to a worker based on a specific skillset, picking equipment, or any other requirement.

NOTE: If different criteria is needed, multiple mobile device menu items will have to be used.

# Setup

Warehouse used: 51

Data: Default Contoso data

## Enable system directed work sequencing

Navigate to Warehouse parameters - General - Mobile device and press button _Enable system directed work sequencing_. This will enable the new System directed query orders.

## Mobile device menu item

Navigate to _WMS_ - _Setup_ - _Mobile device_ - _Mobile device menu_ items and find the MD menu item with Directed by set as System directed. If not available, create a new one and make sure to use the correct Work class.

In standard Contoso environment, **Sales Picking – System** mobile device menu item is already created and can be used for this purpose.

Select **System directed work sequence queries** button in the top blue ribbon to open the new form. There will be an existing line called _Auto generated query_ which you can delete.

1. Create New Line:

1.
  - --Sequence number - _1_
  - --Description field - _Work quantity less than 20 and descending_

After saving, select Edit Query button and on the Sorting specify the following line:

- --Table – _Work lines_
- --Derived table – _Work lines_
- --Field – _Work quantity_
- --Search direction – _Descending_

1. If only Work with specific criteria should be included in the sequencing, you can specify that on the Range. In this example, we will want to include only Work with less than 20 eaches (lowest unit of measure).

On the same Sys Dir Order Query line, select Edit Query button again and on the Range tab, add a new line. Note that there are already some lines included which should not be removed.

- --Table – _Work lines_
- --Derived table – _Work lines_
- --Field – _Inventory work quantity_
- --Criteria – \&lt;_20 (less than 20)_

This is now the criteria based on which the mobile device menu item will be fed the eligible work. If more Query criteria lines are used, the system will first use the Query line with lowest sequence number.

Therefore, all eligible Work for Sequence number 1 will first be fed to the user, and after that all Work for Sequence number 2 will be presented to the user. Hence if certain Range and Sorting need to be used in tandem, they should be specified on the same System directed work sequence query.

Note that this setup will capture any work that has at least one line with less than 20ea. Hence, if the same Work has another line with exactly 20ea or more than 20ea, it will also be valid, as long as at least one line has less than 20ea.

## Location directives

Ensure that the Location Directives will capture the items on the Sales orders. Create a new one or edit the Location Directive Action on a pre-created LD **51 Pick** to remove the Location profile Range restriction if any. Save the change.

# Demo

## Create picking work

Before system directed picking is executed, some outbound work should be created. Based on the specified System directed work sequence queries, create 4 different Work IDs, with the below specifications.

Navigate to _Accounts receivable_ - _Sales orders_ - _All sales order_. Click New to create a new sales order. Pick any customer. In the _General_ section specify Warehouse 51.

1. Sales order 1 (any customer): Add a new line to the sales order, item M9200, quantity 20 each (10 boxes).
2. Sales order 2 (any customer): Add a new line to the sales order, item M9200, quantity 5 ea. Add a second line for item M9201, quantity 1 ea.
3. Sales order 3 (any customer): Add a new line to the sales order, item M9200, quantity 7 ea. Add a second line for item M9202, quantity 8 ea.
4. Sales order 4 (any customer): Add a new line to the sales order, item M9200, quantity 25 ea. Add a second line for item M9202, quantity 10 ea.

Before releasing the orders to warehouse, ensure there is enough inventory on the pick locations for all the items on the orders.

Default Contoso data should support this scenario but review the Location Directive setting to be sure what picking locations are used for sales order picking. You can create manual movements, use replenishment, or any other flow if needed to adjust the inventory.

Reserve the inventory and Release it to warehouse. Four different Work IDs should have been created.

1. Work ID 1 – 20 ea
2. Work ID 2 – 6 ea (sum of both lines)
3. Work ID 3 – 15 ea (sum of both lines)
4. Work ID 4 – 35ea (sum of both lines)

## Mobile device flow execution

Before executing the flow on the mobile device, ensure that only the created work is in Open status for Warehouse 51 and Work order type Sales order. If not, the results of the test may vary as the System direct picking will include all eligible work.

Enter mobile device and select the menu where the System Directed Query Order is located (_Outbound - Sales picking – System_). Based on our setup, the system will feed the user Work, sorted from highest Work line quantity to lowest, but less than 20 each on a single line.

Remember that this setup will capture any work that has at least one line with less than 20ea. Hence, if the Work has another line with exactly 20ea or more than 20ea, it will also be valid.

Select the _Sales Picking – System_ menu and initiate the pick. After selecting the menu, the user will be presented with the Pick step of the Work ID 4. This is due to the System Directed Query Order setup, where we have specified that Work should be sequenced based on Work line Quantity - Descending.

Complete the necessary Pick and Put to Close the Work ID.

Next, Work ID 3 is presented to the worker. One of it&#39;s work lines is next in the sequence based on Work line Quantity. Complete the Pick and Put to Close the Work ID.

Next, Work ID 2 is presented to the worker. This work&#39;s pick line is next in the sequence based on our setup. Complete the Pick and Put to Close the Work ID.

No work should be presented to the user after this completion. Work ID 1 is not eligible for this mobile device menu item, because it has been specified on the Query that only Work headers with Work lines less than 20 should be considered.

# Appendix

The **System directed work sequence queries is**  **inclusive** , which is important to know with certain setups. For example, if the user wishes for a certain menu item to process only work with work unit in eaches and it specifies that on the Range, all Work with at least one Work line with Work unit eaches will be fed to the user. This will therefore also include all Work with other Work units besides _eaches_ (box or pallet) and it will not exclude those. It will exclude only Work where no Work lines have Work Unit set as each.

- --Hence, in the example from this demo, the Work ID 4 was also captured by the query. It was created with 2 lines, one for 25 ea and another one for 10 ea. The Work was still be assigned to the user because at least one Work line had less than 20 ea. This can be prevented with Work breaks, depending on the scenario.
