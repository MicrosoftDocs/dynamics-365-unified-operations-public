# Outbound sorting

# Released in version 10.0.4
#
# About

With this functionality, several industries will experience easier handling of small containers and will enable the warehouse workers to better plan and organize pallet capacity within the truck.

With the outbound sorting  you now can sort packed containers to a correct pallet after packing station and to build a packing hierarchy.

This functionality allows for the building of pallets from containers packed through the [Packing](https://bluehorseshoe.sharepoint.com/SitePages/Packing.aspx)  functionality. The container is not sent to the final shipping location as it would be in the original Packing flow. Instead, this functionality allows the user to close the container and move it to a Sort type location. They can then sort containers onto positions, each position has a license plate. Once the containers have been sorted, work can be created to send the whole LP to the final shipping dock or stage locations based on Location Directives/customer requirements. The closing of the sort position can also immediately move the inventory to the final shipping location and pick it to the order.

# Setup

For this demo, standard Contoso data is used with warehouse 62 with some additions noted below.

## Location type

Navigate to _Warehouse management_ _-__Setup_ _-_ _Warehouse_ _-_ _Location types_ and create a new location type:

- Location type = SORT
- Description = Sort

## Warehouse management parameters

Navigate to _Warehouse management_ _-_ _Setup_ _-_ _Warehouse management parameters_, General – Location types FastTab. Enter the new SORT location type as the Sorting location type.

## Location profile

Navigate to _Warehouse management - Setup - Warehouse - Location profiles_ and create new Location profile for Sorting location.

In the **header** of the new profile, name the new profile:

- **--** Location profile ID – _SORTING_
- **--** Name – _Sorting_

In the **General** tab, the following must be specified:

- **--** Location format – _ASRB_
- **--** Location type – _SORT_
- **--** Use license plate tracking – _Yes_
- **--** Allow mixed items – _Yes_
- **--** Allow mixed inventory statuses – _Yes_

This profile will be used in a new parameter under the Advanced Warehouse parameters form​​.

## Locations

Navigate to _Warehouse management_ _-_ _Setup_ _-_ _Warehouse_ _-_ _Locations_ and create a new _Location_:

Unselect _Generate check digits for_ locations and click _New._ Assign the following criteria:

- **--** Warehouse – _62_
- **--** Location – _SORT_
- **--** Location profile ID – _SORTING_

## Outbound sorting template

The Outbound sort template determines if work will be created out of Sort location and how sorting will take place, either manual or automatic.

For Pallet building after packing station

Navigate to _Warehouse Management_ _-_ _Setup_ _-_ _Packing_ _-_ _Outbound sorting template_ and create a new sorting template.

In the **header** of the new template, specify the following:

- **--** Sort template ID – _AutoWork_
- **--** Description – _Auto Work Creation_
- **--** Outbound sorting template type – _Container_
- **--** Warehouse - _62_
- **--** Location – _SORT_

In the **general** tab, specify the following parameters:

- **--** Sort verification – _Position scan –_ the type of verification used when sorting containers to the sort position
  - **oo** None
  - **oo** License plate scan
  - **oo** Position scan
- **--** Create work on position close – _Yes_
- **--** Position assignment - Automatic

In the top ribbon, select **Edit Query** to specify the criteria used for this Sort template. Under _Sorting_ tab add a new line with the following setup:

- --Table – _Shipments_
- --Derived table – _Shipments_
- --Field – _Carrier service_
- --Search direction – _Ascending_

This will enable the **Outbound sorting template breaks** button in the top ribbon of the template form. Select it to open the new form. Check the Group by field box to group by Shipments – Carrier service.

## Container packing policies

Navigate to _Warehouse management_ _-_ _Setup_ _-_ _Containers_ _-_ _Container packing policies_ and create a new Container packing policy.

In the **header** , specify the following:

- --Container packing policy – _Sort_
- --Description – _Sort_

In the **Overview** fast tab, specify the following parameters:

- --Warehouse – _62_
- --Default location for sorting – _SORT_
- --Weight unit – _kg_
- --Container closing policy – _Automatic release_
- --Container release policy – _Assign container to outbound sorting position_

## Packing profiles

Navigate to _Warehouse management - Setup - Packing - Packing profiles_ and create a new Packing profile to be used with sorting functionality.

New Packing profile should be created with the following criteria:

- --Packing profile ID – _Sort_
- --Description – _Sort_
- --Container packing policy - _Sort_
- --Container ID mode – _Auto_
- --Container type – _Box-Large_
- --Auto create container at container close – _No_

## Mobile device menu items

Navigate to _Warehouse management - Setup - Mobile device - Mobile device menu items_ and create a new menu item to be used for sorting.

In **Header** , specify the following:

- --Menu item name – _Pallet build_
- --Title – _Pallet build_
- --Mode – _Indirect_
- --Use existing work – _No_

In **General** fast tab, the following setting can be specified:

- --Activity code – _Outbound sorting_
- --Outbound sorting template ID – _AutoWork_

## Mobile device menu

Navigate to _Warehouse management - Setup - Mobile device -Mobile device menu_ and add the newly created menu item to the Outbound menu.

## Location directives

Navigate to _Warehouse management_ _-_ _Setup_ _-_ _Location directives_ and change the work order type to Sorted inventory picking.

Create a new location directive:

**Header**

- Seqeunce – 1
- Name – Baydoor
- Work type – Put
- Site – 6
- Warehouse – 62

**Lines:**

- Sequence – 1
- From – 0
- To – 1,000,000

**Location directive actions**

- Sequence – 1
- Name – Baydoor

Edit the query for the action to specify location &#39;Baydoor&#39;

Create a copy of this directive, name &#39;Baydoor Mutli&#39; and enable the &#39;Multiple SKU&#39; button on the header.

## Work classes

Navigate to _Warehouse management - Setup - Work - Work classes_and create new Work class for Sorting:

- --Work class ID – _Sort_
- --Description – _Sort_
- --Work order type – _Sorted inventory picking_

## Work templates

Navigate to _Warehouse management_ _-_ _Setup_ _-_ _Work_ _-_ _Work templates_, change the work order type to Sorted inventory picking. Create a new work template.

**Header**

- Sequence – 1
- Work template – Sort
- Work template description – Sort

Create two lines, a pick and a put. Both use the _Sort_ work class.

# Demo

This demo will simulate a scenario where the packed containers should be automatically sorted to different positions (pallets) after the packing station, based on the shipping carrier service. After all items from the Load are packed and sorted by address, the pallets will be moved to the baydoor.

## Picking

Create a new sales order:

- Customer = US-005
- Warehouse = 62
- Shipping carrier = Air cargo
- Carrier service = Air

Add a line for item A0001, quantity 2. Reserve the order line and release to warehouse.

Complete the created picking work using the mobile device to the pack station.

Create a second sales order:

- Customer = US-006
- Warehouse = 62

Add a line for item A0001, quantity 1. Specify Mode of delivery = Flowe-STD

Add a second line for item A0002, quantity 1. Specify Mode of delivery = Air C-Air

Reserve both lines and release to warehouse.

Complete the created work using the mobile device to the pack station

## Packing

Open the pack form, and specify:

- Warehouse – 62
- Location – Pack
- Packing profile ID – Sort

Enter the target LP used when picking the first sales order. Create a new container, accept the defaults.

Pack quantity 1 of A0001 into the container. Close it, using the system weight.

 The container will be moved to the &#39;SORT&#39; location and is ready for sorting

Create a second container, pack the remaining 1 of A0001 into it. Close it, using the system weight.

Enter the target LP used when picking the second sales order. Create a new container, accept the defaults.

Pack quantity 1 of A0001 into the container. Close it, using the system weight.

Create a second container, pack quantity 1 of A0002 into the container. Close it, using the system weight.

## Sorting

Open the Pallet build menu item on the mobile device.

Enter the first container ID from the first sales order. Since no sort positions currently exist, the user must specify one. Specify SP01.

Because there is no license plate currently associated with SP01, the user must specify one. Enter PLP01

Sort position validation is enabled, so the user is required to enter the sort position ID again.

Navigate to _Warehouse management_ _-_ _Packing and containerization_ _-_ _Outbound sorting position assignments._

This form will show all of the sort positions that are currently active, the LP associated with each, and what containers are in the sort position. Observe that one sort position currently exists, it is using a criteria of Shipment – Carrier service = Air.

The container that has been sorted is shown in Sort position transactions grid.

On the mobile device, scan the second container ID associated with the first order. Because the sorting template is setup to sort automatically, and there is already a sport position that exists with matching criteria, the user is automatically directed to the correct sort position. They only need to scan the position ID to confirm they&#39;re putting the inventory to the right place.

Scan the container containing A0001 from the second order. Because the carrier service is different, the user is prompted to enter and new sort position (use SP02) and assign a license plate to that position (PLP02).

Scan the container containing A0002 from the second order. Because the carrier service matches the first sort position, the user will be directed to put the container on SP01.

Once all inventory has been sorted, the position needs to be closed for work to be created.

On the mobile device, scan the pallet ID PLP02. The user will be asked if they want to close the position. Click OK and the position will be closed, and sorted inventory picking work will be created to take the inventory to the Baydoor.

From the outbound sorting position assignments form, select SP01, and click Close from the action bar. This will perform the same action that was performed on the mobile device: Close the position and create sorted inventory picking work.

Complete the sorted inventory picking work normally. Once completed the inventory will be picked to the sales order. All other warehouse processes apply at this point.
