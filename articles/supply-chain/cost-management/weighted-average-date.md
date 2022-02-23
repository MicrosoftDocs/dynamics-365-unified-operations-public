---
# required metadata

title: Weighted average date
description: Weighted average date is an inventory model based on the weighted average principle, where issues from inventory are valued at the average value of the items that are received into inventory for each separate day in the inventory closing period. 
author: AndersGirke
ms.date: 10/25/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: InventJournalLossProfit, InventMarking, InventModelGroup, SalesTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac

# ms.tgt_pltfrm: 
ms.custom: 28991
ms.assetid: 945d5088-a99d-4e54-bc42-d2bd61c61e22
ms.search.region: Global
ms.search.industry: Retail
ms.author: aevengir
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Weighted average date with include physical and marking

[!include [banner](../includes/banner.md)]
Weighted average date is an inventory model based on an average that results from the multiplication of each component (item transaction) by a factor (cost price) reflecting its importance (quantity) on each day in the period. Another way to say this is that weighted average is an inventory model that assigns the cost of issue transactions based on the mean value of all inventory received during each day, plus any on-hand inventory from the previous day.

When you run an inventory closing using the weighted average date inventory model, there are two ways a settlement can be created. Typically, all receipts are settled against a virtual issue, which holds the total received quantity and value. This virtual issue has a corresponding virtual receipt from which the issues are settled. In this manner, all issues get the same average cost on each day. The virtual issue and receipt can be seen as a virtual transfer, which is named the *weighted average inventory closing transfer*. This settlement method is called a *weighted average summarized settlement*. If there is only one receipt, all issues can be settled from it and the virtual transfer will not be created. This settlement method is referred to as a *direct settlement*. Any inventory that is on hand after the inventory close is performed is valued at the weighted average from the last day of the previous period and included in the weighted average date calculation in the next period.

You can override the weighted average date principle by marking inventory transactions so that a specific item receipt is settled against a specific issue. A periodic inventory close is required when you use the weighted average date inventory model to create settlements and adjust the value of issues according to the weighted average date principle. Until you run the inventory close process, issue transactions are valued at the running average when the physical and financial updates occurred. Unless you're using marking, the running average is calculated when the physical or financial update is performed.

The weighted average date inventory costing method is calculated by the following formula each day:

![Weighted average formuala](./media/weightedaverageformula.gif) 

The weighted average cost is equal to the beginning quantity times beginning price plus the sum of each receipt quantity times it’s receipt price all divided by the beginning quantity plus the sum of the receipt quantity.

Q = quantity of the transaction  
P = price of the transaction

During inventory close, the calculation is performed every day through the closing period, as shown in the following illustration. 

![Weighted average date daily calculation model.](./media/weightedaveragedatedailycalculationmodel.gif) 

Inventory transactions that leave the inventory, such as sales orders, inventory journals, and production orders, occur at an estimated cost price on the date of posting. This estimated cost price is also referred to as the running average cost price. On the date of inventory close, the system analyzes the inventory transactions for previous periods, previous days, and the current day. This analysis is used to determine which of the following closing principles should be used:

-   Direct settlement
-   Summarized settlement

Settlements are inventory close postings that adjust the issues to the correct weighted average as of the closing date. 

**Note:** For more information about settlements, see the article about inventory close. The following examples illustrate the effect of using weighted average with five configurations:

-   Weighted average date direct settlement when the **Include physical value** option isn't used
-   Weighted average date summarized settlement when the **Include physical value** option isn't used
-   Weighted average date direct settlement when the **Include physical value** option is used
-   Weighted average date summarized settlement when the **Include physical value** option is used
-   Weighted average date when marking is used

## Weighted average date direct settlement when the Include physical value option isn't used
The current version uses the same direct settlement principle that was used for weighted average in earlier versions. The system settles directly between receipts and issues. The system uses this direct settlement principle in specific situations:

-   One receipt and one or several issues have been posted in the period.
-   Only issues have been posted in the period, and the inventory contains on-hand items from a previous closing.

In the following scenario, a financially updated receipt and issue have been posted. During inventory close, the system settles the receipt directly against the issue, and no adjustment to the cost price is required on issue. 

The following illustration shows these transactions:

-   1a. Inventory physical receipt is updated for a quantity of 5 at a cost of USD 10.00 each.
-   1b. Inventory financial receipt is updated for a quantity of 5 at a cost of USD 10.00 each.
-   2a. Inventory physical issue is updated for a quantity of 2 at a cost of USD 10.00 each.
-   2b. Inventory financial issue is updated for a quantity of 2 at a cost of USD 10.00 each.
-   3. Inventory close is performed by using the direct settlement method to settle the inventory financial receipt to the inventory financial issue.

![Weighted average date direct settlement without the Include physical value option.](./media/weightedaveragedatedirectsettlementwithoutincludephysicalvalue.gif) 

**Key to the illustration:**

-   Inventory transactions are represented by vertical arrows.
-   Receipts into inventory are represented by vertical arrows above the timeline.
-   Issues out of inventory are represented by vertical arrows below the timeline.
-   Above or below each vertical arrow, the value of the inventory transaction is specified in the form *Quantity*@*Unit price*.
-   If an inventory transaction value is enclosed in parentheses, the inventory transaction is physically posted into inventory.
-   If an inventory transaction value isn't enclosed in parentheses, the inventory transaction is financially posted into inventory.
-   Each new receipt or issue transaction is designated by a new label.
-   Each vertical arrow is labeled with a sequential identifier, such as *1a*. The identifiers indicate the sequence of inventory transaction postings in the timeline.
-   Inventory closings are represented by a red vertical dashed line and the label *Inventory Close*.
-   Settlements that are performed by inventory close are represented by dashed red arrows that go diagonally from a receipt to an issue.

## Weighted average date summarized settlement when the Include physical value option isn't used
Weighted average is based on the principle that all receipts in a closing period are summarized into a new inventory transfer transaction. This transaction is known as w*eighted average inventory closing*. All the receipts for the day are settled against the issue of the newly created inventory transfer transaction. All issues for the day are settled against the receipt of the new inventory transfer transaction. If the on-hand inventory is positive after the inventory close, the on-hand inventory and the value of the inventory are summarized on the new inventory transfer transaction receipt. If the on-hand inventory is negative after the inventory close, the on-hand inventory and the value of the inventory are the sum of individual issues that haven't been fully settled. 

In the following scenario, several financially updated receipts and issues have been posted during the period. During inventory close, the system evaluates every day to determine how each day should be treated by closing. 

The following illustration shows these transactions: 

**Day 1:**

-   1a. Inventory physical receipt is updated for a quantity of 3 at USD 15.00 each.
-   1b. Inventory financial receipt is updated for a quantity of 3 at USD 15.00 each.
-   2a. Inventory physical issue for a quantity of 1 at a running average cost of USD 15.00.
-   2b. Inventory financial issue for a quantity of 1 at a running average cost of USD 15.00.

The system will use the direct settlement approach for day 1. 

**Day 2:**

-   3a. Inventory physical issue for a quantity of 1 at a running average cost of USD 15.00
-   3b. Inventory financial issue for a quantity of 1 at a running average cost of USD 15.00

The system will use the direct settlement approach for day 2. 

**Day 3:**

-   4a. Inventory physical issue for a quantity of 1 at a running average cost of USD 15.00
-   4b. Inventory financial issue for a quantity of 1 at a running average cost of USD 15.00
-   5a. Inventory physical receipt for a quantity of 1 at USD 17.00 each
-   5b. Inventory financial receipt for a quantity of 1 at USD 17.00 each

Inventory close is performed. The direct settlement must be used, because there are multiple receipts that cross multiple days.

-   7a. A weighted average inventory close transaction financial issue is created at for a quantity of 2 at USD 32.00 to summarize the settlements of all inventory financial receipts to date that haven't been closed.
-   7b. A weighted average inventory close transaction financial receipt is created as the offset to 7a.

The system generates and posts the summarized inventory transfer transaction. Additionally, the system settles all the receipts for the day and on-hand inventory for previous days against the summarized inventory transfer issue transaction. All the issues for the day are settled against the summarized inventory transfer receipt transaction. The weighted average cost price is calculated as USD 16.00. The issue will have an adjustment of USD 1.00 to adjust it to the weighted average cost. The new running average cost price is USD 16.00. 

The following illustration shows this series of transactions, and the effects of using the weighted average inventory model and the summarized settlement principle, but without using the **Include physical value** option. 

![Weighted average date summarized settlement without the Include physical value option.](./media/weightedaveragedatesummarizedsettlementwithoutincludephysicalvalue.gif) 

**Key to the illustration**

-   Inventory transactions are represented by vertical arrows.
-   Receipts into inventory are represented by vertical arrows above the timeline.
-   Issues out of inventory are represented by vertical arrows below the timeline.
-   Above or below each vertical arrow, the value of the inventory transaction is specified in the form *Quantity*@*Unit price*.
-   If an inventory transaction value is enclosed in parentheses, the inventory transaction is physically posted into inventory.
-   If an inventory transaction value isn't enclosed in parentheses, the inventory transaction is financially posted into inventory.
-   Each new receipt or issue transaction is designated by a new label.
-   Each vertical arrow is labeled with a sequential identifier, such as *1a*. The identifiers indicate the sequence of inventory transaction postings in the timeline.
-   Inventory closings are represented by a red vertical dashed line and the label *Inventory Close*.
-   Settlements that are performed by inventory close are represented by dashed red arrows that go diagonally from a receipt to an issue.
-   Solid red diagonal arrows show the receipt transactions being settled to the issue transaction that is created by the system.
-   The solid green diagonal arrow represents the offsetting system-generated receipt transaction that the originally posted issue transaction is settled to.

## Weighted average date direct settlement when the Include physical value option is used
The current version uses the same direct settlement principle for weighted average date that is used in earlier versions. The system settles directly between receipts and issues. The system uses this direct settlement principle in specific situations:

-   One receipt and one or several issues have been posted in the period.
-   Only issues have been posted in the period, and the inventory contains on-hand inventory from a previous closing.

If you select the **Include physical value** check box for an item on the **Item model group** page, the system uses physically updated receipts when it calculates the estimated cost price, or running average. Issues are posted based on this estimated cost price during the period. During the inventory close, only financially updated receipts will be considered in the weighted average calculation.

## Weighted average date summarized settlement when the Include physical value option is used
If you select the **Include physical value** check box for an item on the **Item model group** page, the system uses physically updated receipts when it calculates the estimated cost price, or running average. Issues are posted based on this estimated cost price during the period. During the inventory close, only financially updated receipts will be considered in the weighted average calculation. Weighted average settlement is based on the principle that receipts in a closing period are summarized into a new inventory transfer transaction that is known as *weighted average inventory closing*. All the receipts for the day are settled against the issue of the newly created inventory transfer transaction. All issues for the day are settled against the receipt of the new inventory transfer transaction. If the on-hand inventory is positive after the inventory close, that on-hand inventory and the value of the inventory are summarized on the new inventory transfer transaction (receipt). If the on-hand inventory is negative after the inventory close, the on-hand inventory and the value of the inventory are the sum of individual issues that haven't been fully settled.

## Weighted average date when marking is used
Marking is a process that lets you link an issue transaction to a receipt transaction. Marking can occur either before or after a transaction is posted. You can use marking when you want to be sure of the exact cost of the inventory when the transaction is posted or when the inventory close is performed. 

For example, your Customer Service department accepted a rush order from an important customer. Because this is a rush order, you will have to pay more for this item to meet your customer’s request. You must make certain that the cost of this inventory item is reflected in the margin, or cost of goods sold (COGS), for this sales order invoice. When the purchase order is posted, the inventory is received at a cost of USD 120.00. The sales order document is marked to the purchase order before the packing slip or invoice is posted. The COGS will then be USD 120.00 instead of the current running average cost for the item. If the sales order packing slip or invoice is posted before the marking occurs, the COGS will be posted at the running average cost price. Before inventory close is performed, these two transactions can still be marked to each other. When a receipt transaction is marked to an issue transaction, the valuation method that is defined in the item’s item model group will be disregarded. Instead, the system settles these transactions to each other. 

You can mark an issue transaction to a receipt before the transaction is posted. You can do this from a sales order line on the **Sales order details** page. You can view the open receipt transactions on the **Marking** page. You can mark an issue transaction to a receipt after the transaction is posted. You can match or mark an issue transaction for an open receipt transaction for an inventoried item from a posted inventory adjustment journal. The following illustration shows these transactions:

-   1a. Inventory physical receipt for a quantity of 1 at a cost price of USD 10.00 each.
-   1b. Inventory financial receipt for a quantity of 1 at a cost price of USD 10.00 each.
-   2a. Inventory physical receipt for a quantity of 1 at a cost price of USD 20.00 each.
-   2b. Inventory financial receipt for a quantity of 1 at a cost price of USD 20.00 each.
-   3a. Inventory physical receipt for a quantity of 1 at a cost price of USD 25.00 each.
-   4a. Inventory physical receipt for a quantity of 1 at a cost price of USD 30.00 each.
-   4b. Inventory financial receipt for a quantity of 1 at a cost price of USD 30.00 each.
-   5a. Inventory physical issue for a quantity of 1 at a cost price of USD 21.25 (running average of financial and physical updated transactions).
-   5b. Inventory financial issue for a quantity of 1 is marked to the inventory receipt 2b before the transaction is posted. This transaction is posted at a cost price of USD 20.00.
-   6a. Inventory physical issue for a quantity of 1 at a cost price of USD 21.25.
-   7. Inventory close is performed. Because the financially updated transaction is marked to an existing receipt, these transactions are settled to each other, and no adjustment is made.

The new running average cost price reflects the average of the financially and physically updated transactions at USD 27.50. The following illustration shows this series of transactions, and the effects of using the weighted average date inventory model and marking.

![Weighted average date with marking.](./media/weightedaveragedatewithmarking.gif) 

**Key to the illustration:**

-   Inventory transactions are represented by vertical arrows.
-   Receipts into inventory are represented by vertical arrows above the timeline.
-   Issues out of inventory are represented by vertical arrows below the timeline.
-   Above or below each vertical arrow, the value of the inventory transaction is specified in the form *Quantity*@*Unit price*.
-   If an inventory transaction value is enclosed in parentheses, the inventory transaction is physically posted into inventory.
-   If an inventory transaction value isn't enclosed in parentheses, the inventory transaction is financially posted into inventory.
-   Each new receipt or issue transaction is designated by a new label.
-   Each vertical arrow is labeled with a sequential identifier, such as *1a*. The identifiers indicate the sequence of inventory transaction postings in the timeline.
-   Inventory closings are represented by a red vertical dashed line and the label *Inventory Close*.
-   Settlements that are performed by inventory close are represented by dashed red arrows that go diagonally from a receipt to an issue.






[!INCLUDE[footer-include](../../includes/footer-banner.md)]
