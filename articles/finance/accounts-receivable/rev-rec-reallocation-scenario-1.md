---
# required metadata

title: Revenue recognition reallocation - scenario 1
description: This topic walks through a reallocation scenario where two sales orders are entered, but only confirmed. The same scenario can be done with more than two sales orders in a confirmed state, with similar results. 
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

# Revenue recognition reallocation - scenario 1

This topic walks through a reallocation scenario where two sales orders are entered, but only confirmed. The same scenario can be done with more than two sales orders in a confirmed state, with similar results. The **Post invoice corrections to Accounts receivable** parameter is set to **No** on the **General ledger parameters** page.

[![General ledger parameter setting with post invoice corrections to Accounts receivable set to No](./media/06_rev-rec-scenarios.png)](./media/06_rev-rec-scenarios.png)

A sales order is created for customer US_SI_0003. The customer is purchasing a laptop (S0012) and a support plan (S0008) for the laptop.  The laptop’s revenue is recognized immediately (no revenue schedule) and revenue for the support plan will be deferred and recognized over 12 months as defined by the date range in the contract. 

[![New sales order lines showing laptop purchase](./media/07_rev-rec-scenarios.png)](./media/07_rev-rec-scenarios.png)

The sales order is confirmed. Both items are set up for revenue price allocation so confirmation calculates the revenue price. The Revenue to recognize can be seen from the **Sales order** Action Pane, (**Manage – Revenue recognition – Revenue price allocation**). The laptop’s revenue will post to the Revenue account in the amount of $1,008.01. The sustained engineering service’s revenue will post to the Deferred revenue account in the amount of $190.99.  The sum of the revenue prices must equal the sum of the lines’ that were set up to capture revenue price allocation, which equals $1,199.00. 

[![Revenue price allocation showing laptop revenue posting to Revenue account](./media/08_rev-rec-scenarios.png)](./media/08_rev-rec-scenarios.png)

At the time of the sale, the customer chose to not purchase software installation (S0001), but later changed their mind.  A second sales order is entered for the same customer.

[![Sales order lines with second sales sale](./media/09_rev-rec-scenarios.png)](./media/09_rev-rec-scenarios.png)

The second sales order is confirmed. Because the sales order only contains one line, revenue price allocation is not performed on confirmation. Revenue price allocation only happens where there are two or more unique items, and the items are set up for revenue price allocation.
If this is the only change to the customer’s contract, the reallocation process can now be run. From either sales order or from Periodic tasks, open the **Reallocate price with new order lines**.  Select the two sales orders and the corresponding sales order lines, then select the **Update reallocation** button. The Reallocated amount column displays the new revenue prices for each sales order line.  

[![Reallocate price with new revenue prices for each sales order line](./media/10_rev-rec-scenarios.png)](./media/10_rev-rec-scenarios.png)

Nothing is shown under the **Expected voucher** button because no invoices have been posted.  

The reallocation is completed by choosing the **Process** button.  It will prompt for a posting date, even if nothing is posted.  After the reallocation is complete, the **Revenue price allocation** page for both sales orders will show the price allocation for all items across both sales orders.  This means you will see an item in Revenue price allocation that doesn’t exist on the sales order because it’s part of the same contract, but on a different sales order.  

> [!Hint]
> You can add additional columns to the grid, such as **Reallocation ID** and **Sales order**, to give context about why these additional items are displayed. 

[![Revenue price allocations lines with additional columns](./media/11_rev-rec-scenarios.png)](./media/11_rev-rec-scenarios.png)

