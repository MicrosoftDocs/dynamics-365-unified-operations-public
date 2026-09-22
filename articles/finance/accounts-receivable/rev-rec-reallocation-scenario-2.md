---
title: Revenue recognition reallocation - Scenario 2
description: Access a reallocation scenario where two sales orders are entered, and then the customer adds an item to the contract after first sales order is invoiced.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.date: 08/11/2026
ms.custom: 
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global 
ms.search.validFrom: 2020-12-21
ms.search.form: Customer
ms.dyn365.ops.version: 10.0.14
---

# Revenue recognition reallocation – Scenario 2

[!INCLUDE [banner](../includes/banner.md)]

This article describes a reallocation scenario where you enter two sales orders, and then the customer adds an item to the contract after you invoice the first sales order. When you add a new item to a contract, you can add it to either a new sales order or the existing sales order.

For this scenario, set the **Post invoice corrections to Accounts receivable** option to **No** on the **Revenue recognition** tab of the **General ledger parameters** page (**Revenue recognition** > **Setup** > **General ledger parameters**).

[![Post invoice corrections to Accounts receivable option set to No.](./media/12_rev-rec-scenarios.png)](./media/12_rev-rec-scenarios.png)

Create a sales order for customer US\_SI\_0003. The customer is purchasing installation services (item number S0001) and a support plan (item number S0008) for a laptop, but they didn't select the laptop yet. Defer the revenue for the installation services until the date when the customer purchases the laptop. Defer and recognize the revenue for the support plan over 12 months, as defined by the date range in the contract.

[![Sales order lines for the installation services and support plan.](./media/13_rev-rec-scenarios.png)](./media/13_rev-rec-scenarios.png)

Confirm the sales order. Because both items are set up for revenue price allocation, the system calculates the revenue price when you confirm the sales order. You can view the revenue that will be recognized on the **Revenue price allocation** page (on the **Sales order** page, on the Action Pane, on the **Manage** tab, in the **Revenue recognition** group, select **Revenue price allocation**). The system posts the revenue for the installation services to a Deferred revenue account in the amount of $250.00. The system also posts the revenue for the support plan to the Deferred revenue account, in the amount of $150.00. The sum of the revenue prices must equal the sum of the lines that you set up to capture revenue price allocation ($400.00).

[![Revenue price allocation page.](./media/14_rev-rec-scenarios.png)](./media/14_rev-rec-scenarios.png)

Fully invoice the sales order. The following illustration shows the accounting entry that the system posts for the invoice.

[![Accounting entry for the fully invoiced sales order.](./media/15_rev-rec-scenarios.png)](./media/15_rev-rec-scenarios.png)

The system also creates the revenue recognition schedule, but it doesn't recognize any of the revenue yet.

[![Revenue recognition schedule page.](./media/16_rev-rec-scenarios.png)](./media/16_rev-rec-scenarios.png)

A few days later, the customer selects a laptop. Enter a second sales order for the customer.

[![Sales order line for the laptop.](./media/17_rev-rec-scenarios.png)](./media/17_rev-rec-scenarios.png)

Confirm the second sales order. Because this sales order contains only one line, the system doesn't do revenue price allocation when you confirm the sales order. Revenue price allocation occurs only if there are two or more unique items, and if those items are set up for revenue price allocation.

If this new sales order is the only change to the customer's contract, you can now run the reallocation process. In one of the two sales orders, select **Reallocate price with new order lines** to open the **Reallocate price with new order lines** page. Alternatively, go to **Revenue recognition** > **Periodic tasks** > **Reallocate price with new order lines**. Select the two sales orders and the corresponding sales order lines, and then select **Update reallocation**. The **Reallocated amount** column shows the new revenue price for each sales order line.

[![New revenue prices on the Reallocate price with new order lines page.](./media/18_rev-rec-scenarios.png)](./media/18_rev-rec-scenarios.png)

Next, select **Expected voucher** to view the accounting entries that the system posts only to General ledger. Because the **Post invoice corrections to Accounts receivable** option is set to **No** on the **General ledger parameters** page, the system doesn't change anything in Accounts receivable when you process the reallocation.

[![Accounting entries on the Expected voucher page.](./media/19_rev-rec-scenarios.png)](./media/19_rev-rec-scenarios.png)

On the **Expected voucher** page, the last three lines reverse the original accounting entry from the posted invoice. The first four lines constitute the new accounting entry that the system posts for the invoice. It's important that you understand that a new invoice isn't presented to the customer. After the reallocation, the customer still owes $426.00, which is the amount that must be posted to Accounts receivable in the new accounting entry. The offsetting tax and the deferred revenue equal $188.69 + $314.48 + $26.00 = $529.17. The deferred revenue amount changed because of the reallocation. The difference of $103.17 is posted to a Partial invoice revenue clearing account. This balance is cleared when the invoice is posted for the second sales order that was included in the reallocation.

To complete the reallocation, select **Process**. You're prompted for a posting date, even if nothing is posted. After the reallocation is completed, the **Revenue price allocation** page for each sales order shows the price allocation for all items across both sales orders. In other words, the **Revenue price allocation** page for each sales order includes an item that doesn't exist on that sales order, because it's part of the same contract but on a different sales order.

> [!TIP]
> To provide context about why these additional items are shown, you can add other columns to the grid, such as **Reallocation ID** and **Sales order**.
>
> [![Additional columns on the Revenue price allocations page.](./media/20_rev-rec-scenarios.png)](./media/20_rev-rec-scenarios.png)

In sales order 00036, the system also updated the revenue recognition schedule, based on the new revenue reallocation price. From this sales order, open the **Revenue recognition schedule** page. Previously, there were 13 lines for item S0008 (a 12-month schedule was assigned to this item). There are now 39 lines: the 13 original schedule lines, 13 reversal schedule lines, and 13 lines that are based on the new revenue price.

[![Updated Revenue recognition schedule page with 39 lines for item S0008.](./media/21_rev-rec-scenarios.png)](./media/21_rev-rec-scenarios.png)

Likewise, there were previously two lines for item S0001, but now there are six.

[![Updated Revenue recognition schedule page with six lines for item S0001.](./media/22_rev-rec-scenarios.png)](./media/22_rev-rec-scenarios.png)

When you select **Voucher** in sales order 000036, the invoice journal shows the original accounting entry. To view the reversing entry and the new accounting entry from the sales order, select **Revenue adjustments** on the Action Pane, and then select **Voucher**.

[![Sales order 000036.](./media/23_rev-rec-scenarios.png)](./media/23_rev-rec-scenarios.png)

Next, open the **All customers** page (**Accounts receivable \> Customers \> All customers**), select customer **US\_SI\_0003**, and then select **Transactions**. The open invoice from sales order 000036 will be shown. If you select the voucher, you will see the original accounting entry, not the new accounting entry from the reallocation. The reversing entry and the new accounting entry can't be viewed from Accounts receivable.

The second sales order is now invoiced. The total invoice that is presented to the customer is for $1,099.00 + $71.44 tax = $1,170.44. The following illustration shows the accounting entry that is posted.

[![Voucher transactions page with the accounting entry that is posted.](./media/24_rev-rec-scenarios.png)](./media/24_rev-rec-scenarios.png)

Because the sum of the revenue and sales is more than $1,170.44, the difference is posted for -$130.17. This amount clears the balance from the Partial invoice revenue clearing account. That balance is posted in the new accounting entry after the reallocation.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
