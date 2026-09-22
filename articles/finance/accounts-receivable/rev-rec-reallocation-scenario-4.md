---
title: Revenue recognition reallocation - Scenario 4
description: Learn about a reallocation scenario where a line is removed from an existing, partially invoiced sales order. The same result occurs for canceled sales orders.
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

# Revenue recognition reallocation – Scenario 4

[!INCLUDE [banner](../includes/banner.md)]

This article describes a reallocation scenario where you remove a line from an existing, partially invoiced sales order. This scenario produces the same result, regardless of whether you remove the line from the sales order or set the line to a canceled status.

For this scenario, set the **Post invoice corrections to Accounts receivable** option to **No** on the **Revenue recognition** tab of the **General ledger parameters** page (**Revenue recognition** > **Setup** > **General ledger parameters**).

:::image type="content" source="./media/37_rev-rec-scenarios.png" alt-text="Screenshot of the Post invoice corrections to Accounts receivable option set to No." lightbox="./media/37_rev-rec-scenarios.png":::

Create a sales order for customer US\_SI\_0003. The customer is purchasing a laptop (item number S0012), installation services (item number S0001), and a support plan for the laptop (item number S0008, "Sustained Engineering Service"). The system immediately recognizes the revenue for the laptop and installation services. The system defers and recognizes the revenue for the support plan over 12 months, as defined by the date range in the contract.

:::image type="content" source="./media/38_rev-rec-scenarios.png" alt-text="Screenshot of the sales order lines for the laptop, installation services, and support plan." lightbox="./media/38_rev-rec-scenarios.png":::

Confirm the sales order. Because all three items are set up for revenue price allocation, the system calculates the revenue price when you confirm the sales order. You can view the revenue that the system recognizes on the **Revenue price allocation** page (on the **Sales order** page, on the Action Pane, on the **Manage** tab, in the **Revenue recognition** group, select **Revenue price allocation**). The system posts the revenue for the laptop to the Revenue account in the amount of $995.84. The system also posts the revenue for the installation services to the Revenue account, in the amount of $314.47. The system posts the revenue for the support plan to a Deferred revenue account in the amount of $188.69. The sum of the revenue prices equals the sum of the lines that you set up to capture revenue price allocation ($1,499.00).

:::image type="content" source="./media/39_rev-rec-scenarios.png" alt-text="Screenshot of the Revenue price allocation page." lightbox="./media/39_rev-rec-scenarios.png":::

Invoice the customer for the laptop and support plan, but not for the installation services. The following illustration shows the accounting entry that the system posts for the invoice.

:::image type="content" source="./media/40_rev-rec-scenarios.png" alt-text="Screenshot of the accounting entry for the invoiced sales order." lightbox="./media/40_rev-rec-scenarios.png":::

The accounting entry posts $1,276.94 to Accounts receivable. However, because this invoice is a partial invoice, the revenue or deferred revenue plus the tax doesn't equal the Accounts receivable amount. The difference of -$14.47 is posted to the Partial invoice revenue clearing account.

The revenue recognition schedule is also created.

:::image type="content" source="./media/41_rev-rec-scenarios.png" alt-text="Screenshot of the Revenue recognition schedule page for the partial invoice." lightbox="./media/41_rev-rec-scenarios.png":::

Later, the customer decides not to purchase installation services. Therefore, remove that line from the sales order. You can't confirm the sales order again because only invoiced lines remain on the sales order.

:::image type="content" source="./media/42_rev-rec-scenarios.png" alt-text="Screenshot of the sales order after the line for installation services is removed." lightbox="./media/42_rev-rec-scenarios.png":::

Even though you can't confirm the sales order, you can reallocate it. In the sales order, select **Reallocate price with new order lines** to open the **Reallocate price with new order lines** page. Select the two remaining sales order lines, and then select **Update reallocation**. The **Reallocated amount** column shows the new revenue price for each remaining sales order line.

:::image type="content" source="./media/43_rev-rec-scenarios.png" alt-text="Screenshot of the new revenue prices on the Reallocate price with new order lines page." lightbox="./media/43_rev-rec-scenarios.png":::

Next, select **Expected voucher** to view the accounting entries.

:::image type="content" source="./media/44_rev-rec-scenarios.png" alt-text="Screenshot of the accounting entries on the Expected voucher page." lightbox="./media/44_rev-rec-scenarios.png":::

On the **Expected voucher** page, the last five lines reverse the original accounting entry from the posted invoice. The first four lines are the new accounting entries that are posted for the invoice. It's important that you understand that a new invoice isn't presented to the customer. After the reallocation, the customer still owes $1,276.94, which is the amount that must be posted to Accounts receivable in the new accounting entry. The new revenue or deferred revenue plus tax equals $1,276.94. Therefore, you don't have to post to the Partial invoice revenue clearing account.

To complete the reallocation, select **Process**. A posting date is entered. After the reallocation is completed, the **Revenue price allocation** page shows the price reallocation for the two remaining items.

:::image type="content" source="./media/45_rev-rec-scenarios.png" alt-text="Screenshot of the price reallocation for the remaining items on the Revenue price allocation page." lightbox="./media/45_rev-rec-scenarios.png":::

The system also updated the revenue recognition schedule based on the new revenue reallocation price. From the sales order, open the **Revenue recognition schedule** page. Previously, there were 13 lines for item S0008 (a 12-month schedule was assigned to this item). There are now 39 lines: the 13 original schedule lines, 13 reversal schedule lines, and 13 lines that are based on the new revenue price.

:::image type="content" source="./media/46_rev-rec-scenarios.png" alt-text="Screenshot of the updated Revenue recognition schedule page with 39 lines for item S0008." lightbox="./media/46_rev-rec-scenarios.png":::

When you select **Voucher**, the invoice journal shows the original accounting entry. To view the reversing entry and the new accounting entry from the sales order, select **Revenue adjustments** on the Action Pane, and then select **Voucher**.

Next, open the **All customers** page (**Accounts receivable** > **Customers** > **All customers**), select customer **US\_SI\_0003**, and then select **Transactions**. The **Customer transactions** page shows only the original invoice (000008), together with the original accounting entry. Because the **Post invoice corrections to Accounts receivable** option is set to **No** on the **General ledger parameters** page, only General ledger is updated. Therefore, the reversing and updated accounting entries aren't shown. The revenue adjustment transactions that were created in [scenario 3](rev-rec-reallocation-scenario-3.md) are shown.

:::image type="content" source="./media/47_rev-rec-scenarios.png" alt-text="Screenshot of the original accounting entry on the Customer transactions page." lightbox="./media/47_rev-rec-scenarios.png":::

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
