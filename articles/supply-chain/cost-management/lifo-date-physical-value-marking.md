---
title: LIFO date with physical value and marking
description: Issues from inventory are settled against the last receipts into inventory based on the date of the inventory transaction.
author: prasungoel
ms.author: prasungoel
ms.reviewer: kamaybac
ms.search.form: InventJournalLossProfit, InventMarking, InventModelGroup, SalesTable
ms.topic: how-to
ms.date: 07/21/2025
ms.custom:
- bap-template
---

# LIFO date with physical value and marking

[!include [banner](../includes/banner.md)]

Last in, first out date (LIFO date) is an inventory management and valuation method where inventory that was produced or acquired last is sold, used, or disposed of first. During the inventory close process in Microsoft Dynamics 365 Supply Chain Management, the system creates settlements where the last receipt is matched against the first issue for each given date starting with the oldest date first, and so on. When you use the last in, first out date (LIFO date) inventory model, if there's no receipt before the issue, the issue is settled against any receipts that occur after the date of the issue. The settlements and matching principle are based on the financial date of the inventory transactions. When there are several issues on the same date, they're settled in the order of last issue, last receipt. A preliminary assessment of the settlements and adjustments can be performed by running the inventory recalculation process.

You can override the LIFO date principle by marking inventory transactions so that a specific item receipt is settled against a specific issue. A periodic inventory close is required when you use the LIFO date inventory model to create settlements and adjust the value of issues according to the LIFO principle. Until you run the inventory close process, issue transactions are valued at the running average when the physical and financial updates occurred. Unless you're using marking, the running average is calculated when the physical or financial update is performed.

We recommend a periodic inventory closing when you use the LIFO date inventory model.

The following examples show the effect of using LIFO date in three configurations:

- LIFO date without the **Include physical value** option
- LIFO date with the **Include physical value** option
- LIFO date with marking

## LIFO date without the Include physical value option

In this example, the item model group isn't marked to include physical value. The illustration that follows shows these transactions:

- 1a. Inventory physical receipt for a quantity of 1 at a cost of USD 10.00 each.
- 1b. Inventory financial receipt for a quantity of 1 at a cost of USD 10.00 each.
- 2a. Inventory physical receipt for a quantity of 1 at a cost of USD 20.00 each.
- 2b. Inventory financial receipt for a quantity of 1 at a cost of USD 22.00 each.
- 3a. Inventory physical issue for a quantity of 1 at a cost price of USD 16.00 (running average of financially posted transactions).
- 3b. Inventory financial issue for a quantity of 1 at a cost price of USD 16.00 (running average of financially posted transactions).
- 4a. Inventory physical receipt for a quantity of 1 at a cost of USD 25.00 each.
- 5a. Inventory physical receipt for a quantity of 1 at a cost of USD 30.00 each.
- 5b. Inventory financial receipt for a quantity of 1 at a cost of USD 30.00 each.
- 6a. Inventory physical issue for a quantity of 1 at a cost price of USD 23.00 (running average of financially posted transactions)
- 7\. Inventory close is performed. Based on the LIFO date method, the first financially updated issue is settled against the last financially updated receipt starting on the first date, and so on. In this example, one settlement is created between 3b and 2b. An adjustment of USD 6.00 is made to 3b, and the resulting final cost is USD 22.00.

The following illustration shows the effects of the LIFO date inventory model when the **Include physical value** option isn't used.

![LIFO date without the Include physical value option.](media/lifo-date-without-include-physical-value.png)

**Key to the diagram**

- Inventory transactions are represented by vertical arrows.
- Physical transactions are represented by shorter light gray arrows.
- Financial transactions are represented by longer black arrows.
- Receipts into inventory are represented by vertical arrows above the axis.
- Issues out of inventory are represented by vertical arrows below the axis.
- Each new receipt or issue transaction is designated by a new label.
- Each vertical arrow is labeled with a sequential identifier, such as *1a*. The identifiers indicate the order of inventory transaction postings in the timeline.
- Each date in the diagram is separated by a thin black vertical line. The date is noted at the bottom of the diagram.
- Inventory closings are represented by a red vertical dashed line.
- Settlements that are performed by inventory close are represented by red diagonal dashed arrows that go from a receipt to an issue.

## LIFO date with the Include physical value option

If the **Include physical value** checkbox is selected for an item on the **Item model groups** page, the system uses both physical and financial receipt transactions to calculate the running average cost price. Where applicable, the system also adjusts the physically updated issue transaction. When the **Include physical value** checkbox is cleared, inventory close that uses the LIFO date inventory model makes settlements only to transactions that are financially updated.

In this example, the item model group is marked to include physical value. 

The illustration that follows shows these transactions:

- 1a. Inventory physical receipt for a quantity of 1 at a cost of USD 10.00 each.
- 1b. Inventory financial receipt for a quantity of 1 at a cost of USD 10.00 each.
- 2a. Inventory physical receipt for a quantity of 1 at a cost of USD 20.00 each.
- 2b. Inventory financial receipt for a quantity of 1 at a cost of USD 22.00 each.
- 3a. Inventory physical issue for a quantity of 1 at a cost price of USD 16.00 (running average of physically and financially posted transactions).
- 3b. Inventory financial issue for a quantity of 1 at a cost price of USD 16.00 (running average of physically and financially posted transactions).
- 4a. Inventory physical receipt for a quantity of 1 at a cost of USD 25.00 each.
- 5a. Inventory physical receipt for a quantity of 1 at a cost of USD 30.00 each.
- 5b. Inventory financial receipt for a quantity of 1 at a cost of USD 30.00 each.
- 6a. Inventory physical issue for a quantity of 1 at a cost price of USD 23.67 (running average of physically and financially posted transactions).
- 7\. Inventory close is performed. Based on the LIFO date method, the first financially updated issue is settled against the last financially updated receipt for each date starting on the first date, and so on. In this example, one settlement is created between 2b and 3b. An adjustment of USD 6.00 is made to 3b, and the resulting final cost is USD 22.00. Additionally, transaction 6a is adjusted to the receipt transaction cost of 5b. The system doesn't settle these transactions because the receipt is updated physically but not financially. Instead, only an adjustment of USD 6.33 is posted to the physical issue transaction, and the resulting adjusted cost is USD 30.00.

The following illustration shows the effects of the LIFO inventory model when the **Include physical value** option is used.

![LIFO date with the Include physical value option.](media/lifo-date-with-include-physical-value.png)

**Key to the diagram**

- Inventory transactions are represented by vertical arrows.
- Physical transactions are represented by shorter light gray arrows.
- Financial transactions are represented by longer black arrows.
- Receipts into inventory are represented by vertical arrows above the axis.
- Issues out of inventory are represented by vertical arrows below the axis.
- Each new receipt or issue transaction is designated by a new label.
- Each vertical arrow is labeled with a sequential identifier, such as *1a*. The identifiers indicate the order of inventory transaction postings in the timeline.
- Each date in the diagram is separated by a thin black vertical line. The date is noted at the bottom the diagram.
- Inventory closings are represented by a red vertical dashed line.
- Settlements that are performed by inventory close are represented by red diagonal dashed arrows that go from a receipt to an issue.

## LIFO date with marking

Marking is a process that lets you link, or mark, an issue transaction to a receipt transaction. Marking can occur either before or after a transaction is posted. You can use marking when you want to be sure of the exact cost of inventory when the transaction is posted or the inventory close is performed. For example, the Customer Service department accepted a rush order from an important customer. Because this order is a rush order, you must pay more for the item to fulfill the customer's request.

You must make sure that the cost of the inventory item is reflected in the margin, or cost of goods sold (COGS), for the sales order invoice. When the purchase order is posted, the inventory is received at a cost of USD 120.00. If this sales order document is marked to the purchase order before the packing slip or invoice is posted, the COGS will be USD 120.00, not the current running average cost for the item. If the sales order packing slip or invoice is posted before the marking occurs, the COGS will be posted at the running average cost price.

Before inventory close is performed, these two transactions can still be marked to each other.

You can mark an issue transaction to a receipt before the transaction is posted. You can do this marking from a sales order line on the **Sales order details** page by selecting **Inventory \> Marking** on the **Sales order lines** FastTab. You can view the open receipt transactions on the **Marking** page.

You can also mark an issue transaction to a receipt after the transaction is posted. You can match or mark an issue transaction for an open receipt transaction for an inventoried item from a posted inventory adjustment journal.

The illustration that follows shows these transactions:

- 1a. Inventory physical receipt for a quantity of 1 at a cost of USD 10.00 each.
- 1b. Inventory financial receipt for a quantity of 1 at a cost of USD 10.00 each.
- 2a. Inventory physical receipt for a quantity of 1 at a cost of USD 20.00 each.
- 2b. Inventory financial receipt for a quantity of 1 at a cost of USD 22.00 each.
- 3a. Inventory physical issue for a quantity of 1 at a cost price of USD 16.00 (running average of financially posted transactions).
- 3b. Inventory financial issue for a quantity of 1 at a cost price of USD 16.00 (running average of financially posted transactions).
- 3c. Inventory financial issue for 3b is marked to inventory financial issue for 1b.
- 4a. Inventory physical receipt for a quantity of 1 at a cost of USD 25.00 each.
- 5a. Inventory physical receipt for a quantity of 1 at a cost of USD 30.00 each.
- 5b. Inventory financial receipt for a quantity of 1 at a cost of USD 30.00 each.
- 6a. Inventory physical issue for a quantity of 1 at a cost price of USD 23.00 (running average of financially posted transactions)
- 7\. Inventory close is performed. Based on the marking principle that uses the LIFO date method, the marked transactions are settled against each other. In this example, 3b is settled against 1b, and an adjustment for USD -6.00 is posted to 3b to bring the value to USD 10.00. In this example, no additional settlements are made, because the close creates settlements only for financially updated transactions.

The following illustration shows the effects of the LIFO date inventory model when marking between issues and receipts is used. 

![LIFO date with Marking.](media/lifo-date-with-marking.png)

**Key to the diagram**

- Inventory transactions are represented by vertical arrows.
- Physical transactions are represented by shorter light gray arrows.
- Financial transactions are represented by longer black arrows.
- Receipts into inventory are represented by vertical arrows above the axis.
- Issues out of inventory are represented by vertical arrows below the axis.
- Each new receipt or issue transaction is designated by a new label.
- Each vertical arrow is labeled with a sequential identifier, such as *1a*. The identifiers indicate the order of inventory transaction postings in the timeline.
- Each date in the diagram is separated by a thin black vertical line. The date is noted at the bottom of the diagram.
- Inventory closings are represented by a red vertical dashed line.
- Settlements and markings that are performed by inventory close are represented by red diagonal dashed arrows that go from a receipt to an issue.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
