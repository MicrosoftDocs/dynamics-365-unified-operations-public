--- 
title: Purchase order line data discrepancies 
description: You see data discrepancies or data corruption in your purchase order lines.
author: SmithaNataraj 
ms.date: 12/07/2021 
ms.topic: troubleshooting 
ms.search.form: PurchLineManualCorrection, PurchTable, PurchLine, InventTrans
audience: Application User 
ms.reviewer: kamaybac 
ms.search.region: Global 
ms.author: smnatara 
ms.search.validFrom: 2021-12-07
ms.dyn365.ops.version: 10.0.24 
--- 
# Purchase order line data discrepancies

## Symptoms

When inspecting the lines of a purchase order, you notice one or more of the following issues:

- Data discrepancy or corruption in purchase order line remainders (delivery or invoice)
- Corruption in a purchase order line or header status
- You aren't able to invoice a purchase order, for example due to one or more of the following error messages:
  - "Stopped (error): Transaction has already been posted."
  - "The quantity cannot be invoiced because inventory transactions with a status of Received are insufficient."
  - "Insufficient inventory transactions with status "Purchased" for item %0 quantity %1"
- You aren't able to finalize or close a purchase order, for example due to one of the following issues:
  - The **Finalize** button is greyed out.
  - You aren't able to cancel the ordered quantity of a purchase order line for a purchase order in confirmed and received state.

## Cause

These issues are usually caused by data corruption or a discrepancy in the remainder quantities for one or more purchase order lines.

## Resolution

You can usually fix these issues by updating the purchase status,delivery remainders and/or invoice remainders for the relevant purchase order lines, as described in the following procedure.

1. Go to **Procurement and sourcing \> Periodic tasks \> Cleanup \> Correct purchase order lines manually**.
1. Use the **Purchase order** field to find and select the purchase order that is giving you trouble.
1. In the **Purchase oder lines** section, select a line where you found a discrepancy.
1. Inspect the data shown in the **Inventory transactions** section. If you notice any inconsistencies between a purchase order line and its inventory transactions then, on the Action Pane, select one of the following commands, depending on where you see the problem.
    - **Recalculate \> Recalculate deliver remainder** – Automatically updates the purchase order line and header statuses. This function only works for stocked purchase order lines (item on the line is stocked item) (non-stocked items and catch weight items aren't currently supported).
    - **Recalculate \> Recalculate invoice remainder** – Automatically update the purchase order line and header statuses. This function only works for stocked purchase order lines (item on the line is stocked item) (non-stocked items and catch weight items aren't currently supported).
    - **Recalculate \> Recalculate status**  –  Recalculates the status of the selected line. This calculation based on the existing logic, which means the purchase order header status will be updated based on the new purchase order line status as needed.
1. If you still see inconsistencies in the remainder quantities, then you can edit them directly as needed using the following fields:
    - **Deliver remainder**
    - **Inventory deliver remainder**
    - **Invoice remainder**
    - **Inventory invoice remainder**
