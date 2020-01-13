# Change work pool on work

# Released in version 10.0.5
#
# About

Change Work pool button is a simple addition to the system which enables the warehouse manager to simply change the Work pool of the already created Work ID. It therefore introduces the ability to react faster to any possible changes on the shop floor and to better streamline the physical process when required by changing situations.

# Setup

No specific setup is required for this functionality to work, the warehouse only has to utilize Work pools in their process.

## Work pool

Navigate to _Warehouse management_ _-_ _Setup - Work - Work pools_ and create two Work pools.

- Webshop
- CallCenter

Save selection

## Work template

Navigate to _Warehouse management - Setup - Work - Work templates_ and select template &#39;62 Pick to pack.&#39; In the Work pool field specify work pool _Webshop._

Any work created by this Work template will now inherit Work pool _Webshop_.

# Demo

This demo will demonstrate how to change the Work pool on already created Work to change the stream of work processing.

Before starting, ensure there is enough quantity on-hand for items A0001 and A0002 in warehouse 62.

Navigate to _Sales and marketing - Sales orders - All sales orders_ and create a new Sales order. Specify Customer account = US-004, Warehouse = 62.

- Add a line for item A0001, quantity 2 pcs.
- Add a line for item A0002, quantity 2 pcs.

Release the order to warehouse. New Shipment and Wave are created.

Navigate to _Warehouse management - Outbound Waves - Shipment Waves - All Waves_ and open the newly created Wave to ensure the Shipment has been added to it. Process the Wave to create Work (if automatic Wave processing is not enabled). Work is now created with Work pool _Webshop._

Navigate to _Warehouse management - Work - Work details_ and select the newly created Work ID.

On the top ribbon, select Work and click on the _Change Work pool ID_ button. New sub-form will open where a different Work pool can be selected. Any Work pool from the Work pool list can be selected.

Confirm selection and observe how the Work pool has changed for the selected Work ID.

NOTE: With this process, Work pool can also be added to Work ID with no work pool associated after work creation. Similarly, Work pool can also be removed from any Work with already associated Work pool.
