# Partial release and partial shipment

## Release status on a sales order stays as Partially released even after Sales order is Invoiced.

**Issue:** When a sales order is a delivery order but on the same order has an item(s) with a different mode of delivery, once the order is invoiced it still sits with a Released Status of "Partially Released".On a sample sales order there were two items, 1st item was for delivery, 2nd item was for pick up. The delivery was done and so was the pickup, so both lines are invoiced, so with the status of Partially Released which is misleading.

**Fix:** The release status only applies to order lines with items that are enabled for warehouse management, which is why in this scenario it remains at 'partially released'. Microsoft has evaluated this issue and determined it to be a feature limitation. An extension could be added as part of the packing slip/invoicing process to update the release status.
