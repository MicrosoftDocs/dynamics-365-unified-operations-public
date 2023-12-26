---
# required metadata

title: Moving average
description: Moving average is a perpetual costing method based on the average principle, where the costs on inventory issues do not change when the purchase cost does. The difference is capitalized and is based on a proportional calculation. The amount that remains is expensed. 
author: JennySong-SH
ms.date: 08/28/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: InventModelGroup
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: dfd10099-8f7f-44b1-917e-df37c2fe8773
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yanansong
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Moving average

[!include [banner](../includes/banner.md)]

Moving average is a perpetual costing method based on the average principle, where the costs on inventory issues do not change when the purchase cost does. The difference is capitalized and is based on a proportional calculation. The amount that remains is expensed.

When you use moving average, inventory settlements and inventory marking are not supported. Inventory close does not affect products that have moving average as the inventory model group, and it does not generate any settlements between the transactions.

The following are prerequisites when you use moving average cost as a costing method.

1. On the **Item model groups** page, set up an item model group that has **Moving average** selected in the **Inventory model** field.

    > [!NOTE]
    > By default, when **Moving average** is selected, the **Post physical inventory** and **Post financial inventory** fields are also selected.

1. On the **Posting** page, assign accounts to the **Price difference for moving average**. You use the **Price difference for moving average** account when cost has to be proportionally expensed. This occurs in following two scenarios:
    - There is a difference in cost between a purchase receipt and the purchase invoice because there is a difference between the original inventory quantity and the current on-hand quantity.
    - The transactions bring the inventory from negative to zero, and there is a difference between the transaction cost and the current moving average cost.

1. On the **Posting** page, assign accounts to the **Cost revaluation for moving average** accounts on the **Inventory** tab. You use the **Cost revaluation for moving average** account when you want to adjust the moving average cost for a product to a new unit price.

1. On the **Released products** page, assign the moving average item model group to the product.

    > [!NOTE]
    > The inventory close process only closes the accounting period. It does not affect products that have moving average assigned to them as an item model group.

## Convert to the moving average costing method

Products can be converted to use the moving average inventory valuation method. This type of conversion is usually done at the end of the year, after the last month of the current year is closed. It is done by using the product’s current costing model. You can change your inventory costing method from a costing method that is based on average cost or standard cost to a method that is based on moving average.

If you are changing your costing method from a standard costing method to a moving average method, you have to complete the following tasks:

1. Make adjustments to get inventory quantities and values down to 0 (zero).
1. After the inventory value and quantity are 0 (zero), change the item model group to moving average.
1. Make adjustments to get the quantity and value back into inventory.

You cannot change your inventory costing method from a moving average method to a First in, First out (FIFO) method, a Last in, First out (LIFO) method, or a weighted average method.

> [!NOTE]
> Converting from standard cost to moving weighted average is a manual process.

The following examples illustrate the effect of using the moving average costing method. There are four configurations:

- Purchase order and proportionally expensed cost difference
- Moving average product and inventory adjustment
- Moving average with production
- Moving average with a backdated transaction

## Purchase order and proportionally expensed cost difference

With moving average, the product’s cost is determined by the purchase receipt. When the purchase invoice is posted, if there is a difference in cost between the purchase receipt and the purchase invoice, the difference is proportionally adjusted to the current products in stock, and any remaining amount is expensed.

In this example, a purchase order is created and received at one cost, and the purchase invoice is posted with a different cost.

1. Create a purchase order for a quantity of 2 and a unit price of 10.00.
1. Create a purchase receipt of the product.
1. Create a sales order for a quantity of 1 and a unit price of 10.00.
1. Create a purchase invoice for a quantity of 2 and a unit price of 12.00.

The difference in unit price, 2.00, is posted to the Price difference for moving average account when the purchase invoice is posted. The reason is that two products were purchased for a cost of 20.00. One of the products was sold for a unit price of 10.00. The purchase invoice was posted at a unit price of 12.00 with a quantity of 2. The unit price of the product cannot be posted at 14.00.

## Moving average product and inventory adjustment

If you need to adjust the moving average cost of a product, inventory adjustments are allowed as of today’s date. You cannot backdate an inventory adjustment to correct the moving average cost of a product. You cannot have the cost flow through subsequent transactions.

In this example, the moving average cost is adjusted for a product.

1. Select the product that you want to adjust the moving average cost for. 

 > [!NOTE]
 > The **Revaluation for moving average** page examines the inventory available for a product. The product selected has a posted quantity of 1, a posted a value of 12.00, a posted unit cost of 12.00, and a unit cost of 12.00.
    
1. Update the **Unit cost** field to 16.00. The system calculates the remaining fields.
1. The adjustment is posted.

> [!NOTE]
> You can only adjust the moving average cost as of today’s date.

On the **Settlements for voucher** page, you can see an adjustment of 4.00 posted to the Cost revaluation for moving average account.

## Moving average with production

Moving average supports produced items. If you plan to use moving average in a production environment, select **Use estimated cost price** on the **Production control parameters** page. This means that the cost price that is calculated during estimation is used instead of the actual BOM calculation cost price.

## Moving average with a backdated transaction

Backdated transactions are assigned the current moving average cost, and the product’s physical quantity is updated, but the product’s moving average cost is not affected. In this moving average example, a backdated transaction for a moving average product is posted.

1. Create an inventory adjustment for the moving average product for a quantity of 1 and a cost of 20.00.
1. The inventory transaction history for the product would resemble the following:
    - An inventory transaction of 1, a cost of 16.00, a posting date of January 15, and a transaction date of January 15.
    - An inventory adjustment of 1, a cost of 20.00, a posting date of January 1, and a transaction date of January 15.
1. Post the adjustment.

On the **Inventory transactions** page, you can see that 4.00 is expensed as the current moving average for the product is 16.00. You can post in the past, but the difference in cost is expensed, so the moving average cost is not affected.

## Negative inventory balances

Transactions are handled differently depending on whether the new on-hand quantity after the transaction is negative, zero, or positive.

### New balance is negative or zero

If the new on-hand quantity is negative or zero, the transaction is costed at the current average costs. If there is a difference between the purchase price and the current average costs, it's posted to **Price difference for moving average**.

### New balance is positive

If the new on-hand quantity is positive after the transaction, the transaction is split into two parts and costed differently, as summarized in the following table.

| Part | Description |
|---|---|
| Quantity from negative to zero | Inventory uses the current moving average cost of the item rather than the transaction cost for that portion of the receipt quantity that increases the on-hand balance from negative to zero. The difference between the transaction cost and the current moving average cost is posted to **Price difference for moving average**. |
| Quantity from zero to positive | Inventory uses the transaction cost for that portion of the receipt quantity that increases the on-hand balance from zero to positive.                                                  |

## Inventory value report

In this moving average example, the inventory value report is printed to support the current moving average calculation for a product. The Inventory value report can print the transactions in chronological order, together with the cost to support the moving average cost calculation of a product. The report displays the moving average cost for the product. In the **Inventory value reports** dialog box, a date interval allows you to select the **Transaction time** or the **Posting date** to sort the report by. The **Posting date** option is how the report is traditionally printed. The **Transaction time** option is the actual date that the transaction is reported and the moving average cost for the product is updated. You can print the Inventory value report by using the **Transaction time sorting** option if you want to see the moving average cost calculation over time. The following table displays the transactions for the product that the report is printed for when the **Transaction time sorting** option is used.

| Transaction time | Date         | Transaction type           | Quantity | Amount | Average unit cost |
|------------------|--------------|----------------------------|----------|--------|-------------------|
|                  | October 1    | Beginning balance          | 0        | 0.00   | 0.00              |
| October 8        | September 28 | Backdated receipt          | 1        | 16.00  | 16.00             |
| October 3        | October 3    | Purchase receipt           | 2        | 20.00  | 12.00             |
| October 5        | October 5    | Sales order                | -1       | -10.00 | 13.00             |
| October 7        | October 7    | Purchase invoice           |          | 2.00   | 14.00             |
| October 8        | October 8    | Moving average revaluation |          | 4.00   | 16.00             |
|                  | October 31   | Total                      | 2        | 32.00  | 16.00             |

> [!NOTE]
> You cannot reconcile the general ledger with inventory by using the **Transaction time sorting** option. The report must be printed by using the **Posting date** option.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]