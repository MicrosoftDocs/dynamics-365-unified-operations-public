--- 
title: Purchase order line data discrepancies 
description: You see data discrepancies or data corruption on your purchase order lines.
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

When you inspect the lines of a purchase order, you notice one or more of the following issues:

- There is a data discrepancy or corruption in purchase order line remainders (delivery or invoice).
- There is corruption in a purchase order line or header status.
- You can't invoice a purchase order because, for example, you receive one or more of the following error messages:

    - "Stopped (error): Transaction has already been posted."
    - "The quantity cannot be invoiced because inventory transactions with a status of Received are insufficient."
    - "Insufficient inventory transactions with status "Purchased" for item %0 quantity %1."

- You can't finalize or close a purchase order because of, for example, one of the following issues:

    - The **Finalize** button is unavailable.
    - You can't cancel the ordered quantity of a purchase order line for a purchase order that is in a confirmed and received state.

## Cause

These issues are usually caused by data corruption or a discrepancy in the remainder quantities for one or more purchase order lines.

## Resolution

You can usually fix these issues by updating the purchase status, delivery remainders, and/or invoice remainders for the relevant purchase order lines, as described in the following procedure.

1. Go to **Procurement and sourcing \> Periodic tasks \> Cleanup \> Correct purchase order lines manually**.
1. In the **Purchase order** field, find and select the purchase order that is giving you trouble.
1. In the **Purchase order lines** section, select a line where you found a discrepancy.
1. In the **Inventory transactions** section, inspect the data that is shown. If you notice any inconsistencies between a purchase order line and its inventory transactions, select one of the following commands on the Action Pane, depending on where you see the inconsistencies:

    - **Recalculate \> Recalculate deliver remainder** – Automatically update the purchase order line and header statuses. This function works only for stocked purchase order lines (that is, lines where the item is a stocked item). Non-stocked items and catch-weight items aren't currently supported.
    - **Recalculate \> Recalculate invoice remainder** – Automatically update the purchase order line and header statuses. This function works only for stocked purchase order lines (that is, lines where the item is a stocked item). Non-stocked items and catch-weight items aren't currently supported.
    - **Recalculate \> Recalculate status** – Recalculate the status of the selected line. This calculation is based on the existing logic. Therefore, the purchase order header status will be updated as required, based on the new purchase order line status.

1. If you still see inconsistencies in the remainder quantities, you can use the following fields to edit them directly as required:

    - Deliver remainder
    - Inventory deliver remainder
    - Invoice remainder
    - Inventory invoice remainder
