---
# required metadata

title: Troubleshoot Sales orders
description: This topic describes how to fix issues that you might encounter while working with discrete manufacturing.
author: SmithaNataraj
manager: tfehr
ms.date: 05/07/2020
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
ms.search.validFrom: 2020-5-7
ms.dyn365.ops.version: AX 10.0.14

---
# Troubleshoot Discrete Manufacturing

This topic describes how to fix common issues that you might encounter while working with Discrete Manufacturing.

##  Error 'Warehouse management processes are currently being used. If work lines are not yet registered, you can cancel the created work and any load or shipment lines, and then continue with the picking or shipping process'
The cause of this is that the inventory transaction is in status Picked which means that the material is picked. Therefore, it is not possible to reserve or release work for that line.

**Issue Resolution**

1. Reverse production order status to Estimated or Released
2. Or click "Stop and unpick" button on the Warehouse tab of the production order (this will unpick all picked transactions). Then, click "Remove stop" to proceed with processing the production order.

Here is an explanation of the Unpick and Stop function:

**Unpick**
This action will reverse the status of inventory transactions for BOM/Formula lines in status "Picked" to "On order". The lines gets to status "Picked" when work for raw material picking is completed. This state blocks the production order from being reset to status: Created. The Unpick function can then be used to revert the transactions from status Picked, and then the production order can be reset to status Created.

**Stop**
This actions sets a stop flag on the production order which prevents any status update on the production order (You can find the Stop flag field under the Warehouse fasttab on the production order details page).

>Note:
>- The fields are only visible when the production order is created for items enabled for the warehouse processes.
>- The field group is only visible under the Warehouse tab in the production order details page. The fields are not visible under the Warehouse tab in the production order list page

## Resource name not updated after being modified in Global address book
Whenever the worker name is modified from the global address book, resource name is not getting updated based on these changes, in the resource group master.

**Resolution**
This is currently an unsupported scenario. To resolve the issue, you need to manually update the resource name. 

## 'Insert the active version of bill of material and route?' popup not displayed while creating new production order
When creating a new production order, after entering the item number, the Site & Warehouse are automatically defaulted with the site and warehouse defined in ‘Default order settings’ of the FG item and active BOM & Route are inserted without the pop-up alert message “Insert active version for bill of material and route?”.

**Resolution**
The user is not prompted for inserting BOM and route when selecting a product that has site and warehouse is defined in the default order settings. It will only be prompted when the product does not have those defined in the default order settings.

## While performing multiple Report as Finished actions on a production order having scrap percentage setup in the route, suggested Good and Error quantities are incorrect for the second report as finished and beyond
**Business Scenario**
During the production cycle, the users will have to report the produced quantity in the system using the ‘Report as finished’ functionality. This will be done by multiple users at all production sites. During this action, the system initiates a value which is not correct at all.

For each ‘Report as finished’, the user will have to get rid of the wrong value in order to get accurate values to report to Production managers.

**Resolution**
In the current implementation the good and error quantities in the report as finished dialog is calculated from the route transactions that has been generated from posted route card journals on the production order.

In this scenario the route card journal is set up to be automatically created when doing report as finished. When the report as finished dialog is opened for the first time on the production order, the error quantity will be shown as zero, because no route card journals exists on the production order. When completing the first report as finished with quantity = 10, a route card journal is automatically created and posted with error quantity 1.11 and good quantity = 10. When doing the second report as finished the error quantity will default to 1.11 in the report as finished dialog, because that is the quantity that is found from the route card journal that was posted when the first report as finished was completed. The good quantity is calculated as the remaining quantity minus the error quantities that have been previous posted. In this scenario 90 pieces remains to be reported as finished and 1.11 was posted as error quantity in the first reporting therefore the good quantity defaulted in the dialog for the second report as finished will be calculated as 90-1.11 = 88.89.

As a suggestion to obtain the desired behavior, consider overriding the defaulted good quantity of 88.89 with 90 and remove the error quantity of 1.11 and then complete the report as finished without selecting the End option. When doing that, a route card journal will be created and posted with good quantity = 90 and error quantity = 10. After that, open the report as finished dialog again. Now the error quantity will show as 11.11 which is the sum of the error quantities from the two reporting as finished processes. The good quantity will default to -11.11 because no good quantities remains to be reported as finished and the error quantity is subtracted.

## Production order are not displayed in Marking form

**Business Scenario**
1. Create production order of level 1 item
2. Create production order of level 2 item
3. Estimate both orders
4. Go to production formula of level 1 item
5. Select line for level 2 item and click "Inventory" and then "Marking"
Result: Production order for level 2 item should be there, but is not shown.

**Possible cause**
Standard cost items, WMS and CW items cannot be handled with marking. Verify if the items are any of these types.

## Unable to end the production order, the following error occurs 'Calculating BOM consumptionCost value must be negative upon issue from inventory'
This issue has been fixed in 10.0.15.

## When status is changed for a production order from "Reported as finished" to "End" the following error message is displayed - 'Update conflict. The standard cost does not match with the financial inventory value after the update' and the infolog message 'A critical error has occurred in function InventCostMovement.checkVariance'. 
The cause of this error message is by design as the underlying data was changed by another process, while this was running. Process will try 5 attempts to update the data and if there is an update conflict still, then the process will throw the update conflict exception. Mitigation is to resume the batch job and it should finish.

**Resolution**
If the batch job consistently fails on resuming, then:
Check that the Rounding precision for Ledger's default currency has not changed to a value that is not compliant with the rounding applied to values in InventSum. If it has changed, we probably need to change it back. Look for ModifiedDateTime would typically in this case show that it was recently changed.

## Release to warehouse fails with error "Item RM could not be fully reserved. Ensure that the full quantity is available, or reserve the items manually if the Reservation field on the BOM line is set to Manual or Started. Could not release the order to warehouse because some materials could not be reserved". However, the status is updated to Released.
A production order that is set to Require full reservation, but all items are not available, when released throws the above error. But, the status is updated to Released though nothing has been released to the warehouse. 

**Resolution**
This behavior is by design and is working as expected.

## When starting a Batch order from the mobile device the picking list journal is not created nor posted, though the production start parameters are set to 'Always' for 'Automatic BOM Consumption' and 'Complete picking list journal' is set.
The Production Control -> Start Default parameters are not used by the hand held flow for starting a production or batch order. Automatic BOM consumption on the hand held device is fixed to Flushing principle. That means that only formula or BOM lines with flushing principle Start will be flushed when using the hand held device for starting.

**Resolution**
Ensure to set the flushing principle on the formula lines.

## Unable to end production orders after completion. Getting the error for 'Report as Finished' 'Total good quantity reported as finished for the production will be X. Feedback for the last operation is 0.00 in total', for production order end 'Negative cost amount for receipts is not allowed'.
When you try to post a report as finished journal on a production order and you get the message “Total good quantity reported as finished for the production will be X. Feedback for the last operation is 0.00 in total”. 

**Possible cause**
This happens if the quantities posted in the last operations were incorrect, i.e. the quantities posted when they were ended or started.

For example if production was started but the quantity to be started is not allocated, then the route card journal will be posted with nothing. Validate this by going to the View -> Route Card, for the production order.

**Workaround**
This issue can fixed by posting additional journals for those operations which did not have the journals posted correctly. You can do this by **Starting** the production order again and choosing to post the additional journals. This will not start the production order, but will only post the journals. 

After this, you can see the route card should show the quantities posted. It should then be possible to end the production orders successfully.

