# Warehouse slotting

# Released in version 10.0.1

#

# About

Slotting allows users to gather consolidate demand by item and unit of measure from orders, in status either ordered, reserved, or release. Once demand has been generated, it can be located to locations that will be used for picking based on quantity, unit, physical dimensions, fixed locations, etc. Once the slot plan has been established, replenishment work can be created to bring the appropriate amount of inventory to each location.

This functionality allows for warehouse managers to plan the picking locations in the warehouse intelligently prior to releasing order to the warehouse and creating picking work.



# Setup

## Slotting Unit of Measure Tiers

Unit of measure tiers allow multiple units of measure to be grouped together for the purposes of slotting. For example, if there are multiple sizes of boxes that all get picked from the same box picking area, one tier could be created for all the sizes of boxes.

The header requires the following fields:

- Slotting unit of measure tier id – EaBoxPl
- Description – Each Box Pallet

A line must be created for each unit of measure that should be part of the tier. Each line requires:

- Unit – Box
- Description – Will be auto populated once unit is entered – Box
- Unit class – Will be auto populated once unit is entered – Quantity

## Directive code

Navigate to _Warehouse management_ - _Setup_ - _Directive code_ and create a new directive code - Slotting

## Slotting Templates

Navigate to _Warehouse management_ - _Setup_ - _Replenishment_ - _Slotting templates_. Each slotting template controls how inventory gets assigned to location for a specific warehouse.

In the header of the template the following must be specified:

- Slotting template Id – _61_
- Description – _61_
- Slot template demand – Currently only sales order demand is supported
- Slot demand strategy – _Ordered_
  - Ordered – The full ordered quantity on the sales order will be considered as demand
  - Reserved – Only the sales order line quantities that are reserved (physical and ordered) will be considered as demand
- Warehouse – _61_
- Allow wave demand to use unreserved quantities - _Yes_

A query can also be specified to narrow the scope of what demand is evaluated.

### Slotting template details

Once the template is created, a line must be created for each slotting specification.

The following fields need to be populated:

- Line – _1_
- Description – _Fixed location_
- Minimum quantity – The minimum quantity of demand that is required for the line - _1_
- Maximum quantity – The maximum quantity of demand that is valid for this line - _1000000_
- Unit – The unit of measure the minimum and maximum quantities refer to - _blank_
- Slotting Unit of Measure Tier Id – What unit(s) of measure of demand are valid to be used on this line (See Slotting Unit of Measure Tiers) – _EaBoxPl_
- Assign slot criteria – _Consider qty_
  - Assume Empty – Assumes that all locations in the picking area are empty, does not check the locations for inventory.
  - Consider Qty – Checks if the locations in the picking area already contain inventory. Skips any locations that are not empty
- Directive code – Location directive to use when finding the picking location of the replenishment work- _Slotting_
- Overflow location – Location inventory will be put to if the quantity fails to find a location during processing of the line - _Empty_
- Allow let up – When enabled, if any demand couldn&#39;t be slotted, movement work will be created to take inventory out of locations that have inventory, but nothing was slotted to. The template is then run again, ignoring the inventory in the locations. Works best when Assign slot criteria = Consider qty. – _Yes_
- Use fixed locations – _Only fixed locations for the product_
  - Fixed and non-fixed locations – Will not restrict to only using fixed locations
  - Only fixed locations for the product – Will only slot to locations that are fixed locations for the product
  - Only fixed locations for the product variant – Will only slot to locations that are fixed locations for the product variant

Create a second template line:

- Line – 2
- Description – Other
- Minimum Qty – 1
- Maximum Qty – 1000000
- Unit – empty
- Slotting unit of measure tier ID – EaBoxPl
- Assign slot criteria – Consider Qty
- Directive code – Slotting
- Allow let up – Yes
- Use fixed locations – Fixed and non-fixed locations

In the query for the second line, specify the criteria for what location(s) the demand this line can be slotted to – _Location profile ID = PICK-06_

## Location Directives

### Pick

Create a new replenishment location directive for slotting picks.

- Name – Slotting Pick
- Work type – Pick
- Site – 6
- Warehouse – 61
- Directive code – Slotting

Create a new line

- From quantity – 0
- To quantity – 1000000

Create an action:

- Name – Bulk
- Strategy – None
- Query – Specify Zone ID = BULK

# Process

## Create demand

Before slotting can take place, demand must first be created.

Navigate to _Sales and Marketing_ - _Sales orders_ - _ All sales order_. Click New to create a new sales order. Enter US-007 as the customer. In the _General_ section specify warehouse 61.

Add a new line to the sales order, item L0101, quantity 20 ea. Add a second line for item T0100, quantity 8 ea

Create another sales order, customer US-008, warehouse 61, add item T0100, quantity 1 pl.

## Slotting

### Generate demand

Navigate to _Warehouse management_ - _Setup_ - _Replenishment_ - _Slotting templates_ and select the slotting template created earlier. Click on &#39;Generate demand&#39; in the action bar. This will evaluate all demand that is in the system and matches the slotting template query. The total demand across all order will be consolidated into one line per Qty/UOM.

Note- If desired, demand can be edited manually, or imported in from an external system using data management. Whatever is in the slotting demand will be used in the next step, regardless of where it came from.

### Locate demand

Once demand has been generated, click on &#39;Locate demand&#39; in the action bar.

The slotting process will run, and the results can then be viewed by clicking on &#39;Slotting Plan&#39; in the action bar.

The slotting plan shows the location that each item/qty was assigned, as well as if overflow was used, if let up work was created, and what template line was used. Any demand that was not able to be slotted will be highlighted in red.

### Create replenishment

After the slotting plan has been created, you can click on &#39;Run Replenishment&#39; in the action bar to create replenishment based on the plan.

Location directives to use will be identified based on the directive code specified on each template line.

# Appendix

## Automatic slotting

A menu item exists to run slotting automatically.

Navigate to _Warehouse management_ - _Replenishment_ - _Run slotting_. In this menu item you can specify what slotting steps you want to run; one or all:

- Generate Demand
- Locate Demand
- Create Replenishment Work

You can also specify what slotting template to use.

This menu item can have a recurrence set to run automatically as desired.
