---
# required metadata
title: Partial ledger settlements
description: This topic explains how partial ledger settlements are set up and processed in General ledger. 
author: JodiChristiansen
ms.date: 10/17/2024
ms.topic: article


# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2024-10-17
ms.dyn365.ops.version: 10.0.42

---

# Partial ledger settlements

[!include [banner](../includes/banner.md)]

The ledger settlement process enables an organization to "reconcile" clearing accounts. In this way, the organization ensures that the amount that is posted to a main account is fully cleared out of that account.

## Example

An organization pays an insurance company 12,000 US dollars (USD) in October for a yearly policy. The 12,000 USD can't yet be fully expensed, because the insurance company hasn't fulfilled its contractual obligations. As each month passes, 1,000 USD is recognized as an expense, and 1,000 USD is cleared from the accrued expense account as a credit amount. Therefore, the accrued expense account begins with a balance of 12,000 USD debit. Then, each month, a 1,000 USD credit is posted to reduce the balance in the account. After 12 months, the 12,000 USD is cleared, and ledger settlement can be completed by marking the 13 transactions, which net to 0 (zero). You can't settle the 12,000 USD debit until all the credits are posted. If expenses of this type cross fiscal years, it can be difficult to use ledger settlements and the advanced awareness options, because settlements can't cross fiscal years.

In Microsoft Dynamics 365 Finance version 10.0.42, functionality for partial ledger settlements is available. This functionality fixes the issue of expenses that cross fiscal years, because it enables a partial ledger settlement to be done at the end of the year (or each month or fiscal period). In the preceding example of an insurance policy, at the end of December, 3,000 USD has been cleared from the accrued expense account. Therefore, on the **Ledger settlements** page, the original 12,000 USD debit and three 1,000 USD credit transactions can be selected and ledger-settled. The remaining 9,000 USD is then carried forward to the next year for ledger settlement.

Another benefit of partial ledger settlements is that settlements that originate in accounts payable or accounts receivable can be automatically settled in the general ledger. To enable this functionality, set the **Subledger to ledger auto settlement** option to **Yes** on the **Ledger settlements** tab of the **General ledger parameters** page (**General Ledger** \> **Ledger setup** \> **General ledger parameters**).

## Prerequisites for partial ledger settlements

To use partial ledger settlements, set the following options to **Yes** on the **General ledger parameters** page:

- Enable advanced awareness options
- Enable post currency realized gains/losses for ledger settlements

> [!NOTE]
> In version 10.0.40, the **Enable advanced awareness options**, **Enable post currency realized gains and losses for ledger settlements**, and **Enable process automation for ledger settlements** features were moved from Feature management and became options on the **General ledger parameters** page.

> [!IMPORTANT]
> After you enable the functionality for partial ledger settlements, it can't be disabled or turned off, because data is migrated to new tables. All previous ledger settlement options that are required can't be disabled or turned off either. These options include **Enable advanced awareness options** and **Enable post currency realized gains/losses for ledger settlements**. However, the **Enable process automation for ledger settlement** and **Subledger to ledger auto settlement** options can be set to **Yes** or **No** at any time.

For partial ledger settlements, as in the existing functionality for ledger settlements, the main account must be added to the list of accounts. The exception to this rule is any account that is settled in the subledger (accounts payable or accounts receivable). If the **Subledger to ledger auto settlement** option is set to **Yes**, accounts of that type are automatically settled and don't have to be included in the list of accounts. If they are added to the list, you can view them on the **Ledger settlements** page.

## Partially settle transactions

If the **Awareness between ledger settlement and year-end close** and **Partial ledger settlements** options are set to **Yes**, the **Ledger settlements** page changes in the following ways:

- The main account is required, because all ledger settlements must be completed for transactions in a single main account.
- All ledger settlements must be completed within a fiscal year.
- You can change the posting layer as you require, but you can't settle transactions that are in different posting layers.
- To show the main account and dimensions separately, select a financial dimension set.
- The **Status** filter has a **Partially settled** status, and you can select more than one status at a time. The following status options are available:

    - **All**
    - **Not settled** (the default option)
    - **Settled**
    - **Partially settled**

- The accounting currency and reporting currency totals are shown.
- The **Reverse marked transactions** button is moved to the **Ledger settlements history** page.

For partial ledger settlements, debits don't have to equal credits. Therefore, if transactions are partially settled, some transactions have a remaining balance. Settlement history is now tracked for all transactions, and the following columns are added to the grid to track this information.

- History
- Amount in reporting currency
- Remaining amount in transaction currency
- Remaining amount in accounting currency
- Remaining amount in reporting currency

When a debit transaction is partially settled with a credit transaction, or when a credit transaction is partially settled with a debit transaction, the status of the fully settled transaction is **Settled**. The status of the partially settled transaction is **Partially settled**, and the remaining amount columns show the amount that must still be settled. One debit transaction can be settled with multiple credit transactions, or one credit transaction can be settled with multiple debit transactions. For example, voucher GJ00105 is a debit for 1,000 USD. Voucher GJ00210 for 700 USD and voucher GJ00236 for 300 USD are marked for settlement with the debit.

| Status      | Voucher | Date       | Settlement ID | Date settled | Debit    | Credit | Amount remaining |
|-------------|---------|------------|---------------|--------------|----------|--------|------------------|
| Not settled | GJ00105 | 10/01/2024 |               |              | 1,000.00 |        |                  |
| Not settled | GJ00210 | 10/15/2024 |               |              |          | 700.00 |                  |
| Not settled | GJ00236 | 11/05/2024 |               |              |          | 400.00 |                  |

After settlement, the **Settlement ID** column is set to **Multiple** for the debit transaction, because more than one credit was settled. Each pair of debit/credit transactions has its own settlement ID, which is shown in the **Settlement ID** column. Because the second credit transaction for 400.00 isn't fully settled, the status is **Partially settled**, and the remaining amount is updated to **100.00**.

| Status            | Voucher | Date       | Settlement ID | Date settled | Debit    | Credit | Amount remaining |
|-------------------|---------|------------|---------------|--------------|----------|--------|------------------|
| Settled           | GJ00105 | 10/01/2024 | Multiple      | 11/05/2024   | 1,000.00 |        | 0.00             |
| Settled           | GJ00210 | 10/15/2024 | 012264        | 11/05/2024   |          | 700.00 | 0.00             |
| Partially settled | GJ00236 | 11/05/2024 | 012265        |              |          | 400.00 | 100.00           |

## View settlements/Ledger settlements history

To view the settlement ID and the history of settlements, select a transaction that has a **Settlement ID** value, and then select **View settlements** on the Action Pane. The **Ledger settlements history** page shows each pair of debit and credit transactions that was settled by using the settlement ID that was created for each pair.

Use the **Ledger settlements history** page to reverse any transactions that are already settled. When you select a transaction, the corresponding transaction that has the same settlement ID is automatically selected. Select **Reverse marked transactions**, select the reversal date options, and enter a comment as required. Then select **Reverse**. If a transaction was settled and then reversed, and it has a status of **Partially settled** or **Not settled**, the **History** column has a check mark to indicate that there is history. To view all settlement history, select **View settlements**. To view all reversed settlements, select the **Show reversals** checkbox.

The **User ID** column provides an audit trail of the user ID that settled or the reversed the transaction.

## Ledger settlements inquiry

To view ledger-settled transactions, go to **General ledger** \> **Inquiries and reports** \> **Ledger settlements inquiry**.

The **Remaining amount in transaction currency**, **Remaining amount in accounting currency**, and **Remaining amount in reporting currency** columns in the grid show values for partially settled transactions.

If the **Settlement ID** column is set to **Multiple**, select **View settlements** to open the **Ledger settlement history** page, where you can view the full settlement history.

## Subledger to ledger auto settlement

The **Subledger to ledger auto settlement** option is found on the **Ledger settlements** tab of the **General ledger parameters** page. Before you enable it, the following options must be set to **Yes**:

- Enable advanced awareness options
- Enable post currency realized gains/losses for ledger settlements
- Partial ledger settlements

The **Subledger to ledger auto settlement** option can be turned on (set to **Yes**) and turned off (set to **No**) as required. When it's set to **Yes**, the accounts payable and accounts receivable accounts are automatically settled during the settlement process in the subledger. You must set this option to **Yes** to do automatic settlement. However, the accounts receivable and accounts payable accounts don't have to be manually added to the list of accounts. If the accounts are added to the list of accounts, they can be viewed on the **Ledger settlements** page. Transactions that are automatically settled can then be viewed. As required, you can manually settle any transactions that use the accounts payable or accounts receivable accounts.

Other subledger accounts that are added to the list of accounts aren't automatically settled. However, those subledger accounts can be manually settled on the **Ledger settlements** page.

Existing transactions in the accounts payable and accounts receivable accounts aren't automatically settled if the related subledger transactions were settled before the **Subledger to ledger auto settlement** option was set to **Yes**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
