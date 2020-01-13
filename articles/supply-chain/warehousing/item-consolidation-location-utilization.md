# Item consolidation - location utilization

# Released in version 10.0.6
#
# About

The new location utilization form serves as a tool to warehouse managers to easily view and filter the volumetric utilization of location across the warehouse. If deemed necessary, the user can select locations and create inventory movement work straight from the form in order to consolidate items, better utilizing warehouse space.

# Setup

## Released product

Navigate to _Product information management - Products - Released products_ and select M9201. Click on Physical dimensions in the Manage inventory – Warehouse section of the ribbon.

Create a new record and specify unit = ea. The rest of the fields should auto populate.

## Location profile

Navigate to _Warehouse management_ _-_ _Setup -  Warehouse - Location profiles_ and select FLOOR-05.

Ensure the &#39;Enable item in location&#39;, &#39;Enable location status&#39; options are enabled. If they were not already enabled, run the warehouse location status consistency check after enabling.

Expand the Dimensions FastTab, and set:

- Volume utilization percentage: 100
- Volumetric method used for inventory location: Use location volume
- Actual location height: 10
- Actual location width: 10
- Actual location depth: 10
- Maximum weight: 100

# Process

Open the mobile device, log in to warehouse 51, and navigate to _Inventory - Adjust In._

Enter Loc = LP-001, make up a new LP, and Item = M9201. Enter 10 ea as the quantity and confirm the adjustment.

Using the same menu item, enter Loc = LP-002, make up a new LP, and Item = M9201. Enter 15 ea as the quantity and confirm the adjustment.

Navigate to _Warehouse management - Periodic tasks - Item Consolidation_. Enter warehouse 51.

You&#39;ll see two records displayed, one for each location that you adjusted item M9201 into. The Utilization percentage column shows the volumetric usage of each location.

To consolidate inventory, select all the locations you want to consolidate, and click on &#39;Consolidate Inventory&#39; in the action bar. Enter the location to consolidate into, and the movement type code to use.

The system will create one work ID for each move that needs to be completed. If you enter one of the locations already containing inventory, then only one work ID will be created. If you enter a new location, then two will be created.
