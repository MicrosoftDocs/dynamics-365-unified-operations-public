# Outbound warehouse operations

## Sales order could not be released.

**Issue:** Order is in credit management and a valid postal address must be entered for all sales lines associated with sales order XXXX before shipments can be created. Orders cannot be released to the warehouse without a valid delivery address (per the address format set-up in the Organization Administration module).

**Fix:** Add or update the address on the sales order/line(s) and then release to warehouse.

## The shipment for Load has been confirmed. No lines for posting or quantity=0.

**Issue:** Shipment was confirmed but no posting happened.

**Fix:** Shipment confirmation has no impact on posting; it only updates the shipment and load status. Posting must occur in a separate process.

## Direct delivery activation on sales order line.

**Issue:** Sales order: XXXX Item number: XXXX Direct delivery is not able to process for warehouse XXXX as it has warehouse management enabled. Please specify another warehouse that is not enabled for warehouse management.
