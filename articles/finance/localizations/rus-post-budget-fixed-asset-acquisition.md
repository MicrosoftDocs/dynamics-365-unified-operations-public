---
# required metadata

title: Create and post budget journals for fixed asset acquisitions (Russia)
description: This topic explains how to create and post a budget journal for a fixed asset acquisition for Russia. 
author: ShylaThompson
ms.date: 09/19/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BudgetModel 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Create and post budget journals for fixed asset acquisitions (Russia)

[!include [banner](../includes/banner.md)]

You can create financial plans and current budgets in the **Fixed assets** module by using budget models. A budget model represents a collection of planned turnovers for specific accounts and periods.

1. Select **Budgeting** \> **Setup** \> **Basic budgeting** \> **Budget models**.
2. Select **New** to create a budget model.
3. In the **Budget model** field, enter a code for the budget model. In the **Name** field, enter a name for the budget model.
4. Close the **Budget model** page.
5. Select **Fixed assets (Russia)** \> **Journals** \> **FA budget journal**.
6. Select the **List** tab, and then select **New** to create a journal.
7. In the **Name** field, select a journal name.
8. Select **Lines** to open the **Journal voucher** page, where you can enter fixed asset budget transactions.
9. Select the **List** tab, and then select **New** to create a line for a budget transaction.
10. In the **Budget model** field, select the budget model.
11. In the **Accounting** field, you can change the fixed asset value model.
12. In the **Transaction type** field, select **Putting into operation**.
13. In the **Date** field, you can change the transaction date.
14. In the **Account type** field, you can change the type of account.
15. In the **Account** field, select a fixed asset number.
16. In the **Transaction text** field, select a transaction text.
17. In the **Debit** or **Credit** field, enter a transaction amount.
18. In the **Offset account type** field, select the type of ledger account.
19. In the **Offset account** field, select the ledger account number.

    > [!NOTE]
    > If the posting profile is set up for this transaction, the **Offset account** field automatically shows the account number.

20. Repeat steps 9 through 19 for every additional type of fixed asset transaction.

    > [!NOTE]
    > To create transactions for group acquisitions or group depreciation calculations, select **Putting into operation** or **Depreciation**. When you create an acquisition transaction, specify the transaction date and budget model. When you create a transaction for a depreciation calculation, specify the transaction date, budget model, and value model for the transaction.

21. Select **Validate** \> **Validate** to verify the asset information in the journal.
22. Select **Post** \> **Transfer to fixed asset budget** to transfer the transactions to the fixed asset budget.
23. Select **Post** \> **Transfer to fixed asset and ledger budget** to transfer the transactions to the fixed asset and general ledger budget.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]