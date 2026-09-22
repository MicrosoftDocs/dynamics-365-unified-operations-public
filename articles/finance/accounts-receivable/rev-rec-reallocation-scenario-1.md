---
title: Revenue recognition reallocation - Scenario 1
description: Access a reallocation scenario where two sales orders are entered, but they are only confirmed. You can get similar results if more than two sales orders are confirmed.
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

# Revenue recognition reallocation – Scenario 1

[!INCLUDE [banner](../includes/banner.md)]

This article describes a reallocation scenario where you enter two sales orders, but you only confirm them. If more than two sales orders are in a confirmed state, you see similar results.

For this scenario, set the **Post invoice corrections to Accounts receivable** option to **No** on the **Revenue recognition** tab of the **General ledger parameters** page (**Revenue recognition** > **Setup** > **General ledger parameters**).

:::image type="content" source="./media/06_rev-rec-scenarios.png" alt-text="Screenshot of the Post invoice corrections to Accounts receivable option set to No on the Revenue recognition tab of the General ledger parameters page." lightbox="./media/06_rev-rec-scenarios.png":::

Create a sales order for customer US\_SI\_0003. The customer purchases a laptop (item number S0012) and a support plan for it (item number S0008, "Sustained Engineering Service"). The system immediately recognizes the revenue for the laptop (there's no revenue recognition schedule). The system defers and recognizes the revenue for the support plan over 12 months, as defined by the date range in the contract.

:::image type="content" source="./media/07_rev-rec-scenarios.png" alt-text="Screenshot of the sales order lines for the laptop and support plan." lightbox="./media/07_rev-rec-scenarios.png":::

Confirm the sales order. Because both items are set up for revenue price allocation, the system calculates the revenue price when you confirm the sales order. You can view the revenue that the system recognizes on the **Revenue price allocation** page (on the **Sales order** page, on the Action Pane, on the **Manage** tab, in the **Revenue recognition** group, select **Revenue price allocation**). The system posts the revenue for the laptop to the Revenue account in the amount of $1,008.01. The system posts the revenue for the support plan to the Deferred revenue account in the amount of $190.99. The sum of the revenue prices equals the sum of the lines that you set up to capture revenue price allocation ($1,199.00).

:::image type="content" source="./media/08_rev-rec-scenarios.png" alt-text="Screenshot of the Revenue price allocation page." lightbox="./media/08_rev-rec-scenarios.png":::

The customer chooses not to purchase installation services (item number S0001) at the time of the sale but later changes their mind. Enter a second sales order for the same customer.

:::image type="content" source="./media/09_rev-rec-scenarios.png" alt-text="Screenshot of the sales order line for installation services." lightbox="./media/09_rev-rec-scenarios.png":::

Confirm the second sales order. Because this sales order contains only one line, the system doesn't do revenue price allocation when you confirm the sales order. Revenue price allocation occurs only if there are two or more unique items, and if those items are set up for revenue price allocation.

If this new sales order is the only change to the customer's contract, you can now run the reallocation process. In one of the two sales orders, select **Reallocate price with new order lines** to open the **Reallocate price with new order lines** page. Alternatively, go to **Revenue recognition** > **Periodic tasks** > **Reallocate price with new order lines**. Select the two sales orders and the corresponding sales order lines, and then select **Update reallocation**. The **Reallocated amount** column shows the new revenue price for each sales order line.

:::image type="content" source="./media/10_rev-rec-scenarios.png" alt-text="Screenshot of the new revenue prices on the Reallocate price with new order lines page." lightbox="./media/10_rev-rec-scenarios.png":::

If you select **Expected voucher**, nothing is shown, because no invoices have been posted.

To complete the reallocation, select **Process**. You're prompted for a posting date, even if nothing is posted. After the reallocation is completed, the **Revenue price allocation** page for each sales order shows the price allocation for all items across both sales orders. In other words, the **Revenue price allocation** page for each sales order includes an item that doesn't exist on that sales order, because it's part of the same contract but on a different sales order.

> [!TIP]
> To provide context about why these additional items are shown, add other columns to the grid, such as **Reallocation ID** and **Sales order**.
>
> :::image type="content" source="./media/11_rev-rec-scenarios.png" alt-text="Screenshot of additional columns on the Revenue price allocations page." lightbox="./media/11_rev-rec-scenarios.png":::

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
