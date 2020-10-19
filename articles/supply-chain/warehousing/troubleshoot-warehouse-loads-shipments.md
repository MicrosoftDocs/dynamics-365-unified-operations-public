# Load building and shipments

## You can't create a load line for this order line because it contains inventory dimensions that are invalid. You can't reference inventory dimensions that are located below the location dimension in the reservation hierarchy. Remove the invalid dimensions from the order line.

**Issue:** Cannot execute Release to warehouse on a Return sales order

**Fix:** Unfortunately, the product does not support load processing for a sales return process and thereby not possible to get released to the warehouse.

## One of the lines is already on a load. Unable to release to warehouse.

**Issue:** If you choose the process path of manually creating loads or have the process setup such that Loads are created already upon Sales Order line entry, then the assumption that the subsequent releasing is done manually following the route and rating from the load.

The other scenario here is that the user is trying to perform an automatic Release To Warehouse, but the wave process failed to create work, which results in an open shipment/load still being created. This then blocks the user from subsequent attempts to automatically release the order until they either (a) delete the open shipment/load, or (b) re-process the wave manually.

**Fix:** To release from the Sales Order form, or to release automatically from the release sales order form, no load must exist. The load will be created automatically once the wave is processed.

## The delivery note correction cannot be processed.

**Issue:** After posting of delivery note we are not able to cancel the posted Delivery note since the button Cancel is disabled. Also, not able to correct the delivery note while performing the correct delivery note following error thrown. "The delivery note correction cannot be processed. The delivery note only contains items that are subject to warehouse management processes, as these are not supported by Delivery Note correction."

**Fix:** In order to correct posted packing slips for items which are enabled for warehouse management, the posting must occur from the load, not from the order directly.

## How to Create Work from Outbound Loads rather than waves.

**Issue:** Is it possible to create work from outbound loads rather than waves?

Repro steps:

1. Create an outbound load using a sales or transfer order.

2. Release load to warehouse.

3. Currently, no picking work is being generated.

**Fix:** If work needs to be generated immediately when the load is released, then Wave template needs to be configured accordingly. On wave template, set the following settings to Yes:

-   Automate wave creation.

-   Process wave at release to warehouse.

-   Automate wave release.

## Partially shipped load cannot be released again.

**Issue:** A "Partially shipped" load cannot be released again to the warehouse. The message "Operation complete" appears at release to the warehouse, but nothing happens, no work gets created for the remaining quantity. This happens when originally there is an Incomplete reservation and using Transport Load functionality.

**Fix:** KB number: 4574490: Partially shipped loads can be re-waved and re-processed.
