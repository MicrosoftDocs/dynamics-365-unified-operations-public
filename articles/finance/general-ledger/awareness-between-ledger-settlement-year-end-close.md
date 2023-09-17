---
# required metadata

title: Awareness between ledger settlement and year-end close
description: This article provides information about enhancements which impact ledger settlements and the General ledger year-end close.
author: kweekley
ms.date: 04/06/2022
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
# ms.assetid:
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2022-01-31
ms.dyn365.ops.version: 10.0.25

---

# Awareness between ledger settlement and year-end close

[!include [banner](../includes/banner.md)]


In Microsoft Dynamics 365 Finance version 10.0.25, the **Awareness between ledger settlement and year-end close** feature is available in the **Feature management** workspace. This feature adds two primary enhancements that affect ledger settlement and general ledger year-end close.

During general ledger year-end close, ledger transactions that have been settled will no longer be included in the opening balance of the next fiscal year. This enhancement ensures that only unsettled ledger transactions are included in the opening balance. It's important when general ledger foreign currency revaluation is run. Foreign currency revaluation is run only for ledger transactions that have a status of **Not settled**. However, before the **Awareness between ledger settlement and year-end close** feature was released, the opening balance summarized both transaction that have a status of **Settled** and those that have a status of **Not settled**, and the status of the summarized amount was set to **Not settled**.

The second enhancement lets you post detailed opening balance transactions during general ledger year-end close. If the **Keep detail during year-end close** option is set to **Yes**, a separate opening balance will be created for each ledger transaction that isn't settled. This setting is defined for each main account in the ledger settlement setup. By keeping detailed transactions for the opening balance, you greatly improve the ability to settle the unsettled ledger transactions in the next fiscal year.

To support the new enhancements, changes were made to ledger settlement and year-end close.

### Changes to ledger settlement

- Ledger settlement must be done within a fiscal year.
- Ledger settlement must be done for transactions in a single main account.The main account is now a required filter on the **Ledger settlement** page.
- Ledger settlement and the reversal of ledger settlement can't be done for transactions that are posted within a closed fiscal year (in other words, the year-end close has been run).

### Changes to year-end close

- A year-end close can't be reversed if any opening balance transactions have been settled in the next fiscal year. This change applies when a year-end close is reversed, or when a year-end close is rerun and the **Delete existing year-end entries when re-closing the year** option is set to **Yes** in General ledger parameters.
- If the **Keep detail during year-end close** option is set to **Yes** for any balance sheet account in the ledger settlement, more detailed opening balance transactions will be created for that main account.

## Before you enable the feature

Because of the changes in functionality and the data model, it's important that you consider the following points before you enable the feature:

- Because only settled transactions are brought forward into the opening balance, you must unsettle transactions from the current fiscal year that are settled with transactions in the previous fiscal year. The transactions must be resettled against transactions within the current fiscal year. This can be done through an adjusting entry in the current fiscal year. The adjustment reverses the summarized opening balances and offsets with the detailed transaction necessary to settle the ledger entries in the current year. 

  > [!IMPORTANT]
  > If this isn't done, you will receive an **out-of-balance** error when you run the year-end close for the current fiscal year. If it's not possible to unsettle and resettle the ledger transactions with the same fiscal year, don't enable this feature until after the year-end close is complete. Enable the feature immediately after year-end close is complete and before any new ledger transactions are settled in the next fiscal year. 
  
- All transactions that have been marked for settlement but haven't been settled will automatically be unmarked when the feature is enabled. To prevent any loss of work, settle all marked transactions before you enable the feature.
- Some organizations run the year-end close multiple times for the same fiscal year. Don't enable the feature if the year-end close has already been run once and will be run again for the same fiscal year. The feature must be enabled before you process the first year-end close or after you process the last year-end close for the fiscal year.

  If you want to enable the feature, but the year-end close has already been run once, you must reverse the year-end close before you can enable the feature.

- Because settlement across main accounts is no longer permitted, adjust your chart of accounts or processes as required to ensure that ledger settlement can be done in the same main account.
- The feature can't be enabled if the public sector year-end close process is being used.

## Set up ledger settlement

After you enable the feature, and before you run the next year-end close, each organization must determine whether it will keep the transaction details during the year-end close. The choice has no impact on opening balance postings from previous year-end close processes.

The **Keep detail during year-end close** option is set for each main account on the **Ledger settlement setup** page.

1.	Go to **General ledger** > **Ledger setup** > **General ledger parameters**.
2.	On the **Ledger settlements** tab, select **Ledger settlement accounts**.

-or-

1.	Go to **General ledger** > **Periodic tasks** > **Ledger settlements**.
2.	Select **Ledger settlement accounts**.

Two columns have been added to the **Ledger settlements** page:
	
- **Main account type** – This column is for informational purposes only. It shows the type that is assigned to the main account.
- **Keep detail during year-end close** – By default, the option is set to **No**. It can be set to **Yes** only if the value in the **Main account type** column is **Balance sheet**, **Asset**, or **Liability**. When the option is set to **No**, opening balances will be posted in summary, as is typical during year-end close. If it's set to **Yes**, opening balances will be created in detail for each ledger transaction that isn't settled for the main account.

## Year-end close

When you run the year-end close by going to **General ledger** > **Period close** > **Year end close**, the process creates the opening balances for the main accounts that are defined for ledger settlement. The opening balances are created in either summary or detail, depending on the ledger settlement setup. The process excludes ledger transactions that are settled, regardless of whether you post the opening balance for each main account in summary or in detail.

For example, multiple transactions are posted to main account 130100 in fiscal year 2021.

| Journal number | Voucher  | Date       | Type      | Ledger account | Account name        | Description       | Currency | Amount in transaction currency | Amount  | Amount in reporting currency |
|----------------|----------|------------|-----------|----------------|---------------------|-------------------|----------|--------------------------------|---------|------------------------------|
| 20853          | FTV-3000 | 12/3/2021  | Operating | 130100-001-    | Accounts receivable | Service fee       | USD      | 100                            | 100     | 100                          |
| 20855          | FTV-3004 | 12/5/2021  | Operating | 130100-002-    | Accounts receivable | Utilities         | USD      | 175                            | 175     | 175                          |
| 20854          | CMV-4000 | 12/16/2021 | Operating | 130100-001-    | Accounts receivable | Refund            | USD      | -100                           | -100    | -100                         |
| 20851          | ARP-8000 | 12/20/2021 | Operating | 130100-002-    | Accounts receivable |                   | USD      | -0.88                          | -0.88   | -0.88                        |
| 20853          | ARPM0004 | 12/20/2021 | Operating | 130100-002-    | Accounts receivable |                   | EUR      | -127.11                        | -174.12 | -174.12                      |
| 20856          | CMV-4010 | 12/21/2021 | Operating | 130100-002-    | Accounts receivable | Credit on account | USD      | -175                           | -175    | -175                         |
| 20857          | FTV-3011 | 12/28/2021 | Operating | 130100-001-    | Accounts receivable | Utilities         | USD      | 400                            | 400     | 400                          |
| 20910          | FTV-3020 | 12/29/2021 | Operating | 130100-002-    | Accounts receivable | Service           | USD      | 300                            | 300     | 300                          |

Of these transactions, three are settled during ledger settlement.

There is an invoice for 175 US dollars (USD 175). This invoice was paid by a payment in euros (EUR), and a cash discount was taken.

| Journal number | Voucher  | Date       | Type      | Ledger account | Account name        | Description | Currency | Amount in transaction currency | Amount  | Amount in reporting currency |
|----------------|----------|------------|-----------|----------------|---------------------|-------------|----------|--------------------------------|---------|------------------------------|
| 20855          | FTV-3004 | 12/5/2021  | Operating | 130100-002-    | Accounts receivable | Utilities   | USD      | 175                            | 175     | 175                          |
| 20851          | ARP-8000 | 12/20/2021 | Operating | 130100-002-    | Accounts receivable |             | USD      | -0.88                          | -0.88   | -0.88                        |
| 20853          | ARPM0004 | 12/20/2021 | Operating | 130100-002-    | Accounts receivable |             | EUR      | -127.11                        | -174.12 | -174.12                      |

The results for main account 130100 depend on whether the feature is enabled before the year-end close is run. If the feature is enabled, the result also depends on the setting of the Keep detail during year-end close option.

### The feature isn't enabled
The year-end close creates three opening balance transactions for main account 130100 in 2022. The sum of the transactions in the accounting currency is USD 525.

| Journal number | Voucher  | Date     | Type    | Ledger account | Account name        | Description | Currency | Amount in transaction currency | Amount  | Amount in reporting currency |
|----------------|----------|----------|---------|----------------|---------------------|-------------|----------|--------------------------------|---------|------------------------------|
| 20910          | YEC_2021 | 1/1/2022 | Opening | 130100-002-    | Accounts receivable |             | USD      | 299.12                         | 299.12  | 299.12                       |
| 20910          | YEC_2021 | 1/1/2022 | Opening | 130100-001-    | Accounts receivable |             | USD      | 400                            | 400     | 400                          |
| 20910          | YEC_2021 | 1/1/2022 | Opening | 130100-002-    | Accounts receivable |             | EUR      | -127.11                        | -174.12 | -174.12                      |

Even though the payment's transaction for EUR -127.11 was ledger settled, the transaction still comes forward as a beginning balance.

### Feature is enabled and Keep detail during year-end close = No

The year-end close creates two opening balance transactions for main account 130100 in 2022. The sum of the transactions in the accounting currency is still USD 525, but the ledger-settled transactions are excluded from the opening balance. The total amount for account 130100-002- is USD 125 instead of USD 299.12, and the transaction for EUR 127.11/USD 174.12 is totally excluded.

| Journal number | Voucher  | Date     | Type    | Ledger account | Account name        | Description | Currency | Amount in transaction currency | Amount | Amount in reporting currency |
|----------------|----------|----------|---------|----------------|---------------------|-------------|----------|--------------------------------|--------|------------------------------|
| 20910          | YEC_2021 | 1/1/2022 | Opening | 130100-002-    | Accounts receivable |             | USD      | 125                            | 125    | 125                          |
| 20910          | YEC_2021 | 1/1/2022 | Opening | 130100-001-    | Accounts receivable |             | USD      | 400                            | 400    | 400                          |

### Feature is enabled and Keep detail during year-end close = Yes

The year-end close creates five opening balance transactions for main account 130100 in 2022. A separate opening balance transaction is created for each of the five transactions that weren't settled. The sum of the transactions in the accounting currency is still USD 525.

| Journal number | Voucher  | Date     | Type    | Ledger account | Account name        | Description       | Currency | Amount in transaction currency | Amount | Amount in reporting currency |
|----------------|----------|----------|---------|----------------|---------------------|-------------------|----------|--------------------------------|--------|------------------------------|
| 20910          | YEC_2021 | 1/1/2022 | Opening | 130100-001-    | Accounts receivable | Service fee       | USD      | 100                            | 100    | 100                          |
| 20910          | YEC_2021 | 1/1/2022 | Opening | 130100-001-    | Accounts receivable | Refund            | USD      | -100                           | -100   | -100                         |
| 20910          | YEC_2021 | 1/1/2022 | Opening | 130100-002-    | Accounts receivable | Credit on account | USD      | -175                           | -175   | -175                         |
| 20910          | YEC_2021 | 1/1/2022 | Opening | 130100-001-    | Accounts receivable | Utilities         | USD      | 400                            | 400    | 400                          |
| 20910          | YEC_2021 | 1/1/2022 | Opening | 130100-002-    | Accounts receivable | Service           | USD      | 300                            | 300    | 300                          |

When transaction details are kept, the original detailed transactions aren't affected. They remain posted and unsettled in the fiscal year that is being closed. A copy of those transactions is created for the opening balance. The following values from the original transactions are copied to the opening balance transactions.

- Ledger account (the main account and all financial dimensions)
- Amounts in the transaction, accounting, and reporting currencies
- Description
- Posting layer
- Posting type

   > [!NOTE]
   > No other opening balance transactions are assigned a posting type. Therefore, the posting type can be used to differentiate opening transactions that were brought forward in detail.

Some fields from the original transactions must change in the opening balance detailed transactions. The date of opening balance transactions is always the first day of the next fiscal year. The journal number must change, and the voucher number changes to the value that was entered in the year-end close dialog box.

Information from the original transactions can be found on the **Ledger settlement** page. Each detailed opening balance transaction shows the **Original transaction date** column in the grid. This column can help you match transactions in the new fiscal year. In Microsoft Dynamics 365 Finance version 10.0.33, you can view the **Original document** and **Original document date** columns. You can select **View original voucher** to drill back to the full original voucher.

## <a name="settle-transactions"></a>Settle transactions
To settle ledger transactions, follow these steps.

1. Go to **General ledger** > **Periodic tasks** > **Ledger settlements**.
2.	Set the filters at the top of the page.

    1. Select a date range. Alternatively, select a date interval code to automatically fill in the date range.

       - The date range can't cross fiscal years. If the date range crosses fiscal years, no transactions will be shown when you select **Display transactions**.
       - If the date range is in an open fiscal year, transactions can be settled, and the settlement can be reversed. If the date range is in a closed fiscal year, or if the year-end close is completed, transactions are shown, but they can't be settled or unsettled. You can unmark transactions only in a closed fiscal year. If the date range is in a closed fiscal year, the **Mark selected**, **Settle marked transactions**, and **Reverse marked transactions** buttons are unavailable.

    2. Select the main account to show transactions for. This field is required. The lookup shows only the main accounts that are selected on the **Ledger settlement** page for the company's chart of accounts.
    3. Select the posting layer. You can't settle transactions that are in different posting layers.
    4. To show the main account and dimensions in separate columns, select a financial dimension set.

3.	Select **Display transactions** to show all the transactions that match the filters that you set. If you change any of the filters or the dimension sets, you must select **Display transactions** again.
4.	Select lines for settlement. The value in the **Selected amount** field at the top of the page increases or decreases to reflect the total amount on the selected lines.
5.	When you've finished selecting transactions, select **Mark selected**. For each selected transaction, a check mark appears in the **Marked** column. Additionally, the value in the **Marked amount** field above the grid increases or decreases to reflect the total amount on the marked lines.
6.	When the value in the **Marked amount** field is **0** (zero), select **Settle marked transactions**.

    - Partial settlement isn't permitted. For example, you can't settle a $100 debit transaction against a $90 credit transaction. The remaining $10 credit transaction must also be marked for inclusion in the settlement.
    - Enter a settlement date. The date must be on or after the latest date of the transactions that are marked for settlement.

The status of the marked transactions is updated to **Settled**.

> [!IMPORTANT]
> All transactions that you've marked for settlement for the active legal entity and the selected main account will be settled. The transactions don't have to appear on the page. They will be settled even if they are hidden because of a filter.

Some processes, such as reversal of a transaction, automatically settle ledger transactions. For example, a payment and invoice are settled in Accounts receivable, and the settlement generates a realized gain/loss. The settlement of the payment and invoice doesn't settle any ledger transactions, such as transactions for the Accounts receivable ledger account. However, if the payment and invoice are unsettled in Accounts receivable, the reversing accounting entry that was posted during the reversal of the Accounts receivable settlement will cause the original and reversing accounting entries to be ledger settled in General ledger. When the **Awareness between ledger settlement and year-end close** feature is enabled, the ledger settlement of a reversal doesn't automatically occur if the reversing date is in a different fiscal year.

## Use Excel for ledger settlement

Transactions that are shown on the **Ledger settlement** page can be exported to Excel. In Excel, you can further filter transactions to determine which transactions to mark for settlement.
Both Ledger settlement entities export ledger transactions only for the main account that is selected on the **Ledger settlement** page. Although transactions for closed fiscal years can still be marked or unmarked by using Excel, they can't be settled. Additionally, settled transactions can't be reversed for that fiscal year.

## Make transactions easier to find

The **Ledger settlements** page includes capabilities that make it easier to view the transactions that you require for settlement.

•	Use the **Marked** filter to filter transactions based on whether the **Marked** checkbox for them is selected.
•	Use the **Status** filter to filter transactions based on their status.
•	Select **Sort by absolute amount** to sort the amounts by absolute value. In this way, you can group debits and credits that have the same amount.

## Reverse a settlement

You can reverse a settlement that was made by mistake.

1.	Follow steps 1 through 3 in the [Settle transactions](#settle-transactions) section to show the transactions that you're interested in.
2.	In the **Status** filter, select **Settled**.
3.	Select lines for reversal.
4.	Select **Reverse marked transactions**. The status of all transactions that have the same settlement ID is updated to **Not settled**.

> [!IMPORTANT]
> All transactions that have the same settlement ID will be reversed, even if they aren't marked. For example, four lines were marked and settled. All four lines have the same settlement ID. If you mark one of those four lines and then select **Reverse marked transactions**, all four lines will be reversed.






