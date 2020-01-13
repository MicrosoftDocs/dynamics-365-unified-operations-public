# Zone threshold replenishment

# Released in version 10.0.2
#
# About

Zone based replenishment is a feature which utilizes min/max replenishment strategy but evaluates entire warehouse zones, if set, instead of just individual locations. This gives companies the ability to better and faster determine whether additional inventory is needed within a picking zone.

The setup for the new feature is very similar to location-based replenishment. As new replenishment template is created for min/max replenishment, the user can simply specify whether the threshold should be evaluated per Location or per Zone. In case of zones, specific zones are then added to the Zone selection query and those will be evaluated by the newly created replenishment template when processed.

Just like location-based min/max replenishment, the zone-based min/max replenishment is based on setting up a minimum threshold of inventory that triggers the creation of replenishment work order for selected items and item variants. In return, replenishment will be created for quantity that increases inventory up to the desired zone maximum threshold.

Key difference with current location-based min/max replenishment is that zone replenishment does not require fixed locations to evaluate whether locations should store a certain item or not. Zone based replenishment therefore allows you to use min/max replenishment without fixed locations for each item or item variant within the warehouse. When the quantity in the zone falls below the specified minimum, replenishment will be created, and location directives will find what specific location to put the inventory to.

# Setup

## Directive codes

Navigate to _Warehouse management -  Setup -Directive codes_ and create a new directive code

- Directive code – _Zone replen_
- Directive description – _Zone replenishment_

## Replenishment template

Navigate to _Warehouse management  - Setup - Replenishment - Replenishment_ templates and create new Replenishment template with Replenishment type set as Min/max.

In **Overview** section, enter the following:

- --Replenish template – _Zone min/max replen_
- --Description – _Zone min/max replenishment_
- --Replenishment type – _Minimum or maximum_

In the **Replenishment template details** , the following setup must be specified:

- --Sequence number 1
- --Description – _Pick zone replenishment_
- --Replenishment unit – _each (ea)_
- --Directive code – This will tie Replenishment template with the Location directive put - _Zone replen_
- --Minimum quantity – the minimum quantity of the item within the zone. The quantity at which the replenishment will be triggered - _50_
- --Maximum quantity – the maximum quantity of the item within the zone – _150_
- --Unit – The unit the min and max relate to - _ea_
- --Demand increment – _Round up_
- --Replenish empty fixed locations – _Yes_
- --Replenish only fixed locations – _No_
- --Product query mode – _Product query_
- --Warehouse - _61_
- --Threshold scope – This will determine whether the template should evaluate Locations or Zone - _Zone_

In the **Select products query** , select item A0001.

In the **Select zones to replenish** query, select zone FLOOR.

## Location directives

Unlike Location based min/max replenishment, zone-based replenishment will require the setup of Put location directive, because the system evaluates the whole zone instead of just the outbound work pick location and inheriting the replenishment put location from there.

Navigate to Warehouse management _-_ Setup _-_ Location directives

1. Create new **Pick Location directive** for Work order type Replenishment:

- --Name – _Zone pick_
- --Work order type – _Pick_
- --Site – _6_
- --Warehouse – _61_
- --Directive code – _leave empty_
- --Multi SKU – _No_

In the lines section, create a new Line with the following setup:

- --Sequence number – _1_
- --From quantity – _0_
- --To quantity – _10000000_
- --Locate quantity – _None_
- --Allow split – _Yes_

In the Location directive Actions, create a new line with the following setup:

- --Sequence number – _1_
- --Name – _Pick from bulk_
- --Fixed location usage – _Fixed and non-fixed locations_
- --Strategy – _None_

On the Location Directive Actions Query, select the locations you want to replenish from:

- --Table: Locations; Derived table: Locations, Field: Zone ID; Criteria: BULK

1. Create new **Put Location directive** for Work order type Replenishment:

- --Name – _Zone put_
- --Work order type – _Put_
- --Site – _6_
- --Warehouse – _61_
- --Directive code – _Zone replen –_ here the Replenishment template line is linked with the Put Location directive
- --Multi SKU – _No_

In the lines section, create a new Line with the following setup:

- --Sequence number – _1_
- --From quantity – 0
- --To quantity – _1000000_
- --Locate quantity – _None_
- --Allow split – _Yes_

In the Location directive Actions, create a new line with the following setup:

- --Sequence number – _1_
- --Name – _Zone put_
- --Fixed location usage – _Fixed and non-fixed locations_
- --Strategy – _Consolidate_

On the Location Directive Actions Query, specify the Zone where replenishment should occur to. This should be the same as Zone specified on the Replenishment template:

- --Table: Locations; Derived table: Locations, Field: Zone ID; Criteria: FLOOR

# Demo

## Inventory on-hand

1. Ensure there is on-hand inventory for item A0001 on two different locations within the pick zone specified on the replenishment template line. This is to simulate how the calculation occurs for the whole zone, instead of only for a single location. The total quantity should be under the Minimum quantity specified on the Replenishment template line. Use any of the warehouse processes to adjust inventory if needed.
2. Ensure there is enough inventory for item A0001 on the bulk location where the replenishment work should pick the items from.

## Run Zone min/max replenishment

Navigate to Warehouse management _-_ Replenishment _-_ Replenishments

In the Records to include section, click on Filter, and select the Zone min/max replen Replenishment template. Click OK to run the replenishment template.

Replenishment work will be created to pick inventory from the BULK zone and replenishment it to the FLOOR zone.

# Appendix

- To setup Replenishment work to go to the desired zone you can link the replenishment template lines and location directives through one of two ways:
  - The first way is to edit the location directive header query and filter the replenishment template lines selected.
  - The second way is to use a directive code on the replenishment template line and match it to the Put location directive.
- If dynamic locations are used, replenishment work will be created to the first available location, or to a location that already contains inventory, if the location directive action is setup to use the Consolidate strategy.
- If fixed locations are used and replenished, standard min/max replenishment should be used.
