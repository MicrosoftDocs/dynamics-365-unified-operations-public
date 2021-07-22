---
# required metadata

title: Why can’t I reverse this transaction? 
description: This topics describes multiple reasons why transactions can't be reversed as well as listing solutions. 
author: kweekley
ms.date: 07/21/2021
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
ms.search.validFrom: 2021-07-21
ms.dyn365.ops.version: 10.0.20

---

# Why can’t I reverse this transaction?

[!include [banner](../includes/banner.md)]

This topics describes multiple reasons why transactions can't be reversed as well as listing solutions. 

## Symptom

Organizations may encounter situations where they have posted a transaction that they need to reverse. Occasionally the system will prevent them from reversing these transactions, which leads to two questions:

- Why can’t I reverse this transaction?  
- And how does the Mass reversal feature affect this?

## Resolution

Transactions must meet specific criteria to be reversed. The validation for each module area is provided below. This topic focuses on transactions within Finance but some of the concepts and validation can be applied to other areas, such as Supply chain management. 

Where a transaction is reversed may also impact whether or not it can be reversed. For example, a vendor payment (posted as a check) can only be reversed from the bank accounts’ transaction page, under **Checks**. It can't be reversed from the General ledger on the Voucher transaction page. Turning on the **Mass reversal for multiple documents** feature (referred to as the Mass reversal feature) in the **Feature management** workspace impacts how many transactions can be reversed and where the transactions can be reversed from.  Turning this feature on does two things:

- Allows more than one transaction to be reversed at the same time.  Before this feature, each transaction had to be reversed one at a time.  This feature allows more than one transaction, for some types of transactions, to be selected and reversed from the journal it was posted or from Voucher transactions, assuming the individual transactions could be reversed before enabling the feature.

- Allows reversal of *some* subledger transactions from the journal (General journal) or Voucher transactions instead of requiring reversal from the subledger page. For example, previously a vendor invoice journal could only be reversed from Vendor transactions. Now the invoice journal can also be reversed from the ‘General ledger’ side through the journal or Voucher transactions. But this isn’t true for all types of transactions, as defined in each section. 

Turning on the Mass reversal feature does *not* allow more types of transactions to be reversed. If a transaction type couldn’t be reversed before, the transaction still can’t be reversed, even after the Mass reversal feature is turned on. For example, Purchase order vendor invoices can’t be reversed, regardless of whether or not the Mass reversal feature has been turned on. 

For more information about the Mass reversal feature, see [Reverse journal posting](reverse-journal-posting.md). 

### General ledger

General ledger adjustments are entered with only ledger accounts, and therefore only update General ledger.  

If Mass reversal feature isn't turned on, most general ledger adjustments can be individually reversed from the **Transactions for [main account]** page for the ledger (LedgerTransAccount), which shows each transaction that’s been posted to the main account. The page is typically opened from the **Trial balance list** page, or by clicking the **Transactions** button on the **Voucher transactions** page. 

If the Mass reversal feature is turned on, one or more General ledger vouchers can now be reversed from the **Voucher transactions** page, and the journal the transaction was posted from. 

The exceptions to this are General ledger foreign currency revaluation, consolidation, and year-end close transactions. Those transactions are reversed on the pages that the year-end close was run from.

Transactions can’t be reversed for the following reasons.

- General journal
  - Fiscal period is on-hold or permanently closed
    - If the reversing date is in a fiscal period that is not Open, it cannot be reversed. 
    - If the transaction supports entry of a reversing date, the transaction can still be reversed by changing the reversal date to an open period.  
  - Year-end close process has been run
   - The transaction’s accounting date is in a fiscal year that has been through a year-end close. Note that a period within the fiscal year can still be open, but the transaction can't be reversed if the year-end close process has been run for the fiscal year. The fiscal year has a different status than the periods within the fiscal year. 
   - The year-end close can be reversed and then the transaction can be reversed. This solution may not be an option. It may be simpler to enter a reversing transaction manually in an open period of either the closed fiscal year or the next fiscal year, depending on the status of the fiscal close. If a new transaction is posted into an open period of the fiscal year that has been through the year-end close process, the year-end close will need to be run again. 
  - Transaction reversal is already in process
    - If the transaction is in the process of being reversed, that process must be carried through to completion. A separate reversal process can't be done. 
    - After the reversal is complete, a reversed transaction can be reversed again, which is reversing the reversal.
  - Ledger settlement
   - If one or more lines of the transaction has been ledger settled (the record exists in the LedgerTransSettlement table) through **General ledger – Periodic tasks – Ledger settlements**, it can't be reversed.
   - The ledger settlement can be reversed, which will allow the voucher to be reversed.
  - Intercompany
    - If the transaction is an intercompany transaction, it can't be reversed. 
    - The transaction is *not* an intercompany transaction but is posted to a due to or due from main account that was defined in the Intercompany setup page.
  - Accruals
   - The accrued general ledger voucher can be reversed.  This will reverse the accrued entry and all the corresponding accrual sub-transactions.
   - The individual accrual sub-transactions can't be reversed.  
- Revenue recognition journal
  - Revenue recognition transactions can't be reversed. 
  - When recognizing revenue through the Revenue recognition journal, the voucher only posts to Ledger accounts so when viewed from pages such as Voucher transactions, they appear as if they are only General ledger entries.  
- Foreign Currency Revaluation
  - Foreign currency revaluation transactions can be reversed, but only from the General ledger **Foreign currency revaluation** page that the revaluation was run from. 
  - The reversal can only be completed if it is posted into an open fiscal period.   
- Consolidation
  - Consolidation transactions can be reversed, but only from the **Consolidation transactions** page.
  - The reversal can only be completed if it is posted into an Open fiscal period.   
- Year-end close
  - The year-end close transactions (both Closing and Opening transactions) can be reversed by:
    - Choosing the **Undo previous close** option in the **Year-end close** dialog if General ledger year-end close enhancements feature hasn't been enabled.
    - Choosing the company and fiscal year record that were created for the year-end close on the **Year-end close** page, and then choosing the **Reverse year-end close** button if the General ledger year-end enhancements feature has been turned on. 
  - Note that the ‘reversal’ of the year-end close actually deletes the Closing and Opening transactions. A reversing voucher is never posted. 

## Accounts payable

Multiple transaction types update the Accounts payable subledger, including vendor invoices, vendor invoice journals, and expense reports.

If the Mass reversal feature hasn't been turned on, you can reverse transactions one at a time using either the **Vendor transactions** page for invoices, or the **Bank account** page for check payments. 

If the Mass reversal feature has been turned on, one or more Accounts payable transactions can also be reversed from the **Voucher transactions** page and the journal it was posted from. Vendor payments still can be reversed only from the bank account. Also note that the vendor transactions can't be reversed from the **Transactions for (main account)** page for the ledger. They can be reversed from the **Voucher transactions** page. 

Note that some transactions can’t be reversed at all, such as Purchase order vendor invoices and electronic vendor payments. 

### Vouchers can’t be reversed for the following reasons

- Fiscal period is on-hold or closed
  - If the reversing date is in a fiscal period that isn't open, it can’t be reversed. 
  - If the transaction supports entry of a reversing date, the transaction can still be reversed by changing the reversal date to an open period.  
- General ledger year-end close process has been run
  - The transaction’s accounting date is in a fiscal year that has been closed in General ledger. Note that a period within the fiscal year can still be open, but the transaction can’t be reversed if the year-end close process has been run for the fiscal year. The fiscal year has a different status than the periods within the fiscal year. 
  - The year-end close can be reversed, and then the transaction can be reversed. This solution may not be an option. It might be simpler to enter a reversing transaction manually in an open period of either the closed fiscal year or the next fiscal year, depending on the status of the fiscal close. If a new transaction is posted to an open period of the fiscal year that has been through the year-end close process, the year-end close will need to be run again.
- Subledger journal entry not transferred to General ledger
  - This applies only to the non-Purchse order vendor invoice. 
  - Use the **Subledger journal entries not yet transferred** page to transfer the entry to General ledger, and then the non-purchase order vendor invoice can be reversed from the **Vendor transactions** page.
- Settlement
  - The transaction (invoice, payment, etc.) is marked for settlement.
  - The transaction (invoice, payment, etc.) is settled.
    - You can verify whether a transaction has been settled, or is marked for settlement, on the **Vendor transactions** page by selecting **View settlements or Settlement – Settlement history**. 
    - You can reverse a settlement from the **Vendor transactions** page (**Settlement > Undo settlement**), if one of the transactions must be reversed.  
- The voucher contains more than one subledger transaction entered in the same voucher number (the One voucher issue).
- The invoice hasn't been approved
  - If the **Approval** check box isn’t marked on the invoice, the invoice can’t be reversed. 
    - Approval in this instance doesn't refer to approvals in the  workflow process, but rather to the **Approval** option on the invoice. This option is used to prevent an invoice from being paid, typically for vendor invoice register invoices. 
- The transaction is in the invoice pool
  - An invoice in the pool can’t be reversed directly from the **Vendor transactions** page. Invoices in the pool can instead be reversed through the cancelation process on the **Invoice approval journal** page.  
- The transaction has a parent invoice that has been corrected (Indian localization)
- The transaction has a promissory status of **Invoice remitted**.
- The transaction is used for a partial tax settlement.
- The transaction contains a Vendor account but is being reversed from the wrong page, such as from **Transactions for (main account)** page. 
  - As described above, certain subledger transactions can only be reversed from specific pages, even with the Mass reversals feature turned on. 

The following types of transactions cannot be reversed:
- Foreign currency revaluation
  - Unlike General ledger foreign currency revaluation, Accounts receivable and Accounts payable foreign currency revaluations cannot be reversed. Instead, the revaluation needs to be run again using the invoice date, which is similar to reversing the previous revaluation. Revaluing with the invoice date will use the exchange rate from the invoice’s date, essentially bring the unrealized gain or loss to zero, which is similar to a reversal. Note that this will not reverse the same amount if the default exchange rate was modified on the invoice.
- Purchase order vendor invoice
  - A credit note must be created to reverse the vendor invoice.  For more information on creating a reversing transaction, see [Create a purchase return order](../../supply-chain/procurement/tasks/create-purchase-return-order.md). 
- Promissory note
- Bank letter of credit export shipment

## Accounts receivable

A number of transaction types update Accounts receivable subledgers, including customer invoices from sales order, customer invoices entered through the general journal, free text invoices, customer payments, and writeoffs. 

If the Mass reversal feature hasn’t been turned on, transactions are reversed individually through either the **Customer transactions** page for invoices, or the **Bank accounts** page for deposits. For details on reversing a payment, see the Cash and bank management section in this topic.

If the Mass reversal feature is turned on, one or more Accounts receivable transactions can also be reversed from the **Voucher transactions** page and the journal it was posted from. Note that deposits still can be reversed only from the bank account, and free text invoices from the originating page (if the feature is enabled to allow corrections). Also note that customer transactions still can’t be reversed from the Transactions for (main account) page for the ledger. But they *can* be reversed from the **Voucher transactions** page. 

Note that some transactions can’t be reversed, such as sales orders customer invoices or writeoffs. 

### Transactions can’t be reversed for the following reasons.

- Fiscal period is On-hold or Permanently closed
  - If the reversing date is in a fiscal period that is not Open, it cannot be reversed. 
  - If the transaction supports entry of a reversing date, the transaction can still be reversed by changing the reversal date to an open period.  
- General ledger year-end close process has been run
  - The transaction’s accounting date is in a fiscal year that has been through a general ledger year-end close. Note that a period within the fiscal year can still be Open, but the transaction cannot be reversed if the year-end close process has been run for the fiscal year. The fiscal year has a different status than the periods within the fiscal year. 
  - The year-end close can be reversed and then the transaction can be reversed. This solution may not be an option. It may be simpler to enter a reversing transaction manually in an open period of either the closed fiscal year or the next fiscal year, depending on the status of the fiscal close. If a new transaction is posted into an open period of the fiscal year that has been through the year-end close process, the year-end. 
- Subledger journal entry not transferred to general ledger
  - This is relevant to only free text invoices. 
  - Use the “Subledger journal entries not yet transferred” page to transfer the entry to GL and then the free text invoice can be reversed if the Corrections functionality is enabled. This will allow the invoice to be corrected or reversed. 
- Settlement
  - The transaction (invoice, payment, etc.) is marked for settlement.
  - The transaction (invoice, payment, etc.) is settled.
    - This can be verified on the **Customer transactions** page by selecting **View settlements** or **Settlement – Settlement history**. 
    - Settlement can be reversed also from the **Customer transactions** page – Settlement – Undo settlement** if one of the transactions must be reversed.  
- The transaction contains more than one subledger transaction entered in the same voucher number (One voucher issue).
- Invoice has not been approved
  - If the Approval box isn’t marked on the invoice, it cannot be reversed.
    - Approval in this instance doesn't refer to approvals in the  workflow process, but rather to the **Approval** option on the voucher lines. This option is used to prevent an invoice from being paid. This option is typically used in Accounts payable but is available also for Accounts receivable invoices entered through journals. 
- The transaction has a parent invoice which has been corrected. (Indian localization)
- The transaction contains a Customer account but is being reversed from the "wrong" page, such as from the **Transactions for (main account)** page.
  - As suggested in the preceding point, certain subledger transactions can only be reversed from specific pages, even when the Mass reversal feature is turned on. 

The following types of transactions can't be reversed:

- Foreign currency revaluation
  - Unlike General ledger foreign currency revaluation, Accounts receivable and Accounts payable foreign currency revaluation cannot be reversed. Instead, the revaluation must be run again using the invoice date, which is similar to reversing the previous revaluation. Revaluing with the invoice date will use the exchange rate from the invoice’s date, essentially bringing the unrealized gain or loss to zero, which is similar to a reversal. Note that this will not reverse the same amount if the default exchange rate was changed on the invoice.
- The transaction has adjusted tax withholding
- Sales order customer invoice
  - A credit note or return must be created to reverse the transaction. For information on how to create the reversing transaction, see [Sales returns](../../supply-chain/warehousing/sales-returns.md).
- Bill of exchange
- Cash register transaction
- Advanced adjustment
- Interest note
- Collections letter
- Bank letter of credit
- Export shipment
- Revenue recognition journal
  - When you recognize revenue through the Revenue recognition journal, the vouchers are posted to Ledger accounts so they appear as if they are only General ledger entries. These entries can't be reversed because the revenue schedule wouldn't be reopened to recognize the revenue again. 

## Cash and bank management

A number of transaction types update the Bank subledger, including vendor payments, customer payments, and bank transfers, through the general journal.

If the Mass reversal option hasn't been turned on, transactions can be reversed individually through the **Bank accounts** page, for checks and deposits, or the **Customer transactions** page for customer payments. 

If Mass reversal is enabled, one or more payments transactions can also be reversed from **Voucher transactions** and the journal from which it posted. Note that deposits still can only be reversed from the bank account. Also note that bank transactions still cannot be reversed from the ledger Transactions for (main account) page, but they can be reversed from the **Voucher transactions** page.  

Note that some transactions can’t be reversed, such as electronic vendor payments. 

### Transactions can’t be reversed for the following reasons:

- Fiscal period is On-hold or Permanently closed
  - If the reversing date is in a fiscal period that is not Open, it can't be reversed. 
  - If the transaction supports entry of a reversing date, the transaction can still be reversed by changing the reversal date to an open period.  
- General ledger year-end close process has been run
  - The transaction’s accounting date is in a fiscal year that has been through a general ledger year-end close. Note that a period within the fiscal year can still be Open, but the transaction can't be reversed if the year-end close process has been run for the fiscal year. The fiscal year has a different status than the periods within the fiscal year. 
  - The year-end close can be reversed and then the transaction can be reversed. This solution may not be an option. It may be simpler to enter a reversing transaction manually in an open period of either the closed fiscal year or the next fiscal year, depending on the status of the fiscal close. If a new transaction is posted into an open period of the fiscal year that has been through the year-end close process, the year-end close will need to be run again.
- Settlement
  - The transaction (payment) is marked for settlement.
  - The transaction (payment) is settled.
    - This can be verified on the **Vendor transactions** or **Customer transactions** page by selecting **View settlements** or **Settlement > Settlement history**. 
    - Settlement can be reversed also from the **Vendor transactions** or **Customer transactions** page, **Settlement > Undo settlement** if one of the transactions must be reversed. 
- The transaction contains more than one subledger transaction entered in the same voucher number (One voucher issue).
- Bridged transactions
  - If the transaction is related to bridging payment, it cannot be reversed.
  - If the bridged payment needs to be reversed, the payment must first be cleared from the bridging account to the bank, and then the payment can be reversed (assuming it meets the other validation criteria). 
- The transaction contains a Bank account but is being reversed from **Transactions for (main account)** page or from the wrong subledger such as Accounts receivable or Accounts payable.  
  - As the preceding point suggests, certain subledger transactions can only be reversed from specific pages, even then the Mass reversals feature has been turned on. 
- Bank foreign currency revaluation
  - Bank foreign currency revaluation can be reversed, but it may be prevented if you're complete the reversal steps out of chronological order. For example, if you ran the revaluation in March and April, the March revaluation cannot be reversed until the April revaluation is reversed first. 

The following types of transactions can't be reversed:
- Vendor payments made as Electronic (EFT)
- Promissory notes
- Bills of exchange

## Fixed assets

A number of transaction types update the Fixed assets subledger, including acquisitions and depreciation.

If the Mass reversal feature hasn’t been turned on, transactions are reversed individually. Depending on the transaction type, they can be reversed in the **Vendor transactions** page, **Fixed asset transactions** page or from Asset leasing.

If the Mass reversal feature has been turned on, one or more Fixed asset transactions can also be reversed from the **Voucher transactions** page in the journal it was posted from. 

### Transactions can’t be reversed for the following reasons.

- Fiscal period is on-hold or permanently closed
  - If the reversing date is in a fiscal period that is not open, it can't be reversed. 
  - If the transaction supports entry of a reversing date, the transaction can still be reversed by changing the reversal date to an open period.  
- The General ledger year-end close process has been run
  - The transaction’s accounting date is in a fiscal year that has been closed in General ledger. Note that a period within the fiscal year can still be open, but the transaction can't be reversed if the year-end close process has been run for the fiscal year. The fiscal year has a different status than the periods within the fiscal year. 
  - The year-end close can be reversed and then the transaction can be reversed. This solution may not be an option. It might be simpler to manually enter a reversing transaction in an open period of either the closed fiscal year or the next fiscal year, depending on the status of the fiscal close. If a new transaction is posted in an open period of the fiscal year that has been through the year-end close process, the year-end close must be run again. 
- Acquisitions  
  - If the acquisition occurred on a purchase order vendor invoice, the reversal must be done by entering a vendor credit note. For information on entering the reversal transaction, see [Create a purchase return order](../../supply-chain/procurement/tasks/create-purchase-return-order.md).
  - If the acquisition occurred on a project transaction.
  - The acquisition cannot be reversed after depreciation is posted for the asset. The depreciation should be reversed first to be able to reverse the acquisition. 
  - If the status of the value model or depreciation book for a fixed asset isn't open, the transaction can't be reversed.
- Disposals
  - The disposal is done through a free text invoice.   
    - The correction of a free text invoice is blocked if it contains a fixed asset. But note that if the asset is disposed of through a journal, the free text invoice can be reversed from the fixed asset record. 
  - If the status of the value model or depreciation book for a fixed Asset is not open, the transaction can't be reversed.
- Depreciation
  - The depreciation *can* be reversed if subsequent depreciation is also posted, but you'll receive a warning because this isn't a best practice. 
  - If the status of the value model or depreciation book for a fixed asset is not “open”, the transaction cannot be reversed.
- Transactions (or reverse transactions) exist for a certain asset and asset book for the voucher’s transaction date or later. 
- The transaction contains an Asset account but is being reversed from Transactions for (main account), or from the "wrong" subledger such as Accounts receivable or Accounts payable.
  - As the preceding point suggests, certain subledger transactions can only be reversed from specific pages, even when the Mass reversal feature is turned on. 
  - If an acquisition occurs on a non-purchase order vendor invoice or a vendor invoice journal, the acquisition can only be reversed from the **Vendor transactions** page in Accounts payable. 
  - If an asset is acquired from Asset leasing, it can be reversed from the **Liability transactions** page in Asset leasing module liability transaction.
