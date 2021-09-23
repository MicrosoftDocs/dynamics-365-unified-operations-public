---
# required metadata
title: Exchange adjustment
description: This topic provides information about bank exchange adjustments for Russia.
author: anasyash
ms.date: 08/16/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: anasyash
ms.search.validFrom: 2019-06-28
ms.dyn365.ops.version: 10.0.0

---

# Exchange adjustment

[!include [banner](../includes/banner.md)]

On the reporting date, the Central Bank of Russia's exchange rate must be used to revalue the cash balance on a foreign currency bank account so that it correctly represents the cash balance value in the accounting currency. The exchange rate difference from the revaluation of the currency bank account is the difference between the value, in the accounting currency, of cash in the bank account on the date of the payment (or on the reporting date of the previous reporting period) and the value, in the accounting currency, of the cash in the bank account on the reporting date.

## Accounting of exchange rate differences
For accounting purposes, exchange rate differences are typically recorded as other income and expenses in the ledger account, such as **ledger account 91 - Other income and expenses**. For the purpose of income tax accounting, exchange rate differences are considered non-operational income and expenses.
The exchange rate difference on the currency bank account can be either positive (when the currency exchange rate increases) or negative (when the currency exchange rate decreases). The following table shows examples of ledger transactions for positive and negative exchange rate differences.

| Ledger transaction                                            | Description                       |
|---------------------------------------------------------------|-----------------------------------|
| Debit 91 (unrealized loss) Credit 52 (currency bank accounts) | Negative exchange rate difference |
| Debit 52 (currency bank accounts) Credit 91 (unrealized gain) | Positive exchange rate difference |

## Setup

### Set up ledger accounts for currency bank account revaluation

1. Go to **General ledger** \> **Currencies** \> **Currency parameters**.
2. On the left side of the **Currency revaluation accounts** page, in the **Legal entities** field, select a company.
3. Select the transaction currency, and then select **Edit**.
4. Set the **Activate parameters** option to **Yes**.
5. On the **General** FastTab, in the grid, in the **Posting** field, select **Unrealized gain**, and then, in the **Main account** field, select the ledger account to post the exchange rate gain to.
6. In the **Posting** field, select **Unrealized loss**, and then, in the **Main account** field, select the ledger account to post exchange rate loss to.
7. In the **Income code** field, select the income/expense code for tax accounting purposes that corresponds to the exchange rate gain.
8. In the **Expense code** field, select the income/expense code for tax accounting purchases that corresponds to the exchange rate loss.
9. Select **Save**.

### Set up a number sequence

1. Go to **Cash and bank management** \> **Setup** \> **Cash and bank management parameters**.
2. On the **Number sequences** tab, in the **Number sequence code** field, select a number sequence code for the **Bank – Exchange adjustment** reference.

## Calculate the exchange rate difference for a bank account
To do revaluation on the reporting date, use the **Foreign currency revaluation** page.

1. Go to **Cash and bank management** \> **Periodic tasks** \> **Foreign currency revaluation – Bank**.
2. On the **Foreign currency revaluation** page, in the **On date** field, select the revaluation date.
3. In the **From currency** and **To currency** fields, define the range of currency codes that should be revalued.
4. Select **Filter** to set up additional criteria for filtering. For example, select a specific currency bank account to revalue.
5. Select **OK**. The exchange difference for the selected date is calculated. You receive a message that indicates the date and amount of the exchange rate transaction.

## View exchange adjustment transactions
You can review the posted exchange adjustment transactions on the **Bank transactions** page.

1. Go to **Cash and bank management** \> **Bank accounts** \> **Bank accounts**.
2. Select the bank account, and then select **Transactions**.
3. On the **Bank transactions** page, review the transactions that were posted because of the revaluation. The **Ledger transaction type** field for these transactions is set to **Foreign currency revaluation**.

> [!NOTE]
> If the **Ledger transaction type** column isn't visible, right-click anywhere in the grid row that shows the column names, select **Add columns**, select **Ledger transaction type** and then select **Insert**.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]