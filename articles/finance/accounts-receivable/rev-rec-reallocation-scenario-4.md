---
# required metadata

title: Revenue recognition reallocation - scenario 4
description: This topic walks through a reallocation scenario where a new line is removed from an existing, partially invoiced sales order. The results of this scenario are the same whether the lines are removed from the sales order or are set to a canceled status.
author: kweekley
manager: aolson
ms.date: 12/21/2020
ms.topic: index-page
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: Customer
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2020-12-21
ms.dyn365.ops.version: 10.0.14

---

# Revenue recognition reallocation - scenario 4

This topic walks through a reallocation scenario where a new line is removed from an existing, partially invoiced sales order. The results of this scenario are the same whether the lines are removed from the sales order or are set to a canceled status.

The General ledger parameter, **Post invoice corrections to Accounts receivable** is set to  No.
 
[![General ledger parameters setting for fourth scenario](./media/37_rev-rec-scenarios.png)](./media/37_rev-rec-scenarios.png)

A sales order is created for customer US_SI_0003. The customer is purchasing a laptop (S0012), installation services (S0001) and support (S0008) for the laptop.  The laptop and install services’ revenue will be recognized immediately and revenue from the support plan will be deferred and recognized over 12 months, as defined by the date range defined in the contract. 

[![Sales order lines with purchase of laptop](./media/38_rev-rec-scenarios.png)](./media/38_rev-rec-scenarios.png)

The sales order is confirmed. All items are setup for revenue price allocation so confirmation calculates the revenue price. The Revenue to recognize can be seen from the **Sales order** Action Pane, under **Manage > Revenue recognition > Revenue price allocation**. The laptop’s revenue will post to Revenue for $995.84, the installation service’s revenue will post for $314.47, and the sustained engineering service will post to a Deferred revenue account in the amount $188.69.  The sum of the revenue prices must equal the sum of the lines that have been set up for revenue price allocation, which is equal to $1,499.00.  

[![Revenue price allocation showing revenue to recognize](./media/39_rev-rec-scenarios.png)](./media/39_rev-rec-scenarios.png)

The customer is invoiced for the laptop and sustained engineering service but not the installation service.  The following accounting entry is posted for the invoice.

[![Voucher transactions showing posted invoice](./media/40_rev-rec-scenarios.png)](./media/40_rev-rec-scenarios.png)

The entry posts $1,276.94 to Accounts receivable, but because this is a partial invoice, the revenue or deferred revenue plus the tax does not equal the accounts receivable amount.  The difference of -$14.47 is posted to the Partial invoice revenue clearing account. 
The revenue recognition schedule is also created.  

[![Revenue recognition schedule for a partial invoice](./media/41_rev-rec-scenarios.png)](./media/41_rev-rec-scenarios.png)

The customer decides to not purchase the install service so that line is removed from the sales order.  Note that the sales order cannot be confirmed again because there are only invoiced lines remaining on the sales order.

[![Sales order that can't be confirmed again](./media/42_rev-rec-scenarios.png)](./media/42_rev-rec-scenarios.png)

Even though the sales order can’t be confirmed, it can reallocated. From the sales order, open **Reallocate price with new order lines**.  With the two sales order lines selected, choose **Update reallocation**.  The Reallocated amount column is updated for the two remaining lines. 

[![Reallocated price with new order lines for fourth scenario](./media/43_rev-rec-scenarios.png)](./media/43_rev-rec-scenarios.png)

Next select **Expected voucher** to see the accounting entries.  
 
[![Expected voucher selected to show accounting entries](./media/44_rev-rec-scenarios.png)](./media/44_rev-rec-scenarios.png)

The last five lines are reversing the original accounting entry from the posted invoice. 

The top four lines are the new accounting entries that are posted for the invoice. It’s important to understand that the customer is not presented with a new invoice.  After the reallocation, the customer still owes $1,276.94 which is the amount that must post to Accounts receivable in the new accounting entry.  The new revenue or deferred revenue amounts plus tax equals $1,276.94 so you won’t need to post to the Partial invoice revenue clearing account. 

You can then complete the reallocation by clicking the **Process** button. A posting date is entered. The **Revenue price allocation** page now displays the price reallocation for the two remaining items.

[![Revenue price allocation for remaining items](./media/45_rev-rec-scenarios.png)](./media/45_rev-rec-scenarios.png)

The revenue recognition schedule was also updated based on the new revenue reallocation price.  From the sales order, open the **Revenue recognition schedule** page.  Previously there were 13 lines for item S0008 which was assigned a 12-month schedule. Now there are 39 lines: 13 original schedule lines, 13 reversal schedule lines, and 13 lines based on the new revenue price.  

[![Revenue recognition schedule showing original schedule, reversed schedule, and new revenue price](./media/46_rev-rec-scenarios.png)](./media/46_rev-rec-scenarios.png)

The Invoice journal displays the original accounting entry when you click **Voucher**. To see the reversing and new accounting entry from the sales order, click the **Revenue adjustments** button from the Action Pane, then click **Voucher**.

Next open the **All customers** page (**Accounts receivable >Customers > All customers**, select customer US_SI_0003, and then click the **Transactions** button.  Only the original invoice (000008) can be seen with the original accounting entry. The reversing and updated accounting entries are not shown because the General ledger parameter was set to only update General ledger. Note that you can see the revenue adjustment transactions created from Scenario 3. 

[![Accounting entries on All customers page with updated accounting entries not shown](./media/47_rev-rec-scenarios.png)](./media/47_rev-rec-scenarios.png)

