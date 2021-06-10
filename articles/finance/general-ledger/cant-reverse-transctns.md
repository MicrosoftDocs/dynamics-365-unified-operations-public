---
# required metadata

title: Why can’t I reverse this transaction? 
description: This topics describes multiple reasons why transactions can't be reversed as well as listing solutions. 
author: kweekley
ms.date: 06/12/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2021-06-12
ms.dyn365.ops.version: 10.0.14

---

# Why can’t I reverse this transaction?

[!include [banner](../includes/banner.md)]

This topics describes multiple reasons why transactions can't be reversed as well as listing solutions. 

## Symptom

Organizations may encounter situations where they have posted a transaction that they need to reverse.  Occasionally the system will prevent them from reversing these transactions, which leads to two questions:

- Why can’t I reverse this transaction?  
- And how does the Mass reversal feature affect this?

## Resolution

Transactions must meet specific criteria to be reversed. The validation for each module area is provided below. This document is focused on transactions within Finance but some of the concepts and validation can be applied to other areas, such as Supply chain management. 

Turning on the **Mass reversal for multiple documents** feature (referred to as the Mass reversal feature) in the **Feature management** workspace impacts how many transactions can be reversed and where the transactions can be reversed from.  Turning this feature on does two things:

- Allows more than one transaction to be reversed at the same time. Before this feature, each transaction had to be reversed one at a time. Mass reversal lets you select and reverse multiple transactions from the journal each one was posted from, or from the **Voucher transactions** page, assuming the individual transactions could be reversed before the Mass reversal feature was turned on.
- Allows reversal of subledger transactions from the journal (General journal) or Voucher transactions instead of requiring reversal from the subledger page. For example, previously a vendor invoice journal could only be reversed from the **Vendor transactions** page.  Now the invoice journal can also be reversed from the ledger through the journal, or from the **Voucher transactions** page. 
Turning on the Mass reversal feature does *not* do the following:
- Allow more types of transactions to be reversed. If a transaction type couldn’t be reversed before, the transaction still can’t be reversed, even after the Mass reversal feature is turned on.  For example, Purchase order vendor invoices can’t be reversed, regardless of whether or not the Mass reversal feature has been turned on. 
For more information about the Mass reversal feature, see [Reverse journal posting](reverse-journal-posting.md). 

### General ledger

General ledger adjustments are entered with only ledger accounts, and therefore only update General ledger.  

If Mass reversal is not enabled, most general ledger adjustments can be individually reversed from the **Transactions for [main account]** page for the ledger (LedgerTransAccount), which shows each transaction that’s been posted to the main account. The page is typically opened from the **Trial balance list** page, or by clicking the **Transactions** button on the **Voucher transactions** page. 

If the Mass reversal feature is turned on, one or more General ledger vouchers can now be reversed from the **Voucher transactions** page, and the journal the transaction was posted from. 

The exceptions to this are General ledger foreign currency revaluation, consolidation, and year-end close transactions. Those transactions are reversed from the pages they were entered on.

Vouchers can’t be reversed for the following reasons.

- General journal
  - The transaction’s accounting date is in a fiscal period that is not open.
    - If the transaction allows entry of a reversing date, you can reverse the transaction by changing the reversing date to a date in an open period.  
- The transaction’s accounting date is in a closed fiscal year. 
    - The year-end close can be reversed and then the transaction can be reversed. However, it might be faster to enter a reversing transaction manually in an open period. If a new transaction is posted into the closed year (but an open period), the year-end close will need to be run again. 
- The transaction is in the process of being reversed.
    - After the reversal is complete, a reversed transaction can be reversed again which amounts to reversing the reversal.
- One or more lines of the transaction have been ledger-settled (which means the record exists in the LedgerTransSettlement table) on the **Ledger settlements** page (**General ledger > Periodic tasks > Ledger settlements**). 
    - A ledger settlement can be reversed, which will allow the voucher to be reversed.
  - Intercompany
   - The transaction is an intercompany transaction.
   - The transaction is not an intercompany transaction but is posted to a due-to or due-from the main account that was defined on the **Intercompany setup** page.
  - The transaction is a sub-transaction of an accrual.
- Foreign currency revaluation
  - The transaction was posted in a fiscal period that’s now on hold or permanently closed. 
  - If your organization’s business processes permit it, the period can be reopened, and the reversal can be completed.
- Consolidated
  - The transaction was posted in a fiscal period that’s now on hold or permanently closed.
  - If your organization’s business processes permit it, the period can be reopened, and the reversal can be completed.
- Year-end close
  - The year-end close transactions (both closing and opening transactions) can be reversed in the following ways. 
   - If the General ledger year-end close enhancements haven’t been enabled in the **Feature management** workspace, the opening and closing transactions can be reversed by choosing the **Undo previous close** option in the **Year-end close** dialog.
	If the General ledger year-end close enhancements have been enabled, the opening and closing transactions can be reversed by choosing the company and fiscal year record that were created for the year-end close on the **Year-end close** page, then click the **Reverse year-end close** button. 

 
## Accounts payable

Multiple transaction types update the Accounts payable subledger, including vendor invoices, vendor invoice journals, and expense reports.

If the Mass reversal feature has not been enabled, transactions can be reversed individually through either the **Vendor transactions** page for invoices or the **Bank account** page for check payments. 

If the Mass reversal feature has been enabled, one or more accounts payable transactions can also be reversed from the **Voucher transactions** page and the journal it was posted from. Note that vendor payments still can only be reversed from the bank account. Also note that the **Vendor transactions** page still cannot be reversed from the Transactions for (main account) page for the ledger, but they can be reversed from the **Voucher transactions** page. 

Note that some transactions can’t be reversed at all, such as Purchase order vendor invoices and electronic vendor payments. 

Vouchers can’t be reversed for the following reasons.
- A transaction’s accounting date is in a closed fiscal period. 
  - If the transaction allows you to enter a reversing date, the transaction can still be reversed by changing the reversing date to an open period. 
- The transaction’s accounting date is in a closed fiscal year. 
  - The year-end close can be reversed, and then the transaction can be reversed. However, it might be faster to simply enter a reversing transaction manually in an open period. If a new transaction is posted to an open period within a closed year, the year-end close will need to be run again. 
- The transaction’s subledger journal entry hasn’t yet been transferred to General ledger. This is relevant to non-Purchase order vendor invoice.
  - Use the **Subledger journal entries not yet transferred** page (**General ledger > Periodic tasks > Subledger journal entries not yet transferred**) to transfer the entry to General ledger. When the transfer is complete, the non-Purchase order vendor invoice can be reversed from the **Vendor transactions** page.
- Settlement
  - The transaction (such as an invoice or payment) is marked for settlement.
  - The transaction is settled.
  - This can be verified on the **Vendor transactions** page by selecting **View settlements** button or selecting **Settlement and selecting – Settlement history** from the menu. Settlement can be reversed also from the **Vendor transactions** page by selecting **Settlement > Undo settlement** if one of the transactions must be reversed.
- The voucher contains more than one subledger transaction that was entered in the same voucher number. (This is an issue with the One voucher feature For more information, see [One voucher](../general-ledger/one-voucher.md)).
- The invoice has not been approved. 
  - This refers to the **Approval** button on the invoice, rather than approval through the workflow process. This option is used to prevent an invoice from being paid, typically for vendor invoice register invoices. 
- The transaction is in the invoice pool.
  - Invoices in the pool can instead be reversed through the cancelation process on the Invoice approval journal page. 
- The transaction has a parent invoice that has been corrected (Indian localization).
- The transaction has a promissory status of invoice remitted.
- The transaction is used for a partial tax settlement.
- The transaction contains a vendor account but is being reversed from the wrong page, such as from the Transactions for (main account) page. 
  - As described above, certain subledger transactions can only be reversed from specific pages, even when the **Mass reversals** feature has been turned on. 
- The following transaction types can’t be reversed:
  - Foreign currency revaluation
  - Unlike General ledger foreign currency revaluation, foreign currency revaluations in Accounts receivable and Accounts payable can’t be reversed. Instead, the revaluation needs to be run again using the invoice date, which is similar to reversing the previous revaluation because it uses the exchange rate from the date of the invoice.  Note that this will not *reverse* the same amount if the exchange rate was modified from the default entry on the invoice.
  - Vendor invoice (with a purchase order)
  - Promissory note
  - Bank letter of credit export shipment

## Accounts receivable

A number of transaction types update Accounts receivable subledgers, including customer invoices from sales order, customer invoices entered through the general journal, free text invoices, customer payments, and write offs. If the Mass reversal feature hasn’t been turned on, transactions are reversed individually through either the **Customer transactions** page for invoices, or the **Bank accounts** page for deposits. 

If Mass reversal is enabled, one or more accounts receivable transactions can also be reversed from Voucher transactions and the journal from which it posted. Note that deposits still can only be reversed from the bank account and Free text invoices from the originating page (if the feature is enabled to allow corrections). Also note that customer transactions still can’t be reversed from the Transactions for (main account) page for the ledger, but they can be reversed from the **Voucher transactions** page. 

Note that some transactions can’t be reversed, such as sales orders, customer invoices, or write offs. 

Vouchers can’t be reversed for the following reasons.

- The transaction’s accounting date is in a closed fiscal period.
  - If the transaction supports entry of a reversing date, the transaction can still be reversed by changing the reversal date to an open period. 
- The transaction’s accounting date is in a fiscal year that has been closed. 
  - The year-end close can be reversed and then the transaction can be reversed, but it might be faster to simply enter a reversing transaction manually in an open period. If a new transaction is posted into the closed year (but an open period), the year-end close will need to be run again. 
- The transaction contains more than one subledger transaction entered in the same voucher number (a One voucher issue).
- Settlement
  - The transaction (such as an invoice or payment) is marked for settlement.
  - The transaction (such as an invoice or payment) is settled.
  - This can be verified on the Customer transactions page by selecting View settlements or Settlement – Settlement history. Settlement can also be reversed from the **Customer transactions** page by clicking the **Settlement** button, and then  selecting **Undo settlement** from the menu, if one of the transactions must be reversed.  
- The transaction has not been approved. 
  - This refers to  **Approval** option on voucher lines, rather than approval through the workflow process.  Withholding approval on vouchers lines is used to prevent an invoice from being paid. This option is typically used in Accounts payable but is available also for Accounts receivable invoices that have been entered through journals. 
- The transaction has a parent invoice which has been corrected. (Indian localization)
- The transaction contains a customer account but is being reversed from the wrong page, such as the **Transactions for (main account)** page.
  - As described above, certain subledger transactions can only be reversed from specific pages, even when the **Mass reversals** feature has been turned on. 
- The following types of transactions can’t be reversed:
- Foreign currency revaluations.
  - Unlike the currency revaluation in General ledger, currency revaluations in Accounts receivable and Accounts payable can’t be reversed. Instead, the revaluation needs to be run again using the invoice date, which is similar to reversing the previous revaluation because it uses the exchange rate from the invoice’s date. Note that this won’t reverse the same amount if the exchange rate was modified from the default rate on the invoice.
- Bills of exchanges
- Cash register transactions
- Advanced adjustments
- Interest notes
- Collection letters
- Adjusted tax withholding
- Bank letters of credit export shipments

### Bank and cash management

A number of transaction types update the Bank subledger, such as vendor payments, customer payments, and bank transfers, through the general journal.

If the Mass reversal option has not been enabled, transactions are individually reversed through the **Bank accounts** page, for checks and deposits, or the **Customer transactions** page for customer payments. 

If the Mass reversal feature has been turned on, one or more Accounts receivable transactions can also be reversed from the **Voucher transactions** page and the journal it was posted from. Note that deposits still can only be reversed from the **Bank account** page. Also note that bank transactions still cannot be reversed from the ledger using the **Transactions for (main account)** page, but they can be reversed from the **Voucher transactions** page. 

Note that some transactions can’t be reversed, such as electronic vendor payments. 

Vouchers can’t be reversed for the following reasons:

- The transaction’s accounting date is in a closed fiscal period.
  - If the transaction allows you to enter a reversing date, you can still reverse it by entering a reversal date that’s in an open period. 
- The transaction’s accounting date is in a closed fiscal year. 
  - The year-end close can be reversed and then the transaction can be reversed. However, it might be faster to enter a reversing transaction manually in an open period. If a new transaction is posted into an open period within the closed year, you’ll need to close the year again. 
- Settlement
  - The transaction (payment) is marked for settlement.
  - The transaction (payment) is settled.
  - You can verify the settlement on the Customer transactions page by selecting View settlements or by clicking the **Settlement**, and then selecting **Settlement history** from the menu. Settlement can be reversed also from the **Customer transactions** page by clicking the **Settlement** button, and then selecting **Undo settlement** from the menu, if one of the transactions must be reversed. 
- The transaction contains more than one subledger transaction entered in the same voucher number (a One voucher issue).
- If the transaction is related to bridging payment, then the reversal will be prevented.
  - If the bridged payment needs to be reversed, the payment must first be cleared from the bridging account to the bank, and then the payment can be reversed (assuming it meets the other validation criteria). 
- The transaction contains a Bank account but is being reversed from the **Transactions for (main account)** page, or from the wrong subledger such as Accounts receivable or Accounts payable.
  - As described above, certain subledger transactions can only be reversed from specific pages, even if the **Mass reversals** feature has been turned on. 
- Bank foreign currency cannot be reversed out of date order.  
  - For example, if you ran the revaluation in March and April, the April revaluation must be reversed before the March revaluation can be reversed. 

## Fixed assets

A number of transaction types update the fixed asset subledger, such as acquisitions, or depreciation.

If the Mass reversal feature hasn’t been turned on, transactions are reversed individually. Depending on the transaction type, they can be reversed on the **Vendor transactions** page, the ** Fixed asset transactions** page or from **Liability transactions** page in Asset leasing. 

If the Mass reversal feature has been turned on, one or more Fixed asset transactions can also be reversed from the **Voucher transactions** page in the journal it was posted from. 

Vouchers can’t be reversed for the following reasons.

- The transaction’s accounting date is in a closed fiscal period.
  - If the transaction supports entry of a reversing date, the transaction can still be reversed by changing the reversal date to an open period. 
- The transaction’s accounting date is in a fiscal year that has been closed. 
  - The year-end close can be reversed and then the transaction can be reversed, but it might be faster to simply enter a reversing transaction manually in an open period. If a new transaction is posted into an open period within the closed year, you’ll need to close the year again. 
- Acquisitions
  - If the acquisition occurred on a Purchase order vendor invoice.
  - The reversal must be done by entering a vendor credit note.
  - If the acquisition occurred on a project transaction.
  - The acquisition cannot be reversed after depreciation is posted for the asset. The depreciation should be reversed first to be able to reverse the acquisition. 
  - If the status of the value model or depreciation book for a fixed asset is not open, the transaction can’t be reversed.
- Disposals
  - The disposal is done using a free text invoice.  
  - The correction of a free text invoice is prevented if it contains a fixed asset. But note that if the disposal is done through a journal, it can be reversed from the fixed asset. 
  - If the status of the value model or depreciation book for a Fixed Asset is not “open”, the transaction cannot be reversed.
- Depreciation
  - The depreciation *can* be reversed if subsequent depreciation is also posted, but a warning is given since this is not a best practice. 
  - If the status of the value model or depreciation book for a fixed asset is not “open,” the transaction can’t be reversed.
- Transactions (or reverse transactions) exist for a certain asset and asset book for the voucher’s transaction date or later.
- The transaction contains an Asset account but is being reversed from the **Transactions for (main account)** page, or from the wrong subledger such as Accounts receivable or Accounts payable.
  - As described above, certain subledger transactions can only be reversed from specific pages, even if the Mass reversal feature has been turned on. 
o	If an acquisition occurs on a non-Purchase order vendor invoice or a vendor invoice journal, the acquisition can be reversed only from the **Vendor transactions** page in Accounts payable. 
If an acquisition occurs from Asset leasing, it can be reversed from the Asset leasing module using the **Liability transactions** page.
