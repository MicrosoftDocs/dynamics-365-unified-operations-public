# Location license plate positioning

# Released in version 10.0.5
#
# About

LP Location positioning allows the user to see where the LP is located a multi pallet location, such as double deep pallet racking.

This functionality adds an sequence number to the license plate for each license plate that is put to a location. The sequence number orders the license plates within a storage location. This feature intelligently solves scenarios where customers are using gravity racking system and need to know which license plate is front facing for picking purposes.

# Setup

Navigate to _Warehouse management_ _-_ _Setup - Warehouse - Location profiles_ and select BULK-05. Two new options have been added:

- Enable license plate position – Enables the LP positioning functionality for the location profile
- Display mobile device LP position – Only editable when the functionality is enabled, controls if the user on the mobile device should be shown the position when performing adjustment in and cycle counting transactions.

Enable both.

# Process

Open the mobile device, log in to warehouse 61, and open _Inventory – Spot Counting_

Enter location 01A01R1S1B and click Count. Click Add LP or Item. Enter Item A0001. Enter a new LP. LP Position 1 will be displayed. Enter quantity 10 and click OK. Click Add LP or Item. Enter Item A0002. Enter a new LP. Set the LP position to 2. Enter quantity 10 and click OK. Click Finished.

Enter location 01A01R1S2B and click Count. Click Add LP or Item. Enter Item A0002. Enter a new LP. LP Position 1 will be displayed. Enter quantity 10 and click OK. Click Finished.

Open work details, and accept both cycle counting work IDs.

Navigate to _Warehouse management – Inquiries and reports – On hand by location_. Enter Site 6, Warehouse 61. View that location 01A01R1S1B has two LPs, A0001 with position 1, and A0002 with position 2. View that location 01A01R1S2B has one LP for A0002 with position 1.

Navigate to _Warehouse management – Setup – Location directives_ and select 61 SO Pick order. Select Line 2.

Change the Sequence number for &#39;Pick less than pallet&#39; to 2. Add a new location directive action:

- Sequence number: 1
- Name: Pick position 1

Edit the query and add a join from Inventory dimensions to License plate. Add another join from License plate to Location license plate positioning. Add a range for Location license plate position – LP Position = 1.

Create a sales order in warehouse 61. Add a line for item A0002, reserve and release to warehouse.

Work will get created picking from location 01A01R1S2B because the LP in that location has position 1.
