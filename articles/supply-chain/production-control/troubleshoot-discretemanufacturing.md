---
# required metadata

title: Troubleshoot discrete manufacturing
description: This topic describes how to fix issues that you might encounter while working with discrete manufacturing.
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

This topic describes how to fix common issues that you might encounter while working with discrete manufacturing.

## I get the error "Warehouse management processes are currently being used. If work lines are not yet registered, you can cancel the created work and any load or shipment lines, and then continue with the picking or shipping process."

### Issue description

This error is caused because the inventory transaction is in status *Picked*, which means that the material is picked. Therefore, you can't reserve or release work for that line.

### Issue resolution

To resolve this issue, do one of the following actions:

- Change the production order status back to *Estimated* or *Released*.
- Open the relevant **Production orders** detail page. Then on the Action Pane, open the **Warehouse** tab and, from the **Stop** group select **Stop and unpick** (this will unpick all picked transactions). Then select **Remove stop** to proceed with processing the production order.

Here are some explanations of the *Unpick* and *Stop* functions:

- **Unpick**: This action reverses the status of inventory transactions for bill of materials (BOM) and formula lines in status *Picked* to *On order*. The lines are assigned a status *Picked* when work for raw material picking is completed. The *Picked* status blocks the production order from being reset to status *Created*. In this case, use the unpick function to revert the transactions from status *Picked*, and then reset the production order to status *Created*.
- **Stop**: This action sets a **Stopped** flag on the production order, which prevents any status update on the order. The **Stopped** flag is located on the **Warehouse** FastTab of the **Production orders** details page.

> [!NOTE]
>
> - The actions are only visible when the production order is created for items enabled for warehouse processes.
> - The **Stop** group is only visible on the **Warehouse** tab on the Action Pane of the **Production orders** details page. The group isn't visible on the **Warehouse** FastTab of the **Production orders** list page

## The matching resource name isn't updated after I modify a worker name in the global address book

### Issue description

Whenever I modify a worker name in the global address book, the matching resource name isn't updated in the resource group master.

### Issue resolution

This is currently an unsupported scenario. To resolve the issue, you must manually update the resource name.

## When I create a new production order, the "Insert the active version of bill of material and route?" pop-up alert message isn't displayed

### Issue description

When you create a new production order, after entering the **Item number**, the **Site** and **Warehouse** fields are automatically defaulted with the site and warehouse defined in the **Default order settings** of the finished-goods item. Also, the active **BOM number** and **Route number** are inserted without showing the pop-up alert message "Insert active version for bill of material and route?".

### Issue resolution

You aren't prompted to insert BOM and route numbers when selecting a product that has site and warehouse defined in the **Default order settings**. You will only be prompted when the product doesn't have those values defined in its **Default order settings**.

## Production orders aren't shown on the "Marking" page

### Issue description

Certain production orders aren't shown on the **Marking** page.

### Issue resolution

Products with the following configuration are not available for marking and will therefore not be visible in the marking form:

- Product defined as type *catch weight*
- Products enabled for the advanced warehouse processes
- Products configured to be controlled by the *Standard cost* principle

## When trying to end a production order, I see the following error: "Calculating BOM consumptionCost value must be negative upon issue from inventory."

This issue was fixed in release 10.0.15.

## When the status of a production order changes from "Reported as finished" to "End", I see the error "Update conflict. The standard cost does not match with the financial inventory value after the update," and the infolog message "A critical error has occurred in function InventCostMovement.checkVariance."

The cause of this error message is by design as the underlying data was changed by another process. The process will try to update the data up to five times, and if the conflict still exists, then you will see these error messages. Mitigation is to resume the batch job and it should finish.

If the batch job consistently fails on resuming, then check that the rounding precision for ledger's default currency hasn't changed to a value that isn't compliant with the rounding applied to values in `InventSum`. If it has changed, you probably need to change it back. Look for `ModifiedDateTime`, which would typically, in this case, show that it was recently changed.

## When releasing to warehouse, I see the error "Item RM could not be fully reserved. Ensure that the full quantity is available, or reserve the items manually if the Reservation field on the BOM line is set to Manual or Started. Could not release the order to warehouse because some materials could not be reserved". However, the status is updated to "Released".

### Issue description

If not all BOM line items are physically available when a production order is released, and the **Release to warehouse** policy is set to *Require full reservation* on the production order, then this error will be shown.

### Issue resolution

This behavior is by design and is working as expected.

## When starting a batch order from the warehouse app, the picking list journal isn't created or posted, even though the production start parameters are set to "Always" for "Automatic BOM Consumption" and the "Complete picking list journal" flag is set.

### Issue description

The **Default values** set on the **Production control > Start** dialog box aren't used by the warehouse app for starting a production or batch order. Automatic BOM consumption in the warehouse app is fixed to the flushing principle. That means that only formula or BOM lines with flushing principle *Start* will be flushed when starting production using the warehouse app.

### Issue resolution

The warehouse app for *Start* is fixed to only flush BOM or formula lines with flushing principle *Start*.

## When I try to end a production order and report as finished, I get the error "Total good quantity reported as finished for the production will be  %1. Feedback for the last operation is 0.00 in total."

### Issue description

When you try to post a report as finished journal on a production order and you get the error message "Total good quantity reported as finished for the production will be %1. Feedback for the last operation is 0.00 in total".

### Possible cause

This happens if the quantities posted in the last operations were incorrect. For example, if production was started but the quantity to be started is not allocated, then the route card journal will be posted with nothing. To confirm the situation, open the production order and, on the Action Pane, open the **View** tab and select **Route card**.

### Workaround

You can fix this issue by posting additional journals for those operations that didn't have the journals posted correctly. You can do this by starting the production order again and choosing to post the additional journals. This won't start the production order, but will post the journals.

After this, the route card should show the quantities posted. It should then be possible to end the production orders successfully.

## Is it possible to report a production order as finished while reporting the error quantity, but not time or material quantity?

It isn't possible to report the error quantity on a production order without also reporting the goods quantity. This is *not* a supported scenario. The report as finished update will eventually fail when you try to end the production order, and you will get the error message "Missing report as finished quantity."

## Is it possible to trace finished goods serial numbers against the consumed goods serial numbers?

We currently don't support the tracing of finished goods serials against serials for material consumed by a production order for making the finished goods. The workaround is to create production orders for quantity = 1.