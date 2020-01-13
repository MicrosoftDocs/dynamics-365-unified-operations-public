# Location product dimension mixing

# Released in version 10.0.5
#
# About

This new Location profile functionality enables better location managing when using product variants or products with dimensions, such as with fashion industry. It allows you to decide whether configurations, colors, style, and sizes can be mixed on a certain location (profile) or if only one or a combination of some of those dimensions can be put to the same location.

# Setup

## Allow product dimension mixing

Navigate to _Warehouse management_ _-_ _Setup - Warehouse - Location profiles_ and select _BULK_ Location profile.

Set the &#39;Enable location product dimension specific mixing&#39; parameter to Yes. Note, this can only be enabled when &#39;Allow mixed items&#39; is set to No. Expand the _Allowed product dimension mixing_ FastTab. Set the &#39;Size&#39; option to Yes

## Create new product master and product variants

Navigate to _Product information management - Products - Product masters_ and create new Product Master B0001.

- Product dimension group – Size
- Size group – CASUALSHIR
- Generate variants automatically - Yes

Release the product to USMF

- Ensure that the item is using Warehouse management system.
- Tracking dimension group – None
- Reservation hierarchy – Default
- Item group – Audio
- Item model group – FIFO
- Unit sequence group – ea

## Location directives

Navigate to _Warehouse management - Setup - Location directives_ and select _Work order type Purchase order_ and select the LD for Warehouse 24.

On the LD Action section, add a new line:

- Sequence number – 1 (it should be in front of the already existing line)
- Name – Put to BULK Location profile
- Fixed location usage – Fixed and non-fixed locations
- Allow negative inventory – blank
- Batch enabled – blank
- Strategy – None\*

\*NOTE: If using LD Strategy &#39;Consolidate,&#39; the _Allow product dimension mixing_ setup will be overridden and items will be put to the same location even if not allowed by the setup.

On that line, select Edit query and add a new line on Range:

- Table – Locations
- Derived table – Locations
- Field – Location profile ID
- Criteria - BULK

Save selection and confirm.

## Mobile device menu item

Navigate to _Warehouse management - Setup - Mobile device - Mobile device menu items_ and create a new menu item to be used for sorting.

In **Header** , specify the following:

- --Menu item name – _PO line receiving_
- --Title – _PO line receiving_
- --Mode – _Work_
- --Use existing work – _No_

In **General** fast tab, the following setting can be specified:

- --Work creation process – Purchase order line receiving and putaway
- --Generate license plate – _Yes_

## Mobile device menu

Navigate to _Warehouse management -  Setup - Mobile device - Mobile device menu_ and add the newly created menu item to the desired menu.

# Demo

This demo will demonstrate how two different product variants can still be put to the same location when the Location profile does not allow mixed items but _Allow product dimension mixing_ is enabled. In this case, we will use the variant _Size_ as the criteria.

Before starting, ensure there are empty locations in Warehouse 24 with Location profile BULK.

## Create Purchase order

Navigate to _Accounts payable - Purchase orders -All purchase order_ and create a new Purchase order. Specify Vendor account = 1001, Warehouse = 24.

- Add a line for item B0001, **Size 200** , quantity 2 pcs.
- Add a line for item B0001, **Size 500** , quantity 2 pcs.
- Add a line for item A0001, quantity 1

## Process the PO via WMA

Open Mobile device with user, enabled for Warehouse 24 and select the previously created _Purchase Order Line_ receiving menu item.

1. Enter the PO number and line number 1 and specify quantity 2ea. Receive that to create and process Putaway Work (Work 1).
2. Repeat this for PO line 2. Specify quantity 1ea and confirm. New Putaway Work (Work 2) is created to the same location as Work 1.
3. Repeat once again for PO line 2. Specify quantity 1ea and confirm. New Putaway Work (Work 3) is created to the same location as Work 1.
4. This is due to the Consolidation LD strategy and the _Allow product dimension mixing_ allowing the _Size_ to be mixed on a location.
5. Now, process the last PO line (line 3) and specify quantity 1 for item A0001. Receive that to create and process Putaway Work (Work 4). This is because the location profile does not allow mixed products.

This Demo can be repeated with not allowing any of the Product dimension to be mixed (in this case, disable the _Size_ under the _Allow product dimension mixing_). When receiving the PO in that case, each Product variant will be put to a new location.
