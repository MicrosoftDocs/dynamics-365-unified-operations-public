---
title: Currency revaluation for Accounts payable and Accounts receivable
description: Learn about the foreign currency revaluation process that you run to update the value of open transactions in Accounts payable and Accounts receivable.
author: music727
ms.author: mibeinar
ms.topic: article
ms.date: 02/24/2025
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: CustExchRateAdjustment, VendExchRateAdjustment
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: defb1ea5-1f3e-4859-87d8-3f9954d3f388
---

# Currency revaluation for Accounts payable and Accounts receivable

[!include [banner](../includes/banner.md)]

Fluctuations in exchange rates cause the theoretical value (book value) of open transactions in foreign currencies to vary over time. This article provides information about the foreign currency revaluation process to update the value of open transactions in Accounts payable and Accounts receivable. 

The theoretical value, or book value, of open transactions in foreign currencies varies over time because of fluctuations in exchange rates. To update the value of open transactions in Accounts payable and Accounts receivable, run the foreign currency revaluation process. Foreign currency revaluation can be run for both Accounts payable and Accounts receivable. The process uses a new exchange rate to revalue the open amounts, or not settled amounts, on a specified date. The differences between the original posted amounts and the revalued amounts cause an unrealized gain or loss for each open transaction. The Accounts payable and Accounts receivable subledgers are then updated to reflect the unrealized gain or loss, and an accounting entry is posted to General ledger.

>[!NOTE]
> If the **Enable process automation for accounts receivable and accounts payable foreign currency revaluation** feature is enabled, process automations for Accounts payable and Accounts receivable foreign currency revaluations are available. For more information, see [Process automation](../../fin-ops-core/fin-ops/sysadmin/process-automation.md).

## Simulate a foreign currency revaluation
Before you revalue foreign currency amounts on open transactions, you can run a simulation report of the foreign currency revaluation for the same date and method. To run the simulation report, on the **Foreign currency revaluation** page, click **Simulation**. The report provides a preview of the unrealized gain or loss amount, based on the parameters defined for the simulation.

## Process a foreign currency revaluation
Use the **Foreign currency revaluation** page under **Periodic tasks** to revalue open transactions. You can run the process in real time or schedule it to run by using a batch. When you define the settings for the revaluation process, verify whether you want to print a report of the results. The revaluation report can't be reprinted after the process is completed. If you generate the foreign currency revaluation report, it shows various balances at the customer or vendor level and the currency level:

-   The balances of customers or vendors that have foreign currency transactions that have been revalued. The following balances are shown:
    -   The total original balance in the foreign currency.
    -   The total foreign currency amount in the accounting currency, as of the previous revaluation.
    -   The total foreign currency amount in the accounting currency, as of the current revaluation.
    -   The difference between the previous and current revaluation. This difference is the additional unrealized gain or loss.
-   The total unrealized gain or loss for each currency.

A record is kept every time that you run a foreign currency revaluation. From the record on the **Foreign currency valuation** page, select **Transactions** to view the detailed list of transactions created because of the revaluation. Each voucher transaction represents the open transaction that was revalued. If an open transaction was revalued more than one time, you see two records that use the same voucher. One record is for the reversal of the previous unrealized gain or loss, and the other record is for the new unrealized gain or loss. To run the revaluation process, click **Foreign currency revaluation**. Define appropriate settings for the following parameters:

-   **Method** – The method that is used in the selected foreign currency revaluation job:
    -   **Standard** – Foreign currency revaluation jobs are posted, regardless of whether the result is a profit or a loss.
    -   **Minimum** – Foreign currency revaluation jobs are posted only if the result is a loss.
    -   **Invoice date** – Foreign currency revaluation jobs use the original exchange rate of the transactions, which are revalued to their original value in the accounting currency. The effect of any prior foreign currency revaluation is canceled.
-   **Considered date** – The date when all transactions that have open (not settled) amounts on that date are found. Foreign currency amounts are revalued by using the exchange rates that are entered on the **Currency exchange rates** page for the considered date. When foreign currency amounts are revalued on a considered date, this date becomes the last foreign currency revaluation date for the transactions that are adjusted. If you run foreign currency revaluation for a considered date that's earlier than the last foreign currency revaluation date on transactions that have already been adjusted, the periodic job doesn't adjust transactions that are open on the earlier considered date, but that have a more recent last foreign currency revaluation date. If you run foreign currency revaluation for a considered date that's later than the settlement date of an invoice, the invoice is considered open (not settled) on the considered date and is involved in the foreign currency revaluation.
-   **Date of rate** – The date that determines the exchange rate that is used in the foreign currency revaluation.
-   **Use posting profile from** – The posting profile used to enter the default main account for Accounts receivable or Accounts payable for the accounting entries of the foreign currency revaluation transactions:
    -   **Posting** – The posting profile of the customer transaction is used.
    -   **Select** – Enter the posting profile in the **Posting profile** field.
-   **Posting profile** – If **Select** is selected in the **Use posting profile from** field, the posting profile entered in this field determines the posting profile of the foreign currency revaluation transactions.
-   **Financial dimensions** – The financial dimensions that are posted on the accounting entries of the foreign currency revaluation transactions. The financial dimensions aren't validated against the rules for the account structure. The account structure that was in place at the time the invoices were posted might not be the same as the rules that were in place when the revaluation was completed. There's no option to select specific financial dimensions in the revaluation process, so the account structure validation is skipped.  
    -   **None** – No financial dimensions are posted. If you have a required financial dimension in your account structure, the revaluation process still runs and creates accounting entries that have no financial dimensions. You receive a warning message first, so that you can cancel the revaluation.
    -   **Table** – The financial dimensions of the customer account or vendor account are posted on the foreign currency revaluation transactions.
    -   **Posting** – The financial dimensions of the transaction that is being revalued are posted on the foreign currency revaluation transactions. By default, the financial dimensions from the original transaction's Accounts receivable or Accounts payable ledger account is used for the revaluation transaction's Accounts receivable or Accounts payable main account. The financial dimensions from the original transaction's expense, asset, or revenue ledger account are used for the revaluation transaction's unrealized gain or loss main account.

## Additional exchange rate type for foreign currency revaluation

In version 10.0.39, the **Exchange rate type enhancement for accounts payable and accounts receivable foreign currency revaluation** feature is available. This feature lets you use additional exchange rate types for foreign currency revaluation. You can define the accounting currency exchange rate type and the reporting currency exchange rate type for each legal entity, or for each customer and vendor group. When you run foreign currency revaluation, these defined exchange rate types can override the default type that's defined in the ledger setup.

### Set up an additional exchange rate type for Accounts payable foreign currency revaluation

1. Go to **Accounts payable** \> **Setup** \> **Accounts payable parameters**.
2. On the **Ledger and sales tax** tab, in the **Exchange rate type source** field, select one of the following options:

    - **Ledger** – Use the exchange rate type that's defined in the ledger setup.
    - **Specific** – Use the accounting currency exchange rate type and reporting currency exchange rate type that are defined in the current legal entity.
    - **Group** – Use the accounting currency exchange rate type and reporting currency exchange rate type that are defined in the vendor group.

### Set up an additional exchange rate type for Accounts receivable foreign currency revaluation

1. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
2. On the **Ledger and sales tax** tab, in the **Exchange rate type source** field, select one of the following options:

    - **Ledger** – Use the exchange rate type that's defined in the ledger setup.
    - **Specific** – Use the accounting currency exchange rate type and reporting currency exchange rate type that are defined in the current legal entity.
    - **Group** – Use the accounting currency exchange rate type and reporting currency exchange rate type that are defined in the customer group.

> [!NOTE]
> Exchange gain or loss isn't aggregated. At the time of settlement, the unrealized gain or loss for each open transaction should be reversed to recalculate any realized gain or loss. If the total gain or loss is posted to the general ledger, it isn't possible to reverse per transaction.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
