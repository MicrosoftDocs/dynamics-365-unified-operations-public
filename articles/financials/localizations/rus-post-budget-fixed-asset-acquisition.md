---
# required metadata

title: Create and post a budget journal for a fixed asset acquisition (Russia)
description: This topic provides information about creating and posting a budget journal for a fixed asset acquisition for Russia. 
author: ShylaThompson
manager: AnnBe
ms.date: 09/19/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Create and post a budget journal for a fixed asset acquisition (Russia)

[!include [banner](../includes/banner.md)]

Financial plans and current budgets can be created in the Fixed assets module using budget models. A budget model represents a collection of planned turnovers for specific accounts and periods.


1.  Click **Budgeting** \> **Setup** \> **Basic budgeting** \> **Budget models**.
2.  Press the **New** button to create a new budget model.
3.  In the **Budget model** field, enter a code of the budget model and in the **Name** field, enter a name for the budget model.
4.  Close the form.
5.  Click **Fixed assets (Russia)** \> **Journals** \> **FA budget journal**.
6.  On the **List** tab, press the **New** button to create a new journal.
7.  In the **Name** field, select a journal name.
8.  Click **Lines** to open the **Journal voucher** form, where you can enter fixed asset budget transactions.
9.  On the **List** tab, press the **New** button to create a new line for budget transaction
10. In the **Budget model** field, select the budget model.
11. In the **Accounting** field, view or modify the fixed asset value model.
12. In the **Transaction type** field, select **Putting into operation**.
13. In the **Date** field, view or modify the transaction date.
14. In the **Account type** field, view or modify the type of account.
15. In the **Account** field, select a fixed asset number.
16. In the **Transaction text** field, select a transaction text.
17. In the **Debit** or **Credit** field, enter a transaction amount.
18. In the **Offset account type** field, select the ledger account type.
19. In the **Offset account** field, select the ledger account number.
    
    > [!NOTE]
    > If the posting profile is set up for this transaction, the <STRONG>Offset account</STRONG> field displays the account number automatically.

20. Repeat steps 9 through 19 for each fixed asset transaction type.
    
    > [!NOTE]
    > Click **Putting into operation** and **Depreciation** to create group acquisition and depreciation calculation transactions. Specify the transaction date and budget model when you create an acquisition transaction. Specify the transaction date, budget model, and value model for the transaction when you calculate depreciation.

21. Click **Validate** \> **Validate** to verify the asset information in the journal.
22. Click **Post** \> **Transfer to fixed asset budget** to transfer the transactions to the fixed asset budget.
23. Click **Post** \> **Transfer to fixed asset and ledger budget** to transfer the transactions to the fixed asset and general ledger budget.
