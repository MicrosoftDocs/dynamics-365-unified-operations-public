---
title: Commission settlement on payments
description: Learn about commission settlement on payments, including prerequisites and a process for setting up the default commission settlement method.
author: mrolecki
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/16/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Italy
ms.search.validFrom: 2020-06-01
ms.search.form: 
ms.dyn365.ops.version: 10.0.10
---

# Commission settlement on payments

[!include [banner](../../includes/banner.md)]

In Italy, companies don't typically settle the commissions for their sales agents when they issue invoices. Instead, they settle the commissions when customers pay the full balance of their invoices.

## Prerequisites

Before you can use the functionality for commission settlement on payments, the following prerequisites must be met:

- The primary address of the legal entity must be in Italy.
- The **Commission settlement on payments** feature must be turned on in the **Feature management** workspace. For more information, see [Feature management overview](/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview).

## <a name="default-commission-settlement-period">Set up the default commission settlement method

1. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
1. On the **Accounts receivable parameters** page, on the **Settlement** tab, on the **Other** FastTab, in the **Commission settlement** field, select the default commission settlement method that is used when you create a sales order:

    - **On invoice** – Charge commissions during the invoice process.
    - **On payment** – Charge commissions during the payment process.

:::image type="content" source="../media/emea-ita-exil-commission-setup-parameters.PNG" alt-text="Screenshot of the Accounts receivable parameters page showing the Settlement tab with Commission settlement field options.":::

## Set up commission calculations

You can set up the calculation of commissions for an **On payment** commission by going to **Sales and marketing** \> **Commissions** \> **Commission calculation**.

:::image type="content" source="../media/emea-ita-exil-commission-%20calculation-setup.PNG" alt-text="Screenshot of the Commission calculation setup page displaying On payment commissions section with Payment thresholds option.":::

If the **Payment thresholds** option in the **On payment commissions** section is set to **Yes**, you can specify two limits (thresholds) for commission calculations:

- If the commission amount that is reached (as a percentage of the reachable amount) is below the lower limit, no commissions are accrued.
- When the upper limit is reached, the whole reachable amount is accrued.

Between the two limits, commissions are accrued in the regular way.

### Example

Consider the following example:

- **Total amount of the invoice:** €1,000
- **Lower limit:** 10 percent
- **Upper limit:** 80 percent

The following payments are made:

- €50 (5 percent of the total amount of the invoice): Because commissions are below the lower limit of 10 percent, no accrual occurs.
- €100 (10 percent of the total amount of the invoice): The invoice is settled at 15 percent. Therefore, commissions are accrued at that percentage.
- €500 (50 percent of the total amount of the invoice): The invoice is settled at 65 percent. Commissions are also accrued at 65 percent.
- €200 (20 percent of the total amount of the invoice): The invoice is settled at 85 percent. Because this figure exceeds the upper limit, commissions become fully settled at 100 percent.
- Further payments don't change the amount that is accrued, because that amount already reached the upper limit. However, accrual transactions are still created.

You can add another setup to the individual agent who belongs to a specific group. In commission calculations, the setup on agents (employees) has higher priority than the setup on sales.

## Set the commission settlement and preview commission transactions on the Sales order page

After you create a sales order, you can update the commission settlement in the sales order header.

1. Go to **Accounts receivable** \> **Orders** \> **All sales orders**.
1. Select and open a sales order.
1. On the **Sales order details** page, in the **Header** view, on the **Setup** FastTab, update the value of the **Commission settlement** field as needed.

:::image type="content" source="../media/emea-ita-exil-commission-sales-order.png" alt-text="Screenshot of the Sales order details page in Header view showing the Commission settlement field on the Setup FastTab.":::

By default, the **Commission settlement** field gets its value from the **Accounts receivable parameters** page. For more information, see [Set up the default commission settlement method](#default-commission-settlement-period).

You can also preview the sales commission calculation from a sales order for either open or invoiced orders. On the **Sales order details** page, on the **General** tab, select **Related information** \> **Commission preview**.

:::image type="content" source="../media/emea-ita-exil-commission-preview.PNG" alt-text="Screenshot of the Commission preview page displaying commission transaction details for a sales order.":::

> [!NOTE]
> You can combine sales orders in a single invoice if all the sales orders for invoicing have the same **Commission settlement** value in the sales order header.

### Get an overview of commission transactions on a sales order invoice

You can also view commission transactions on the **Invoice journal** page.

1. Go to **Accounts receivable** \> **Inquiries and reports** \> **Invoices** \> **Invoice journal**.
1. On the **Invoice** tab, select **Details** \> **Commission transactions**.

> [!NOTE]
> When you post the invoice, the system creates commission and voucher transactions. If the value in the **Commission settlement** field is **On invoice** in the sales order header, the system creates a **Settlement** record. If the value in the **Commission settlement** field is **On payment** in the sales order header, the system creates the **Settlement** record only after the invoice and a payment are settled.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
