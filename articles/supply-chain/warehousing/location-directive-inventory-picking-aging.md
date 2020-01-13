# Location directive inventory picking aging

# Released in version 10.0.2
#
# About

Two new location directive strategies are introduced to be used in picking: FIFO (First In First Out) and LIFO (Last In First Out). These work in conjunction with aging date fields on the location and license plate to track when inventory first entered the warehouse.

These strategies can be used for both batch and non-batch tracked items, to ship items to customers based on when the inventory entered the warehouse. This can be especially useful for non-batch tracked inventory where an expiration date is not available to use for sorting.

When inventory in first received/created in the warehouse, the license plate is updated with the current date populated as the aging date. This date is then used by the strategies to determine what is the oldest/youngest inventory in the warehouse. If inventory is moved to a non-license plate tracked location, the location itself is updated with an aging, which will also be used by the strategies.

Note: This features requires the warehouse location status feature be enabled, the location profiles used to store inventory have location status enabled (in demo data for this demo FLOOR-05), and the consistency check run so that the data is accurate.

# Location aging FIFO

The Location aging FIFO location directive strategy will allocate based on aging date, finding the location containing the oldest aging date.

## Setup

Navigate to _Warehouse management - Setup_ _-_ _Location directives_ and select 63 Pick containerization. In the Location Directive Actions FastTab, change the strategy for Sequence 1 from &#39;None&#39; to &#39;Location aging FIFO.&#39; Click on Edit query in the Location Directive Actions grid and add a Range for Locations – Zone ID = FLOOR.

On the mobile device, login to warehouse 63, and navigate to _Quality - Scrap._ Enter LP 63\_1 and click OK to adjust out the license plate.

This will leave inventory in two locations. FL-001 has an aging date of 4/15/2017, while FL-002 has an aging date of  1/29/2017. Both locations contain item A0001.

## Process

Navigate to _Sales and marketing - Sales order - All sales orders_ and create a new order. Specify Customer account = US-001 and Warehouse = 63. Add a line to the order and specify item A0001, quantity 1 pcs.

Reserve the order line and release to warehouse.

Click on &#39;Work details&#39; in the Warehouse dropdown of the Sales order lines action bar. Notice that the pick location for the work is FL-002, as this is the location containing the license plate with the oldest aging date.

# Location aging LIFO

The Location aging LIFO location directive strategy will allocate based on aging date, finding the location containing the newest aging date.

## Setup

Cancel the work created for the FIFO example.

Navigate to _Warehouse management - Setup - Location directives_ and select 63 Pick Containerization. In the Location Directive Actions FastTab, change the strategy for sequence 1 from &#39;Location aging FIFO&#39; to &#39;Location aging LIFO.&#39;

## Process

Navigate to _Warehouse management - Outbound waves -  Shipment waves - All waves_ and select the wave containing the order created previously. Click on &#39;Process&#39; in the WAVE – WAVE section of the ribbon.

Click on &#39;Work&#39; in the WAVE – RELATED INFORMATION section of the ribbon. Notice that the pick location of the work is FL-001, as that is the location containing the license plate with the newest aging date.
