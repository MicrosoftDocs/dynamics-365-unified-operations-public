# Put to Wall  Put to Store

# Released in version 10.0.5
#
# About

With this feature you can handle scenarios where consolidation of product is required to a prepack staging area based on configurable criteria. Companies shipping to stores or handling small items will benefit from this functionality due to decreased picking time as it allows for picking to a single target license plate and it can leverage greater number of put positions than cluster picking.

This workflow directs picked product to a Sorting location for distribution into various types of Containers. Generally, each Sorting Location includes multiple Sort Positions. Each sort position is assigned according to the criteria set by business process, typically final destination, shipment, or load. Once product arrives, it is distributed to each Sort Position by quantity associated to the order, destination, shipment, or load.  When a container is full or complete, it is moved to a Staging Location or a Shipping Location for further handling depending on business process.

This warehousing functionality is also called Put-to-light, Break opens, etc.

# Setup

For this demo, standard Contoso data is used with warehouse 62 with some additions noted below.

## Location type

Navigate to _Warehouse management_ _-_ _Setup_ _-_ _Warehouse_ _-_ _Location types_ and create a new location type for Sorting.

- --Location type – SORT
- --Description – Sort

## Warehouse management parameters

Navigate to _Warehouse management_ _-_ _Setup_ _-_ _Warehouse management parameters_ and expand the General – Location types section.

In the &#39;Sorting location type&#39; field specify the new &#39;SORT&#39; location type that was created.

## Location profile

Navigate to _Warehouse management - Setup - Warehouse - Location profiles_ and create new Location profile for Sorting location.

In the **header** of the new profile, name the new profile:

- **--** Location profile ID – _Sort_
- **--** Name – _Sort_

In the **General** tab, the following must be specified:

- **--** Location format – _PACK_
- **--** Location type – _SORT_
- **--** Use license plate tracking – _Yes_
- **--** Allow mixed items – _Yes_
- **--** Allow mixed inventory statuses – _Yes_

## Locations

Navigate to _Warehouse management_ _-_ _Setup_ _-_ _Warehouse_ _-_ _Locations_ and create a new locationas shown below.

Unselect _Generate check digits for_ locations and click _New._ Assign the following criteria:

- **--** Warehouse – _62_
- **--** Location – _Sort_
- **--** Location profile ID – _Sort_

## Packing profiles

Navigate to _Warehouse management_ _-_ _Setup_ _-_ _Packing_ _-_ _Packing profiles_ and create a new record

- **--** Packing profile ID – _Sort_
- **--** Description – _Sort_
- **--** Container packing policy – leave blank
- **--** Container ID mode – _Auto_
- **--** Container type - _PALLET 48X48_

## Outbound sorting template

The Sort template controls if sort positions will be created, what criteria will be used, and other attributes of the sorting process.

Navigate to _Warehouse management_ _-_ _Setup_ _-_ _Packing_ _-_ _Outbound sorting templates_ and create a new sorting template.

In the **header** of the new template, specify the following:

- **--** Outbound sorting template ID – _Wave Sort_
- **--** Description – _Wave sort_
- **--** Sort template type – _Wave dmeand_ - determines how sorting is performed
  - **oo** Wave dmeand – for _Put to wall_ functionality
  - **oo** Container – for _Pallet building after packing_ functionality
- **--** Warehouse - _62_
- **--** Location – _Sort_

In the **general** tab, specify the following parameters:

- **--** Sort verification – _Position scan_ - the type of verification used when performing sort put away.
  - **oo** None
  - **oo** License plate scan
  - **oo** Position scan
- **--** Create work on position close? – _Yes_ - automatically create outbound work when a sort position is closed?
- **--** Assign sort position criteria – _Only user empty position_ - The criteria used to assign sort positions during wave processing.
  - **oo** _Only use empty position_ will take into account positions that already have inventory associated
  - **oo** _Assume position empty_ will disregard any inventory already on the position while assigning and use all available positions.
- **--** Wave step code – _Sort_ – You may need to create a new record in Wave step codes if that feature is enabled.
- **--** Auto close sort position – _No -_ automatically close sort position when no more inventory is expected
- **--** Number of positions – _3_
- **--** Sort position prefix – _SP-_
- **--** Auto pack sort position – _Yes_
  - **oo** If _yes_, the system will automatically pack completed sort positions to a container and create a Container ID based on Packing profile ID specified.
- **--** Packing profile ID – _Sort_

In the ribbon, select &#39;Edit query&#39; to specify the criteria used for this sorting template. Under _Sorting_ tab add a new line with the following setup:

- --Table – _Load details_
- --Derived table – _Load details_
- --Field – _Shipment ID_
- --Search direction – _Ascending_

This will enable the &#39;Outbound sorting template breaks&#39; button in the ribbon of the template form. Select it to open the new form. Check the box to group by Shipment ID. This will create one sort position per shipment that is container in the wave.

## Wave process methods

Navigate to _Warehouse management_ _-_ _Setup_ _-_ _Waves_ _-_ _Wave process methods_ and click &#39;Regenerate methods&#39; to add &#39;sorting&#39; to this list of available methods.

## Wave template

Navigate to _Warehouse management - Setup - Waves - Wave templates_ and edit the 62 Shipping default wave template to use if for wave demand sorting.

In the Header change &#39;Process wave at release to warehouse&#39; to No, and set &#39;Assign to open waves&#39; to Yes.

In the Methods FastTab, move sorting from the remaining methods grid to the selected methods grid. Specify the wave step code used in the sorting template.

## Mobile device menu items

Navigate to _Warehouse management - Setup - Mobile device - Mobile device menu items_ and create a new menu item to be used for sorting the demand to the position.

- --Menu item name – _Sort_
- --Title – _Sort_
- --Mode – _Indirect_
- --Use existing work – _No_

In GeneralFastTab:

- --Activity code – _Outbound sorting_
- --Outbound sorting template ID – _Wave Sort_

## Mobile device menu

Navigate to _Warehouse management - Setup - Mobile device - Mobile device menu_ and add the newly created menu item to the Outbound menu.

## Location directives

Location directives must be created to guide the work created after the sorting is completed.

Navigate to _Warehouse management - Setup - Location directives_ and select Work order type _Sorted inventory picking_.

Create a new location directive.

- --Sequence – 1
- --Name – _Put to Baydoor_

In the Location directives FastTab

- --Work type – _Put_
- --Site – 6
- --Warehouse – 62

In the Line FastTab create a new record:

- --Sequence number – 1
- --From quantity – 0
- --To quantity – 1000000

In the Location Directive Actions FastTab create a new record:

- --Sequence number – 1
- --Name – _Baydoor_
- --Edit query – Range = Location – Location – Baydoor
  - --

## Work classes

Navigate to _Warehouse management - Setup - Work - Work classes_and create new work class for Sorting:

- --Work class ID – _Sorting_
- --Description – _Sorting_
- --Work order type – _Sorted inventory picking_

## Work templates

Navigate to _Warehouse management - Work - Work templates_ and select the &#39;62 Pick to pack&#39; work template.

Click on &#39;Work header breaks&#39; in the ribbon, and uncheck the box for grouping by Shipment ID

Select Work order type _Sorted inventory picking._  Create a new Work template.

In the header

- --Work template – _Sorted picking_
- --Work template description – _Sorted picking_

In the Work Template Details create two lines:

- --Pick – Mandatory – Work class ID = Sorting
- --Put – Mandatory – Work class ID = Sorting

# Demo

This demo will simulate a scenario where the warehouse is storing small items in locations and has to pack them into boxes before shipping, but where Packing station functionality is not really suitable. Workers are picking orders for multiple customers and different addresses at the same time to increase the picking speed. After the picking has been finished, the workers arrive to the sorting location where the picked items can be sorted to the correct box, based on required criteria. In this example, Shipment ID will be used to determine that, as each shipment has a different address. After all items from the Load are packed and sorted by Shipment, the boxes will be moved to the staging area and eventually loaded to truck.

Prior to starting with the demo, ensure that all standard WH functionality is set up correctly for your warehouse. I have used standard Contoso WH 62 for this purpose and have not tweaked any standard configuration, besides what is described in the setup.

## Create demand

Before the functionality can be demonstrated, some demand should be created.

Due to the nature of the demo, I will create three different Sales orders for three different customers to simulate different delivery address. This will create three different Shipments.

Navigate to _Sales and Marketing - Sales orders - All sales order_. Click New to create a new Sales Order. Enter desired customer. In the _General_ section specify Warehouse 62.

1. Sales order 1 (Customer 1): Add a new line to the sales order, item A0001, quantity 5 pcs. Add a second line for item A0002, quantity 10 pcs
2. Sales order 2 (Customer 2): Add a new line to the sales order, item A0001, quantity 7 pcs. Add a second line for item A0002, quantity 3 pcs
3. Sales order 3 (Customer 3): Add a new line to the sales order, item A0001, quantity 8 pcs.

Before creating Shipments, ensure there is enough inventory on the pick locations for all the items on the orders. Review the Location Directive setting to be sure what picking locations are used for sales order picking. You can create manual movements, use replenishment, or any other flow if needed to adjust the inventory. Reserve the inventory.

Release each sales order to warehouse to create a Shipment. There should be three different shipments created. All three shipment will be added to one new wave.

Navigate to _Warehouse management - Outbound waves -  Shipment waves - All waves_ to open the _All waves_ form where new wave can be found.

Select the wave and click &#39;Process&#39; in the Wave section of the ribbon. During Wave processing, the sorting method will use the sorting template to assign the inventory to sort positions.

Navigate to _Warehouse management_ _-_ _Packing and containerization_ _-_ _Outbound sorting_ _position assignments_ to see the position that have been created. This form will show each position, as well as the criteria that is applicable for the position.

One Work ID has been created to bring inventory from the picking location to the sorting location. Complete the work.

## Sorting / Put-to-wall on Mobile device

Now that all inventory has been put to Sorting location, it needs to be sorted to the correct sort position.

Enter the mobile device and open the menu where the new sorting menu item is located.

Select the _Sort_ menu item and initiate sorting of the items.

1. Enter the Target License Plate of the picked Work order
2. Enter the Item number – _one of the items from the Work order_
3. The first sort position being used will be displayed. The user will be prompted to assign a license plate to the sort position
4. On next screen, the system will show some information, including which sort position the item should be put to and how much of it.
5. Confirm the Sort position
6. Repeat this process for all picked lines on the Work order. This should also be done if there are multiple pick lines with the same item number.
7. As this is repeated for all items, the system evaluates the criteria from the next scanned item (work line) and determines to which sorting position it should be put. The user automatically directed to Put the item to the correct Sorting position and depending on the confirmation setup, to confirm this by entering the Position number or License plate.
  1. If automatic sorting is enabled, manual override is not available.

Once finished, open _Sort position assignment_ form to review the status of the positions. You can observe that more transactions are shown, signifying more items have been added to the position.

During setup of the Sort template, it has been specified that the position should be _Closed_ automatically once the last expected inventory is put to it, hence the are in _Closed_ status and Work has been created to move the sorted inventory to _Baydoor_ location.

If the position should be closed manually, this should be done before it can be moved to the Baydoor area.

Closing of Positions can occur in few different ways:

1. Via the Mobile device, where the user can scan one of the items already on the Position and select the _Close_ button. This will close the position.
  1. As the user scans already sorted container, an error message &#39;_The item is already sorted to position&#39;_ will be shown, but the user can still proceed with closing the position.
2. Via _Sort position assignment_ form, where the user can select the position and press the _Close position_ button on the top ribbon.

Note, that for this Work to be processed correctly, MD menu item with the matching Work class should be used for movement and loading process.

Complete the Work to finish the flow and Ship confirm when ready.

# Appendix

- --Items cannot be moved between positions once assigned to one. The system will evaluate how many of each items should go to a certain position.
- --Once movement work has been created from Sorting location, the work should not be cancelled. If so, the Position and Containers within will be deleted from the system and unable for further processing. The inventory will also be removed.
- --Sort template can be configured to create Container automatically on Position Close. This will create standard Container ID structure, based on the Packing profile specified.
