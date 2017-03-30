---
# required metadata

title: Running average cost price
description: The inventory close process settles issue transactions to receipt transactions, based on the inventory valuation method that is selected in the item’s item model group. However, before inventory close is run, the system calculates a running average cost price that is typically used when issue transactions are posted.
author: YuyuScheller
manager: AnnBe
ms.date: 2016-04-07 15 - 11 - 47
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: InventModelGroup, InventOnhandItem, InventTrans
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2094
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 79003
ms.assetid: adc3f245-dc9d-4327-88fb-6a579194a5fe
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: mguada
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Running average cost price

The inventory close process settles issue transactions to receipt transactions, based on the inventory valuation method that is selected in the item’s item model group. However, before inventory close is run, the system calculates a running average cost price that is typically used when issue transactions are posted.

The system estimates this running average cost price for an item by using the following formula: 
Estimated price = (Physical amount + Financial amount) ÷ (Physical quantity + Financial quantity)

## Using the running average cost price
The following table shows when the system posts inventory transactions by using the running average cost price, and when it uses the cost price that is defined on the item master record instead.

| Condition                                               | The system uses the estimated running average cost price | The system uses the cost price that is defined on the item master |
|---------------------------------------------------------|----------------------------------------------------------|-------------------------------------------------------------------|
| Both the numerator\* and denominator\*\* are positive.  | Yes                                                      | No                                                                |
| The numerator\*, denominator\*\*, or both are negative. | No                                                       | Yes                                                               |
| The denominator\*\* is 0 (zero).                        | No                                                       | Yes                                                               |

\* Numerator = (Physical amount + Financial amount) \*\* Denominator = (Physical quantity + Financial quantity) 
**Note:** If the **Include physical value** option isn't selected for an item, the system uses 0 (zero) for both the physical amount and the physical quantity. For information about this option, see [Include physical value](include-physical-value.md).

## Avoiding pricing amplification
On rare occasions, the system prices several issues before it has enough receipts to base the price on. This scenario can cause estimates of the running average cost price to be overly inflated. However, there are steps that you can take to avoid pricing amplification, or to reduce its impact when it does occur. **Scenario** The following transactions occur for an item that you've selected the **Include physical value** option for:

1.  You financially receive a quantity of 100 at USD 100.00.
2.  You financially issue a quantity of 200.
3.  You physically receive a quantity of 101 at USD 202.00.

When you examine the estimated running average cost price for the item, you expect a cost price of USD 1.51. Instead, you find an estimated running average of USD 102.00, which is based on the following formula: Estimated price = \[202 + (-100)\] ÷ \[101 + (-100)\] = 102 ÷ 1 = 102 This pricing amplification occurs because, when 200 items are issued financially in step 2, the system must price 100 of the items before it has any corresponding receipts. This situation causes negative inventory. The system then estimates a unit price of USD 1.00, as we might expect. However, when the corresponding 100 receipts arrive, they are at a unit price of USD 2.00 each. 

**Note:** Although the issues create negative inventory, inventory is positive when the issue price is calculated. Therefore, the running average cost price is used instead of the price on the item master. At this point, the system has an inventory value offset of USD 100.00. Although that offset was built up over 100 pieces, where there was a unit offset of USD 1.00 each, we now have only one piece in inventory. Therefore, the offset of USD 100.00 is allocated to this one piece. The result is the overly inflated estimated cost price. 

**Note:** For comparison, notice that if steps 2 and 3 are reversed in the scenario, 200 items will be issued at a unit price of USD 1.51, and one piece will remain at a unit price of USD 1.51. Because this pricing amplification scenario can occur when negative inventory is involved, it's difficult to avoid in the following cases:

-   You must estimate issue prices on the on-hand value and quantity.
-   You must adjust the on-hand value and quantity on issues and receipts.
-   Your business model allows you to send out, or price, more pieces than you have.
-   You must accept any receipt value and quantity that are submitted to you.

However, if your business model allows for the following practices, they can help you avoid the negative quantities that make the pricing amplification scenario possible:

-   If you select the **Include physical value** option for an item, clear the **Physical negative inventory** check box on the **Item model groups** page.
-   If you do *not* select the **Include physical value** option for an item, clear the **Financial negative inventory** option on the **Item model groups** page.

Additionally, consider that the maximum offset in your physical inventory value is limited by the number of physical transactions, and the difference between physical and financial prices. Provided that all physical transactions are eventually updated financially, the physical value can't rise to extreme levels. Finally, note that the amplification effect decreases significantly when the accumulated offset is spread out over several on-hand pieces instead of just one.

