# Picking and Packing

## Dimension Location cannot be left blank if dimension Serial number is set.

**Issue:** When a transfer order is created for an advance WMS enabled warehouse for a serial item, after completing the work when trying to confirm the shipment, the error is generated.

**Fix:** The "From" warehouse has transit warehouse which had an empty Default Receipt Location value for the transit warehouse. To solve this, specify a location for default receipt location. Ensure default receipt location on the transit warehouse is license plate controlled.

## **Invalid license plate.**

**Issue:** Error message is being received on the Warehouse Mobile App.

**Fix:** Ensure the License Plate ID exists in the License Plates table and that the item(s)/quantity on the LP is available (i.e. not blocked)

## **Field 'Load weight'(=-XXXX) can only contain positive numbers. Update has been cancelled.**

**Issue:** Load Weight Error appears from Pack station to Staging location when work is open or from Staging to Dock location.

**Fix:** Run consistency check process for the Warehouse load weight consistency check.

## **The quantity is not valid for unit XXXX.**

**Issue:** Unable to split pick across multiple batches.

**Fix:** The warehouse worker will need to use the "Short picking" process on the Warehouse Mobile App. Assuming the issue is that the user is trying to pick multiple batches from the same location, then they could also use the 'Full' option on the Warehouse Mobile App.

## **You cannot move inventory to a license plate controlled location.**

**Issue:** Unable to reduce picked quantities on a load

**Fix:** This used to be true in earlier versions; however, it's now possible to unpick to a License Plate controlled location. The user must specify the location \*and\* License Plate in the reduce picked quantity form from the load line.

## **The Item XXXX is not in location XXXX in warehouse XXXX.**

**Issue:** When a specific Batch and Serial number is reserved for a piece of work, scanning a license plate which doesn't contain that Batch/Serial number gives an incorrect error message.

## **Printing delivery note or packing content by warehouse.**

**Issue:** Is it possible to print by warehouse or site in Work audit template line updates?

**Fix:** If you are printing a document with print management settings, you can limit the scope (site/warehouse) through print management, instead of directly through the work audit template lines update form under edit print settings.

## **Unable to cancel packing slip when posted in SO.**

**Issue:** For WMS-enabled picking/shipping processes, cancellation of the packing slip is not possible when it was posted from the sales order.

**Fix:** In order to correct posted packing slips for items which are enabled for warehouse management, the posting must occur from the load, not from the order directly. Microsoft has evaluated this issue and determined it to be a feature limitation. Generally, a sales order that has been picked and shipped through Warehouse management processes can be packing slip updated from the Load/Shipment and the Sales order document itself. However, if the user chooses the latter, then packing slip reversal is not possible either from the load or sales order. It is therefore recommended to customers to use the Packing slip posting from the load - in which case the reversal (to be done from the load) will be enabled.

## **Not enough work can be found for cluster.**

**Issue:** When using system directed cluster picking process, using a cluster profile on which it's able to pick e.g. 10 positions. This process works as planned. When start picking when there are only 8 positions (work) to be picket, the following error is shown "Not enough work can be found for cluster".

**Fix:** The cluster profile can be configured to disable the 'Activate positions' parameter, select \*\*No\*\*, which should resolve this error.
