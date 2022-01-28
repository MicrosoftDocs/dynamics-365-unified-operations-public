---
# required metadata

title: Running average cost price
description: The inventory close process settles issue transactions to receipt transactions, based on the inventory valuation method that is selected in the item’s item model group. However, before inventory close is run, the system calculates a running average cost price that is typically used when issue transactions are posted.
author: AndersGirke
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: InventModelGroup, InventOnhandItem, InventTrans
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac


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

[!include [banner](../includes/banner.md)]

The inventory close process settles issue transactions to receipt transactions, based on the inventory valuation method that is selected in the item’s item model group. However, before inventory close is run, the system calculates a running average cost price that is typically used when issue transactions are posted.

The system estimates this running average cost price for an item by using the following formula: 

Estimated price = (Physical amount + Financial amount) ÷ (Physical quantity + Financial quantity)

## Default item cost
The default item cost for a released product can be configured in one of two ways.
1. You can create a standard cost by using the **Item price** button on the **Released product** page in the **Manage costs** tab in the Action Pane. With this option you must use a standard cost costing verion and the cost must be activated.
2. You can define a default item cost price for a released product on the **Manage costs** FastTab in the **Released product details** page by entering a **Price**.

In addition to entering or creating a price, you can select the **Use latest cost price** check box on the **Manage costs** FastTab in the **Released product details** page. When you enable the **Use latest cost price** option, the system will automatically update the **Price** field when you post a financial update. For example, if you post a purchase order invoice, the field will populate with the purchase price from that invoice.  

If you have a cost price in an active costing version, and enter a price on the **Manage costs** FastTab, the system will use the price from the active costing version before it will use the **Price** defined on the **Manage costs** FastTab.

## Using the running average cost price
The following table shows when the system posts inventory transactions by using the running average cost price, and when it uses the cost price that is defined on the item master record instead.

| Condition                                               | The system uses the estimated running average cost price | The system uses the default item cost price |
|---------------------------------------------------------|----------------------------------------------------------|---------------------------------------------|
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

## Avoid a zero cost price on issues 
When you do not select the **Include physical value** option on the **Item model group** page, it is possible that an issue from inventory can have a zero cost price if there are no financially updated receipts in inventory. To avoid this scenario, there are a few options to consider.
-   Select the **Include physical value** option on the **Item model group**. This option will prevent a zero cost price on an issue as long as the receipt is physically updated. If you do not allow negative physical inventory, then issues will calculate the running average from the physically updated transactions.
-   Create a default item cost price by activating a costing verion with a standard cost, or enter the price on the **Manage costs** FastTab on the **Released product details** page. This is the best option when you do not select the **Include physical value** option on the **Item model group** page becuase the system will always have a fallback price to use.
-   Select the option to **Use latest cost price** on the the **Manage costs** FastTab on the **Released product details** page. This option will keep the **Price** field up to date each time you financially update a receipt. If you select this option, but do not enter a default price or activate a cost in a standard costing version, you can still have a zero cost on an issue. 

If you have issue transactions with zero cost, the Inventory close and adjustment process will correct the cost price by creating an ajustment once the receipts are financially updated. Keep in mind that this update may happen in a different financial period than when the items were physically received or issued.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
