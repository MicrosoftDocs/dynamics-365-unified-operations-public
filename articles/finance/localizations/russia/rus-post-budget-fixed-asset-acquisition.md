---
title: Create and post budget journals for fixed asset acquisitions (Russia)
description: Learn how to create and post a budget journal for a fixed asset acquisition for Russia in Microsoft Dynamics 365 Finance.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 08/29/2025
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2018-10-28
ms.search.form: BudgetModel
---

# Create and post budget journals for fixed asset acquisitions (Russia)

[!include [banner](../../includes/banner.md)]

This article explains how to create and post a budget journal for a fixed asset acquisition for Russia in Microsoft Dynamics 365 Finance.

You can create financial plans and current budgets in the **Fixed assets** module by using budget models. A budget model represents a collection of planned turnovers for specific accounts and periods.

To create financial plans and current budgets in the **Fixed assets** module using budget models, follow these steps.

1. In Dynamics 365 Finance, go to **Budgeting** \> **Setup** \> **Basic budgeting** \> **Budget models**.
1. Select **New** to create a budget model.
1. In the **Budget model** field, enter a code for the budget model. In the **Name** field, enter a name for the budget model.
1. Close the **Budget model** page.
1. Select **Fixed assets (Russia)** \> **Journals** \> **FA budget journal**.
1. Select the **List** tab, and then select **New** to create a journal.
1. In the **Name** field, select a journal name.
1. Select **Lines** to open the **Journal voucher** page, where you can enter fixed asset budget transactions.
1. Select the **List** tab, and then select **New** to create a line for a budget transaction.
1. In the **Budget model** field, select the budget model.
1. In the **Accounting** field, you can change the fixed asset value model.
1. In the **Transaction type** field, select **Putting into operation**.
1. In the **Date** field, you can change the transaction date.
1. In the **Account type** field, you can change the type of account.
1. In the **Account** field, select a fixed asset number.
1. In the **Transaction text** field, select a transaction text.
1. In the **Debit** or **Credit** field, enter a transaction amount.
1. In the **Offset account type** field, select the type of ledger account.
1. In the **Offset account** field, select the ledger account number.

    > [!NOTE]
    > If the posting profile is set up for this transaction, the **Offset account** field automatically shows the account number.

1. Repeat steps 9 through 19 for every additional type of fixed asset transaction.

    > [!NOTE]
    > To create transactions for group acquisitions or group depreciation calculations, select **Putting into operation** or **Depreciation**. When you create an acquisition transaction, specify the transaction date and budget model. When you create a transaction for a depreciation calculation, specify the transaction date, budget model, and value model for the transaction.

1. Select **Validate** \> **Validate** to verify the asset information in the journal.
1. Select **Post** \> **Transfer to fixed asset budget** to transfer the transactions to the fixed asset budget.
1. Select **Post** \> **Transfer to fixed asset and ledger budget** to transfer the transactions to the fixed asset and general ledger budget.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
