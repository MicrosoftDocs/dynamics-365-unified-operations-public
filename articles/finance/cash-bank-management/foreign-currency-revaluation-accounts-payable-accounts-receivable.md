---
# required metadata

title: Currency revaluation for Accounts payable and Accounts receivable
description: This article provides information about the foreign currency revaluation process that you run to update the value of open transactions in Accounts payable and Accounts receivable. 
author: angelad116
ms.date: 10/24/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CustExchRateAdjustment, VendExchRateAdjustment
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: defb1ea5-1f3e-4859-87d8-3f9954d3f388
ms.search.region: Global
# ms.search.industry: 
ms.author: angelading
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Currency revaluation for Accounts payable and Accounts receivable

[!include [banner](../includes/banner.md)]

Fluctuations in exchange rates cause the theoretical value (book value) of open transactions in foreign currencies to vary over time. This article provides information about the foreign currency revaluation process that you run to update the value of open transactions in Accounts payable and Accounts receivable. 

The theoretical value, or book value, of open transactions in foreign currencies varies over time because of fluctuations in exchange rates. To update the value of open transactions in Accounts payable and Accounts receivable, run the foreign currency revaluation process. Foreign currency revaluation can be run for both Accounts payable and Accounts receivable. The process uses a new exchange rate to revalue the open amounts, or not settled amounts, on a specified date. The differences between the original posted amounts and the revalued amounts will cause an unrealized gain or loss for each open transaction. The Accounts payable and Accounts receivable subledgers are then updated to reflect the unrealized gain or loss, and an accounting entry is posted to General ledger.

## Simulate a foreign currency revaluation
Before you revalue foreign currency amounts on open transactions, you can run a simulation report of the foreign currency revaluation for the same date and method. To run the simulation report, on the **Foreign currency revaluation** page, click the **Simulation** button. The report provides a preview of the unrealized gain or loss amount, based on the parameters that are defined for the simulation.

## Process a foreign currency revaluation
Use the **Foreign currency revaluation** page under **Periodic tasks** to revalue open transactions. You can run the process in real time or schedule it to run by using a batch. When you define the settings for the revaluation process, be sure to verify whether you want to print a report of the results. The revaluation report can't be reprinted after the process is completed. If you generate the foreign currency revaluation report, it will show various balances at the customer/vendor level and the currency level:

-   The balances of customers or vendors that have foreign currency transactions that have been revalued. The following balances are shown:
    -   The total original balance in the foreign currency.
    -   The total foreign currency amount in the accounting currency, as of the previous revaluation.
    -   The total foreign currency amount in the accounting currency, as of the current revaluation.
    -   The difference between the previous and current revaluation. This difference is the additional unrealized gain or loss.
-   The total unrealized gain or loss for each currency.

A record is kept every time that you run a foreign currency revaluation. From the record on the **Foreign currency valuation** page, select **Transactions** to view the detailed list of transactions that were created because of the revaluation. Each voucher transaction represents the open transaction that was revalued. If an open transaction was revalued more than one time, you will see two records that use the same voucher. One record will be for the reversal of the previous unrealized gain or loss, and the other record will be for the new unrealized gain or loss. To run the revaluation process, click the **Foreign currency revaluation** button. Define appropriate settings for the following parameters:

-   **Method** – The method that is used in the selected foreign currency revaluation job:
    -   **Standard** – Foreign currency revaluation jobs are posted, regardless of whether the result is a profit or a loss.
    -   **Minimum** – Foreign currency revaluation jobs are posted only if the result is a loss.
    -   **Invoice date** – Foreign currency revaluation jobs use the original exchange rate of the transactions, which are revalued to their original value in the accounting currency. The effect of any prior foreign currency revaluation is canceled.
-   **Considered date** – The date when all transactions that have open (not settled) amounts on that date are found. Foreign currency amounts are revalued by using the exchange rates that are entered on the **Currency exchange rates** page for the considered date. When foreign currency amounts are revalued on a considered date, this date becomes the last foreign currency revaluation date for the transactions that are adjusted. If you run foreign currency revaluation for a considered date that's earlier than the last foreign currency revaluation date on transactions that have already been adjusted, the periodic job doesn't adjust transactions that are open on the earlier considered date, but that have a more recent last foreign currency revaluation date. If you run foreign currency revaluation for a considered date that's later than the settlement date of an invoice, the invoice is conisdered open (not settled) on the considered date and is involved in the foreign currency revaluation.
-   **Date of rate** – The date that determines the exchange rate that is used in the foreign currency revaluation.
-   **Use posting profile from** – The posting profile that is used to enter the default main account for Accounts receivable or Accounts payable for the accounting entries of the  foreign currency revaluation transactions:
    -   **Posting** – The posting profile of the customer transaction is used.
    -   **Select** – Enter the posting profile in the **Posting profile** field.
-   **Posting profile** – If **Select** is selected in the **Use posting profile from** field, the posting profile that you enter in this field determines the posting profile of the foreign currency revaluation transactions.
-   **Financial dimensions** – The financial dimensions that are posted on the accounting entries of the foreign currency revaluation transactions. The financial dimensions are not validated against the rules for the account structure. The account structure that was in place at the time the invoices were posted might not be the same as the rules that were in place when the revaluation was completed. There is no option to select specific financial dimensions in the revaluation process, so the account structure validation is skipped.  
    -   **None** – No financial dimensions are posted. If you have a required financial dimension in your account structure, the revaluation process is still run and creates accounting entries that have no financial dimensions. You will receive a warning message first, so that you can cancel the revaluation.
    -   **Table** – The financial dimensions of the customer account or vendor account are posted on the foreign currency revaluation transactions.
    -   **Posting** – The financial dimensions of the transaction that is being revalued are posted on the foreign currency revaluation transactions. By default, the financial dimensions from the original transaction's AR/AP ledger account will be used for the revaluation transaction's AR/AP main account, and the financial dimensions from the original transaction's expense/asset/revenue ledger account will be used for the revaluation transaction's unrealized gain/loss main account.

> [!NOTE]
> Exchange gain or loss isn't aggregated. At the time of settlement, the unrealized gain or loss for each open transaction should be reversed to recalculate any realized gain or loss. If the total gain or loss is posted to the general ledger, it isn't possible to reverse per transaction.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
