---
# required metadata

title: Foreign currency revaluation for General ledger
description: This article provides an overview of the following for the general ledger foreign currency revaluation process -  setup, running the process, calculation for the process, and how to reverse the revaluation transactions, if necessary. 
author: kweekley
ms.date: 11/15/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CurrencyLedgerGainLossAccount
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: 842e8561-560f-4cc6-8668-70cca60b1ba3
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Foreign currency revaluation for General ledger

[!include [banner](../includes/banner.md)]

This article provides an overview of the following for the general ledger foreign currency revaluation process -  setup, running the process, calculation for the process, and how to reverse the revaluation transactions, if necessary. 

As part of a period-end, accounting conventions require general ledger account balances in foreign currencies to be revalued using different exchange rate types (current, historical, average, etc.). For example, one accounting convention requires assets and liabilities to be revalued at the current exchange rate, fixed assets at the historical exchange rate, and profit and loss accounts at the monthly average. The General ledger foreign currency revaluation can be used to revalue the balance sheet and profit and loss accounts. 

> [!NOTE]
> Foreign currency revaluation is also available in Accounts receivable (AR) and Accounts payable (AP). If you are using those modules, the outstanding transactions should be revalued using the foreign currency revaluation in those modules. The AR and AP foreign currency revaluation will create an accounting entry in General ledger to reflect the unrealized gain or loss, ensuring that the subledgers and general ledger can be reconciled. Because the AR and AP foreign currency revaluation create accounting entries in General ledger, the accounts receivable and accounts payable main accounts should be excluded from the General ledger foreign currency revaluation. 

When you run the revaluation process, the balance in each main account posted in a foreign currency will be revalued. The unrealized gain or loss transactions that are created during the revaluation process are system-generated. Two transactions might be created, one for the accounting currency and a second for the reporting currency, if relevant. Each accounting entry will post to the unrealized gain or loss and the main account being revalued.

## Prepare to run foreign currency revaluation
Before you run the revaluation process, the following setup is required.

On the **Main account** page:
 - If the main account should be revalued in General ledger, select **Foreign currency revaluation**. If the main account shouldn’t be revalued (such as for AR and AP if revalued in the subledgers), clear this option.
 - If the main account is marked for revaluation, enter the **Exchange rate type**. This exchange rate type will be used for revaluing the main account. A separate field, **Financial reporting exchange rate type**, is available for financial reporting. The two fields are not kept in sync, allowing for different exchange rate types to be used for revaluation and financial reporting.

On the **Ledger** page:
 - Specify the **Exchange rate type**. If the exchange rate type is not defined on the main account, this exchange rate type will be used during foreign currency revaluation.
 - Specify the realized gain, realized loss, unrealized gain, and unrealized loss accounts for currency revaluation. Realized gain and realized loss accounts are used when settling AR and AP transactions, and unrealized gain and unrealized loss accounts are used for revaluing open transactions and general ledger main accounts.

On the **Currency revaluation accounts** page:
 - Select different currency revaluation accounts for each currency and company. If no accounts are defined, the accounts from the **Ledger** page are used.

## Process foreign currency revaluation
After the setup is complete, use the **Foreign currency revaluation** page to revalue the balances of the main accounts. You can run the process in real time or schedule it to run by using a batch. 

The **Foreign currency revaluation** page will display the history of each revaluation process, including when the process was run, what criteria was defined, a link to the voucher created for the revaluation, and a record if a previous revaluation was reversed. To run the revaluation process, select the **Foreign currency revaluation** button. 

The **From date** and **To date** values define the date interval for calculating the foreign currency balance that will be revalued. When you revalue profit and loss accounts, the sum of all transactions that occur within the date interval are revalued. When you revalue balance sheet accounts, the **From date** is ignored. Instead, the balance to be revalued is determined by going from the beginning of the fiscal year until the **To date**. 

The **Date of rate** can be used to define the date for which the exchange rate should default. For example, you can revalue the balances between the date range of January 1 to January 31, but use the exchange rate defined for February 1. 

Select which main accounts to revalue: All, Balance sheet, or Profit and loss. Only main accounts marked for revaluation (on the **Main account** page) will be revalued. If you want to further restrict the range of main accounts, use the **Records to include** tab to define a range of main accounts, or individual main accounts. 

The revaluation process can be run for one or more legal entities. The lookup will display only the legal entities to which you have access. Select the legal entities for which you want to run the revaluation process. 

The revaluation can be run for one or more foreign currencies. The lookup will include all currencies that were posted within the date range relevant for the type of main account (Balance sheet or Profit and loss), for the legal entities selected to revalue. The accounting currency will be included in the list, but nothing will be revalued if the accounting currency is selected. 

Set **Preview before posting** to **Yes** if you would like to review the result of the General ledger revaluation. The preview in General ledger is different from the simulation in the AR and AP foreign currency revaluation. The simulation in AR and AP is a report, but general ledger has a preview which can be posted, without having to run the revaluation process again. The results of the preview can be exported to Microsoft Excel to retain the history of how the amounts were calculated. You can't use batch processing if you want to preview the results of the revaluation. From the preview, the user has the option to post the results of all legal entities using the **Post** button. If there's an issue with the results for a legal entity, the user also has the option to post a subset of the legal entities using the **Select legal entities to post** button.

If you would like to exclude adjustments that were posted using the **Reporting currency adjustments journal** from the revaluation process, set **Exclude reporting currency adjustments** to **Yes**. By default, reporting currency adjustments are included in the revaluation. 

After the foreign currency revaluation process is complete, a record will be created to track the history of each run. A separate record will be created for each legal entity and posting layer.

## Calculate unrealized gain/loss
The unrealized gain/loss transactions are created differently between General ledger revaluation and the AR and AP revaluation process. In AR and AP, the previous revaluation is completely reversed (assuming the transaction isn’t settled yet) and a new revaluation transaction is created for the unrealized gain/loss based on the new exchange rate. This is because we revalue each individual transaction in AR and AP. In General ledger, the previous revaluation is not reversed. Instead, a transaction is created for the delta between the balance of the main account, including any previous revaluation amounts, and the new value based on the exchange rate for the Date of Rate. 

**Example** The following balances exist for main account 110110.

| Date   | Ledger account| Transaction amount | Accounting amount |
|------------|--------------------|------------------------|-----------------------|
| January 20 | 110110 (Cash)      | 500 EUR (Debit)        | 1000 USD (Debit)      |

The main account is revalued on January 31.  The unrealized gain/loss is calculated as follows.

| Current balance in transaction currency | Current balance in accounting currency | Exchange rate at revaluation | New accounting currency amount | Unrealized gain/loss    |
|--------------------|---------------------------|----------------------------------|------------------------------------|-----------------------------|
| 500 EUR            | 1000 USD                  | 166.6667                         | 833.33 USD (500 x 1.666667)        | 166.67 loss (833.33 – 1000) |

The following accounting entry will be created.

| Date   | Ledger account       | Debit | Credit |
|------------|--------------------------|-----------|------------|
| January 31 | 110110 (Cash)            |           | 166.67     |
| January 31 | 801400 (Unrealized loss) | 166.67    |            |

No new transactions are posted for the month of February.  The main account is revalued on February 28.

| Current balance in transaction currency | Current balance in accounting currency | Exchange rate at revaluation | New accounting currency amount | Unrealized gain/loss    |
|---------------------------------------|-----------------------------------|-------------------------------|--------------------|-----------------------------|
| 500 EUR                 | 833.33 USD (1000 - 166.67)       | 250.0000              | 1250 USD (500 x 2.5)               | 416.67 gain (1250 – 833.33) |

The following accounting entry will be created.

| Date    | Ledger account       | Debit | Credit |
|-------------|--------------------------|-----------|------------|
| February 28 | 110110 (Cash)            | 416.67    |            |
| February 28 | 801600 (Unrealized gain) |           | 416.67     |

## Reverse foreign currency revaluation
If you need to reverse the revaluation transaction, select the **Reverse transaction** button on the **Foreign currency revaluation** page. A new foreign currency revaluation historical record will be created to maintain the historical audit trail of when the revaluation occurred or was reversed. 

You can reverse the results of the revaluation out of date order, but you may need to also reverse a more current revaluation to ensure the correct balances for each revalued main account. The reversals can occur out of date order because there is no way to control which main accounts are revalued and the frequency of when they are revalued. For example, an organization may choose to revalue their cash main accounts on a quarterly basis, but all other main accounts monthly.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
