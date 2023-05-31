---
# required metadata

title: Inventory close
description: As part of the process to settle issue transactions with receipt transactions, you can also choose to have the general ledger updated to reflect the adjustments that have been made.
author: JennySong-SH
ms.date: 04/22/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: InventClosing
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: c210c882-6849-4704-b78c-a777dd6cfdb6
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yanansong
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Inventory close

[!include [banner](../includes/banner.md)]

As part of the process to settle issue transactions with receipt transactions, you can also choose to have the general ledger updated to reflect the adjustments that have been made.

The inventory close process settles issue transactions to receipt transactions, based on the inventory valuation method that is selected in the item’s item model group. As part of the settlement process, you can specify that the general ledger should be updated, so that it reflects the adjustments that have been made. However, until inventory close or recalculation has been run, issue transactions are posted at the calculated running average cost price. 

After inventory close, you can no longer post in periods that are before the inventory closing date that you set, unless you reverse a completed inventory close process. For example, if inventory close is run for the period that ends on January 31, you can't post transactions that have a date that is earlier than January 31. 

Items in inventory are assigned to one of two inventory types: item or service. Inventory close performs the same functions for both types. However, for service items, inventory close still settles issues to receipts. 

How often the inventory close process is run varies by company. However, transaction volume should help determine how often you decide to run inventory close. In general, most companies run inventory close as part of their month-end close and reconciliation procedures.

## Inventory recalculation and the general ledger
If adjustments to inventory and the general ledger are required during a month or other inventory period, you can run inventory recalculation instead of inventory close. Inventory recalculation makes adjustments but doesn't make settlements to inventory transactions. 

During inventory recalculation, on-hand inventory is adjusted, inventory transactions are adjusted, and inventory recalculations and inventory closes are run. These tasks affect any ledger account that is linked to the original inventory transaction. 

**Example** 

When you create a purchase order from a sales order, the general ledger accounts that are used for the original sales order are updated. Even if the ledger accounts for the item group that is assigned to the item were changed after the sales order was posted, and an inventory recalculation created an adjustment amount, the adjustment amount is posted to the original ledger accounts. The adjusted amount isn’t posted to the new ledger accounts that are assigned to the item. 

After the update is completed, you can review the ledger voucher that is posted because of one of these tasks.

1.  On the **Closing and adjustment** page, on the **Overview** tab, select the update to review.
2.  Click **Details**, and then select **Voucher**.

## Effects of the inventory close process on the general ledger
Several of the tasks that you can perform on the **Closing and adjustment** page cause an update to general ledger. For example, the general ledger is updated when you make inventory on-hand adjustments, make inventory transaction adjustments, run inventory recalculation, and run inventory close. 

The ledger accounts that are updated because of these tasks are linked to the original inventory transaction. For example, if a sales order is settled to a purchase order, the general ledger accounts that were used for the original sales order are adjusted. This behavior occurs even if the ledger accounts for the item group that is assigned to the item have changed since the sales order was posted. After inventory close creates a settlement amount, the settlement amount is still posted to the original ledger accounts, not to the new ledger accounts that are assigned to the item. The general ledger might also be updated if you reverse an inventory close. 

> [!NOTE] 
> - Inventory close is a required step in the month-end closing procedure for all inventory models except moving average.  You will be warned if you try to close a financial period without first performing the inventory close as of the period end date.
> - Before you run the closing procedure, you can view a list of items that can't be settled during the update.
> - We recommend that you run inventory close during off-peak hours, to distribute computing resources more evenly.

## The inventory close log
After the inventory close process has been completed, a message in the message center might inform you that a unit cost price might be incorrect because a transaction could not be fully settled. 

Before this message is shown, the system reports the item number and the affected transaction. The message informs you that the cost amount that is used for this transaction wasn't updated because of the inventory close. This message appears when a transaction of the issue type can't be settled. 

During the inventory close process, the system checks each financial dimension to see whether there are more issues than receipts up to the specified closing date. This type of imbalance can occur when an inventory transaction from a purchase order isn't fully posted financially, either because the vendor invoice hasn't been received, or because bill of materials (BOM) components that are included in a production on a higher level aren't financially posted. (The sub-production isn't cost-calculated.) In this case, the subsequent close won't adjust all issues to the correct cost price, because not enough receipt information is available. 

For each run of the closing procedure, the system indicates whether a log that contains the warnings is stored and can be viewed. 

If you receive many warnings in the message, we recommend that you perform the following actions:

-   Update receipts financially.
-   Advance the closing date.
-   Reevaluate the business procedures.

In some circumstances, you might not be able to do anything about the warnings. For example, if marking is used, and the marked purchase order has a financial date that is after the closing date, the closing date can't be changed.

## Reversing a completed inventory close
Occasionally, you might have to reverse a completed inventory close to return settlements to the state that they had before adjustments were made. When you reverse a completed inventory close, inventory is reopened to enable posting in the period that the inventory close covers. Related changes might also be made in the general ledger. After you've finished making adjustments, you can run inventory close again for the period that you're working with. 

> [!NOTE] 
> Only the last inventory period that was closed can be reopened. To reverse an earlier inventory close, you must reverse each subsequent inventory close one at a time, starting with the most recent close.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]