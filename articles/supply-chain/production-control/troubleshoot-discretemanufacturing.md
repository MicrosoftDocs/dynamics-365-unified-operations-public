---
# required metadata

title: Troubleshoot discrete manufacturing
description: This topic describes how to fix issues that you might encounter while you work with discrete manufacturing.
author: SmithaNataraj
manager: tfehr
ms.date: 11/04/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: smnatara
ms.search.validFrom: 2020-11-04
ms.dyn365.ops.version: 10.0.15

---
# Troubleshoot discrete manufacturing

This topic describes how to fix issues that you might encounter while you work with discrete manufacturing.

## I receive the following error message: "Warehouse management processes are currently being used. If work lines are not yet registered, you can cancel the created work and any load or shipment lines, and then continue with the picking or shipping process."

### Issue description

This issue occurs if you try to reserve or release work for a line, but the inventory transaction has a status of *Picked*, which indicates that the material has been picked.

### Issue resolution

To fix this issue, follow one of these steps.

- Change the status of the production order back to *Estimated* or *Released*.
- Open the details page for the relevant production order. On the Action Pane, on the **Warehouse** tab, in the **Stop** group, select **Stop and unpick** to unpick all picked transactions. Then select **Remove stop** to process the production order.

Here is an explanation of the *Unpick* and *Stop* functions:

- **Unpick** – This function reverses the status of inventory transactions for bill of materials (BOM) lines and formula lines that have a status from *Picked* through *On order*. When work for raw material picking is completed, the status of the lines is set to *Picked*. This status prevents the production order from being reset to *Created* status. In this case, you can use the *Unpick* function to revert the transactions from *Picked* status and then reset the production order to *Created* status.
- **Stop** – This function sets a **Stopped** flag on the production order to prevent any status update on the order. You can find the **Stopped** flag on the **Warehouse** FastTab of the production order details page.

> [!NOTE]
>
> - The buttons are visible only when the production order is created for items that are enabled for warehouse processes.
> - The **Stop** group is visible only on the **Warehouse** tab on the Action Pane of the production order details page. It isn't visible on the **Warehouse** FastTab of the **Production orders** list page.

## The matching resource name isn't updated after I change a worker name in the global address book.

### Issue description

If you change a worker name in the global address book, the matching resource name isn't updated in the resource group master.

### Issue resolution

This scenario isn't currently supported. To fix the issue, you must manually update the resource name.

## When I create a new production order, I don't receive the following message: "Insert the active version of bill of material and route?"

### Issue description

When you create a new production order, after you enter the item number, the **Site** and **Warehouse** fields are automatically set to the default site and warehouse that are defined on the **Default order settings** page for the finished goods item. Additionally, the active BOM number and route number are automatically entered. You don't receive the following message that prompts you for those values:

> Insert active version for bill of material and route?

### Issue resolution

You aren't prompted to insert BOM and route numbers if you select a product that a site and warehouse are defined for on the **Default order settings** page. You're prompted only if those values aren't defined for the selected product.

## Production orders aren't shown on the Marking page.

### Issue description

Some production orders aren't shown on the **Marking** page.

### Issue resolution

Products that have the following configuration aren't available for marking. Therefore, they won't be shown on the **Marking** page:

- The products are defined as products of the *catch weight* type.
- They are enabled for the advanced warehouse processes.
- They are configured to be controlled by the *Standard cost* principle.

## When I try to end a production order, I receive the following error message: "Calculating BOM consumptionCost value must be negative upon issue from inventory."

This issue was fixed in release 10.0.15.

## When the status of a production order is changed from Reported as finished to End, I receive the following error messages: "Update conflict. The standard cost does not match with the financial inventory value after the update" and "A critical error has occurred in function InventCostMovement.checkVariance."

This issue occurs because the underlying data was changed by another process. The process will try to update the data up to five times. If the conflict still exists after five attempts, you will receive the following error messages:

> Update conflict. The standard cost does not match with the financial inventory value after the update.

> A critical error has occurred in function InventCostMovement.checkVariance.

This behavior is by design. To mitigate the issue, resume the batch job. It should finish running.

If the batch job consistently fails after you resume it, verify that the rounding precision for the ledger's default currency is compliant with the rounding that is applied to values in the InventSum table. If the rounding precision has been changed to a non-compliant value, you probably must change it back to a compliant value. Look for **ModifiedDateTime**. In this case, the value will typically show that the rounding precision was recently changed.

## When I release to a warehouse, I receive the following error message: "Item RM could not be fully reserved. Ensure that the full quantity is available, or reserve the items manually if the Reservation field on the BOM line is set to Manual or Started. Could not release the order to warehouse because some materials could not be reserved." However, the status is updated to Released.

### Issue description

If not all BOM line items are physically available when a production order is released, and the **Release to warehouse** policy is set to *Require full reservation* on the production order, you will receive the following error message:

> Item RM could not be fully reserved. Ensure that the full quantity is available, or reserve the items manually if the Reservation field on the BOM line is set to Manual or Started. Could not release the order to warehouse because some materials could not be reserved.

### Issue resolution

This behavior is by design and is working as expected.

## When I start a batch order from the warehouse app, the picking list journal isn't created or posted, even though the production start parameters are set to Always for Automatic BOM Consumption, and the Complete picking list journal flag is set.

### Issue description

In the dialog box that appears when you select **Production control \> Start**, default values can be set. However, the warehouse app doesn't use those default values to start a production order or batch order. Automatic BOM consumption in the warehouse app is fixed to the flushing principle. Therefore, only formula lines or BOM lines where the flushing principle is set to *Start* will be flushed when the warehouse app is used to start production.

### Issue resolution

The warehouse app for *Start* is fixed so that only formula lines or BOM lines where the flushing principle is set to *Start* are flushed.

## When I try to end a production order and report as finished, I receive the following error message: "Total good quantity reported as finished for the production will be %1. Feedback for the last operation is 0.00 in total."

### Issue description

When you try to post a report as finished journal on a production order, you receive the following error message:

> Total good quantity reported as finished for the production will be %1. Feedback for the last operation is 0.00 in total.

### Possible cause

This issue occurs if the quantities that were posted in the last operations were incorrect. For example, if production is started, but the quantity that must be started isn't allocated, the route card journal will be posted with nothing. To confirm the situation, open the production order, and then, on the Action Pane, on the **View** tab, select **Route card**.

### Workaround

You can fix this issue by posting additional journals for the operations that the journals weren't correctly posted for. Restart the production order, and select to post the additional journals. This action won't start the production order, but it will post the journals. The route card should then show the quantities that were posted, and you should be able to end the production orders successfully.

## Can I report a production order as finished while I report the error quantity, but not while I report the time or material quantity?

You can't report the error quantity on a production order unless you also report the good quantity. This scenario is **not** supported. The report as finished update will eventually fail when you try to end the production order, and you will receive the following error message:

> Missing report as finished quantity.

## Can I trace the serial numbers of finished goods against the serial numbers of consumed goods?

You can't trace the serial numbers of finished goods against the serial numbers of material that a production order consumes to make those finished goods. This scenario isn't currently supported. The workaround is to create production orders for a quantity of 1.
