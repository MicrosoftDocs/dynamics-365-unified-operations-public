--- 
title: Purchase order line data discrepancies 
description: You see data discrepancies or data corruption in your purchase order lines.
author: SmithaNataraj 
ms.date: 12/07/2021 
ms.topic: troubleshooting 
ms.search.form: 
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

To help find the cause, activate this app troubleshooting rule to check for inconsistency between a purchase order line and inventory transactions: [Inventory transaction is not consistent with purchase line - Dynamics Wiki](https://dynamics.wiki/index.php/Inventory_transaction_is_not_consistent_with_purchase_line#How_to_activate_rules) <!-- KFM: This looks like an internal resource. What do we want to tell users about this? Call Microsoft Support and request something we mention here? -->

## Resolution

You can usually fix these issues by updating the purchase status or the delivery/invoice remainders for the relevant purchase order lines, as described in the following procedure.

1. Go to **Procurement and sourcing \> Periodic tasks \> Cleanup \> Correct purchase order lines manually**.
1. The page gives the following capabilities: <!-- KFM: Update the following to provide instructions on how to do each of these things (eg, name UI labels, fields and values). -->
    - Recalculate the purchase order line status. This is based on the existing logic, which means the purchase order header status will be updated based on the new purchase order line status if needed.
    - Manually edit the 4 Qty fields (RemainInventPhysical, RemainInventFinancial, RemainPurchPhysical, RemainPurchFinancial). When doing so, the purchase order line status on the line gets recalculated based on existing logic.
    - Only for stocked purchase order lines (item on the line is stocked item) (non-stocked items and catch weight items aren't currently supported):
        - Recalculate the deliver remainder quantities. This will automatically update the purchase order line and header statuses.
        - Recalculate the invoice remainder quantities. This will automatically update the purchase order line and header statuses.
        - The recalculations of the Qty fields are based on InventTrans, so use this after determining the InventTrans are correct.

> [!NOTE]
>
> - The **Correct purchase order lines manually** page helps you fix purchase order line issues but not inventory transaction issues. It assumes that the inventory transactions are correct.
> - For non-stocked purchase order lines, updating the inventory delivery/invoice remainders won't help because they are always 0 (they don't have inventory). <!-- KFM: Can we give more/better advice for this situation? -->
