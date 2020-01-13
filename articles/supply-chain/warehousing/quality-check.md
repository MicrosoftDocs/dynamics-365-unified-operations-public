# Quality check
# Released in version 10.0.5
#
# About

With this functionality, you can perform rapid quality checks on the spot at the time of receiving to the inbound dock area. These spot checks are beneficial when packaging or any other easily recognizable part of the item is being inspected. It serves as a quick look to see if anything is standing out as faulty before stocking the inventory to its&#39; location.

This function offers an alternative to existing quality check process with more flexibility and faster processing.

At the time of receiving, the worker is required to perform a desired quality check and must decide whether to accept or reject each license plate scanned after they have been registered. Accepted license plates will be guided to the storage location as normal, while rejected license plates will be diverted to a quality check location for further inspection. Existing put away work will be cancelled and new &#39;Quality Check&#39; work order will be created and the user will automatically continue with the put step. This process can also be automated to divert all scanned license plates to the quality check location immediately.

# Setup

## Quality Check Template

Navigate to _Warehouse management_ _-_ _Setup - Work - Quality check template_ and create a new record.

- Quality Check Template Name: Dock check
- Acceptance policy: Prompt user
- Quality processing policy: Create quality order
- Test group: Enclosure

## Work class

Navigate to _Warehouse management - Setup - Work - Work classes_ and create a new work class.

- Work class ID: QC Check
- Description: QC Check
- Work order type: Quality in quality check

## Work template

Navigate to _Warehouse management - Setup - Work - Work templates_ and change the Work order type to Purchase orders. Select 51 PO Receipt.

Add a new line to the Work Template Details grid.

- Work type: Quality check
- Work class ID: Purchase
- Quality Check Template Name: Dock check

Move the new line to line number two (between the Pick and Put).

Change the work order type to Quality in quality check and create a new record:

- Work template: 51 Quality Check
- Work template description: 51 Quality Check

Add a line:

- Work type: Pick
- Work class ID: QC Check

Add a second line:

- Work type: Put
- Work class ID: QC Check

## Location directives

Navigate to _Warehouse management - Setup - Location directives_ and change the Work order type to Quality In Quality Check. Create a new record:

- Name: 51 To Quality
- Work type: Put
- Site: 5
- Warehouse: 51

Create a line:

- From quantity: 1
- To quantity: 1000000

Create a Location Directive Action:

- Name: Quality

Open the edit query for the action and add a range for Locations – Location = QMS

## Mobile device menu items

Navigate to _Warehouse management -  Setup - Mobile device  - Mobile device menu items_. Select Purchase Put-away.

In the Work classes grid, add a new record for QC Check

# Process

Navigate to _Procurement and sourcing - Purchase orders - All purchase orders_ and create a new order. Specify Vendor account = 104 and Warehouse = 51.

Add a line for item M9203, quantity 3 PL.

Open the mobile device and navigate to _Inbound - Purchase Line Receive_. Enter your purchase order number and LineNum 1. Receive 1 PL.

Click on Work details from the purchase order line action bar. Copy the Target license plate from the created putaway work.

On the mobile device navigate to _Inbound -  Purchase Put-away_. Enter the license plate you copied. Confirm the pick from RECV.

On the quality check screen, choose &#39;Reject&#39;.

The original purchase order putaway work will be completed (the put location will be overridden to RECV) and you will now be directed to complete the put of the newly created Quality in quality check work. Confirm the Put to QMS.

A quality order has been created, and can be processed using normal quality procedures.
