---
# required metadata

title: Bank foreign currency revaluation 
description: This article provides an overview of the process of bank foreign currency revaluation. It includes information about setup, running the process, the calculation for the process, and reversal of revaluation transactions.
author: ericwangchen
ms.date: 06/05/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BankCurrencyRevalHistory
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2019-03-08
ms.dyn365.ops.version: 10.0

---

# Bank foreign currency revaluation

[!include [banner](../includes/banner.md)]


This article provides an overview of the process of bank foreign currency revaluation. It explains how to set up and run the process, and provides information about the calculation for the process. It also explains how to reverse revaluation transactions, if reversal is required.

As part of a period end, accounting conventions require that bank account balances in foreign currencies be revalued by using different exchange rate types (current, historical, average, and so on). The bank foreign currency revaluation feature can be used to revalue one or more bank accounts. The feature is also a global feature. Therefore, from a single page, you can revalue banks across all the legal entities that you have access to.

> [!NOTE]
> When you run the revaluation process, the balance in each bank account that is posted in a foreign currency will be revalued. The unrealized gain or loss transactions that are created during the revaluation process are system-generated. Two transactions might be created, one for the accounting currency and one for the reporting currency, if a reporting currency is relevant. Each accounting entry will be posted to the unrealized gain or loss and the main account that is being revalued.

## Prepare to run foreign currency revaluation

Before you run the revaluation process, the following setup is required.

- On the **Ledger** page, specify the exchange rate type. If an exchange rate type isn't defined on the main account, this exchange rate type is used during foreign currency revaluation.
- On the **Ledger** page, specify the realized gain, realized loss, unrealized gain, and unrealized loss accounts for currency revaluation. Realized gain and realized loss accounts are used when Accounts receivable and Accounts payable transactions are settled. Unrealized gain and unrealized loss accounts are used to revalue open transactions and general ledger main accounts.
- On the **Currency revaluation accounts** page, select different currency revaluation accounts for each currency and company. If no accounts are defined, the accounts from the **Ledger** page are used.
- On the **Cash and bank management parameters** page, on the **Number sequences** tab, add a number sequence for foreign currency revaluation.


> [!NOTE]
> If your legal entity uses a Russian, Polish, or Hungarian country/region code, you can already do bank foreign currency revaluation. You won't be able to use the foreign currency revaluation that is used by other countries or regions.

## Process foreign currency revaluation

After the setup is completed, use the **Foreign currency revaluation** page in Cash and bank management to revalue the balances of one or more bank accounts across all legal entities. You can run the process in real time, or you can schedule it to run by using a batch.

The **Foreign currency revaluation** page shows the history of each revaluation process. It shows when the process was run and what criteria were defined, and provides a link to the voucher that was created for the revaluation. It also shows whether a previous revaluation was reversed. To run the revaluation process, select **Foreign currency revaluation** on the Action Pane to open the **Bank - foreign currency revaluation** dialog box.

The **Revaluation date** field defines the cutoff date for calculating the foreign currency balance that will be revalued. The sum of all bank transactions that occurred up through this date is revalued.

The **Exchange rate date** field defines the date of the exchange rate that will be used to revalue the currency balances. For example, you can revalue the balances as of January 31 but use the exchange rate that is defined for February 1.

The revaluation process can be run for one or more legal entities. The lookup shows only the legal entities that you have access to. Select the legal entities for which you want to select the bank accounts that are eligible for foreign currency revaluation. All the bank accounts for those legal entities will be shown in the grid.

Set the **Preview before posting** option to **Yes** if you want to review the results of the revaluation before you post it. The foreign currency revaluation has a preview that can be posted. You don't have to run the revaluation process again. You can export the results in the preview to Microsoft Excel to keep a history of how the amounts were calculated. You can't use batch processing if you want to preview the results of the revaluation.

Select **OK** to process the foreign currency revaluation. A record is created to track the history of each run. A separate record is created for each legal entity and posting layer.

## Calculate unrealized gain/loss

In Cash and bank management, the bank currency is considered to be the base currency and it is not revalued. The balance of the bank account in the accounting currency is revalued using the exchange rates between the bank currency and the accounting currency on the **Exchange rate date**. The balance of the bank account in the reporting currency is also revalued using the exchange rates between the bank currency and the reporting currency on the **Exchange rate date**.

A transaction is created for the difference between the balance of the bank account and the new balance that is calculated for the accounting currency. Another transaction is created for the difference between the balance of the bank account and the new balance that is calculated for the reporting currency. The entries for these transactions are marked as reconciled. 

No entry is made for the accounting currency if the bank currency matches the accounting currency. Likewise, no entry is made for the reporting currency if the bank currency matches the reporting currency.

The foreign currency revaluation transaction is also split across the dimensions that are found on the bank transactions. The split is based on the balance for each dimension. For example, the total bank balance is 10,000, but the balance for business unit 001 is 4,000, whereas the balance for business unit 002 is 6,000. In this case, 40 percent of the revaluation amount is posted to the revaluation account that has business unit 001, and 60 percent is posted to the revaluation account that has business unit 002. If the account structure doesn't include a business unit, the full amount is posted to the revaluation account.

#### Bank foreign currency revaluation enhancement

As of Dynamics 365 Finance version 10.0.36, a new **Enhancements to bank foreign currency revaluation** feature is available. This feature provides an alternative way to calculate bank foreign currency revaluation. Before this feature, the process of bank foreign currency revaluation considered every financial dimension value when it calculated the gain or loss. This feature enables organizations to select all or none of the financial dimensions when the gain or loss is calculated. In addition, this feature changes the calculation logic. It calculates the balance of the bank account by considering either all financial dimensions or no financial dimensions. It then calculates the unrealized gain or loss per ledger account. 

> [!IMPORTANT]
> After this feature is enabled, it can't be disabled.

#### Example 1 - Different exchange rate on the dimensions

The following table shows three ending balances in the transaction currency (EUR) for a foreign currency bank account in the USMF legal entity. The accounting currency is USD, and the reporting currency is USD. 

| Main account | Financial dimension 1 | Financial dimension 2 | Financial dimension 3 | Ending balance - EUR | Ending balance - USD | Exchange rate - EUR/USD |
| ------------ | --------------------- | --------------------- | --------------------- | -------------------- | -------------------- | ----------------------- |
| Bank - EUR   | 001                   | Not applicable        | Not applicable        | 10,000               | 12,000               | 1.2                     |
| Bank - EUR   | 002                   | Not applicable        | Not applicable        | 20,000               | 23,500               | 1.175                   |
| Bank - EUR   | 003                   | Not applicable        | Not applicable        | 30,000               | 36,600               | 1.22                    |

Assuming the exchange rate between EUR and USD is 1:1.21 at the time point of revaluation date, then the gain/loss is calcualted as

| Main account | Financial dimension 1 | Financial dimension 2 | Financial dimension 3 | Ending balance - EUR | Ending balance - USD | Foreign exchange gain/loss -USD |
| ------------ | --------------------- | --------------------- | --------------------- | -------------------- | -------------------- | ------------------------------- |
| Bank - EUR   | 001                   | Not applicable        | Not applicable        | 10,000               | 12,000               | 100                             |
| Bank - EUR   | 002                   | Not applicable        | Not applicable        | 20,000               | 23,500               | 700                             |
| Bank - EUR   | 003                   | Not applicable        | Not applicable        | 30,000               | 36,600               | -300                            |

#### Example 2 - Postive and negative balance on the dimensions

The following table shows one positive balance and one negative balance in the transaction currency (EUR) for a foreign currency bank account in the USMF legal entity. The accounting currency is USD, and the reporting currency is USD. 

| Main account | Financial dimension 1 | Financial dimension 2 | Financial dimension 3 | Ending balance - EUR | Ending balance - USD | Exchange rate -EUR/USD |
| ------------ | --------------------- | --------------------- | --------------------- | -------------------- | -------------------- | ---------------------- |
| Bank - EUR   | 001                   | Not applicable        | Not applicable        | 10,000               | 12,000               | 1.2                    |
| Bank - EUR   | 002                   | Not applicable        | Not applicable        | -9,000               | -10,800              | 1.2                    |

Assuming the exchange rate between EUR and USD is 1:1.21 at the time point of revaluation date, then the gain/loss is calcualted as

| Main account | Financial dimension 1 | Financial dimension 2 | Financial dimension 3 | Ending balance - EUR | Ending balance - USD | Foreign exchange gain/loss -USD |
| ------------ | --------------------- | --------------------- | --------------------- | -------------------- | -------------------- | ------------------------------- |
| Bank - EUR   | 001                   | Not applicable        | Not applicable        | 10,000               | 12,000               | 100                             |
| Bank - EUR   | 002                   | Not applicable        | Not applicable        | -9,000               | -10,800              | -90                             |

> [!NOTE]
> To use this enhancement when you revalue foreign currency, you must first run **Reset foreign currency revaluation, define dimension level** (**Cash and bank management** \> **Periodic tasks** \> **Reset foreign currency revaluation, define dimension level**).

### Reverse foreign currency revaluation

If you must reverse the revaluation transaction, select **Reverse transaction** on the **Foreign currency revaluation** page. A new foreign currency revaluation historical record is created to maintain the historical audit trail that tracks when the revaluation occurred or was reversed.

To reverse several revaluations, you must reverse the most current revaluation first. Then continue to reverse older revaluations in date order. You can then process new revaluations for the periods that you reversed.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
