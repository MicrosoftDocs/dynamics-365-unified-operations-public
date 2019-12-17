# Warehouse location status

# Released in version 10.0.1
#
# About

This functionality introduces new fields on locations table for more flexibility in working with and maintaining of locations. Location statuses dictate the status of location and can be included in the location directives query for better warehouse flow control.

The location status feature adds four new fields to the Locations form to track additional information about the current state of the location:

- Item number

- Item that is currently in the location. If the location contains multiple items, this field will be blank

- Last activity date and time

- Timestamp of the last warehouse transaction that was performed against the location

- Aging date

- Date the inventory in the location was brought into the warehouse.
- Calculated based on the license plate aging date. Accurate for license plate tracked locations. Not guaranteed to be accurate for non license plate tracked locations.

- Location status

- Four options:

- Undetermined: Location profile does not track status. Current status unknown
- Empty: No inventory currently in the location
- Picking: Outbound transactions have been performed against the location after it was last empty

- Storage: Only inbound transactions have been performed since the location was last empty

These fields allow warehouse managers to get a better overview of the status of the locations in the warehouse and enable more advanced reporting and filtering.



# Setup

Navigate to _Warehouse management_ - _Setup_ - _ Warehouse_ - _Location profiles_ and select BULK-06. In the General FastTab, Location Updates section, ensure that Enable item in location, Enable location activity date and time, and Enable location status are set to Yes. These parameters control if the references field on the location are active or not. Do the same for profile PIKC-06

# Process

Navigate to _Procurement and Sourcing_ - _Purchase orders_ - _All purchase orders_ and create a new purchase order. Specify Vendor account = 104 and Warehouse = 61. Add a line to the order for item A0002, quantity 5 pcs.

Open the mobile device and navigate to _Inbound_ - _Purchase Receive._ Enter your PO number and item, followed by the full quantity of the line.

From your purchase order, click on Work details in the lines action bar, and note the Work ID that was created.

On the mobile device navigate to _Inbound_ - _Purchase Put-away_ and enter the work ID. Complete the pick and the put, noting the putaway location.

Navigate to _Warehouse management_ - _Setup_ - _Warehouse_ - _Locations_ and filter on Location = your putaway location from the purchase order work.

The location status column will be populated with &#39;Storage&#39; because the last transaction against the location was put. The item number column is populated with A0002, the item that was received and put to the location. The Last Activity Date and Time column will be populated with the timestamp that the work was completed to the location.

On the mobile device, navigate to _Quality_ - _Movement_ and enter the putaway location from the purchase order work as the location. Confirm the full quantity. Enter 06A07R2S1B as the put location and accept the system generated license plate.

In the locations form, refresh and view the original putaway location again. Notice that the Location Status is now &#39;Empty&#39; and the Item number column is blank.

View the record for 06A07R2S1B and notice that the status has changed to Storage and the Item number and Last Activity Date and Time fields have been updated.

Navigate to _Sales and marketing_ - _Sales orders_ - _ All sales order_s and create a new sales order. Specify customer US-002 and warehouse 61. Add a line to the sales order for item A0002, quantity 1 pcs. Reserve the order line and release to warehouse.

Click on Warehouse - Work details from the sales order line action bar. Copy the Work ID that was created.

On the mobile device, navigate to _Outbound_ - _Sales picking_ and enter the copied work ID. Enter the LP created earlier and confirm the pick and put.

Go back to the location form and notice that the Location Status for the location the sales order work picked from has been updated to &#39;Picking,&#39; as well as the Las Activity Date and Time.

# Appendix

These location fields are only update by warehouse transactions. Moving inventory using a journal, or other non WHS processes will not update these fields.
