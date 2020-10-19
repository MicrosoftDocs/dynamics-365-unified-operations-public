# Reservations in warehouse management

## Reservations cannot be removed because there is work created which relies on the reservations.

**Issue:** Cannot unreserve inventory due to reliant work to complete.

**Fix:** Please investigate if open packing group work exists to bring item from packing station to baydoor. Review the transactions to verify what is physically reserving the inventory and complete or delete the work to free up the reservation.

## Inventory quantity -XXXX could not be updated due to insufficient inventory transactions for item XXXX with dimensions Size=XXXX, Color=XXXX, Additions=XXXX, Site=XXXX, Warehouse=XXXX, Location=XXXX, Inventory status=Available, License plate=XXXX, Batch number=XXXX for reference Id XXXX on Lot Id XXXX.

**Issue:** Cannot update an inventory quantity due to insufficient inventory transactions with the specified dimensions.

**Fix:** Ensure that there are no inventory transactions which are physically reserving the quantity - could be an open quality order, an inventory blocking record, or an output order, for example.

## Physical on-hand Site=XXXX, Warehouse=XXXX, Inventory status=Available, Batch number=XXXX, Owner=XXXX: XXXX cannot be reserved because only 0.00 are available in the inventory.

**Issue:** Cannot update an inventory quantity due to insufficient inventory transactions with the specified dimensions.

**Fix:** Seems to be due to open work. Either complete work or receive without work creation. Ensure that there are no inventory transactions which are physically reserving the quantity - could be an open quality order, an inventory blocking record, or an output order, for example.

## How to make a partial reservation of a load from load planning workbench form?

**Issue:** When using an item with batch above hierarchy the Release to warehouse from Load Planning Workbench for partial quantity doesn't work. The following error will appear, and no work gets created for the partial quantity.

Error: "To be assigned to wave, load lines must specify the dimensions above the location. To assign these dimensions, reserve and recreate the load line."

If we use an item with batch below reservation hierarchy instead of batch above, then the release of a load from Load Planning Workbench for partial quantity works fine.

**Fix:** This is by design. If you place a dimension above the location in the reservation hierarchy, then it must be specified prior to Release To Warehouse. Microsoft has evaluated this issue and determined it to be a feature limitation when releasing to warehouse from load planning workbench. It is not possible to release partial quantities when not all dimensions above location are specified.
