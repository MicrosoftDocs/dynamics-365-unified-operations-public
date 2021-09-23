--- 
title: Warehouse management processes are currently being used 
description: When reserving or releasing work, you may get a message that warehouse management processes are currently being used. Fix the issue with one of these steps. 
author: SmithaNataraj 
ms.date: 06/24/2021 
ms.topic: troubleshooting 
# ms.search.form: 
audience: Application User 
ms.reviewer: kamaybac 
ms.search.region: Global 
ms.author: smnatara 
ms.search.validFrom: 2021-06-24 
ms.dyn365.ops.version: 10.0.20 
--- 
# Can't reserve or release work because processes are currently being used

## Symptoms

While working with discrete manufacturing, you receive the following error:

> Warehouse management processes are currently being used. If work lines are not yet registered, you can cancel the created work and any load or shipment lines, and then continue with the picking or shipping process.

## Cause

This issue occurs if you try to reserve or release work for a line, but the inventory transaction has a status of *Picked*, which indicates that the material has been picked.

## Resolution

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
