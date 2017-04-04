---
# required metadata

title: LIFO Date with physical value and marking
description: Last in, First out Date (LIFO Date) is an inventory model based on the LIFO principle. Issues from inventory are settled against the last receipts into inventory based on the date of the inventory transaction. By using LIFO Date, if there is no receipt before the issue, the issue is settled against any receipts that occur after the date of the issue. Several issues on the same date may be settled in the order of last issue, last receipt. 
author: YuyuScheller
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: InventJournalLossProfit, InventMarking, InventModelGroup, SalesTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 121
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 51592
ms.assetid: d9f13274-3268-444f-85c8-b686fd39286d
ms.search.region: Global
ms.search.industry: Retail
ms.author: yuyus
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# LIFO Date with physical value and marking

Last in, First out Date (LIFO Date) is an inventory model based on the LIFO principle. Issues from inventory are settled against the last receipts into inventory based on the date of the inventory transaction. By using LIFO Date, if there is no receipt before the issue, the issue is settled against any receipts that occur after the date of the issue. Several issues on the same date may be settled in the order of last issue, last receipt. 

When you use the Last in, First out Date (LIFO Date) inventory model, if there is no receipt before the issue, the issue is settled against any receipts that occur after the date of the issue. Several issues on the same date can be settled in the order of last issue, last receipt. When you use LIFO Date, you don't have to use the LIFO Date rule. Instead, you can mark inventory transactions so that a specific item receipt is settled against a specific issue. 

We recommend a periodic inventory closing when you use the LIFO Date inventory model. 

The following examples show the effect of using LIFO Date in three configurations:

-   LIFO Date without the **Include physical value** option
-   LIFO Date with the **Include physical value** option
-   LIFO Date with marking

## LIFO Date without the Include physical value option
In this example, the item model group isn't marked to include physical value. The illustration that follows shows these transactions:

-   1a. Inventory physical receipt for a quantity of 1 at a cost of USD 10.00 each.
-   1b. Inventory financial receipt for a quantity of 1 at a cost of USD 10.00 each.
-   2a. Inventory physical receipt for a quantity of 1 at a cost of USD 20.00 each.
-   2b. Inventory financial receipt for a quantity of 1 at a cost of USD 20.00 each.
-   3a. Inventory physical receipt for a quantity of 1 at a cost of USD 25.00 each.
-   4a. Inventory physical issue for a quantity of 1 at a cost price of USD 15.00 (running average of financially updated transactions).
-   4b. Inventory financial issue for a quantity of 1 at a cost price of USD 15.00 (running average of financially updated transactions).
-   5a. Inventory physical receipt for a quantity of 1 at a cost of USD 30.00 each.
-   5b. Inventory financial receipt for a quantity of 1 at a cost of USD 30.00 each.
-   6. Inventory close is performed. Based on the LIFO Date method, the last financially updated issue will be settled against the last financially updated receipt by date. An adjustment of USD 5.00 will be made on the issue transaction. These transactions will be settled against each other.

The new running average cost price reflects the average of the financially updated transactions at USD 15.00. 

The following illustration shows the effects of the LIFO Date inventory model when the **Include physical value** option isn't used. ![LIFO Date with Include Physical Value](./media/lifodatewithoutincludephysicalvalue.gif) 

**Key to the diagram**

-   Inventory transactions are represented by vertical arrows.
-   Receipts into inventory are represented by vertical arrows above the timeline.
-   Issues out of inventory are represented by vertical arrows below the timeline.
-   Above (or below) each vertical arrow, the value of the inventory transaction is specified in the format Quantity@Unitprice.
-   An inventory transaction value that is enclosed in parentheses indicates that the inventory transaction is physically posted into inventory.
-   An inventory transaction value that isn't enclosed in parentheses indicates that the inventory transaction is financially posted into inventory.
-   Each new receipt or issue transaction is designated by a new label.
-   Each vertical arrow is labeled with a sequential identifier, such as *1a*. The identifiers indicate the order of inventory transaction postings in the timeline.
-   Inventory closings are represented by a red vertical dashed line and the label *Inventory Close*.
-   Settlements that are performed by inventory close are represented by red diagonal dashed arrows that go from a receipt to an issue.

## LIFO Date with the Include physical value option
You can select the **Include physical value** check box for an item on the **Item model groups** page. In this case, the system uses both physical and financial receipt transactions to calculate the running average cost price. Where applicable, the system also makes adjustments to the physically updated issue transaction. When the **Include physical value** check box is cleared, inventory close that uses the LIFO Date inventory model makes settlements only to transactions that are financially updated. 

In this example, the item model group is marked to include physical value. 

The illustration that follows shows these transactions:

-   1a. Inventory physical receipt for a quantity of 1 at a cost of USD 10.00 each.
-   1b. Inventory financial receipt for a quantity of 1 at a cost of USD 10.00 each.
-   2a. Inventory physical receipt for a quantity of 1 at a cost of USD 20.00 each.
-   2b. Inventory financial receipt for a quantity of 1 at a cost of USD 20.00 each.
-   3a. Inventory physical receipt for a quantity of 1 at a cost of USD 25.00 each.
-   4a. Inventory physical issue for a quantity of 1 at a cost price of USD 18.33 each (running average of financially updated transactions).
-   4b. Inventory financial issue for a quantity of 1 at a cost price USD 18.33 each (running average of financially updated transactions).
-   5a. Inventory physical receipt for a quantity of 1 at a cost of USD 30.00 each.
-   5b. Inventory financial receipt for a quantity of 1 at a cost of USD 30.00 each.
-   6. Inventory close is performed. Based on the LIFO Date method, the last updated issue will be adjusted or settled against the last updated receipt by date. These transactions will not be settled by each other, because the financial receipt transaction is adjusted to a physical update transaction. Instead, only an adjustment of USD 6.67 will be made on the issue transaction.

The new running average cost price reflects the average of the financially updated transactions at USD 20.00. 

The following illustration shows the effects of the LIFO inventory model when the **Include physical value** option is used. ![LIFO Date with Include Physical Value](./media/lifodatewithincludephysicalvalue.gif) 

**Key to the diagram**

-   Inventory transactions are represented by vertical arrows.
-   Receipts into inventory are represented by vertical arrows above the timeline.
-   Issues out of inventory are represented by vertical arrows below the timeline.
-   Above (or below) each vertical arrow, the value of the inventory transaction is specified in the format Quantity@Unitprice.
-   An inventory transaction value that is enclosed in parentheses indicates that the inventory transaction is physically posted into inventory.
-   An inventory transaction value that isn't enclosed in parentheses indicates that the inventory transaction is financially posted into inventory.
-   Each new receipt or issue transaction is designated by a new label.
-   Each vertical arrow is labeled with a sequential identifier, such as *1a*. The identifiers indicate the order of inventory transaction postings in the timeline.
-   Inventory closings are represented by a red vertical dashed line and the label *Inventory Close*.
-   Settlements that are performed by inventory close are represented by red diagonal dashed arrows that go from a receipt to an issue.

## LIFO Date with marking
Marking is a process that lets you link, or mark, an issue transaction to a receipt transaction. Marking can occur either before or after a transaction is posted. You can use marking when you want to be sure of the exact cost of inventory when the transaction is posted or the inventory close is performed. 

For example, the Customer Service department accepted a rush order from an important customer. Because this order is a rush order, you will have to pay more for this item in order to fulfill your customer’s request. You must make sure that the cost of this inventory item is reflected in the margin, or cost of goods sold (COGS), for this sales order invoice. 

When the purchase order is posted, the inventory is received at a cost of USD 120.00. If this sales order document is marked to the purchase order before the packing slip or invoice is posted, the COGS will be USD 120.00, not the current running average cost for the item. If the sales order packing slip or invoice is posted before the marking occurs, the COGS will be posted at the running average cost price. 

Before inventory close is performed, these two transactions can still be marked to each other. 

For example, a receipt transaction is marked for an issue transaction. In this case, the valuation method that is defined in the item’s item model group is disregarded, and the system settles these transactions against each other. 

You can mark an issue transaction to a receipt before the transaction is posted. You can do this from a sales order line on the **Sales order details** page. You can view the open receipt transactions on the **Marking** page. 

You can also mark an issue transaction to a receipt after the transaction is posted. You can match or mark an issue transaction for an open receipt transaction for an inventoried item from a posted inventory adjustment journal. 

The illustration that follows shows these transactions:

-   1a. Inventory physical receipt for a quantity of 1 at a cost of USD 10.00 each.
-   1b. Inventory financial receipt for a quantity of 1 at a cost of USD 10.00 each.
-   2a. Inventory physical receipt for a quantity of 1 at a cost of USD 20.00 each.
-   2b. Inventory financial receipt for a quantity of 1 at a cost of USD 20.00 each.
-   3a. Inventory physical receipt for a quantity of 1 at a cost of USD 25.00 each.
-   4a. Inventory physical receipt for a quantity of 1 at a cost of USD 30.00 each.
-   4b. Inventory financial receipt for a quantity of 1 at a cost of USD 30.00 each.
-   5a. Inventory physical issue for a quantity of 1 at a cost price of USD 21.25 each (running average of financial and physical updated transactions).
-   5b. Inventory financial issue for a quantity of 1 is marked to inventory receipt 2b before the transaction is posted. This transaction is posted with a cost price of USD 20.00 each.
-   6a. Inventory physical issue for a quantity of 1 at a cost price of USD 21.25 each.
-   7. Inventory close is performed. Because the financially updated First in, First out (FIFO) transaction is marked to an existing receipt, these transactions are settled to each other, and no adjustment is made.

The new running average cost price reflects the average of the financially and physically updated transactions at USD 27.50. 

The following illustration shows the effects of the LIFO inventory model when marking between issues and receipts is used. ![LIFO Date with Marking](./media/lifodatewithmarking.gif) 

**Key to the diagram**

-   Inventory transactions are represented by vertical arrows.
-   Receipts into inventory are represented by vertical arrows above the timeline.
-   Issues out of inventory are represented by vertical arrows below the timeline.
-   Above (or below) each vertical arrow, the value of the inventory transaction is specified in the format Quantity@Unitprice.
-   An inventory transaction value that is enclosed in parentheses indicates that the inventory transaction is physically posted into inventory.
-   An inventory transaction value that isn't enclosed in parentheses indicates that the inventory transaction is financially posted into inventory.
-   Each new receipt or issue transaction is designated by a new label.
-   Each vertical arrow is labeled with a sequential identifier, such as *1a*. The identifiers indicate the order of inventory transaction postings in the timeline.
-   Inventory closings are represented by a red vertical dashed line and the label *Inventory Close*.
-   Settlements that are performed by inventory close are represented by red diagonal dashed arrows that go from a receipt to an issue.


